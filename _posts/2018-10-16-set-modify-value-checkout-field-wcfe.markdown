---
layout: post
title:  Set or modify value of a checkout field  - WooCommerce Checkout Field Editor Pro
categories: jekyll update
---

If you like to set or modify value of a checkout field from checkout page, you can use below code snippet.

Use below code snippet in your theme's or child theme's `functions.php` file. Update the string `{field_name}` in filter tag in the code snippet with your field name.

	function thwcfe_field_value_changer($value){
	  $value = 'New Value';
	  return $value ;
	}
	add_filter('thwcfe_woocommerce_form_field_value_{field_name}', 'thwcfe_field_value_changer');

Note: Using this code, you just change value of input field. But users always have option to update this value of input field.
