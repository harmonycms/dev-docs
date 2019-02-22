# Chapter 3. Rendering menus

Once you've setup your menu, rendering it is easy. If you followed the [chapter 3](create-your-first-menu.md#create-new-menu) to create a simple menu called `main_menu`, you can render it using the next twig function:

```markup
{{ menu_render('main_menu') }}
```

{% hint style="warning" %}
This twig function is a helper provided by the HarmonyMenuBundle.  
It will not return an exception if the menu does not exists compared to `knp_menu_render()`
{% endhint %}

## Customizing the rendered markup

### Updating the template file

Currently, KnpMenu provide a default `knp_menu.html.twig` template who is used to render each menu.  
If you want to use a custom template to render a specific menu, you can add an option to specify the template file, like:

```text
{{ knp_menu_render('main_menu', { template: 'main_menu.html.twig' }) }}
```

### Using Twig functions

The best way to render and customize the rendered menu would be to use the built-in functions provided by our HarmonyMenuBundle.  
Here is an example on how to render a menu in a Bootstrap 4 theme:

#### Using our HarmonyMenuBundle twig function helper

```text
{{ menu_render('main_menu', {
    'currentClass': 'active',
    'childrenAttributes': { 'class': 'navbar-nav ml-auto' },
    'attributes': { 'class': 'nav-item' },
    'linkAttributes': { 'class': 'nav-link' }
}) }}
```

#### Using KnpMenu twig functions

If you prefer to use the built-in functions from KnpMenuBundle, you can have the same result, with this demo code:

```markup
{% set menu = knp_menu_get('main_menu') %}
{% do menu.setChildrenAttribute('class', 'navbar-nav ml-auto') %}
{% for child in  menu.children %}
    {% do child.setAttribute('class', 'nav-item') %}
    {% do child.setLinkAttribute('class', 'nav-link') %}
{% endfor %}
{{ knp_menu_render(menu, {'currentClass': 'active'}) }}
```

For more example, see the [official documentation](https://symfony.com/doc/master/bundles/KnpMenuBundle/index.html#rendering-menus).

