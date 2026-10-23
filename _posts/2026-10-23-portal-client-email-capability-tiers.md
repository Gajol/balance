---
layout: single
title:  "Portal client email: capability tiers"
date:   2026-10-23 08:50:00 -0400
description: Ten capabilities at three tiers, so a product team can choose a level rather than approve a list.
excerpt: "What to do when the captured requirement is 'send email and manage client lists' and the architecture cannot start. Ten capabilities, three tiers each, and a picker that tallies the build."
tags: [ux, "product management"]
theme: digital
---

A portal modernization I am working on had its email requirement captured as *the ability to send email and manage email client lists*. That is true, and it is not enough to design against. It does not say who is emailed, on what trigger, with whose consent, or how anyone would know the right people received it.

The usual move is to go back and ask for more detail. That had been tried for months. Asking people to produce requirements asks them to generate an abstraction, which is a genuinely hard task; asking them to correct a draft asks them to react, which almost anyone can do. So instead of asking again, I wrote down the answers I would guess, deliberately including ones I expected to be wrong.

## Tiers rather than a feature list

The part that changed the conversation was splitting the work into ten capabilities and giving each one three tiers:

- **Foundation** — the portal can launch and send lawfully.
- **Targeted** — the site sends by itself: preference centre, segmented campaigns, approval, automatic suppression.
- **Personalised** — content finds the client: digests, saved searches, correction notices.

A capability can sit at a different tier from its neighbours. Tier 2 consent with Tier 1 measurement is a perfectly reasonable choice, and being able to say that out loud is most of the value. A product owner who cannot approve a list of twenty-five use cases can usually pick a level for ten capabilities.

Two things fell out of it that a feature list would have hidden.

**Some capabilities are coupled.** Multi-factor authentication is in scope, which makes sign-in codes an email that the client triggers. Those have to go through the API, so the sending capability cannot sit at its lowest tier no matter what the campaign side needs. The tier picker in the document flags that pairing when you select it.

**Some tiers are not degrees of the same thing.** How client feedback gets answered — by email reply, by a secure message inside the portal, or offline — looks like three levels of ambition. It is three different projects with different records, different classifications and different costs. That one has no safe default, so it is the item to escalate rather than assume.

## What the document is for

It is a strawman. It is meant to be marked up, and the point of publishing a draft with wrong answers in it is that corrections arrive far faster than answers do. Anything not corrected by a date becomes a recorded assumption rather than an open question, which is what lets a stalled requirement turn into something a project manager can track.

[**Read the capability tiers**]({{ site.baseurl }}/portal-email-capability-tiers/)

The page is self-contained — it carries its own styling and script and loads nothing from the network, so it also opens offline from a file share. Every capability has a tier selector that tallies a rough build size as you go, and every code reference in the text has a tooltip, so you can read "settles D-2" without going to find out what D-2 was.

The platform behind it is a shared notification service for sending, Drupal as the source of truth, with Solr and Matomo for search and measurement. The shape of the argument does not depend on any of that. Any team handed *send email* as a requirement has the same ten questions to answer.
