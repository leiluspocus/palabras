--- 
title: 'SQL Magento Get the list of SKUs that are in a catalog_price_rule'
date: "2015-11-24T12:16:55+00:00"
template: post 
draft: false
slug: /en/sql-magento-get-the-list-of-skus-that-are-in-a-catalog_price_rule/
category: Snippets
tags:
  - magento
  - sql
---


> 👴 _Careful_ You're reading an old article ! Some links might be broken and content may be outdated

The parameter « rule_id » can be viewed in the URL when you are editing the catalog price rule.

```SQL 
select sku
from catalog_product_entity
where entity_id in (
SELECT DISTINCT product_id 
FROM catalogrule_product 
WHERE rule_id=&lt;rule_id&gt;
);
```