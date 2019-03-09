# Chapter 3. Menu configuration

Unlike routing, menu configuration is automatically loaded for each modules. A menu is only able to add new entries to the admin menu.

To do that, you will need to create a file called `menu.yaml` in the directory `Resources/config/` of your module. Here is an example to add a new menu item to add a link to your module:

{% code-tabs %}
{% code-tabs-item title="Resources/config/menu.yaml" %}
```yaml
admin_menu:
  tree:
    acme_test:
      label: 'Acme test'
      route: 'acme_test_module_index'
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% hint style="info" %}
For more information on how to configure a menu, see the [Menu Configuration reference](../../../menu/create-your-first-menu.md#configuration-reference).
{% endhint %}

