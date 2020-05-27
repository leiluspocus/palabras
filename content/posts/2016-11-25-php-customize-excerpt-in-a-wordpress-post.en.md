---
title: 'PHP Customize excerpt in a WordPress post'
date: "2016-11-25T09:05:28+00:00"
description: Petit code snippet pour modifier les extraits Wordpress.
template: post
slug: /en/php-customize-excerpt-in-a-wordpress-post/
category: Snippets
tags:
  - php
  - wordpress
---

```php 
add_filter( 'get_the_excerpt', 'my_new_excerpt' );
function my_new_excerpt( $format )
{
    $format = __( ' Blabla' ); // Modify this to your needs!
    return $format;
}
```

Enjoy !