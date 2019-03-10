# Chapter 5. Views

To be able to render content within the admin interface, first of all you need to extends from the **HarmonyAdminBundle** layout file, like:

```markup
{% extends '@HarmonyAdmin/default/layout.html.twig' %}
```

## Page title

```markup
{% block content_title %}
    {{ 'page-title'|trans }}
{% endblock %}
```

## Page content

```text
{% block main %}

{% endblock %}
```

## Stylesheets & Javascripts

```text
{% block head_stylesheets %}
  {{ parent() }}
  {# ... #}
{% endblock %}
```

```text
{% block body_javascript %}
  {{ parent() }}
  {# ... #}
{% endblock %}
```



