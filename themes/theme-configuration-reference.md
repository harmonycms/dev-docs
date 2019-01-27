# Theme configuration reference

#### Templating

The ThemeBundle provides a number of functions to use in templates.

**Twig Extensions**

| Twig Function | Templating Helper | Arguments | Explanation |
| :--- | :--- | :--- | :--- |
| `asset_theme` | _getThemeUrl_ | string $path, string $packageName = null | A Twig function to get assets from a theme path. |
| `asset` | _getAssetUrl_ | string $path, string $packageName = null | Override default function, check asset exists in current active theme, otherwise fallback to original path. |

| Twig Filter | Templating Helper | Arguments | Explanation |
| :--- | :--- | :--- | :--- |
| `theme` | _getThemeUrl_ | string $path, string $packageName = null | A Twig filter to get assets from a theme path. |

