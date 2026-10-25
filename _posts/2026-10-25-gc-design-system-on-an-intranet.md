---
layout: single
title: "Using the GC Design System on an Intranet"
date: 2026-10-25 00:40:00 -0400
description: "The GC Design System gives federal sites a shared look and accessible parts. Pin the version, extend in the open, and keep the defaults."
excerpt: "The GC Design System gives federal sites a shared look and accessible parts. Pin the version, extend in the open, and keep the defaults."
theme: digital
author_profile: false
classes: full-width
tags: [gcds, design system, intranet, accessibility]
---

The GC Design System (GCDS) is the federal design system, run by the Canadian Digital Service. It is for federal use only. An intranet is a good fit, because staff expect the same look, the same accessibility and the same bilingual behaviour as public sites.

## What you get

Five parts: **tokens** (colours, type, spacing), **components** (web components such as buttons, headers and forms), **CSS shortcuts**, **page templates** and **guidance**. Think of four layers: your pages, an optional framework wrapper, the web components, and the tokens underneath.

## Three ways to install it

| Route | When to use it | Watch out for |
| :-- | :-- | :-- |
| npm, pinned to a version | Default for most builds | Keep the package scope current |
| CDN, pinned to a version | Quick start, simple sites | Public CDN; self-host on an isolated network |
| CDN "latest" | Prototypes only | The design changes under you without notice |

## Six keys to success

1. **Pin the version.** Upgrade on purpose, with a test.
2. **Settle identity early.** Signature, language toggle and footer links are set once.
3. **Tokens first.** Adjust tokens before you write custom CSS.
4. **Extend in the open.** If a part is missing, build it as a documented extension, not a private fork.
5. **Keep the defaults.** Deviations cost accessibility and upgrade effort.
6. **Budget 20 to 30 per cent more for French.** Longer text breaks layouts.

## Five decisions to make

Adopt or not. Delivery route. Identity settings. Extension and deviation policy. Owner and release cadence.

Check the current release and terms of use on the design system site before you start.
