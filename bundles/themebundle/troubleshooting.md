# Chapter 2. Troubleshooting

## NoActiveThemeException

When a `NoActiveThemeException` is triggered it's because there is no active theme selected.  
To select an active theme, you have at least 2 choices.

### Using the admin bundle

If you are using the [HarmonyAdminBundle](https://marketplace.harmonycms.net/package/harmony-admin-bundle), you just need to the **Themes** page to activate an installed theme.

### Manually active theme

To manually set an `active_theme` you must define it directly in the next configuration file:

{% code-tabs %}
{% code-tabs-item title="config/packages/liip\_theme.yaml" %}
```yaml
liip_theme:
    active_theme: 'acme-theme'
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% hint style="warning" %}
In the above example this means the `acme-theme` is already installed in your application.
{% endhint %}

