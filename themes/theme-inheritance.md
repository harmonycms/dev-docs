# Theme inheritance

Theme inheritance enables you to easily extend themes and minimize the maintenance efforts.  
You can use an existing theme as a parent theme then create a child theme as a basis for customizations, or minor design updates.

## What is a Parent Theme?

A parent theme is a complete theme which includes all of the required files for the theme to work.  
All themes – excluding child themes – are considered parent themes.

## What is a Child Theme?

As indicated in the overview, a child theme inherits the look and feel of the parent theme and all of its components \(templates, assets, translations and settings\), but can be used to make modifications to any part of the theme. In this way, customizations are kept separate from the parent theme’s files. Using a child theme lets you upgrade the parent theme without affecting the customizations you’ve made to your site.

## How inheritance works?

### Assets

The ThemeBundle will check if any asset exists in the current \(child\) theme, in case it doesn't the bundle will check from the parent theme. In case of the asset does not exists in the parent theme, the current path entered in the `asset_theme` function.

### Templates

Template inheritance is managed natively by Twig itself.  
To learn more about template inheritance, check this documentation: [How to Organize Your Twig Templates Using Inheritance](https://symfony.com/doc/current/templating/inheritance.html)

{% hint style="warning" %}
Template inheritance works only if the parent and child themes use [Twig namespaces](https://symfony.com/doc/current/templating/namespaced_paths.html)
{% endhint %}

### Translations

First of all, the ThemeBundle will try to load translations from the parent theme, if exists. It will after try to load translations from the current \(child\) theme.

By doing that, you will be able to use translations from the parent theme in your current theme.  
You will also be able to override translations in your child theme.  
To do so, you just need to create the same translation filename with the same key to override.

### Settings

## How to create a child theme

### Specify a parent theme

{% code-tabs %}
{% code-tabs-item title="themes/harmony/child-theme/HarmonyChildTheme.php" %}
```php
<?php

namespace Harmony\Theme\ChildTheme;

use Harmony\Sdk\Theme\Theme;
use Harmony\Theme\AcmeTheme\HarmonyAcmeTheme;

/**
 * Class HarmonyChildTheme
 *
 * @package Harmony\Theme\ChildTheme
 */
class HarmonyChildTheme extends Theme
{
    /** Parent theme FQDN class */
    const PARENT = HarmonyAcmeTheme::class;
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

