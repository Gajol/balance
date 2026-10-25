---
layout: single
title: "Changing the GC Design System for an Intranet: Keep, Change, Add"
date: 2026-10-25 00:55:00 -0400
description: "An intranet is not a public site. What to keep from the GC Design System, what to change once, and what to add as plugins, with a page of working examples."
excerpt: "An intranet is not a public site. What to keep from the GC Design System, what to change once, and what to add as plugins, with a page of working examples."
theme: digital
author_profile: false
classes: full-width
toc: true
toc_label: "Contents"
tags: [design system, intranet, accessibility, search, architecture]
---

The GC Design System is built for public service delivery first. An intranet shares most of its needs, but not all. This article says what to keep, what to change once, and what to add. Every point has a working example on the [examples page]({{ '/gcds-intranet-examples/' | relative_url }}).

## The short version

**Keep the parts. Change the surroundings. Add the missing patterns as plugins.**

| Area | Do this |
| :-- | :-- |
| Forms, errors, language toggle | Keep as shipped. Accessibility and French behaviour are the return on adoption. |
| Identity (menu, footer, signature) | Choose on purpose, once. Clear it with the identity program coordinator. |
| Density | One documented variant that changes global tokens in one place. |
| Delivery | Pin the version. Host the build yourself on an isolated network. |
| Missing patterns | Build as plugins on global tokens, and offer them upstream. |

Each example on the page ends with a box, **What changes in the design system**. It says the type of change (configuration, tokens, plugin or outside the design system), what is touched, what is left alone, who owns it and what evidence to keep. The search example updates that box as you switch features on and off. In every case the core design system is not changed.

## Differences between a public site and an intranet

- **Identity.** Components carry public-site elements by default: a topic menu, a government footer, a signature. An intranet should keep only what it is allowed and needs.
- **Density.** Public type is tuned for reading. Directories and tables need more rows per screen.
- **Audience.** Visitors are known staff, so there is no need for spam checks, but there is a need for ownership, review dates and privacy rules.
- **Time.** Public content lasts until removed. Intranet posts such as notices and for-sale items should expire.
- **Reach.** Nothing should be fetched from outside the network.

## Search: the pattern every section needs

Search is not among the shipped components, so it is a plugin. Start with an accessible list. Then add enhancements one at a time, and check each one against what staff do:

1. **Synonyms.** "Holiday" finds "leave".
2. **Close spellings.** "Leve" finds "leave".
3. **Owner and review date.** Show them. Rank owned, current pages first.
4. **Best bets** for the few searches that matter most.
5. **Facets** by type and section.
6. **A helpful zero-result page**, with a "did you mean" and a way to browse.
7. **Previews** on hover and focus, with a button for keyboard and touch.

The [examples page]({{ '/gcds-intranet-examples/' | relative_url }}) lets you switch each one on and off over a small set of made-up pages. Count every zero-result query. It is a to-do list.

## Hover cards: allowed, with conditions

A hover card is a deviation from what ships, so treat it as a plugin. Test it with real users. Make sure it can be dismissed with Esc, that the pointer can move onto it, and that it stays until the person moves away. Give keyboard and touch users the same content, and never hide something essential behind hover alone. Check the component list before you build one, in case the design system adds it.

## Two engagement examples a public site would not have

- **A staff bulletin board** (for sale, wanted, free). Posts expire, rules are shown, contact goes through the staff directory, and anyone can report a post.
- **A recognition wall.** The key choice is who can see a shout-out: the person, their team or everyone. Defaults should be low risk.

Both need an owner, a retention rule and labels that fit in French.

## Where a new thing goes

Ask three questions: Does a shipped component already do it? Could a second organization use it? Does it change how a shipped component looks or acts? The answers send it to the core as shipped, a plugin lane, your own lane, or the override register. Every deviation gets one line in the register, with a reason and evidence.

## Go deeper

- [Changing the GC Design System for an Intranet: Working Examples]({{ '/gcds-intranet-examples/' | relative_url }})
- [Using the GC Design System on an Intranet]({{ '/gc-design-system-on-an-intranet/' | relative_url }})
- [PAT-010: Core first, admit by evidence]({{ '/architecture/pat-010/' | relative_url }})
- [Your Search Box Is Only as Good as Your Content Owners]({{ '/search-needs-content-owners/' | relative_url }})
