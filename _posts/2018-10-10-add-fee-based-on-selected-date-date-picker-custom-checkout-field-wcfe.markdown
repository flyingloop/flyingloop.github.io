---
layout: post
title:  Add a fee based on selected date by date-picker custom checkout field - WCFE
categories: jekyll update
---


First create new checkout field with date picker using Checkout Field Editor plugin. You must add a price for that input field.

Then use below code snippet in your theme's or child theme's `functions.php` file. Update the string `{field_name}` in filter tag in the code snippet with your field name.

	function thwcfe_change_total_price($price, $value){
		
		// Get today date
		$current_time = date( 'd/m/Y', current_time( 'timestamp', 0 ) );
		$today = DateTime::createFromFormat('d/m/Y', $current_time);
		$today->setTime( 0, 0, 0 );
		
		// Get selected date using date picker
		$selected_date = DateTime::createFromFormat('d/m/Y', $value);
		$selected_date->setTime( 0, 0, 0 );
		
		// Find the difference between dates
		$diff = $today->diff( $selected_date );
		$diffDays = (integer)$diff->format( "%R%a" ); // Extract days count in interval

		// Conditionally add fee using switch statement
		switch( $diffDays ) {
			case 0: // for Today
				$price = '';
				break;
			case -1: // for Yesterday
				$price = '';
				break;
			case +1: // for Tomorrow
				$price = $value;
				break;
			default: // for Sometime
				$price = '';
		}

		return $price;

	}
	add_filter('thwcfe_checkout_field_extra_cost_{field_name}', 'thwcfe_change_total_price',10,2);

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
