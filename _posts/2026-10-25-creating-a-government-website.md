---
layout: single
title: "Creating a Government Website: How the Pieces Fit"
date: 2026-10-25 00:50:00 -0400
description: "One map of what it takes to build and run a government website: design, architecture, delivery, operations and ownership, with links to the detailed pages."
excerpt: "One map of what it takes to build and run a government website: design, architecture, delivery, operations and ownership, with links to the detailed pages."
theme: digital
author_profile: false
classes: full-width
toc: true
toc_label: "Contents"
tags: [architecture, devops, design system, web platform, intranet]
---

A website is not one thing. It is a design, a platform, a delivery path, an operations link and a team. Each has its own page on this site. This article puts them in order and says which page to open for which question.

## The short version

1. **Design it** with the federal design system, so it is accessible and bilingual from day one.
2. **Architect it** with a small set of repeatable patterns.
3. **Build and release it** through one pipeline with gates.
4. **Run it** on containers that can move from one host to a cluster.
5. **Watch it** by sending logs once to security and operations, and tell users what is working on a status page.
6. **Own it** with named owners, review dates and a product manager after launch.

## 1. Design: the look, the parts and the rules

Start with the federal design system. It gives tokens, accessible web components, templates and guidance. The main risks are an unpinned version, late identity decisions and a private fork.

- [Using the GC Design System on an Intranet]({{ '/gc-design-system-on-an-intranet/' | relative_url }}): install routes, six keys to success, five decisions.
- [Changing the GC Design System for an Intranet: Keep, Change, Add]({{ '/changing-the-gc-design-system-for-an-intranet/' | relative_url }}) and its [working examples]({{ '/gcds-intranet-examples/' | relative_url }}): identity, density, search enhancements, hover cards and engagement patterns.
- [Can I Trust This Page?]({{ '/can-i-trust-this-page/' | relative_url }}): three signals every page should show.

## 2. Architecture: patterns, not one-offs

Build features from a short list of patterns, so each new feature looks like the last one.

- [Intranet Architecture Pattern Catalog]({{ '/architecture/pattern-catalog/' | relative_url }}): the full list, from "Index, don't copy" to "Check accessibility at every gate".
- [Application Reference Architecture]({{ '/architecture/application-reference-architecture/' | relative_url }}): the wider enterprise context.
- [One Vocabulary]({{ '/one-vocabulary-for-search-analytics-navigation/' | relative_url }}): one taxonomy for search, analytics and navigation.

## 3. Delivery: one pipeline, a few gates

Every change is built once, tested, scanned and recorded. A CMS, a search engine and an analytics tool share one delivery cycle, but each keeps its own version.

- [CI/CD for a Web Platform: The Short Version]({{ '/cicd-for-a-web-platform/' | relative_url }}): levels and gates in plain language.
- [One Delivery Cycle, Three Parts]({{ '/one-delivery-cycle-three-parts/' | relative_url }}): how the platform's parts move together.
- [CI/CD Pipeline Guide]({{ '/cicd-pipeline-guide/' | relative_url }}): the full guide, with a gate filter by maturity level.
- [DevOps Definitions]({{ '/devops-definitions/' | relative_url }}): the terms, with a filter.

## 4. Hosting: Podman now, Kubernetes later

Write the deployment as Kubernetes YAML from day one. Run it on Podman today. Move to a cluster later without a rewrite. On an isolated network, build outside, sign, carry across and promote the same image.

- [Podman Now, Kubernetes Later]({{ '/podman-now-kubernetes-later/' | relative_url }}): the five rules.
- [Podman to Kubernetes working paper]({{ '/podman-to-kubernetes/' | relative_url }}): work breakdown, code, diagrams, change map and sizing.

## 5. Operations: tell security, operations and users

One forwarder sends logs to the enterprise collector. A heartbeat makes silence an alert.

- [Send Logs Once, Route Many]({{ '/send-logs-once-route-many/' | relative_url }}): the three ideas.
- [Tell Staff Before They Call: A Status Page for Your Website]({{ '/a-status-page-for-your-website/' | relative_url }}): one page that shows what is working, and the pattern behind it ([PAT-015]({{ '/architecture/pat-015/' | relative_url }})).
- [Observability and security monitoring working paper]({{ '/observability-security-monitoring/' | relative_url }}): the signal path, tools and examples.

## 6. Ownership: a site is a product

The platform is not finished at launch. People use it, it ages and someone must look after it.

- [Running a Web Platform as a Product: A Reading Guide]({{ '/running-a-web-platform-as-a-product/' | relative_url }}): the chain of ten short articles.
- [Who Runs the Website?]({{ '/who-runs-the-website-operating-model/' | relative_url }}): a simple operating model.
- [Why Your Website Needs a Product Manager After Launch]({{ '/product-manager-after-launch/' | relative_url }}).
- [Content Health]({{ '/content-health-reporting/' | relative_url }}) and [Your Search Box Is Only as Good as Your Content Owners]({{ '/search-needs-content-owners/' | relative_url }}).
- [Getting and Keeping the Team]({{ '/getting-and-keeping-the-team/' | relative_url }}).

## Which page for which question?

| If you are asking | Open |
| :-- | :-- |
| What should it look like, and what can we reuse? | [Using the GC Design System on an Intranet]({{ '/gc-design-system-on-an-intranet/' | relative_url }}) and the [intranet examples]({{ '/gcds-intranet-examples/' | relative_url }}) |
| How do we build a feature that fits? | [Intranet Architecture Pattern Catalog]({{ '/architecture/pattern-catalog/' | relative_url }}) |
| How do we release safely? | [CI/CD short version]({{ '/cicd-for-a-web-platform/' | relative_url }}), then the [full CI/CD guide]({{ '/cicd-pipeline-guide/' | relative_url }}) |
| What does this term mean? | [DevOps Definitions]({{ '/devops-definitions/' | relative_url }}) |
| Where does it run, and how do we move later? | [Podman Now, Kubernetes Later]({{ '/podman-now-kubernetes-later/' | relative_url }}) and the [working paper]({{ '/podman-to-kubernetes/' | relative_url }}) |
| How do security and operations see it? | [Send Logs Once, Route Many]({{ '/send-logs-once-route-many/' | relative_url }}) and the [working paper]({{ '/observability-security-monitoring/' | relative_url }}) |
| Who looks after it? | [Running a Web Platform as a Product]({{ '/running-a-web-platform-as-a-product/' | relative_url }}) |

## What is generic here

Product and organization names are removed on purpose. "CMS", "search" and "analytics" stand for whichever products your team picks. The ideas hold across them.
