--- 
title: Create a copy of a Vagrant machine
date: "2016-06-02T18:09:22+00:00"
template: post
slug: /en/create-a-copy-of-a-vagrant-machine/
category: Developer Life
tags:
  - vagrant
  - devops
---

1. Stop your vagrant machine

```shell
vagrant halt
```

2. Create the copy (it can take sometime)

```shell 
vagrant package --base name_of_your_machine  --output path/to/newly/created/package
```

The machine name is on Virtual Box 🙂
