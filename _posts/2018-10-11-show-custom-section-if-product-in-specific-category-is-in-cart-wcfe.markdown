---
layout: post
title:  Show custom section if product in a specific category is in cart - WCFE
categories: jekyll update
---

The below code snippet is usefull to show a custom section with custom checkout fields in WooCommerce checkout process by verifying that if customer added products in to cart from a specific category.

Use below code snippet in your theme's or child theme's `functions.php` file.


	function thwcfe_get_cart_items_count(){
		global $woocommerce;
		$items = $woocommerce->cart->get_cart();
		$item_count = 0;
		$category = 'accessories'; // Your category to be checked
		
		// Iterate through cart items
		foreach($items as $cart_item){
		   
		   // Check if item is in specific category
		   if(has_term( $category, 'product_cat', $cart_item['product_id'])){
			   $item_count++;
		   }
		   
		}

		return $item_count;
	}

	function thwcfe_section_display_rule_override($show, $section_name){
		// Get item count
		$count = thwcfe_get_cart_items_count();
		
		// Confirm your section
		if($section_name == 'test_section'){
			// Check the count
			$show = $count >= 1 ? true : false;
		}
		return $show;
	}
	add_filter('thwcfe_show_section','thwcfe_section_display_rule_override', 2, 10);
