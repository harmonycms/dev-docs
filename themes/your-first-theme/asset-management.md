---
description: 'Manage your theme''s assets, such as css, javascripts, images, ...'
---

# Chapter 4. Asset Management

When creating a new theme, any assets \(css, javascript, images, ...\) must be set into the `assets` directory of your theme.  
However you need to install this assets inside the `public` directory to allow Symfony to be able to access them.

## Installation

You can use the `theme:assets:install` command to install theme web assets under a public directory as shown bellow:

```bash
php bin/console theme:assets:install --symlink
```

