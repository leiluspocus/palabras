---
title: 'Symfony3 Importing JS / CSS assets from a bundle in your custom templates'
date: "2017-06-30T11:50:44+00:00"
description: How to import bundle assets in a template (Symfony 3)
template: post
slug: /en/symfony3-importing-js-css-assets-from-a-bundle-in-your-custom-templates/
category: Snippets
tags:
  - symfony
---

While implementing the PrestaImage bundle in a Symfony 3 project, I had to include the assets of the bundle in my custom template file. I had first copy / paste manually the files but I thought it was not an easy / clean way to maintain these files.

### Install the assets in the public web folder

I used the magnificient CLI of Symfony :

```php bin/console assets:install web```

This command will :

1. Copy the assets files &#8211; placed under vendor/YOUR\_BUNDLE/Resources/public/js or vendor/YOUR\_BUNDLE/Resources/public/css
2. Create two folders for JS and CSS assets under web/bundles/<your_bundle>/

### Calling the assets in the template

Then you will be able to call the assets in your custom twig template using :

```html
<link rel="stylesheet" href="{{ asset('bundles/YOUR_BUNDLE/css/YOUR_ASSET_NAME.css') }}" />
```

I was surprised that there were no way to directly call the files without copying them, it would save some time and disk space.

