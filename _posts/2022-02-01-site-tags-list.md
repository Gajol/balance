---
layout: posts
title:  "Site Tags - Resources to Help"
date:   2022-02-01 14:55:59 -0500
categories: jekyll tags mermaid
tags: tags jekyll
---

# Tag Help

- [jetholt.com - jekyll-tags-and-categories/](https://jetholt.com/micro/jekyll-tags-and-categories/)
- [Github - Writing](https://docs.github.com/en/get-started/writing-on-github/)
- [Githum Flavoured Markdown](https://github.github.com/gfm/)
	- [Display Liquid Code Blocks](https://michaelcurrin.github.io/dev-cheatsheets/cheatsheets/jekyll/code-blocks/liquid-code.html)

# Mermaid
https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/creating-diagrams

# Scripts

## Site Tags - Raw Liquid

```liquid
<div>
    {{ site.title }}
</div>
```


{% highlight liquid %}
<div>
    {{site.tags}}
</div>
{% endhighlight %}

{{site.tags}}


## Slugify tags...

{% comment %}
The purpose of this snippet is to list all the tags you have in your site.
{% endcomment %}

{% for tag in tags %}
	<a href="#{{ tag | slugify }}"> {{ tag }} </a>
{% endfor %}  
