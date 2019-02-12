# The Theme System

Like defined in every CMS, HarmonyCMS provide to the end user a theme management system. Themes are supported by [LiipThemeBundle](https://packagist.org/packages/liip/theme-bundle). This bundle provides to the end user the possibility to use a theme to change the look of his website.

Themes used in your applications must be enabled in the `/config/themes.php` file:

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
This is code is automatically generated from the HarmonyFlex tool. 
{% endhint %}



