---
title: How to add a new stock option in Woocommerce
date: "2016-03-22T18:53:53+00:00"
template: post
draft: false
slug: /en/how-to-add-a-new-stock-option-in-woocommerce/
category: Snippets
tags:
  - javascript
  - jquery
  - woocommerce
---
Sometimes, clients can come up with some pretty creative ways to handle their inventory &#8230; It was the case for me with a customer who was using WooCommerce.

I had to add a third option but the stock options was not customizable. I ended up deleting the native dropdown of stock options and I implemented a custom field.

In functions.php

```php
add_action('woocommerce_product_options_stock_status', 'add_custom_stock_type');    
function add_custom_stock_type() {
        // Stock status - We remove the default one
        ?>
        <script type="text/javascript">
            jQuery('_stock_status').remove();
        </script>
        <?php   
    }
```

And then I followed [this tutorial](http://www.remicorson.com/mastering-woocommerce-products-custom-fields/) to create a custom field : http://www.remicorson.com/mastering-woocommerce-products-custom-fields/

[Someone on SO](http://stackoverflow.com/questions/26912556/add-stock-option-in-woocommerce/26916930#26916930) proposed an other solution based on my approach but my contract was already done with that client by the time he answered, didn&rsquo;t get the chance to test it out.
 