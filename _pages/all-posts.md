---
title: "All Articles"
permalink: /all/
layout: single
author_profile: false
classes: full-width
excerpt: "Every article on the site, newest first, grouped by year, with the theme and date."
---

Every article, newest first. Use [search]({{ '/search/' | relative_url }}) to find a word, or [tags]({{ '/tags/' | relative_url }}) to browse by topic.

{% assign by_year = site.posts | group_by_exp: "p", "p.date | date: '%Y'" %}
{%- for y in by_year %}
## {{ y.name }}
<ul>
{%- for post in y.items %}
  <li><a href="{{ post.url | relative_url }}">{{ post.title }}</a> <small>{{ post.date | date: "%b %-d" }}{% if post.theme %} &middot; {{ post.theme | capitalize }}{% endif %}</small>{% if post.description %} &mdash; {{ post.description | strip_html | truncate: 150 }}{% endif %}</li>
{%- endfor %}
</ul>
{%- endfor %}
