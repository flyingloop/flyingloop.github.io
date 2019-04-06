---
layout: post
title:  Remove required symbol from input field created by WooCommerce Extra Product Options Pro
categories: jekyll update
---

If you added a new field in product page using Extra Product options plugin, there is an option to make it as required. At that time, an asterisk (*) mark will appear near input field label.

Some of us don't like this asterisk mark. If so, you can use below code snippet.

Use below code snippet in your theme’s or child theme’s functions.php file.

	function thwepo_remove_required_symbol ($symbol,$fname){

		return '';

	}

	add_filter('thwepo_required_html','thwepo_remove_required_symbol', 10, 2);


The argument passed to function are field name and symbol. So there is option to remove symbols for specific field and update the showing asterisk mark with some other HTML markup.
