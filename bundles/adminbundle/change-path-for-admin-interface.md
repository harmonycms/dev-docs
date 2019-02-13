# Chapter 2. Change path for admin interface

By default, HarmonyCMS admin interface is accessible from the `/admin` path. This value is defined in the **prefix** option when loading the routes for HarmonyCMS.

You can change its value to meet your own requirements. Here is the default value for the admin interface:

{% code-tabs %}
{% code-tabs-item title="config/routes/harmony.yaml" %}
```yaml
_admin:
  resource: "admin"
  type: rollerworks_autowiring
  prefix: /admin
```
{% endcode-tabs-item %}
{% endcode-tabs %}

