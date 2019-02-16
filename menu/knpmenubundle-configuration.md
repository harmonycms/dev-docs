# Chapter 1. KnpMenuBundle configuration

KnpMenuBundle came with a sensible default configuration, which is listed below.  
You can define these options if you need to change them:

{% code-tabs %}
{% code-tabs-item title="config/packages/knp\_menu.yaml" %}
```yaml
knp_menu:
    # use "twig: false" to disable the Twig extension and the TwigRenderer
    twig:
        template: KnpMenuBundle::menu.html.twig
    #  if true, enables the helper for PHP templates
    templating: false
    # the renderer to use, list is also available by default
    default_renderer: twig
```
{% endcode-tabs-item %}
{% endcode-tabs %}

