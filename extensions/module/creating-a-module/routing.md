# Chapter 2. Routing

## Controller

## Routing

Such as Symfony, routing is never automatically imported in HarmonyCMS extensions. If you want to include the routes from any module, then they must be manually imported from somewhere \(e.g. `Resources/config/routing.yaml`\). To load routes from controller using annotations, use the next code example:

{% code-tabs %}
{% code-tabs-item title="Resources/config/routing.yaml" %}
```yaml
controllers:
  resource: '../../Controller'
  type: annotation
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Like said before, modules are only available in the admin area. So the routes must be declared for admin area only. For that, you must load your file `routing.yaml` in a **Dependency Injection** class.

To do that, create a file called `AcmeTestExtension.php` in the **DependencyInjection** directory, and add the next code inside:

{% code-tabs %}
{% code-tabs-item title="DependencyInjection/AcmeTestExtension.php" %}
```php
namespace Acme\Extension\TestModule\DependencyInjection;

use Rollerworks\Bundle\RouteAutowiringBundle\RouteImporter;
use Symfony\Component\DependencyInjection\ContainerBuilder;
use Symfony\Component\DependencyInjection\Extension\Extension;

class AcmeTestExtension extends Extension
{
    /**
     * Loads a specific configuration.
     *
     * @param array            $configs
     * @param ContainerBuilder $container
     *
     * @throws \Exception
     */
    public function load(array $configs, ContainerBuilder $container)
    {
        $routeImporter = new RouteImporter($container);
        $routeImporter->addObjectResource($this);
        $routeImporter->import('@AcmeTestModule/Resources/config/routing.yaml', 'admin');
    }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% hint style="info" %}
## Notes

1. HarmonyCMS use the [RouteAutowiringBundle](https://packagist.org/packages/rollerworks/route-autowiring-bundle) to define an `admin` slot. This code allow the module to load it's routes directly to the `admin` slot to be only available through the `/admin` route prefix.
2. In this example, the notation `@AcmeTestModule` is the namespace of the module used to locate a resource file.
{% endhint %}



