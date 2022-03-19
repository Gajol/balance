---
layout: posts
title:  "aaaJekyll Github Pages : Setting up Minimal Mistakes"
date:   2022-01-06 14:55:59 -0500
categories: jekyll update
tags: nielsen themes actions CI
---

# Minimal Mistakes
- [Minimal Mistakes - Github](https://mmistakes.github.io/minimal-mistakes/)
- [Minimal Mistakes - Installation](https://mmistakes.github.io/minimal-mistakes/docs/installation/)
- [Features](https://mmistakes.github.io/minimal-mistakes/about/)
- [Theme Documentation](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/)


# Setting up a GitHub Pages Site using MM Theme
Try to get GitHub Pages working with MM theme
1. [Theme Install](http://gabe-lade.com/theme-setup/)
1. [Jekyll Talk - Develop with a Remote Theme](https://talk.jekyllrb.com/t/how-to-develop-wth-remote-theme/6021) : GitLab Pages question.
1. [SO - Gem steps basics](https://stackoverflow.com/questions/46380722/jekyll-theme-could-not-be-found)
  -  Add the theme-gem to your Gemfile
  -  add the theme to your _config.yml (correctly done already..)
  -  Run: bundle install (just to make sure Bundler is able to use it)
  -  Run: bundle exec jekyll serve
1. [Favicon](https://github.com/mmistakes/minimal-mistakes/issues/585)

# General
- [Markup, HTML and Formatting](https://mmistakes.github.io/minimal-mistakes/markup/markup-html-tags-and-formatting/)
- [Layouts](https://mmistakes.github.io/minimal-mistakes/docs/layouts/)
- [Excerpt Separator](http://jekyllrb.com/docs/posts/#post-excerpts)

# Posts
- [MM - Working with Posts](https://mmistakes.github.io/minimal-mistakes/docs/posts/)
- [MM - Posts - Year Archive](https://mmistakes.github.io/minimal-mistakes/docs/layouts/#archive-layout) : [Grouped by Year](https://github.com/mmistakes/minimal-mistakes/blob/master/docs/_pages/year-archive.md)
- [Jekyll Posts](https://jekyllrb.com/docs/liquid/tags/#linking-to-posts)
   - {% raw  %}`{% post_url 2010-07-21-name-of-post %}`{% endraw  %}

- Layout not applying to posts. [link](https://talk.jekyllrb.com/t/solved-layout-not-applying-to-individual-posts-only/2971)
  - Is it baseurl and base? [link](https://talk.jekyllrb.com/t/relative-url-and-baseurl/2051)

- Last Updated Metadata. [link](https://solomonvictorino.com/better-post-dates-jekyll/).  relative_url, base_url, site.url, site.baseurl.

# Layouts
- [MM Layouts](https://mmistakes.github.io/minimal-mistakes/docs/layouts/) : seems the layout is "posts"

# Navigation
- https://mmistakes.github.io/minimal-mistakes/docs/navigation/

# Tags
- [Posts by Tags](https://mmistakes.github.io/minimal-mistakes/tags/)
- [Taxonomy Archives - by MM](https://mmistakes.github.io/minimal-mistakes/docs/layouts/#taxonomy-archives) - *The theme ships with support for taxonomy (category and tag) pages. GitHub Pages hosted sites need to use a Liquid only approach while those hosted elsewhere can use plugins like jekyll-archives to generate these pages automatically.*.   Look at source for demo site by MM [link](https://github.com/mmistakes/minimal-mistakes/tree/master/docs/_pages).

# Local Machine

``` sh
git clone https://github.com/gajol/balance
git branch gh-pages
// edit Gemfile and set theme
bundle install
```
