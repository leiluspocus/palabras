---
title: VirtualBox CheatSheet
date: "2016-02-18T16:08:10+00:00"
template: post
slug: /en/virtualbox-cheatsheet/
category: Cheatsheets
tags:
  - DevOps
---

Here is a couple of commands I&rsquo;ve used in a previous life while trying to resize a Vagrant machine.

#### List the virtual disk images used by Virtual Box

```vboxmanage list hdds```

#### Remove a hard disk from a Virtual Box registry

```vboxmanage closemedium disk a5bad1ba-5ff7-4b83-87ff-adb18f05269a --delete```

#### [How to resize a hard disk for a Virtual Machine &#8211; Tutorial](https://gist.github.com/christopher-hopper/9755310)
