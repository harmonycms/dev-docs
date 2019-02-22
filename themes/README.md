# The Theme system

Like defined in every CMS, HarmonyCMS provide to the end user a theming management system. Themes are supported by [LiipThemeBundle](https://packagist.org/packages/liip/theme-bundle). This bundle provides to the end user the possibility to use a theme to change the look of his website.  
On top of this bundle, [HarmonyThemeBundle](https://packagist.org/packages/harmony/theme-bundle) has been developed to pre-define the path where themes are stored, list available themes and set a current active theme. Coupled with [HarmonyAdminBundle](https://marketplace.harmonycms.net/package/harmony-admin-bundle), it's now easy for the end user to change the current active theme and even change settings for the activated theme.

## Installation and activation

In HarmonyCMS, a theme is represented the same way has a Symfony Bundle.  
Themes are automatically installed by the HarmonyFlex tool in the **themes** directory, at the root of the user Harmony's project.

By example, if you want to install the acme demo theme, you just need to execute the next command:

```bash
composer require harmony/acme-theme:dev-master
```

Themes used in your applications will be enabled in the `/config/themes.php` file:

{% code-tabs %}
{% code-tabs-item title="config/themes.php" %}
```php
<?php

return [
    App\Acme\TestTheme\AcmeTestTheme::class => ['all' => true],
];
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% hint style="info" %}
By a default HarmonyCMS application use HarmonyFlex tool. Themes are enabled/disabled automatically for you when installing/removing them, so you don't need to look at or edit this **themes.php** file.
{% endhint %}

## What's define a theme?

A theme is a set of files to change the look of a website. A valid HarmonyCMS theme is detected with the key **type** equals to **harmony-theme** from the `composer.json` file. However, like Symfony Bundles, HarmonyCMS theme contain a PHP class used to be loaded during kernel boot.

Here is the list of what a theme must and can contains:

* A theme must be located in the **themes** directory, at the root of the user Harmony's project,
* A theme has is own sub-folder `vendor/name`, in the main themes folder,
* A theme is made of template files \(.html.twig\), image files \(.jpg, .png, ...\), one or more stylesheets files \(.css, .scss, ...\), and usually JavaScript files \(.js\),
* A theme must have a `composer.json` file, used by[ Composer](https://getcomposer.org/) to install it, defines all of the theme’s meta information and of type: **harmony-theme**,
* A theme must have a main class who extends the abstract class: `\Harmony\Sdk\Theme\Theme`,
* A theme must have a preview image file, named preview, in the path: `/assets/images/preview.jpg` \(extensions supported are: jpg, jpeg, png, gif\).

## Learn more

* [Your first theme](your-first-theme/)
* [Theme inheritance](theme-inheritance.md)
* [Theme configuration reference](theme-configuration-reference.md)

