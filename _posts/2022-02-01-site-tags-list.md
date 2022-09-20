---
layout: posts
title:  "Site Tags"
date:   2022-02-01 14:55:59 -0500
categories: jekyll tags
tags: tags jekyll
---

## Site Tags - Raw Liquid
{{site.tags}}

## Slugify tags...

{% comment %}
The purpose of this snippet is to list all the tags you have in your site.
{% endcomment %}

{% for tag in tags %}
	<a href="#{{ tag | slugify }}"> {{ tag }} </a>
{% endfor %}  
