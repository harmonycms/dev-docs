# Chapter 4. Rendering menus

Once you've setup your menu, rendering it is easy. If you follow the chapter 3 to create a simple menu called `main_menu`, you can render it using the next twig function:

```markup
{{ knp_menu_render('my_mega_menu') }}
```

## Customizing the rendered markup

### Updating the template file

Currently, KnpMenu provide a default `knp_menu.html.twig` template who is used to render each menu.

### Using Twig functions

The best way to render and customize the rendered menu would be to use the built-in functions provided by KnpMenuBundle itself. Here is an example on how to render a menu in a Bootstrap 4 theme:

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

