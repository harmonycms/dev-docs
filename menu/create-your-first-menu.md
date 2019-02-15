# Chapter 3. Create your first menu

KNPMenuBundle provide multiple solutions to create menu easily as possible:

1. [Method a. The Easy Way](https://symfony.com/doc/master/bundles/KnpMenuBundle/index.html#method-a-the-easy-way-yay)
2. [Method b. A menu builder as a service](https://symfony.com/doc/master/bundles/KnpMenuBundle/menu_builder_service.html)
3. [Method c. A menu as a service](https://symfony.com/doc/master/bundles/KnpMenuBundle/menu_service.html)

HarmonyMenuBundle add an other way to create menu, with YAML configuration files.  
This bundle will automatically load menu declared in a file called `menu.yaml`.  
This file can be located at `config/menu.yaml`or inside any bundles at `Resources/config/menu.yaml`.

## Create new menu

Let's now create a simple menu with some links.

{% code-tabs %}
{% code-tabs-item title="config/menu.yaml" %}
```yaml
main_menu:
    tree:
        home:
            label: 'Home'
            route: index
        about:
            label: 'About'
            route: about
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% hint style="warning" %}
When creating menu item, please **DO NOT** add HTML attributes \(e.g. `class`, `id`, ...\) using the options **attributes**, **linkAttributes**, **childrenAttributes** or **labelAttributes**.  
This values must me defined inside each themes, when rendering the menu.  
See: [Chapter 4. Rendering menus](rendering-menus.md)
{% endhint %}

## Configuration reference

Here is the full reference of available configuration keys you can use to define your menu:

{% code-tabs %}
{% code-tabs-item title="config/menu.yaml" %}
```yaml
my_mega_menu:
    childrenAttributes: An array of attributes passed to the root ul tag
    tree:
        first_level_item:
            uri: "An uri. Use it if you do not define route parameter"
            route: "A symfony route without @"
            routeParameters: "an array of parameters to pass to the route"
            label: "My first label"
            order: An integer to sort the item in his level.
            attributes: An array of attributes passed to the knp item
            linkAttributes: An array of attributes passed to the a tag
            childrenAttributes: An array of attributes passed to the chidlren block
            labelAttributes: An array of attributes passed to the label tag
            display: boolean to hide the item
            displayChildren: boolean to hide the children
            roles: array of item (string roles) passed to isGranted securityContext method to check if user has rights in menu items
            extras: An array of extra parameters (for example icon img, additional content etc.)
            children: # An array of subitems
                second_level_item:
                    label: My second level
```
{% endcode-tabs-item %}
{% endcode-tabs %}

