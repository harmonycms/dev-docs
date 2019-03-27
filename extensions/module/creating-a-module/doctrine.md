# Chapter 4. Doctrine

## Register mapping

{% code-tabs %}
{% code-tabs-item title="AcmeTestModule.php" %}
```php
<?php
namespace Acme\Extension\TestModule;

use Harmony\Sdk\Extension\Module;
use Doctrine\Bundle\DoctrineBundle\DependencyInjection\Compiler\DoctrineOrmMappingsPass;
use Doctrine\Bundle\MongoDBBundle\DependencyInjection\Compiler\DoctrineMongoDBMappingsPass;
use function class_exists;

class AcmeTestModule extends Module
{

    /**
     * Builds the extension.
     * It is only ever called once when the cache is empty.
     *
     * @param ContainerBuilder $container
     */
    public function build(ContainerBuilder $container)
    {
        // get all bundles
        $bundles = $container->getParameter('kernel.bundles');

        $mappings = [realpath(__DIR__ . '/Resources/config/doctrine-mapping') => 'Acme\Extension\TestModule\Model'];
        if (class_exists(DoctrineMongoDBMappingsPass::class) && isset($bundles['DoctrineMongoDBBundle'])) {
            $container->addCompilerPass(DoctrineMongoDBMappingsPass::createXmlMappingDriver($mappings, []));
        } elseif (class_exists(DoctrineOrmMappingsPass::class) && isset($bundles['DoctrineBundle'])) {
            $container->addCompilerPass(DoctrineOrmMappingsPass::createXmlMappingDriver($mappings));
        }
    }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Register custom types

{% code-tabs %}
{% code-tabs-item title="AcmeTestModule.php" %}
```php
<?php
namespace Acme\Extension\TestModule;

use Doctrine\DBAL\Types\Type as DoctrineType;
use Doctrine\ODM\MongoDB\Types\Type as MongoDbType;
use Harmony\Bundle\CoreBundle\Doctrine\Type\PhpEnumType;
use Harmony\Bundle\CoreBundle\Doctrine\Type\PhpOdmEnumType;
use Harmony\Sdk\Extension\Module;
use function class_exists;

class AcmeTestModule extends Module
{

    /**
     * Boots the Extension.
     *
     * @return void
     * @throws \Doctrine\DBAL\DBALException
     * @throws \Doctrine\ODM\MongoDB\Mapping\MappingException
     * @throws \Doctrine\ODM\MongoDB\MongoDBException
     */
    public function boot()
    {
        parent::boot();

        if (class_exists(DoctrineType::class) && !DoctrineType::hasType(CustomType::class)) {
            PhpEnumType::registerEnumType(CustomType::class);
        }
        if (class_exists(MongoDbType::class) && !MongoDbType::hasType(CustomType::class)) {
            PhpOdmEnumType::registerEnumType(CustomType::class);
        }
    }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

