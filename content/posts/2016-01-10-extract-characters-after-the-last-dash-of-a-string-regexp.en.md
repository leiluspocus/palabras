---
title: 'Extract characters after the last dash of a String RegExp'
date: "2016-01-10T16:51:21+00:00"
template: post
draft: false
slug: /en/extract-characters-after-the-last-dash-of-a-string-regexp/
category: Snippets
tags:
  - php
  - regexp
---
I wanted to extract characters after the last dash of a string. Regular expression are such a powerful tool to use in these cases. Here&rsquo;s the one I needed for my problem :

```(\w+)[^-]*$```

Please note that with PHP, you need to use the preg_match method and surround the regexp with slashes.

```php
preg_match ('/(\w+)[^-]*$/', 'cgo3020-red-xs', $results); // returns xs in $results[0]
```

Here&rsquo;s a pretty convenient tool to test your regexp:  https://regex101.com/
