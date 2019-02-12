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

