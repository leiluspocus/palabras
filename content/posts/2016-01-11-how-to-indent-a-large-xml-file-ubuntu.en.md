---
title: How to indent a large XML file (Ubuntu)
date: "2016-01-11T15:59:23+00:00"
template: post
draft: false
slug: /en/how-to-indent-a-large-xml-file-ubuntu/
category: Productivité
tags:
  - command line interface
  - xml
---

I had to indent an extremely large XML file today. I tried to use different IDE (PHPStorm, Sublime Text 3), however the file was way too large and it took a long time to process.

Best way to do that is by using command line.

```xmllint --format input.xml -o indented-output.xml```
