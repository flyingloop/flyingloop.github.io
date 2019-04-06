---
layout: post
title:  Conditionally display checkout field based on day & time - WooCommerce Checkout Field Editor Pro
categories: jekyll update
---

If you like to display a checkout field on a specific time in a specific days in week, you can use below code snippet.

The below code snippet will show a checkout field named as `field_name` in between 7 AM & 6 PM for all days except weekend(sunday & saturday).

	function thwcfe_show_checkout_field($show, $field_name){
	  if($field_name == 'field_name'){
		$show = false;
		$currentDateTime  = current_time('H:i:s');
		$current_time     = strtotime($currentDateTime);
		$start_time       = strtotime('07:00:00');
		$end_time         = strtotime('18:00:00');

		$weekend = array('Sun','Sat');
		$day = current_time('D');

		if($current_time > $start_time && $current_time < $end_time && !in_array($day, $weekend)){
		  $show = true;
		}
	  }
	  return $show;
	}
	add_filter('thwcfe_show_field', 'thwcfe_show_checkout_field', 10, 2);
