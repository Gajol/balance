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

{%- assign popular_min = 4 -%}

Pick a tag to filter the notes below. Select it again, or choose All, to show everything.

<div class="tag-group">
  <span class="tag-label">Popular</span>
  <div class="tag-cloud">
    <a href="#all" data-tag="all" class="active">All</a>
  {%- for tag in all_tags %}
    {%- assign tagged = items | where_exp: "i", "i.tags contains tag" %}
    {%- if tagged.size >= popular_min %}
    <a href="#{{ tag | slugify }}" data-tag="{{ tag | slugify }}">{{ tag }}<small>{{ tagged.size }}</small></a>
    {%- endif %}
  {%- endfor %}
  </div>
</div>

<div class="tag-group">
  <span class="tag-label">Other</span>
  <div class="tag-cloud">
  {%- for tag in all_tags %}
    {%- assign tagged = items | where_exp: "i", "i.tags contains tag" %}
    {%- if tagged.size < popular_min %}
    <a href="#{{ tag | slugify }}" data-tag="{{ tag | slugify }}">{{ tag }}<small>{{ tagged.size }}</small></a>
    {%- endif %}
  {%- endfor %}
  </div>
</div>

<div class="tag-grid">
{%- for tag in all_tags %}
  {%- assign tagged = items | where_exp: "i", "i.tags contains tag" | sort: "title" %}
  <div class="tag-card" id="{{ tag | slugify }}" data-tag="{{ tag | slugify }}">
    <h2>{{ tag }} <small>{{ tagged.size }}</small></h2>
    <ul>
    {%- for i in tagged %}
      <li><a href="{{ i.url | relative_url }}">{{ i.title }}</a></li>
    {%- endfor %}
    </ul>
  </div>
{%- endfor %}
</div>

<script>
(function () {
  var pills = document.querySelectorAll('.tag-cloud a');
  var cards = document.querySelectorAll('.tag-card');
  function show(tag) {
    pills.forEach(function (p) { p.classList.toggle('active', p.dataset.tag === tag); });
    cards.forEach(function (c) { c.style.display = (tag === 'all' || c.dataset.tag === tag) ? '' : 'none'; });
  }
  pills.forEach(function (p) {
    p.addEventListener('click', function (e) {
      e.preventDefault();
      var t = p.dataset.tag;
      var same = p.classList.contains('active') && t !== 'all';
      show(same ? 'all' : t);
      history.replaceState(null, '', same || t === 'all' ? location.pathname : '#' + t);
    });
  });
  var h = location.hash.slice(1);
  show(h && document.getElementById(h) ? h : 'all');
})();
</script>
