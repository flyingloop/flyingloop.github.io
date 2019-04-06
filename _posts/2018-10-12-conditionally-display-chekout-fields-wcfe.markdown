---
layout: post
title:  Conditionally display chekout fields - WooCommerce Checkout Field Editor Pro
categories: jekyll update
---

There is already too many inbuilt conditions are avilable in WooCommerce Checkout Field Editor plugin.

But if you have some amazing conditions that are not covered by our plugin, here is a simple code snippet for you to display or hide checkout fields based on your conditions.

Use below code snippet in your theme’s or child theme’s functions.php file. Update the string {field_name} in filter tag in the code snippet with your field name.

	function thwcfe_show_field_condition($show){

		// Your conditions here
		// $show Variable have the value True or False as per the field settings in your backend
		// Return True to display the field
		// Return False to hide the field

	}

	add_filter('thwcfe_show_field_{field_name}', 'thwcfe_show_field_condition');
