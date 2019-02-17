# Theme inheritance

Theme inheritance enables you to easily extend themes and minimize the maintenance efforts.  
You can use an existing theme as a parent theme then create a child theme as a basis for customizations, or minor design updates.

## What is a Parent Theme?

A parent theme is a complete theme which includes all of the required files for the theme to work.  
All themes – excluding child themes – are considered parent themes.

## What is a Child Theme?

As indicated in the overview, a child theme inherits the look and feel of the parent theme and all of its components \(templates, assets, translations and settings\), but can be used to make modifications to any part of the theme. In this way, customizations are kept separate from the parent theme’s files. Using a child theme lets you upgrade the parent theme without affecting the customizations you’ve made to your site.

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

