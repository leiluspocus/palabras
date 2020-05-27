---
title: 'Sessions keep refreshing CodeIgniter'
date: "2013-06-05T23:22:47+00:00"
template: post
draft: false
slug: /en/sessions-keep-refreshing-codeigniter/
category: PHP
tags:
  - bug
  - codeigniter
  - sessions
---

I had a bug once, the sessions kept expiring even though the token was still valid.

I found out that CI\_sessions were refreshing the session\_id all the time. This was a database issue, be careful on the length of the columns in the database. The column that stored the session_id was too short and the token kept being re-generated since the old one couldn&rsquo;t be recognized.

This was a tricky bug because it didn&rsquo;t raise any obvious PHP error&#8230; Be careful with the schema of your database folks !
