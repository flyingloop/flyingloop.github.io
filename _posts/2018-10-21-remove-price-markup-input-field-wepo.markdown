---
layout: post
title:  Remove price markup from input field created by WooCommerce Extra Product Options Pro
categories: jekyll update
---

If you are creating a new field in product page using Extra Product options plugin, there is an option to add special price for the field.  If user enter or select a value for that field, product price will increase or decrease as per our settings.

But displaying an additional price may iritatae few customers. So our plugin have an option to hide the price markup that shown near input field.

Use below code snippet in your theme’s or child theme’s functions.php file. You need to update your field name in the below code snippet.

	function hide_field_price_display($show, $field_name, $field_type){
		if($field_name === 'field_name'){
			$show = false;
		}
		return $show;
	}
	add_filter('thwepo_display_field_price', 'hide_field_price_display', 10, 3);

