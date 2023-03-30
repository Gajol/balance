---
layout: single
title:  "Jekyll Collections & Minimal Mistakes - Pages"
date:   2022-03-19 14:55:59 -0500
description: Setup for pages and hopefully page-archive, too.
excerpt: "Struggles to get a _pages folder working locally on Linux and then on GitHub pages"
categories: jekyll
tags: jekyll tags categories doug 2023
toc: true
toc_sticky: true
sidebar:
  title: "Git Posts"
  nav: sidebar-sample
---

## Pages
Following Minimal Mistakes [Working with Pages](https://mmistakes.github.io/minimal-mistakes/docs/pages/) requires.\
1. On project folder create `_pages` Directory.
1. Each page's front matter should have a permalink (`permalink: /about/` and `permalink: /` (for home.md))
1. Setup front matter defaults in _config.yml.

This works, and I can directly navigation to pages using the permalink.  For example, to display the `about.md` page with permalink of `/about/` I can navigation to `site-url/about`.

## Page Archive - Minima Theme vs Minimal Mistakes.
The navigation on my site using a page-archive is not working.   This is where you need to tell Jekyll to generate content, and this needs to work both locally and on Github Pages (GHP does not support Jekyll plugins).
- [Minimal Mistakes - Page Archive Exmample on GHP](https://mmistakes.github.io/minimal-mistakes/page-archive/)

- Unsure what I did with the *minima* theme orginal Gajol GHP's?   I had tags working there, but I created a _includes and a _layouts folder.   In the includes I copied the gem "collecttags.html" and in the layouts there was a page, post, tagpage & head HTML page.   This was based on the *minima* theme.  So the process for creating archives between *minima* and *Minimal Mistakes* is likely different.  
  - The [MM theme](https://github.com/mmistakes/minimal-mistakes) does not archive pages - [MM site](https://mmistakes.github.io/minimal-mistakes/).   Pages are simply refered to directly by directly URL.  For example, the data/navigation file links to the about.md directly as `title: "About" url: https://mmistakes.github.io/minimal-mistakes/about/`

## Try to Copy "Collections Approach"
Can I do this similar to collections - see [Jekyll Collections]({{ site.baseurl }}{% post_url 2022-03-19-jekyll-collections %}) - cannot get post_url Liquid to work?  I have lost the link to the explanation, but I believe the steps are as follows:
1. Find the head.html file in the Minimal Mistakes gem.  This file is the gems installation folder: `~/gems/gems/minimal-mistakes-jekyll-4.24.0`
1. Copy the `layouts/head.html` to your local `project _layouts` folder.   You likely have to create the `_layouts` folder in your project site if this is your first layout customization.

- [x] : I will look at this later.  For now pages will be static pages related to the site (About, Home, 404-NotFound, etc).   Site Content like technology, software, recreational activities will be in specific collections.

## Miscellaneous - Linked Posts
- [Linked Posts](https://mmistakes.github.io/minimal-mistakes/post%20formats/post-link/) : To use, just add link: http://url-you-want-linked to the post’s YAML front matter and you’re done.
- [Link to Other Posts](https://github.com/mmistakes/minimal-mistakes/issues/581) : ...

## Posts with Sticky TOC

- [MM Post on Sticky Table of Contents - TOC](https://mmistakes.github.io/minimal-mistakes/layout-table-of-contents-sticky/)
