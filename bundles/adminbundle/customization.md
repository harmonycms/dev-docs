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

{% hint style="danger" %}
Be very careful, some bundles, extensions or themes use FOSJSRouting who provide a default `fos_js_routes.json` file including the admin prefix. If you have to change the admin prefix, you will probably need to dump the routing js configuration.
{% endhint %}

## Customize content

This bundle is shipped by default with the free version of [AdminCAST Bootstrap 4 Admin Template](http://admincast.com).  
If you are currently developing an extension for HarmonyCMS and are designing some pages to match with the admin interface, you should check the [demo](http://admincast.com/admincast/preview/html/) version of the template to take some examples.

