---
title: Getting started with Magento
date: "2017-08-17T23:36:15+00:00"
description: You never worked on a Magento project ? Here are some baby steps to get started smoothly on a Magento project.
template: post
slug: /en/getting-started-with-magento-2/ 
category: Rétroviseur
tags:
  - magento
---

When I started working with Magento 1, I was frightened by the quantity of files and modules. The clients I worked for had several modules and a lot of things needed to be refactored, both projects were on Magento 1.

Here are some « baby steps » I followed when I began with Magento 1. I would like to remember them when I will get started on a Magento 2 project 🙂

## Identify the business rules

Each client has its own challenges, one client might have to do something an other client won&rsquo;t have to do. I once worked for a client who had 3 stocks options: « In stock », « Out of stock », « Likely to be out of stock » which was unthinkable for my last client 😀
  
**The more you know about the business of your client, the more you will deliver features that fits his expectations.**

## Setup a way to debug efficiently

It takes a little bit of time to setup Xdebug but it is &#8211; oh sooo &#8211; valuable. With XDebug, you will be able to debug any line you want in your Magento project by simply adding a breakpoint. You will be able to view the content of your variables, the stack&#8230;
  
Setup Xdebug on your Magento project and install the xdebug extension on Chrome. For front-end development, I used to love Firebug but now, I&rsquo;m using the native console of Chrome because this is my favorite browser 🙂

## Identify the controllers / models behind basic actions

It&rsquo;s important to understand how are these actions handled in the code logic to be able to develop features around these actions. Besides the code logic, visualizing where is the data stored in the database (which tables, how to get the data quickly with MySQL queries for example) can be useful for quick business reports generation.

_Basic views_ 

  * Product view (images, variants, product description)
  * Cart view
  * Checkout view
  * Orders view

_Tricky e-commerce logic_

  * The logic of promotions (how is a discount applied to a product?)
  * Logic of cart rules (how is a discount applied to a shopping cart?)

## Develop a « Hello World » module

It will make you understand the « frightening » architecture through a very simple example for both front-end and back-end. For example, you can develop a module that adds a « Hello world » on product pages.

## Understand the caching process

Last but not least, maybe one of the most difficult points to me: fully understand how a page is cached with Magento. Time speed is critical for your website conversion, the browsing experience must be as fast as possible. It&rsquo;s however tricky for e-commerce because stocks can be evolving quickly: how can you cache data that can be modified frequently? Here are some answers you will need to find the answer to :

  * What are the sections cached in the website and how are they cached ?
  * Is the project using a reverse proxy ? (Varnish)
  * Is there a CDN for static files ? (images, CSS, Javascripts)

Once you will understand the caching process, you will be able to optimize the pagespeed and understand some bugs you will face. 

## Create a list of technical references

Magento has an extremely large community, which is awesome. I used to try to remember the most active people. They can be « trusted » even though you always have to test / fully understand the solutions you find online of course. I learned a lot about Magento 1 through reading the blogs / responses on StackOverflow of the people from this list

  * <a href="http://inchoo.net/blog/" target="_blank">Inchoo</a>
  * <a href="http://alanstorm.com/" target="_blank">Alan Storm</a>
  * <a href="http://fbrnc.net/" target="_blank">Fabrizio Branca</a>
  * <a href="http://anna.voelkl.at/magento/" target="_blank">Anna Völkl</a>
  * <a href="http://vinaikopp.com/blog/list/" target="_blank">Vinai Kopp</a>

If you have a tip to give on how to get started with Magento 2, don&rsquo;t hesitate to leave a comment, I will be happy to read !

**Extra links :** 

[Magento the right way &#8211; A Cheatsheet about Magento&rsquo;s best practices https://magentotherightway.com/](https://magentotherightway.com/)

Magento Compiler Mode http://alanstorm.com/magento\_compiler\_path

http://info2.magento.com/rs/magentosoftware/images/Conquer\_the\_5\_Most\_Common\_Magento\_Coding\_Issues\_to\_Optimize\_Your\_Site\_for_Performance.pdf


<strong> <a href="https://www.slideshare.net/ivanchepurnyi/making-magento-flying-like-a-rocket-a-set-of-valuable-tips-for-developers" title="Making Magento flying like a rocket! (A set of valuable tips for developers)" target="_blank">Making Magento flying like a rocket! (A set of valuable tips for developers)</a> </strong> from <strong><a href="https://www.slideshare.net/ivanchepurnyi" target="_blank">Ivan Chepurnyi</a></strong>