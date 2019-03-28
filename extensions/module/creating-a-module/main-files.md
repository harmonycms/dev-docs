# Chapter 1. The main files

This section creates and enables a new module to show there are only a few steps required. The new module is called **AcmeTestModule**, where the `Acme` portion is just a dummy name that should be replaced by some "vendor" name that represents you or your organization \(e.g. ABCTestModule for some company named `ABC`\).

## The main class

Let's start by creating file called `AcmeTestModule.php`at the root of your module project:

{% code-tabs %}
{% code-tabs-item title="AcmeTestModule.php" %}
```php
namespace Acme\Extension\TestModule;

use Harmony\Sdk\Extension\Module;

class AcmeTestModule extends Module
{
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% hint style="info" %}
The name `AcmeTestModule` follows the same standards has [Bundle naming conventions](https://symfony.com/doc/master/bundles/best_practices.html#bundles-naming-conventions).
{% endhint %}

This empty class is the only piece you need to create the new module. Though commonly empty, this class is powerful and can be used to customize the behavior of the module. When installed, the module will automatically be enabled in the next file:

{% code-tabs %}
{% code-tabs-item title="config/extensions.php" %}
```php
return [
    // ...
    Acme\Extension\TestModule\AcmeTestModule::class => ['all' => true],
];
```
{% endcode-tabs-item %}
{% endcode-tabs %}

And while it doesn't do anything yet, **AcmeTestModule** is now ready to be used.

## Composer.json

```javascript
{
  "name": "acme/test-module",
  "description": "",
  "homepage": "",
  "license": "LGPL-3.0-or-later",
  "type": "harmony-extension",
  "version": "1.0.0",
  "authors": [
    {
      "name": "David Sanchez",
      "email": "david38sanchez@gmail.com",
      "homepage": "https://harmonycms.net"
    }
  ],
  "require": {
    "php": ">=7.1.3",
    "harmony/sdk": "dev-master"
  },
  "autoload": {
    "psr-4": {
      "Acme\\Extension\\TestModule\\": ""
    }
  }
}

```

