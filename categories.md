---
title: Categories
layout: page
---

<ul>
{% assign categories = site.categories | sort %}
	{% for category in categories %}
	{% capture category_name %}{{ category | first }}{% endcapture %}
		<li><a href="{{ site.url }}/category/{{ category_name }}">{{ category_name }}</a></li>
	{% endfor %}
</ul>
