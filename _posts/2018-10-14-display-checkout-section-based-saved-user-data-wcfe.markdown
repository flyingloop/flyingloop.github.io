---
layout: post
title:  Display checkout section based on saved user data - WooCommerce Checkout Field Editor Pro
categories: jekyll update
---

If you are using Checkout Editor plugin, you can save the checkout field data as user meta.

In few situations, we need to display checkout page sections based on these saved user data. Rememeber that this is only possible for logged in users.

Use below code snippet in your theme’s or child theme’s functions.php file. Update the user meta key, values and section identifier in the code snippet with your details.

	function thwcfe_conditional_section_hide($show, $section_name){
	  if(is_user_logged_in()){
		$user_id = get_current_user_id();
		$user_meta = get_user_meta($user_id, 'billing_first_name', true);

		if($user_meta === 'saved_user_data'){
		  if($section_name == 'section_name'){
			$show = false;
		  }
		}
	  }
	  
	  return $show;
	}
	add_filter('thwcfe_show_section', 'thwcfe_conditional_section_hide', 10, 2);
