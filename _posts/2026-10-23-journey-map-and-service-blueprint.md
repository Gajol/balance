---
layout: single
title:  "From strawman to blueprint: designing client email"
date:   2026-10-23 12:00:00 -0400
description: How a strawman, a set of capability tiers, a journey map and a service blueprint work together, and what each one is for.
excerpt: "A requirement that says 'send email' is not enough to design against. Four artefacts, used in order, turn it into something a business, a security team and an integration team can all work from."
theme: digital
tags: [ux, "product management", "service design", email, requirements]
classes: full-width
author_profile: false
---

A requirement that says *send email and manage client lists* is true, and it is not enough. It does not say who gets the email, why, with whose consent, or what has to exist behind the screen for it to work. Architecture cannot start from that sentence, and asking again for "more detail" rarely helps.

This is how I closed that gap on a client portal. It uses four artefacts, in order. Each one answers a different question.

## 1. The strawman

Asking people to write requirements asks them to produce an abstraction. That is hard. Asking them to correct a draft asks them to react, and almost anyone can do that.

So I write down the answers I would guess, and I leave some of them wrong on purpose. I publish the draft with a date. Anything nobody corrects by that date becomes a **recorded assumption**, not an open question. A project manager can track an assumption. They cannot track a silence.

## 2. Capability tiers

The strawman needs a shape. I split the email work into ten capabilities and gave each one three tiers: Foundation, Targeted and Personalised. A product owner who cannot approve a list of twenty-five use cases can usually pick a level for ten capabilities.

Each choice also carries forward. Every capability ends with what it means for the **BRD**, for **security** and for **integration**. A choice that is cheap to write down can be expensive to secure, and reading the three side by side shows the real price.

[Read the capability tiers]({{ site.baseurl }}/client-email-tiers/) (the interactive page), or the [short article about it]({{ site.baseurl }}/client-email-capability-tiers/).

## 3. The journey map

The tiers say **what** the service can do. They do not say what it feels like to be the client. A **journey map** does.

A journey map follows one kind of client through the service over time. For each step it shows:

- the channel the client uses (form, email, web page, sign-in);
- what they are trying to do;
- how they probably feel;
- the pain point, and what success looks like.

An **emotional curve** runs across the steps, from very frustrated to very positive. The lowest point is usually the first thing to fix.

One rule matters more than the rest. **A journey map built without research is a hypothesis.** Mark every feeling as assumed, draw the curve with a dashed line, and say what research would confirm it. Used that way, it is a good prompt for a workshop. Treated as a finding, it misleads.

## 4. The service blueprint

A journey map shows what the client sees. A **service blueprint** adds the work and systems they never see, using the same steps as columns.

Its rows are called lanes:

1. **Customer action** and **touchpoint**: what the client does and where.
2. **Frontstage actions**: what the service shows them.
3. *Line of visibility.* Above it the client sees the work. Below it they do not.
4. **Backstage actions**: the staff work, such as approving a send or reviewing a notice.
5. *Line of internal interaction.* It separates the teams from the systems.
6. **Support systems**: the CMS, the search index, the notification service.

Two views come out of the blueprint. A **dependency view** shows what breaks if one system stops. A **process flow** shows one lane step by step, including the unhappy paths.

The blueprint earns its keep because every cell has to name something real: a screen, a role or a system. If nobody has decided, the cell says "to confirm". In my example, the journey map looked fine. The blueprint showed that every send passes through one outbound access rule with no fallback. That is a single point of failure, and the map could never have shown it.

[Read the journey map and service blueprint]({{ site.baseurl }}/client-email-journey-blueprint/)

## How they fit together

| Artefact | Question it answers | Main audience |
|---|---|---|
| Strawman | What do we think the answers are? | The business, to correct |
| Capability tiers | What level of service do we choose? | Product owner, BAs |
| Journey map | What does the client go through? | Product, content, communications |
| Service blueprint | What work and systems make it happen? | Architects, delivery, operations |

## What I learned

- Naming real things exposes gaps. Writing every cell as a real screen, role or system found open items I had not seen: system owners, the sign-in code method, account recovery, delegated access.
- Unknowns can be shown instead of hidden. The client types were unknown, so the page shows where they would matter and marks personas "to be resolved". The structure holds while the unknown is closed.
- The next step after the web draft is finished files. I stop for approval first, because a web draft changes in minutes and a finished deck does not.

All of this is my own judgement, built from one project. The useful test is whether a drawing changed a decision, so I will measure that next time.
