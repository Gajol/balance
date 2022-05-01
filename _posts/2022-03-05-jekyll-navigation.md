---
layout: posts
title:  "Jekyll Navigation"
date:   2022-03-05 14:55:59 -0500
categories: jekyll update
tags: markdown github navigation sidebar
---
Learning Github Pages and Jekyll Navigation.
- [Jekyll RB Tutorials - Navigation](https://jekyllrb.com/tutorials/navigation/)
  - [Include based on Property - Order](https://jekyllrb.com/tutorials/navigation/)

## Permalinks
- [Permalinks](https://jekyllrb.com/docs/permalinks/) are the output path for your pages, posts, or collections. They allow you to structure the directories of your source code different from the directories in your output.

## Sidebar - Find another Jekyll Theme
- [Stack Overflow - Sidebar](https://stackoverflow.com/questions/63410862/sidebar-on-github-pages).
- [Themes for Documentation](https://jekyllthemes.io/jekyll-documentation-themes) : some free others paid-themes.
  - [Open API Inspired Theme](https://jekyllthemes.io/theme/carte)
  - [Free Themes](https://cloudcannon.com/blog/free-jekyll-themes-for-2022/)
  - [Minimal Mistakes Theme](https://github.com/mmistakes/minimal-mistakes)
  - [Developr](https://github.com/sujaykundu777/devlopr-jekyll): deployable to github pages and firebase (netlify, heroku, AWS Amplify, ...). [Netlify Demo](https://devlopr.netlify.app/).

## Sample Data-Drive Navigation List
{{ site.data.samplelist.docs_list_title }}

   {% for item in site.data.samplelist.docs %}
      - {{ item.url }} and {{ item.title }}
   {% endfor %}

## Test
From [Jekyll Github Pages](http://jekyllrb.com/docs/github-pages/) regarding using relative pages: (unsure why they include the quotes as the resulting URL is where %22 is a '"': http://localhost:4000/jekyll/update/2022/03/05/%22/jekyll/update/2022/03/05/test.html%22)
- [{{ page.title }}]("{{ page.url | relative_url }}")
- [{{ page.title }}]({{ page.url | relative_url }})


## White Space Control
Looping through pages, produces raw-text even though the attempt was to output links to the pages.  *Working with Liquid and Markdown is always a bit tricky because white-space is so significant in Markdown, and the intermediate Liquid-generated Markdown is hidden during the Jekyll compilation process.*
- [Liquid Outputs as Raw Text](https://talk.jekyllrb.com/t/liquid-outputs-raw-text-and-not-markdown/3834/5)
- [Shopify - Liquid Whitespace](https://shopify.github.io/liquid/basics/whitespace/)

- Pages on this site:

{% assign sorted_pages = site.pages | sort:"order" %}
{% for node in sorted_pages %}
   {%- capture sitelink -%}[{{node.title}}]({{node.url}}){%- endcapture -%}
   - {{sitelink}} : {{node.url}}
{% endfor %}
