---
layout: posts
title:  "Github Actions"
date:   2022-03-04 14:55:59 -0500
categories: pandoc
tags: pandoc github-actions
---

Try to get the actions and the makefile to work on the gulp-generated MD file.   The gulp-generated MD file is a version-controlled file in Github.   The file is generated on the Linux server and pushed to github.

The makefile generates the PDF, but pandoc does not process the markdown syntax.   For example, the headers and lists show with #, ##, and - instead of being formatted.

- [Pandoc Github Action Examples](https://github.com/pandoc/pandoc-action-example)
- [Github - Using Workflows](https://docs.github.com/en/actions/using-workflows#referencing-a-container-on-docker-hub)
- [Github - Actions - Release](https://github.com/softprops/action-gh-release)
- [Github TOC - gitdown or...](https://stackoverflow.com/questions/9721944/automatic-toc-in-github-flavoured-markdown)
- [Makefile Symbols](https://stackoverflow.com/questions/3220277/what-do-the-makefile-symbols-and-mean)

## Thought
The gulp/gitdown script creates HTML anchors before each heading similar to this:
``` HTML
<a name="introduction"></a>
```
This seems to cause pandoc to stop process the file as markdown.

Google "pandow with markdown and HTML anchors"
- [gitdown](https://www.npmjs.com/package/gitdown)

## Decision
To display the gulp-generated markdown on github, the gitdown "contents" with HTML anchors is needed.  This allows the output-markdown to be usable on Github directly.

The drawback, is this file (with the HTML <a> anchor tags) is rather useless for the Github Actions workflow to generate a PDF.   A separate build for a PDF using pandoc can be done with a ARA.md that does not have anchors.
1. Use gulp to generate a combined markdown without a TOC.  This ensures are no anchors in the output file: foo.md.
1. Use github actions (pandoc) to generate a PDF from this markdown.   Can an line-option in pandoc be used to generate a TOC???  [pandoc toc q&a](https://stackoverflow.com/questions/25591517/pandoc-inserting-pages-before-generated-table-of-contents)
  - see [Auto TOC for GH flavour markdown](https://stackoverflow.com/questions/9721944/automatic-toc-in-github-flavoured-markdown).
  - uses [DocToc Nodejs](https://github.com/thlorenz/doctoc).  Can be used as a [pre commit hook](http://pre-commit.com/).
    - Concern/TBD: This pre commit hook can change TOC files for Markdowns (I guess if the file is unchanged the Markdow is unchanged - so not an issue.)


### Result
Working better after playin with Gulp and serialize the tasks.   The build now gives a LateX
[LaTex Too Deeply Nest Error](https://texfaq.org/FAQ-toodeep).   There is __no indication__ of where this nesting issue is.
