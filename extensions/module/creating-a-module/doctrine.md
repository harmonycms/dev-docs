# Chapter 4. Doctrine

## Register mapping

{% code-tabs %}
{% code-tabs-item title="AcmeTestModule.php" %}
```php
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

