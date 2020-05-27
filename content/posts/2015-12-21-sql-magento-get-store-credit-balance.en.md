---
title: 'SQL Magento - Get store credit balance'
date: "2015-12-21T17:48:06+00:00"
draft: false
template: post 
slug: /en/sql-magento-get-store-credit-balance/
category: Snippets
tags:
  - magento
  - sql
---

Valid for Magento EE 1 only. The feature of store credits isn&rsquo;t native in CE edition.

```SQL 
select amount 
from enterprise_customerbalance 
where customer_id = @customer_id ;
```