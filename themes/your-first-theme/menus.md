# Chapter 5. Menus

In HarmonyCMS, we separate the business logic \(_menu content_\) and menu rendering \(_how to display menu_\).  
When you are creating your theme, you'll need to display at some places a navigation menu, a sidebar menu, ... These menus are rendered directly in your theme views but the user who will use your theme does not have to use them all.

## Creating a simple menu

Let's see how simple it is to display a navigation menu in your theme.  
The only think you have to do is using the twig function `menu_render()` to call and display a menu with a specific name.  
By convention, you will always call the main navigation menu `main_menu` this will be easier for the end user to use the same menu with different themes.

Here is a simple example:

{% code-tabs %}
{% code-tabs-item title="index.html.twig" %}
```markup
<nav class="navbar">
  <div class="collapse navbar-collapse">
    {{ menu_render('main_menu') }}    
  </div>
</nav>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Like explain before, this code will only return the rendered markup navigation menu if the user has define a menu named `main_menu` like described in this documentation: [Create your first menu](../../menu/create-your-first-menu.md).

## Learn more

* [Customizing the rendered markup](../../menu/rendering-menus.md#customizing-the-rendered-markup)

