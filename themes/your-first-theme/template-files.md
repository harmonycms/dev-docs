# Chapter 3. Template files

## Twig namespaces

Usually, when you refer to a template, you'll use the relative path from the main directory at the root of the theme:

```markup
{# this template is located in themes/harmony/acme-theme/layout.html.twig #}
{% extends "layout.html.twig" %}

{# this template is located in themes/harmony/acme-theme/user/profile.html.twig #}
{{ include('user/profile.html.twig') }}
```

If the application defines lots of templates and stores them in deep nested directories, you may consider using **Twig namespaces**, which create shortcuts to template directories.

In HarmonyCMS, the HarmonyThemeBundle take care of that for you! This bundle will register each themes \(activated or not\) has a Twig namespace.

In our case, the registered namespace if called `HarmonyAcmeTheme`, but you must prefix the `@` character when using it in templates \(that's how Twig can differentiate namespaces from regular paths\). Assuming there's a file called `sidebar.html.twig` in the `themes/harmony/acme-theme/` directory, you can refer to it as:

```markup
{{ include('@HarmonyAcmeTheme/sidebar.html.twig') }}
```

Execute this command to verify if your template name is correct and know which template file will be loaded:

```bash
php bin/console debug:twig @HarmonyAcmeTheme/sidebar.html.twig
```

