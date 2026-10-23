---
title: "Tags"
permalink: /tags/
layout: single
author_profile: false
classes: tags-page
excerpt: "Find notes by topic."
---

{%- assign items = site.pages | concat: site.posts | concat: site.books | concat: site.architecture | where_exp: "i", "i.tags" -%}
{%- assign all_tags = "" | split: "," -%}
{%- for i in items -%}
  {%- assign all_tags = all_tags | concat: i.tags -%}
{%- endfor -%}
{%- assign all_tags = all_tags | uniq | sort -%}

Pick a tag to jump to its notes.

<div class="tag-cloud">
{%- for tag in all_tags %}
  {%- assign tagged = items | where_exp: "i", "i.tags contains tag" %}
  {%- assign n = tagged.size %}
  <a href="#{{ tag | slugify }}">{{ tag }}<small>{{ n }}</small></a>
{%- endfor %}
</div>

<div class="tag-grid">
{%- for tag in all_tags %}
  {%- assign tagged = items | where_exp: "i", "i.tags contains tag" | sort: "title" %}
  <div class="tag-card">
    <h2 id="{{ tag | slugify }}"><a href="#{{ tag | slugify }}">{{ tag }}</a> <small>{{ tagged.size }}</small></h2>
    <ul>
    {%- for i in tagged %}
      <li><a href="{{ i.url | relative_url }}">{{ i.title }}</a></li>
    {%- endfor %}
    </ul>
  </div>
{%- endfor %}
</div>
