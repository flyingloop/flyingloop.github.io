---
layout: post
title:  Add a fee based on WooCommerce cart count - WCFE
categories: jekyll update
---

First create new hidden checkout field using Checkout Field Editor plugin. You must add a price for that input field.

Then use below code snippet in your theme's or child theme's `functions.php` file. Update the string `{field_name}` in filter tag in the code snippet with your field name.

	function thwcfe_change_total_price($price, $value){
		
		// Get cart item quantity
		$quantity=WC()->cart->get_cart_contents_count();
		
		// Multiply hidden field price with cart items quantity
		$price = $price*$quantity;
		
		// Return the updated fee
		return $price;

	}
	add_filter('thwcfe_checkout_field_extra_cost_{field_name}', 'thwcfe_change_total_price',10,2);
