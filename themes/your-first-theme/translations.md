# Chapter 7. Translations

Theme's translations are managed the same way they are for whole site.  
The Translation component provided by Symfony is used to internationalize your theme.

## Translation Resource/File Names and Locations

Our own [HarmonyThemeBundle](../../bundles/themebundle/) use the same logic as Symfony to looks for message files \(i.e. translations\).  
The bundle will only check for one particular location in the current theme: the `translations/` directory.

The filename of the translation files is also important: each message file must be named according to the following path: `domain.locale.loader`and must follow some predefined rules:

* **domain**: An way to organize messages into groups \(e.g. `admin`, `navigation` or the default `messages`\);
* **locale**: The locale that the translations are for \(e.g. `en_GB`, `en`, etc\);
* **loader**: How Symfony should load and parse the file \(e.g. `xlf`, `php`, `yaml`\).

{% hint style="warning" %}
The loader can be the name of any registered loader. However, only these loader are supported for themes:

* `xlf`: XLIFF file;
* `php`: PHP file;
* `yaml`: YAML file.
{% endhint %}

The choice of which loader to use is entirely up to you and is a matter of taste. The recommended option is to use `xlf` for translations.

## Create your translation files

{% code-tabs %}
{% code-tabs-item title="translations/acme-theme.en.xlf" %}
```markup
<?xml version="1.0"?>
<xliff version="1.2" xmlns="urn:oasis:names:tc:xliff:document:1.2">
  <file source-language="en" target-language="en" datatype="plaintext" original="file.ext">
    <body>
      <trans-unit id="welcome">
        <source>welcome</source>
        <target>Build responsive, mobile-first themes on the web with the world's most popular front-end component library.</target>
      </trans-unit>
    </body>
  </file>
</xliff>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% hint style="warning" %}
Each time you create a _new_ translation resource \(or install a theme that includes a translation resource\), be sure to clear your cache so that Symfony can discover the new translation resources:

```bash
php bin/console cache:clear
```
{% endhint %}

## Use translation in templates

You can now simply use the translation in any template files of the active theme:

```markup
{{ 'welcome'|trans(domain='acme-theme') }}
```

