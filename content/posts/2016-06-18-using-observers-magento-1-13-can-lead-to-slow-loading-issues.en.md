---
title: Using observers in Magento 1.13 can lead to slow loading issues
date: "2016-06-18T16:02:24+00:00"
description: Story of a tricky bug I had once on Magento 1.13
template: post
draft: false
slug: /en/using-observers-magento-1-13-can-lead-to-slow-loading-issues/
category: Magento
tags:
  - magento EE 1.13
  - performance
---

For one of the Magento projects I worked on, I had to implement a new action in the dropdown list of actions in the back-end.

I tried the Observer option described in this tutorial: 
    <a href="http://www.blog.magepsycho.com/adding-new-mass-action-to-admin-grid-in-magento/">Adding new mass action to admin grid in Magento</a>



However, it slowed down the application because the event I was observing core\_block\_abstract\_prepare\_layout_before was triggered too many times. The Sales admin page could take around 5 to 10 seconds to load. I finally opted for the Block override option, much more elegant.

Lesson learned from this experience ? Be careful with the events you&rsquo;re overriding with Magento and profile your dev environment. The plugin [AOE_Profiler](https://github.com/AOEpeople/Aoe_Profiler/) helped me a lot noticing this issue.
 