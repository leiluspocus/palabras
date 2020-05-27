---
title: Getting started with React Native
date: "2017-09-02T17:31:47+00:00"
template: post
draft: false
slug: /en/getting-started-with-react-native/
category: Cheatsheets
tags:
  - react native
---

It&rsquo;s pretty impressive how we can simply set up a development environment without XCode using Expo.

Make sure you&rsquo;re using the right Node and NPM versions and double check that there are no missing packages while doing the npm install.

I had to run these commands before running npm start on my app (created through create-react-native-app ):

```shell 
sudo sysctl -w kern.maxfiles=5242880
sudo sysctl -w kern.maxfilesperproc=524288
```
 

While you edit your project files (using any IDEA like Atom or Sublime Text), Expo provides live reloading so that you can directly test your application very quickly.

I made a very simple app that only embed a webview. IT can be found here: https://github.com/leiluspocus/react-test

 

### Resources 

* Basic tutorial to get started with React Native: https://facebook.github.io/react-native/docs/tutorial.html
* Packages explorer for React: https://js.coach/react-native/

 

<!-- AddThis Advanced Settings generic via filter on the_content -->

<!-- AddThis Share Buttons generic via filter on the_content -->