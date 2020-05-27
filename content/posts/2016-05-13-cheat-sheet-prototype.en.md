---
title: 'Prototype Cheat Sheet'
date: "2016-05-13T20:37:49+00:00"
template: post
slug: /en/cheat-sheet-prototype/
category: Cheatsheets
tags:
  - javascript
  - prototype
---

I had to deal with Prototype while working with Magento. Here&rsquo;s a little cheat sheet of some very simple stuff I had to do.

## Make an Ajax Request with parameters

```javascript
new Ajax.Request(url, {
                   method:'get',
                   params : { data1 : 'myParam' }
                   onSuccess: function(xhr){
                    console.log(xhr.responseText); 
                    var json = JSON.parse(transport.responseText);
                    }
});
```

## Change value of an input


```javascript
$('ID OF THE ELEMENT').setValue('The new value');
```

## Change data within a span tag


```javascript
$('ID OF THE ELEMENT').update('Your new data');
```
