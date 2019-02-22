# The Extension system

The extension system allow to the end user to easily extend the functionality of HarmonyCMS.  
Extension plugs in to the HarmonyCMS core without requiring modifications to the original files.

## Installation and activation

In HarmonyCMS, an extension is represented the same way has a Symfony Bundle.  
Extensions are automatically installed by the HarmonyFlex tool in the **extensions** directory, at the root of the user Harmony's project.

Extensions used in your applications will be enabled in the `/config/extensions.php` file:

{% code-tabs %}
{% code-tabs-item title="config/extensions.php" %}
```php
<?php

return [
    
];
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% hint style="info" %}
By a default HarmonyCMS application use HarmonyFlex tool. Extensions are enabled/disabled automatically for you when installing/removing them, so you don't need to look at or edit this **extensions.php** file.
{% endhint %}

## Decoupled in sub-extensions

