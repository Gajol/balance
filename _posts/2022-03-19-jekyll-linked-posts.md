---
layout: single
title:  "Jekyll Linked Posts"
date:   2022-03-19 14:55:59 -0500
description: Getting Linked Posts to work with a Jekyll Minimal Mistakes theme and using remote-theme (pages).
excerpt: "For post_url to work with linked posts you need to ensure the site is configured correctly, and you refer to the post correctly using relative URL."
categories: jekyll tags
tags: jekyll posts
sidebar:
  title: "Git Posts"
  nav: sidebar-sample
---

## Problem:  

Links to posts are not working using `posturl` syntax, however, I believe I have setup my site's configuration correctly. Using the Liquid `post_url` does not navigate to the post.
- [Jekyll Collections]({% raw %}{% post_url 2022-03-19-jekyll-collections %}{% endraw %}); the page when rendered has a link of:
- Actual: http://127.0.0.1:4000/jekyll/tags/jekyll-collections/
- Want: http://127.0.0.1:4000/balance/jekyll/tags/jekyll-collections/

## Solution Options:

First ensure `baseurl` and `url` are configured correclty in `_config.yml`.   The correct syntax to work with a `baseurl` is described by Michael [here](https://github.com/mmistakes/minimal-mistakes/issues/581)

1.  Prepend baseurl using `prepend`.   
  - {% raw %}`{% post_url post-filename-without-md-extension | prepend: site.baseurl %}`{% endraw %}
use `post_url` concatenated with `baseurl`
1.  Prepend baseurl using Liquid
  - {% raw %}{{ site.baseurl }}{% post_url post-filename-without-md-extension %}{% endraw %}

## questions
- [] : Would `include basepath` as shown here https://github.com/mmistakes/minimal-mistakes/blob/gh-pages-3.1.6/_pages/about.md help make this easier?
