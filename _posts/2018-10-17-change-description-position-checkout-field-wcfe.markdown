---
layout: post
title:  Change position of description of checkout field  - WooCommerce Checkout Field Editor Pro
categories: jekyll update
---

In WooCommerce Checkout Field Editor Pro, there is an option to add a description for checkout fields. The default position to display description is below the input field.

In some cases, we need to change this position as per theme style. It may for all field or some selected field.

If you like to change the position of the description below label & above input field, you can use below code snippet. 

Use below code snippet in your theme's or child theme's `functions.php` file. Also, update your field name in the code snippet.

	function thwcfe_change_position_desc($position, $key){
	  if($key === 'field_name'){
		$position = true; 
	  }
	  return $position;
	}
	add_filter('thwcfe_display_field_description_below_label', 'thwcfe_change_position_desc', 10, 2);

