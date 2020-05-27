---
title: Permission issue with npm while installing react-devtools
date: "2018-02-27T17:14:15+00:00"
template: post 
draft: false
slug: /en/permission-issue-with-npm-while-installing-react-devtools/
category: Bugs
tags:
  - react native
  - shell
---
I had this error once while trying to install the npm package react-devtools.

```shell 
leiluspocus$ npm i -g react-devtools
npm WARN checkPermissions Missing write access to /usr/local/lib/node_modules
npm ERR! path /usr/local/lib/node_modules
npm ERR! code EACCES
npm ERR! errno -13
npm ERR! syscall access
npm ERR! Error: EACCES: permission denied, access '/usr/local/lib/node_modules'
npm ERR!  { Error: EACCES: permission denied, access '/usr/local/lib/node_modules'
npm ERR!   stack: 'Error: EACCES: permission denied, access \'/usr/local/lib/node_modules\'',
npm ERR!   errno: -13,
npm ERR!   code: 'EACCES',
npm ERR!   syscall: 'access',
npm ERR!   path: '/usr/local/lib/node_modules' }
npm ERR!
npm ERR! Please try running this command again as root/Administrator.

npm ERR! A complete log of this run can be found in:
npm ERR!     /Users/leiluspocus/.npm/_logs/2018-02-27T13_52_59_313Z-debug.log
```

The issue was that I was previously installing npm packages using the root user.

```shell
leiluspocus:lib$ ls -l
total 120 
(...)
drwxr-xr-x  11 root            wheel  374 27 fév 14:52 node_modules
```

It&rsquo;s a mess afterwards and it&rsquo;s easier to handle when the owner is your current user. So, I changed the owner of my folder node_modules using the following command :

```shell 
sudo chown -R $USER /usr/local/lib/node_modules/
```

And it worked like a charm !

```shell 
leiluspocus:lib$ ls -l
total 120
(...)
drwxr-xr-x  11 leiluspocus  wheel  374 27 fév 14:52 node_modules 
leiluspocus:lib$ npm i -g react-devtools
/usr/local/bin/react-devtools -&gt; /usr/local/lib/node_modules/react-devtools/bin.js

&gt; electron@1.8.2 postinstall /usr/local/lib/node_modules/react-devtools/node_modules/electron
&gt; node install.js

Downloading SHASUMS256.txt
[============================================&gt;] 100.0% of 3.43 kB (3.43 kB/s)
+ react-devtools@3.1.0
added 239 packages in 37.236s
```

