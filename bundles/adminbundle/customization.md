# Chapter 2. Customization

## Change path for admin interface

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

## Customize content

This bundle is shipped by default with the free version of [AdminCAST Bootstrap 4 Admin Template](http://admincast.com).  
If you are currently developing an extension for HarmonyCMS and are designing some pages to match with the admin interface, you should check the [demo](http://admincast.com/admincast/preview/html/) version of the template to take some examples.

