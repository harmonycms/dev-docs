# Chapter 4. Doctrine

## Mapping

In an HarmonyCMS module, the Doctrine mapping need to be declared manually inside a configuration file.

{% hint style="warning" %}
Currently, only Doctrine ORM database and mapping are supported.  
Doctrine ODM support is planned to be added.
{% endhint %}

### ORM mapping

To enable the mapping of your entities provided by your module, you need to create a file called `doctrine.yaml` inside the **Resources/config/** directory and add some configuration like this example:

{% code-tabs %}
{% code-tabs-item title="Resources/config/doctrine.yaml" %}
```yaml
doctrine:
  orm:
    mappings:
      AcmeTestModule:
        type: annotation
        is_bundle: false
        dir: "%kernel.extension_dir%/acme/test-module/Entity"
        alias: AcmeTestModule
        prefix: Acme\Extension\TestModule\Entity
```
{% endcode-tabs-item %}
{% endcode-tabs %}

However, this configuration file need to be loaded by the Dependency Injection component.  
To do that, you will need to add some code to your **AcmeTestExtension** class, to load the `doctrine.yaml` file:

{% code-tabs %}
{% code-tabs-item title="DependencyInjection/AcmeTestExtension.php" %}
```php
namespace Acme\Extension\TestModule\DependencyInjection;

use Symfony\Component\Config\FileLocator;
use Symfony\Component\DependencyInjection\ContainerBuilder;
use Symfony\Component\DependencyInjection\Extension\Extension;
use Symfony\Component\DependencyInjection\Extension\PrependExtensionInterface;
use Symfony\Component\DependencyInjection\Loader\YamlFileLoader;

class AcmeTestExtension extends Extension implements PrependExtensionInterface
{
    // ...
    
    /**
     * Allow an extension to prepend the extension configurations.
     *
     * @param ContainerBuilder $container
     *
     * @throws \Exception
     */
    public function prepend(ContainerBuilder $container)
    {
        // Get all bundles
        $bundles = $container->getParameter('kernel.bundles');

        // Yaml loader
        $loader = new YamlFileLoader($container, new FileLocator(dirname(__DIR__) . '/Resources/config'));
        
        // Load doctrine configuration after the DoctrineBundle has been loaded 
        if (isset($bundles['DoctrineBundle'])) {
            $loader->load('doctrine.yaml');
        }
    }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% hint style="info" %}
Has you can see, you need to implement the `PrependExtensionInterface` interface to be able to use the **prepend\(\)** method to load the `doctrine.yaml` file after the **DoctrineBundle** has been loaded.

Otherwise, if you are trying to load this file in the **load\(\)** method, Symfony will throw you an exception because the **DoctrineBundle** is not yet loaded. 
{% endhint %}

