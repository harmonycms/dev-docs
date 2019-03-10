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
      extras: { icon: 'fab fa-font-awesome' }
      route: 'acme_test_module_index'
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% hint style="info" %}
An icon can be added for each menu item, like in the above example.  
You should use icons provided by the **Font Awesome** library and available at the next url: [https://fontawesome.com/icons](https://fontawesome.com/icons?d=gallery)
{% endhint %}

{% hint style="info" %}
For more information on how to configure a menu, see the [Menu Configuration reference](../../../menu/create-your-first-menu.md#configuration-reference).
{% endhint %}

