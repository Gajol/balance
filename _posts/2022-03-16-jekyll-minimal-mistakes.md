---
layout: single
title:  "Jekyll Github Pages : Minimal Mistakes"
date:   2022-01-06 14:55:59 -0500
categories: jekyll update
tags: nielsen themes actions CI
classes: wide
---

## Minimal Mistakes
- [Minimal Mistakes - Github](https://mmistakes.github.io/minimal-mistakes/)
- [Minimal Mistakes - Installation](https://mmistakes.github.io/minimal-mistakes/docs/installation/)
- [Features](https://mmistakes.github.io/minimal-mistakes/about/)
- [Theme Documentation](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/)


## Setting up a GitHub Pages Site using MM Theme
Try to get GitHub Pages working with MM theme
1. [Theme Install](http://gabe-lade.com/theme-setup/)
1. [Jekyll Talk - Develop with a Remote Theme](https://talk.jekyllrb.com/t/how-to-develop-wth-remote-theme/6021) : GitLab Pages question.
1. [SO - Gem steps basics](https://stackoverflow.com/questions/46380722/jekyll-theme-could-not-be-found)
  -  Add the theme-gem to your Gemfile
  -  add the theme to your _config.yml (correctly done already..)
  -  Run: bundle install (just to make sure Bundler is able to use it)
  -  Run: bundle exec jekyll serve
1. [Favicon](https://github.com/mmistakes/minimal-mistakes/issues/585)

## General
- [Markup, HTML and Formatting](https://mmistakes.github.io/minimal-mistakes/markup/markup-html-tags-and-formatting/)
- [Layouts](https://mmistakes.github.io/minimal-mistakes/docs/layouts/)
- [Excerpt Separator](http://jekyllrb.com/docs/posts/#post-excerpts)

## Posts
- [MM - Working with Posts](https://mmistakes.github.io/minimal-mistakes/docs/posts/)
- [MM - Posts - Year Archive](https://mmistakes.github.io/minimal-mistakes/docs/layouts/#archive-layout) : [Grouped by Year](https://github.com/mmistakes/minimal-mistakes/blob/master/docs/_pages/year-archive.md)
- [Jekyll Posts](https://jekyllrb.com/docs/liquid/tags/#linking-to-posts)
   - {% raw  %}`{% post_url 2010-07-21-name-of-post %}`{% endraw%}

- Layout not applying to posts. [link](https://talk.jekyllrb.com/t/solved-layout-not-applying-to-individual-posts-only/2971)
  - Is it baseurl and base? [link](https://talk.jekyllrb.com/t/relative-url-and-baseurl/2051)

- Last Updated Metadata. [link](https://solomonvictorino.com/better-post-dates-jekyll/).  relative_url, base_url, site.url, site.baseurl.

## Layouts
- [MM Layouts](https://mmistakes.github.io/minimal-mistakes/docs/layouts/) : seems the layout is "posts"

## Navigation
- https://mmistakes.github.io/minimal-mistakes/docs/navigation/

## Tags
- [Posts by Tags](https://mmistakes.github.io/minimal-mistakes/tags/)
- [Taxonomy Archives - by MM](https://mmistakes.github.io/minimal-mistakes/docs/layouts/#taxonomy-archives) - *The theme ships with support for taxonomy (category and tag) pages. GitHub Pages hosted sites need to use a Liquid only approach while those hosted elsewhere can use plugins like jekyll-archives to generate these pages automatically.*.   Look at source for demo site by MM [link](https://github.com/mmistakes/minimal-mistakes/tree/master/docs/_pages).

## Favicon
- [GitHub Q&A](https://github.com/mmistakes/minimal-mistakes/issues/949) - [GitHub MM Favicon Issues](https://github.com/mmistakes/minimal-mistakes/issues?q=favicon+is%3Aclosed)
- [Favicon Generator](http://realfavicongenerator.net/) : HTML5, Grunt, Gulp, NodeCLI, Rails, RFG API; plus icons for Apple, Android and Microsoft.
- [Real Favicon Site](http://realfavicongenerator.net/): Test favicon (bypassing browser caching)

Hosting with GitHub Pages, I found I also needed to prepend {{ site.baseurl }} to the href, e.g.
<link rel="shortcut icon" href="{{ site.baseurl }}/assets/images/favicon.ico">

- [MM includes for favicon](https://github.com/mmistakes/minimal-mistakes/blob/gh-pages-3.1.6/_includes/head/custom.html)
minimal-mistakes/_includes/head/custom.html
<link rel="icon" type="image/png" href="{{ base_path }}/images/favicon-16x16.png?v=M44lzPylqQ" sizes="16x16">

### Result HTML to Paste Into Head
<link rel="apple-touch-icon" sizes="180x180" href="/apple-touch-icon.png">
<link rel="icon" type="image/png" sizes="32x32" href="/favicon-32x32.png">
<link rel="icon" type="image/png" sizes="16x16" href="/favicon-16x16.png">
<link rel="manifest" href="/site.webmanifest">
<link rel="mask-icon" href="/safari-pinned-tab.svg" color="#5bbad5">
<meta name="msapplication-TileColor" content="#da532c">
<meta name="theme-color" content="#ffffff">

### Examples
- https://nicolgit.github.io/ | source code https://github.com/nicolgit/ | Q&A with MM: https://github.com/mmistakes/minimal-mistakes/issues/3487
  - placed in _includes/head.html :  <link rel="shortcut icon" type="image/png" href="/favicon.png">
  - changing my custom.html to head.html worked.  But I lost most of the theme - since I need to copy over the MM-gems head.html and just insert the custom.html parts for the favicon.

## Theme
- Using remote theme as suggested by MM to work with [MM Quick Start Guide - Github Pages](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/#installing-the-theme)

## Local Machine

``` sh
git clone https://github.com/gajol/balance
git branch gh-pages
// edit Gemfile and set theme
bundle install
```

## TO DO
- [ ] : [Cleanup Content to be under docs](https://github.com/mmistakes/minimal-mistakes/tree/master/docs)
- [ ] : [Page Archive](https://github.com/mmistakes/minimal-mistakes/blob/master/docs/_pages/sitemap.md)
- [ ] : [Social Config]()
- [ ] : [Twitter Cards for Sharing](https://mmistakes.github.io/minimal-mistakes/docs/configuration/#twitter-cards-and-facebook-open-graph). See [Twitter Cards](https://developer.twitter.com/en/docs/twitter-for-websites/cards/overview/player-card)

## Done
- [x] : [Masthead Navigation](https://mmistakes.github.io/minimal-mistakes/docs/navigation/) : top-header (global) navigation
- [x] : [Pages]({{ site.baseurl }}{% post_url 2022-03-19-jekyll-pages %})
- [x] : [Collections]({{ site.baseurl }}{% post_url 2022-03-19-jekyll-collections %})
- [x] : [Linked Posts working with baseurl]({{ site.baseurl }}{% post_url 2022-03-19-jekyll-linked-posts %})
