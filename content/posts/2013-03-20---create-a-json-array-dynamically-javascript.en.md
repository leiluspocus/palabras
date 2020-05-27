---
title: 'Create a JSON array dynamically Javascript'
date: "2013-03-20T23:21:59+00:00"
template: post
slug: /en/create-a-json-array-dynamically-javascript/
draft: false
category: Snippets
tags:
  - json
---

Using only Javascript 

```javascript 
var res = [];
for (var i = 0; i < results.rows.length; i++) {
    res[i] = {};
    res[i]['id'] = "foo";
    res[i]['name'] = "woohoo";
}
```
