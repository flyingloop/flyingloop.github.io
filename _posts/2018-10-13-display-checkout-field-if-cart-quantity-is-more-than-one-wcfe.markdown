---
layout: post
title:  Display checkout field if cart quantity is more than one - WooCommerce Checkout Field Editor Pro
categories: jekyll update
---

This code snippet is usefull to display checkout field if cart quantity is more than one using WooCommerce Checkout Field Editor Pro plugin.

Use below code snippet in your theme’s or child theme’s functions.php file. Update the string {field_name} in filter tag in the code snippet with your field name.

	function thwcfe_show_field_condition($show){

	  global $woocommerce;
	  $count = $woocommerce->cart->cart_contents_count;
	  if($count < 1){
		$show = false;
	  }
	  
	  return $show;

	}

	add_filter('thwcfe_show_field_{field_name}', 'thwcfe_show_field_condition');
