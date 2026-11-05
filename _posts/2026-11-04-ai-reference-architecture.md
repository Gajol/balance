---
layout: single
title: "An AI Reference Architecture, and How to Test It for Risk"
date: 2026-11-04 19:00:00 -0500
description: "One shared set of parts and controls, so each AI use case does not start from zero. Three slide decks: the architecture, the risk addendum and six scenarios."
excerpt: "One shared set of parts and controls, so each AI use case does not start from zero. Three slide decks: the architecture, the risk addendum and six scenarios."
theme: digital
author_profile: false
classes: full-width
tags: [ai, architecture, risk]
---

Every team that starts an AI project picks its own model, copies its own data and invents its own safeguards. A reference architecture stops that. It is one shared pattern that every use case plugs into.

## What the architecture has

- **Six layers.** Users, AI applications, a gateway, assurance services, models and knowledge, and data and platform.
- **One control plane.** Security, privacy and governance cut across every layer. It is a plane, not a layer.
- **Five principles.** Data stays put. One front door. Rights travel. People decide. Swap the model.
- **A rule behind each principle.** For example: no source is indexed above the use case's tier limit, and tokens are narrowed to the user, never passed on.
- **Risk tiers A to D.** A is a staff aid with no personal information. D is a decision about a client. The tier sets the controls.
- **A roadmap in three stages.** Foundations, shared services, then scale and assure.

## Why a use case benefits

Without it, approvals start from zero, risk is judged differently each time and an audit rebuilds the story by hand. With it, teams reuse the gateway and services, the tier sets the controls and evidence is kept as the work goes.

A reference model is not a product list, not a project design and not a standard. Each solution still needs its own architecture.

## Testing it for risk

The second deck maps the architecture to the NIST AI Risk Management Framework (Govern, Map, Measure, Manage) and to the federal direction on automated decisions and generative AI. The third runs the architecture through six scenarios:

1. Approving a new model
2. Connecting a new AI tool or MCP server
3. Retrieval (RAG) over internal content
4. User and system permissions, where the system uses only a subset of the user's rights
5. Actions that change things
6. Incidents

## The slides

Each deck is built for reading and printing. Each diagram fits a Word page, and each deck can be downloaded.

- [AI reference architecture]({{ '/architecture/ai-reference-architecture-deck/' | relative_url }}): 23 slides
- [AI risk management addendum]({{ '/architecture/ai-risk-management-addendum-deck/' | relative_url }}): 20 slides
- [Six AI risk scenarios]({{ '/architecture/ai-risk-scenarios-deck/' | relative_url }}): 21 slides

## What is my read, not a standard

The layers, the tiers A to D and the rules are my own design. The second approver for tier D is a proposal, not a published requirement. Roadmap timings are planning assumptions. The NIST and federal items are published sources; check them against the originals before relying on them.

*Drafted with Claude.ai.*
