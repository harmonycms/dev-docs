---
description: Here is the list of files required for HarmonyCMS theme to be working.
---

# Chapter 2. The main files

## Composer integration

Every theme should have a default configuration located in a `composer.json` file. The type should be equals to the value `harmony-theme` so HarmonyFlex tool will be able to detect your code has an HarmonyCMS theme.

{% hint style="info" %}
By configuring Composer package along with theme we do not have to duplicate fields like `name`, `description` , `version` or `authors`. This fields are shared between Composer and HarmonyCMS.
{% endhint %}

Here is an example of a `composer.json` file for a HarmonyCMS theme:

{% code-tabs %}
{% code-tabs-item title="composer.json" %}
```text
{
    "name": "vendor/acme-theme",
    "description": "Optional description",
    "type": "harmony-theme",
    "version": "1.0",
    "authors": [
        {
            "name": "Acme theme",
            "email": "acme@theme.com",
            "homepage": "http://example.com",
            "role": "Developer"
        }
    ]
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## The main theme class

Theme SDK provides the main classes needed to create easily as possible a Theme for HarmonyCMS.  
In HarmonyCMS a theme is identical as a Bundle. Like bundles, the developer need to create a main class with a name who is following the same [Bundles naming conventions standard](https://symfony.com/doc/master/bundles/best_practices.html#bundles-naming-conventions).

Here is a simple example of main class for a theme:

```php
<?php

namespace App\Theme\AcmeTheme;

use Harmony\Sdk\Theme\Theme;

class AppAcmeTheme extends Theme
{
    const NAME        = 'App Acme';
    const DESCRIPTION = 'Acme starter theme';
}
```

