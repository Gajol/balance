---
title: "References"
permalink: /references/
layout: single
author_profile: false
excerpt: "Outside sources cited on this site, with archived copies."
classes: full-width
---

Outside sources cited on this site. Each has a link to the original and a link to the Internet Archive copy, in case the original moves or disappears.

<ul>
{%- assign refs = site.data.references | sort %}
{%- for pair in refs %}
  {%- assign r = pair[1] %}
  <li>{{ r.author }}{% if r.year %} ({{ r.year }}){% endif %}. <a href="{{ r.url }}"><em>{{ r.title }}</em></a>{% if r.publisher %}. {{ r.publisher }}{% endif %}. <a href="{% if r.archive %}{{ r.archive }}{% else %}https://web.archive.org/web/2/{{ r.url }}{% endif %}">archived</a>{% if r.copy %} &middot; <a href="{{ r.copy | relative_url }}">copy</a>{% endif %}</li>
{%- endfor %}
</ul>
