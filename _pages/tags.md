---
title: "Tags"
permalink: /tags/
layout: single
author_profile: false
excerpt: "Find notes by topic."
---

Pick a tag to jump to its notes.

{%- assign items = site.pages | concat: site.posts | concat: site.books | concat: site.architecture | where_exp: "i", "i.tags" -%}
{%- assign all_tags = "" | split: "," -%}
{%- for i in items -%}
  {%- assign all_tags = all_tags | concat: i.tags -%}
{%- endfor -%}
{%- assign all_tags = all_tags | uniq | sort %}

<p>
{%- for tag in all_tags %}
  {%- assign tagged = items | where_exp: "i", "i.tags contains tag" %}
  <a href="#{{ tag | slugify }}" class="btn btn--inverse btn--small">{{ tag }} ({{ tagged.size }})</a>
{%- endfor %}
</p>

{% for tag in all_tags %}
{%- assign tagged = items | where_exp: "i", "i.tags contains tag" | sort: "title" %}
<h2 id="{{ tag | slugify }}">{{ tag }}</h2>
<ul>
{%- for i in tagged %}
  <li><a href="{{ i.url | relative_url }}">{{ i.title }}</a></li>
{%- endfor %}
</ul>
{% endfor %}
