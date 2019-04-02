# The Settings system

Settings system, allowing application users to edit some configuration and storing it in database is a common need in a variety of projects.

Settings are managed by [HarmonySettingManagerBundle](https://marketplace.harmonycms.net/package/harmony-settings-manager-bundle).

{% hint style="warning" %}
HarmonySettingManagerBundle provide a user interface who **IS NOT** enabled in HarmonyCMS.  
If you which to enable it, follow the instructions provided by the bundle.
{% endhint %}

## Domain

Domain is like a group for settings. Setting cannot exist without a domain.  
The default is named `default`, which is also always enabled. Domain can hold only one setting with the same name. Settings with the same names must be in different domains. When a setting is requested, the one from a higher priority domain will be returned.

In HarmonyCMS, domains are used to group settings by categories like the `default` is used for general settings of the CMS, when other domains are used for `extensions`or `themes`.

## Tag

## Learn more

* [Chapter 1. Quick start](quick-start.md)
* [Chapter 2. Usage](usage.md)
* [Chapter 3. Settings everywhere](settings-everywhere.md)
* [Chapter 4. Console command](console-command.md)
* [Chapter 5. Reference](reference.md)



