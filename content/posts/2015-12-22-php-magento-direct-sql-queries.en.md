--- 
title: 'PHP / Magento - Direct SQL Queries'
date: "2015-12-22T11:37:54+00:00"
draft: false
template: post 
slug: /en/php-magento-direct-sql-queries/
category: Snippets
tags:
  - magento
  - php
---
Not the cleanest but here&rsquo;s a quick solution to do a direct query on Magento. Might be faster than calling Magento&rsquo;s objects ? 

```php
/**
   * Get the resource model
   */
$resource = Mage::getSingleton('core/resource');
     
 /**
  * Acccess to the database in read only
  */
$readConnection = $resource-&gt;getConnection('core_read');
     
$query = 'SELECT * FROM ' . $resource-&gt;getTableName('catalog/product');
     
/**
 * Execute the query  
 */
$results = $readConnection-&gt;fetchAll($query);
```

[Thank you DevProblems !](http://www.devproblems.com/magento-direct-sql-queries/)
