--- 
title: NoMethodError /Ruby/Gems/2.0.0/gems/sass-3.4.8/lib/sass/plugin/compiler.rb Undefined method start
date: "2016-04-09T16:15:08+00:00"
template: post
draft: false
slug: /en/nomethoderror-rubygems2-0-0gemssass-3-4-8libsassplugincompiler-rb-undefined-method-start/
category: Bugs
tags:
  - devops
  - compass
  - ruby
  - sass
  - shell
---

I had the weirdest issue when initializing my compass project for Greenie.

```shell kikoo:greenie leiluspocus$ sudo compass watch --trace
>>> Compass is watching for changes. Press Ctrl-C to Stop.
NoMethodError on line ["402"] of /Library/Ruby/Gems/2.0.0/gems/sass-3.4.8/lib/sass/plugin/compiler.rb: undefined method `start' for #<Thread:0x007f90d1afd098 sleep></Thread:0x007f90d1afd098>
  /Library/Ruby/Gems/2.0.0/gems/sass-3.4.8/lib/sass/plugin/compiler.rb:402:in `map'
  /Library/Ruby/Gems/2.0.0/gems/sass-3.4.8/lib/sass/plugin/compiler.rb:402:in `listen_to'
  /Library/Ruby/Gems/2.0.0/gems/sass-3.4.8/lib/sass/plugin/compiler.rb:338:in `watch'
  /Library/Ruby/Gems/2.0.0/gems/compass-1.0.3/lib/compass/sass_compiler.rb:46:in `watch!'
  /Library/Ruby/Gems/2.0.0/gems/compass-1.0.3/lib/compass/commands/watch_project.rb:41:in `perform'
  /Library/Ruby/Gems/2.0.0/gems/compass-1.0.3/lib/compass/commands/base.rb:18:in `execute'
  /Library/Ruby/Gems/2.0.0/gems/compass-1.0.3/lib/compass/commands/project_base.rb:19:in `execute'
  /Library/Ruby/Gems/2.0.0/gems/compass-1.0.3/lib/compass/exec/sub_command_ui.rb:43:in `perform!'
  /Library/Ruby/Gems/2.0.0/gems/compass-1.0.3/lib/compass/exec/sub_command_ui.rb:15:in `run!'
  /Library/Ruby/Gems/2.0.0/gems/compass-1.0.3/bin/compass:30:in `block in <top (required)>'
  /Library/Ruby/Gems/2.0.0/gems/compass-1.0.3/bin/compass:44:in `call'
  /Library/Ruby/Gems/2.0.0/gems/compass-1.0.3/bin/compass:44:in `<top (required)>'
  /usr/local/bin/compass:23:in `load'
  /usr/local/bin/compass:23:in `<main>'
```

I solved it [by using a more recent version of Ruby using RVM](http://code.tutsplus.com/tutorials/how-to-install-ruby-on-a-mac--net-21664). RVM is pretty cool because you can switch your Ruby versions very easily. Note that I had to re-install compass afterwards. 