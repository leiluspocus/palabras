---
title: Can't login to Heroku from my mac
date: "2016-08-10T18:42:11+00:00"
description: How I solved the weirdest connexion issue from my mac to Heroku...
template: post
slug: /en/cant-login-to-heroku-from-my-mac/
category: Bugs
tags:
  - devops
  - cli
  - heroku
---

Problem of the day : I wasn&rsquo;t able to connect to Heroku from my mac. The process was blocked on the message « Installing CLI&#8230; » like if it couldn&rsquo;t connect to Heroku.

```shell
MacBook-Air-de-Laila:shredder leiluspocus$ heroku login
heroku-cli: Installing CLI...
Error: getaddrinfo: nodename nor servname provided, or not known (SocketError)
/usr/local/heroku/vendor/gems/excon-0.51.0/lib/excon/socket.rb:100:in `getaddrinfo'
/usr/local/heroku/vendor/gems/excon-0.51.0/lib/excon/socket.rb:100:in `connect'
/usr/local/heroku/vendor/gems/excon-0.51.0/lib/excon/ssl_socket.rb:146:in `connect'
/usr/local/heroku/vendor/gems/excon-0.51.0/lib/excon/socket.rb:28:in `initialize'
/usr/local/heroku/vendor/gems/excon-0.51.0/lib/excon/ssl_socket.rb:8:in `initialize'
/usr/local/heroku/vendor/gems/excon-0.51.0/lib/excon/connection.rb:404:in `new'
/usr/local/heroku/vendor/gems/excon-0.51.0/lib/excon/connection.rb:404:in `socket'
/usr/local/heroku/vendor/gems/excon-0.51.0/lib/excon/connection.rb:106:in `request_call'
/usr/local/heroku/vendor/gems/excon-0.51.0/lib/excon/middlewares/mock.rb:47:in `request_call'
/usr/local/heroku/vendor/gems/excon-0.51.0/lib/excon/middlewares/instrumentor.rb:25:in `request_call'
/usr/local/heroku/vendor/gems/excon-0.51.0/lib/excon/middlewares/base.rb:15:in `request_call'
/usr/local/heroku/vendor/gems/excon-0.51.0/lib/excon/middlewares/base.rb:15:in `request_call'
/usr/local/heroku/vendor/gems/excon-0.51.0/lib/excon/middlewares/base.rb:15:in `request_call'
/usr/local/heroku/vendor/gems/excon-0.51.0/lib/excon/connection.rb:250:in `request'
/usr/local/heroku/vendor/gems/excon-0.51.0/lib/excon.rb:238:in `get'
/usr/local/heroku/lib/heroku/jsplugin.rb:246:in `manifest'
/usr/local/heroku/lib/heroku/jsplugin.rb:259:in `url'
/usr/local/heroku/lib/heroku/jsplugin.rb:149:in `block (2 levels) in setup'
/usr/local/heroku/lib/heroku/jsplugin.rb:137:in `open'
/usr/local/heroku/lib/heroku/jsplugin.rb:137:in `block in setup'
/usr/local/heroku/ruby/lib/ruby/1.9.1/tmpdir.rb:83:in `mktmpdir'
/usr/local/heroku/lib/heroku/jsplugin.rb:135:in `setup'
/usr/local/heroku/lib/heroku/cli.rb:27:in `start'
/usr/local/bin/heroku:24:in `<main></main>'
```

I noticed my Bluetooth was active. It worked after I disabled it.
 