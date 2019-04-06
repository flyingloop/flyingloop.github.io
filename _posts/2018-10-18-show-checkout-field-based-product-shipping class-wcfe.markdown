---
layout: post
title:  Show checkout field based on cart items shipping class  - WooCommerce Checkout Field Editor Pro
categories: jekyll update
---

If you like to show a checkout field based on cart items shipping class, you can use below code snippet.



	function thwcfe_show_field_based_on_shipping_class($show){  
		global $woocommerce;
		$show = false;
		$cart_object = WC()->cart->get_cart();
		$shipping_class='test_shipping_class';

		if($cart_object){
			foreach($cart_object as $cart_item ) {
				$product = $cart_item['data'];
				$class = $product->get_shipping_class();
				if($class === $shipping_class){  
					$show = true;
					break;
				}    
			}
		}
		return $show;
	}
	add_filter('thwcfe_show_field_{field_name}', 'thwcfe_show_field_based_on_shipping_class');


