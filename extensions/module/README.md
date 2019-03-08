# The Module system

A module is similar to a Symfony Bundle, but made to add new features to the admin area only.  
Modules used in your applications must be enabled the `config/extensions.php` file.

{% hint style="info" %}
By default, Harmony application use HarmonyFlex, so modules are enabled/disabled automatically for you when installing/removing them.
{% endhint %}

### What a module can do?

A module has some the ability to:

* Embed components,
* Can define controllers, routes, dependency injections, entities, forms, ...,
* Can also add entries to the admin menu only.

{% hint style="info" %}
A module can only define stuff for the admin area only. That means you need to have the package `harmony/admin-bundle` installed.
{% endhint %}

## Learn more

* [Creating a module](creating-a-module/)

