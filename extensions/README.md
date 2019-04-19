# The Extension system

> HarmonyCMS embedded a top level extensibility principe represented the same way has Symfony Bundle but who are made to do and be used in specific cases.  
> The extension system allow to the end user to easily extend the functionality of the CMS by plugs in to the CMS core without requiring modifications to the original files.

The extensibility system design in decoupled in 3 distinct sub-extensions who can be developed and used in certains use-cases.

## Installation and activation

Extensions are represented the same way has Symfony Bundles. They are automatically installed and activated by the HarmonyFlex tool in the **extensions** directory, at the root of the user's Harmony project.

Installed extensions are enabled in the `/config/extensions.php` file:

{% code-tabs %}
{% code-tabs-item title="config/extensions.php" %}
```php
<?php

return [
    Harmony\Extension\Acme\HarmonyAcmeModule::class => ['all' => true],
];
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% hint style="info" %}
By a default HarmonyCMS application use HarmonyFlex tool. Extensions are enabled/disabled automatically for you when installing/removing them, so you don't need to look at or edit the **extensions.php** file.
{% endhint %}

## Decoupled sub-extensions

Like explain in the previous chapter, extensions divided in 3 sub-types. Each extension's type are made to representing and to be used in a specific place.

### Components

Components can be used in the front and admin areas. They can only be embedded by add-ons \(plugins, modules or themes\). However components cannot define any routes. A component must be parts of a specific type \(WYSIWYG, Carousel, …\).

### Modules

Modules are only made to add new features from the admin area. They can embed components and can define routes, compilers, … like bundles. They also can add entries in the admin menu.

### Plugins

Plugins are like Symfony Bundles, they can do the exact same things. They will be render views in the front \(theme\), define routes and embedded components. They also can have an admin interface to manage them and can add items from admin and main menus.

