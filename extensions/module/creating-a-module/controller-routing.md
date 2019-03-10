# Chapter 2. Controller & Routing

## Controller

A controller is a PHP function you create that reads information from the `Request`object and creates and returns a `Response` object. To be able to add some "page" to the admin interface, you will need to create a controller with some actions, like:

{% code-tabs %}
{% code-tabs-item title="Controller/AcmeTestController.php" %}
```php
namespace Acme\Extension\TestModule\Controller;

use Symfony\Bundle\FrameworkBundle\Controller\AbstractController;
use Symfony\Component\HttpFoundation\Response;
use Symfony\Component\Routing\Annotation\Route;

/**
 * Class AcmeTestController
 * @Route("/acme-test", name="acme_test_module_")
 *
 * @package Acme\Extension\TestModule\Controller
 */
class AcmeTestController extends AbstractController
{

    /**
     * @Route("/", name="index")
     * @return Response
     */
    public function index(): Response
    {
        // ...
    }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

In this previous controller, note the `@Route("/acme-test", name="acme_test_module_")` annotation.  
This annotation define a route **path** and **name** prefixes who need to be unique for your module.

{% hint style="info" %}
By convention, the route **path** and route **name** must reflect the module's name.
{% endhint %}

### Twig namespace

Usually, when you refer to a template, you'll use the relative path from the main `Resources/views` directory at the root of your module.

However, to be able to load template files from your controller in your module, you will need to use the Twig namespace annotation. But don't worry, HarmonyExtensionBundle will register each modulesas a new Twig namespace for you!

The Twig namespace is equivalent to the base module class, here **AcmeTestModule** but, you must prefix the `@` character when using it. So to render a template in your controller, you should write codes like:

```php
return $this->render('@AcmeTestModule/index.html.twig');
```

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



