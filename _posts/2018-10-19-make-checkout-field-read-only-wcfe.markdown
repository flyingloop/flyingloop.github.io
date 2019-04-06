---
layout: post
title:  Make checkout field read only  - WooCommerce Checkout Field Editor Pro
categories: jekyll update
---

If you are using WooCommerce Checkout Field Editor Pro plugin, we can save additional field value as user meta. From next time, these fields are autofill with saved user data.

If you plan to disallow editing of saved user data, you can make these fields as read only after confirm that he is a logged in user.

Use below code snippet in your theme’s or child theme’s functions.php file. Update the string {field_name} in filter tag in the code snippet with your field name.

	function thwcfe_login_make_field_readonly($value){
		// First confirm that user is already logged in
		if(is_user_logged_in()){
			$value = true; 		
		}
		return $value;	
	}
	add_filter('thwcfe_is_readonly_field_{field_name}', 'thwcfe_login_make_field_readonly');
