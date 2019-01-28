---
description: >-
  A HarmonyCMS theme is a set of files which you can edit in order to change
  the  look of your website.
---

# Structure

Here are a few important tidbits:

* All themes have their files located in the `/themes` folder, at the root of Harmony's folder.
* Each theme has its own sub-folder, in the main themes folder.
* Each theme is made of template files \(.html.twig\), image files \(.jpg, .png and such\), one or more CSS files \(.css\), and usually JavaScript files \(.js\).
* Each theme has a `composer.json` file, used by [Composer](https://getcomposer.org) to install it, defines all of the theme’s configuration and meta information.
* Each theme has a `preview` image file, located at the root of the `assets` directory. Supported extensions of this preview file are: `.jpg`, `.jpeg`, `.png`or `.gif`.

Here is its organization, which is explained further below.

```text
acme
├── assets
│   ├── css
│   │   └── main.css
│   ├── images
│   ├── javascripts
│   └── preview.jpg
├── composer.json
├── translations
│   └── messages.en.yml
└── views
    ├── index.html.twig
    └── template.html.twig
```

## Composer integration

Every theme should have a default configuration located in a `composer.json` file. The type should be equals to the value `harmony-theme` so HarmonyCMS will be able to detect your code has an HarmonyCMS theme.

{% hint style="info" %}
By configuring Composer package along with theme we do not have to duplicate fields like `name`, `description` , `version` , `type` or `authors`. This fields are shared between Composer and HarmonyCMS.
{% endhint %}

Here is an example of a `composer.json` file for a HarmonyCMS theme:

{% code-tabs %}
{% code-tabs-item title="composer.json" %}
```text
{
    "name": "vendor/acme-theme",
    "description": "Optional description",
    "type": "harmony-theme",
    "version": "1.0",
    "authors": [
        {
            "name": "Acme theme",
            "email": "acme@theme.com",
            "homepage": "http://example.com",
            "role": "Developer"
        }
    ]
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### Extra keys

{% code-tabs %}
{% code-tabs-item title="composer.json" %}
```text
{
  "extra": {
    "harmony-theme": {
      "name": "Acme demo theme",
      "description": "Extra description for Acme theme",
      "preview": "/themes/%current_theme%/preview.jpg",
      "parents": [
        "vendor/other-theme"
      ]
    }
  }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

