# Kernel configuration

## Parameters

### Symfony parameters

| Name | Value | Method |
| :--- | :--- | :--- |
| `kernel.project_dir` |  | `getProjectDir()` |
| `kernel.environment` | `dev` or `prod` |  |
| `kernel.debug` | `true` or `false` |  |
| `kernel.cache_dir` | /var/cache/%env% | `getCacheDir()` |
| `kernel.logs_dir` | /var/log | `getLogDir()` |
| `kernel.bundles` |  |  |
| `kernel.bundles_metadata` |  |  |
| `kernel.charset` | UTF-8 | `getCharset()` |
| `kernel.container_class` |  |  |

{% hint style="info" %}
To get the complete, updated list and description of all available parameters provided by the Symfony [Kernel](https://github.com/symfony/symfony/blob/4.2/src/Symfony/Component/HttpKernel/Kernel.php) class, see: [Configuring in the Kernel](https://symfony.com/doc/current/reference/configuration/kernel.html).
{% endhint %}

### Harmony extra parameters

| Name | Value | Method |
| :--- | :--- | :--- |
| `kernel.app_name` | Harmony |  |
| `kernel.app_version` | 1.0 |  |
| `kernel.theme_dir` | /themes | `getThemeDir()` |
| `kernel.themes` | ThemeInterface\[\] | `getThemes()` |
| `kernel.extension_dir` | /extensions | `getExtensionDir()` |
| `kernel.extensions` | ExtensionInterface\[\] | `getExtensions()` |

{% hint style="info" %}
HarmonyCMS provide an [abstract kernel class](https://github.com/harmonycms/core-bundle/blob/master/Component/HttpKernel/AbstractKernel.php) who need to be extended from by your application Kernel class.  
This class override and add some stuff to the default Kernel class provided by Symfony.
{% endhint %}

