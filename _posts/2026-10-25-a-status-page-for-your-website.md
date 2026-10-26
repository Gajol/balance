---
layout: single
title: "Tell Staff Before They Call: A Status Page for Your Website"
date: 2026-10-25 14:40:00 -0400
description: "One page that lists each feature in plain words, with one status for each. It tells people what is working before they phone the help desk."
excerpt: "One page that lists each feature in plain words, with one status for each. It tells people what is working before they phone the help desk."
theme: digital
author_profile: false
classes: full-width
tags: [architecture, observability]
---
{% include series-nav.html %}

When search stops working, people do not know why. Is it their browser, their network or the platform? They phone the help desk. So does the next person. A status page answers the question once, for everyone.

## What a good one looks like

[Wealthsimple](https://status.wealthsimple.com/), a Canadian investment firm, publishes a public status page. It shows two things worth copying:

- **More than twenty features**, named the way a customer would name them: Account Login, Deposit, E-transfer, Trade and Orders.
- **One status for each**, in a short word such as "Operational".

It does not list servers or software. A customer cannot act on "database cluster B". They can act on "E-transfer".

## Five ideas to borrow

1. **Name features the way people do.** List what staff do, not what you run.
2. **Use a short, fixed set of statuses.** For example: Working, Slower than usual, Not working, Planned maintenance, Not known. Write each one in English and French.
3. **Let signals set the status, not only checks.** A check uses the feature like a person would, once a minute. Events the platform already records count too, such as how old the search index is. A heartbeat shows each source is alive. If a source goes quiet, the status becomes "Not known". It never stays at "Working" by default.
4. **Let a named owner explain it.** A short note says what is wrong, what to do and when the next update comes. The owner is a position, not a person.
5. **Serve the page apart from the site.** A banner inside the main site goes down with the site. A small static page, on its own, still loads.

## Two examples

**Search** (CMS page, search engine, analytics tool). Three signals:

- A check runs one known English and one known French query and expects a known test page back. If it fails, the status is "Not working".
- Index lag, per language. If the newest published page is missing from the index for too long, the status is "Slower than usual".
- The analytics tool's search counts and zero-result rate, per language. A jump in searches with no results, or searches falling to near zero during working hours, flags the owner. It does not change the status alone, because usage numbers are slow and noisy.

**Usage reports** (analytics tool). Three signals: a heartbeat that the last tracking hit arrived recently, the last report job finished, and the report page opens. If hits stop while the site is up, the status is "Not known", and the note tells owners their numbers may be incomplete.

The rule behind both: a failed check or an event past its limit can change the status. Usage numbers only raise a flag. The worst status among the signals wins. Use aggregate counts only, never one person's searches.

## What changes on a government network

- **No hosted status service.** The checks, the file and the page all run on the isolated network.
- **Staff only to start.** A page for the public needs its own security review.
- **Text, not colour.** Write the status in words next to each feature. Do not refresh the page by itself, because that can move a screen reader's place.
- **Two languages, together.** A note is not published in one language only.
- **Email carries a link, not the story.** A change notice says which feature and what status, then points to the page.

## Where it fits

The same checks and heartbeats that feed [security and operations monitoring]({{ '/send-logs-once-route-many/' | relative_url }}) can feed the status page. The data is collected once. The page is the version written for users.

## Go deeper

- [PAT-015: Publish a status page]({{ '/architecture/pat-015/' | relative_url }}): the rule, two diagrams, a journey map, a service blueprint, a wireframe, a detailed mockup, the trade-offs and seven questions to ask a vendor.
- [Intranet Architecture Pattern Catalog]({{ '/architecture/pattern-catalog/' | relative_url }}): the other patterns it leans on.
- [Observability and security monitoring]({{ '/observability-security-monitoring/' | relative_url }}): the signal path behind the checks.

## Questions to settle first

- Which five features matter most to staff? Start with those.
- Who is the owner of each, and who writes the first notice at 8 a.m. on a Monday?
- How fast must a notice go out? Name the time.
