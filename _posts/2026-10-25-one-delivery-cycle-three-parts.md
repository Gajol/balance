---
layout: single
title: "One Delivery Cycle, Three Parts"
date: 2026-10-25 00:10:00 -0400
description: "A CMS, a search engine and an analytics tool share one cycle but keep their own versions. Test them together every time."
excerpt: "A CMS, a search engine and an analytics tool share one cycle but keep their own versions. Test them together every time."
theme: digital
author_profile: false
classes: full-width
tags: [devops, web platform, architecture]
---

A government web platform is rarely one product. A typical set is a content management system (CMS), a search engine and an analytics tool. They depend on each other, but each has its own upgrades and risks.

## One pipeline or three?

Neither. Run **one delivery cycle with three separately versioned parts.**

- **One build job per part.** A theme edit does not rebuild search.
- **One release manifest.** A small file lists the exact versions of all three parts that were tested together. That file is what moves to staging and production.
- **Test together, always.** Even when only one part changed, run the search checks and the tracking check on the whole set.
- **Keep changes reversible.** Add the new field first, switch over, then remove the old one. Each part can then roll back alone.

## Same signals, different jobs

The platform writes standard logs and health checks. The delivery team, the network operations centre and the security operations centre each take what they need. Nobody builds a second pipeline just for them.

## Go deeper

The [CI/CD Pipeline Guide]({{ '/cicd-pipeline-guide/' | relative_url }}) covers the delivery cycle, the signals table and the option to use a shared platform team's pipeline template.
