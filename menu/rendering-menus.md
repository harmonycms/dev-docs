# Chapter 4. Rendering menus

Once you've setup your menu, rendering it is easy. If you follow the chapter 3 to create a simple menu called `main_menu`, you can render it using the next twig function:

```markup
{{ knp_menu_render('my_mega_menu') }}
```

## Customizing the rendered markup

### Updating the template file

Currently, KnpMenu provide a standard `knp_menu.html.twig` template who is used to render each menu.

### Using YAML menu attributes

