---
layout: single
title:  "Jekyll Collections & Minimal Mistakes - Typos Matter"
date:   2022-02-01 14:55:59 -0500
description: Setup for collections within Jekyll Minimal Mistakes theme.
excerpt: "A unique line of text to describe this post that will display in an archive listing and meta description with SEO benefits."
categories: jekyll tags
tags: jekyll excerpt
sidebar:
  title: "Git Posts"
  nav: sidebar-sample
---

It turned out that I had a typo in the collection I was making.  The directory for where the markdown posts was to be stored, `_portfolio` had a typo.   As a result, there were no source-pages for Jekyll to process into the `_site/portfolio` folder.   
- [Minimal Mistakes Collections](https://mmistakes.github.io/minimal-mistakes/docs/collections/)
- [Jekyll Collectoins](https://jekyllrb.com/docs/collections/#output)

There was no real logging information on the console where jekyll was started via `bundle exec jekyll serve`.  I should see if there were ways to debug this more easily by looking at jekyll logs or starting jekyll with more output.


## Github Pages Nuances
I believe for the collections, page-archive and other features to work on github pages you need to use the includes method.  GitHub Pages does not support plugins as per [Minimal Mistakes](https://mmistakes.github.io/minimal-mistakes/docs/helpers/).  Instead MM uses the Liquid `-- include --` approach.   [Jekyll Filters](https://jekyllrb.com/docs/liquid/filters/) help iterate through content and build template-objects.
