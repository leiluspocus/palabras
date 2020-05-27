---
title: 'Parsing errors JSON'
date: "2013-06-25T23:26:03+00:00"
template: post
draft: false
slug: /en/parsing-errors-json/
category: Bugs
tags:
  - javascript
  - json
  - parsing objects
---

Parsing JSON with the jQuery method ```$.parseJSON``` can be tricky to debug, specially when you&rsquo;re using a mobile device. 

Here is a list of errors I encoutered, and the reason why they were raised.

**Unexpected token u** 
The method tries to parse a undefined variable 

**Unexpected token o** 
The method tries to parse [Object object]
