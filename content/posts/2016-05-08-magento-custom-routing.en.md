---
title: 'Magento Custom routing'
date: "2016-05-08T19:58:55+00:00"
template: post
draft: false
slug: /en/magento-custom-routing/
category: Magento
tags:
  - awesome tutorials
---
If you implemented several store views in your Magento shop (let&rsquo;s say for French and English), if you implement a new router, he will be associated to this views.

<span style="text-decoration: underline;">Ex</span>: In Magento&rsquo;s default behavior,

```shell
your-store.com/my_router # KO 
your-store.com/fr/my_router # OK 
your-store.com/en/my_router # OK
```

The solution to this problem is to implement **custom routing**. [Inchoo wrote an awesome article about it](http://inchoo.net/magento/custom-router-in-magento/).
