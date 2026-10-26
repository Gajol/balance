---
title: "Technology and Balancing Life"
permalink: /
layout: single
author_profile: true
classes: full-width
---

Notes on technology, how people think, and how the world works, plus time on the bike.

- [**Digital**]({{ '/digital/' | relative_url }}) &mdash; architecture, digital government, service design and DevOps. Start with the [Pattern Catalog]({{ '/architecture/pattern-catalog/' | relative_url }}).
- [**Psychology**]({{ '/psychology/' | relative_url }}) &mdash; book summaries on judgment, choice and growing up.
- [**Economics**]({{ '/economics/' | relative_url }}) &mdash; energy, food, trade and policy.
- [**Cycling**]({{ '/cycling/' | relative_url }}) &mdash; bikes, routes and trips.

## Recent articles
<ul>
{%- for post in site.posts limit: 5 %}
  <li><a href="{{ post.url | relative_url }}">{{ post.title }}</a> <small>({{ post.date | date: "%B %-d, %Y" }})</small>{% if post.excerpt %} &mdash; {{ post.excerpt | strip_html | strip_newlines | truncate: 140 }}{% endif %}</li>
{%- endfor %}
</ul>

See all notes by [topic]({{ '/tags/' | relative_url }}).
