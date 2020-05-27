---
title: 'Connect a Gumstix via Serial Eclipse Ubuntu'
date: "2012-11-29T23:10:47+00:00"
template: post
slug: /en/connect-a-gumstix-via-serial-eclipse-ubuntu/
category: Bugs
tags:
  - gumstix
  - terminal
  - ubuntu
---

I was following this well-written <a href="http://wiki.gumstix.org/index.php?title=Eclipse_on_Gumstix_for_new_users" target="_blank">tutorial</a> to set up eclipse for my gumstix when I came to the part « Connect your gumstix » (with the Eclipse Terminal). Before setting up the terminal connection on Eclipse, make sure that Eclipse will have the permissions to access to the folder. I didn&rsquo;t have the permissions and I had the error « /dev/ttyUSB0: No such folder error » even if my board was plugged.
  
A simple **chmod** on the folder resolves the issue. Make also sure that you have an UTF-8 encoding, otherwise you gonna have a bad time while reading what&rsquo;s going on on your board ! 😀
