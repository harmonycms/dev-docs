# Chapter 5. Settings

Theme's settings are managed the same way they are for whole site.  
A custom provider for the [HarmonySettingsManagerBundle](https://marketplace.harmonycms.net/package/harmony-settings-manager-bundle) has been defined that automatically load settings from the current active theme.

## How to write settings for a theme?

In HarmonyCMS theme, settings are defined inside a file called `settings.yaml`, located at the root of your theme. However normalized data need to be written in your YAML file.  
Here is a simple example:

{% code-tabs %}
{% code-tabs-item title="settings.yaml" %}
```yaml
settings:
  - name: foo
    description: 'foo desc'
    type: bool
    data: false
    tags:
        - 'super_switch'
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% hint style="warning" %}
**Attention**  
Theme's settings cannot specify a `domain` key. The domain will always be equals to `theme` for internal use only.
{% endhint %}

