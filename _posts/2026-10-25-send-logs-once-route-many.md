---
layout: single
title: "Send Logs Once, Route Many"
date: 2026-10-25 00:30:00 -0400
description: "The platform watches itself on its own observability platform, then sends logs one way through a data diode. Security and operations each take what they need."
excerpt: "The platform watches itself on its own observability platform, then sends logs one way through a data diode. Security and operations each take what they need."
theme: digital
author_profile: false
classes: full-width
tags: [devops, observability, security]
---
{% include series-nav.html %}

A web platform has to tell two enterprise teams how it is doing: the security operations centre (SOC) and the network operations centre (NOC). The simple way is to send each signal once and let the enterprise route it.

## Four ideas

- **Watch the site from inside first.** The web platform has its own observability platform inside the isolated network. It stores logs, runs the health checks and shows the team its own dashboards and alerts.
- **Send once, route many, one way.** One export sender passes the events the contract lists through a data diode. A data diode carries data in one direction only, so there are no replies, no probes in and no resend requests. Each event carries a running number, so the enterprise can spot a gap.
- **Agree a contract.** A small file in Git lists the required fields, ports, severity names and owners. Nothing can be sent back across the diode, so the contract is also how the enterprise's needs reach the team, by change request.
- **Treat silence as a failure.** A heartbeat event every minute means a quiet link raises an alert on the enterprise side. Without it, a broken link looks like a calm system.

## Where infrastructure as code fits

The pipeline does not carry the logs. It builds, tests and deploys the settings that do: the log format, the forwarder and the alert rules. Because they live in Git, logging cannot be switched off by accident, and the link can be rebuilt on demand.

## Keep personal information out

The SOC needs a user ID and source address. It does not need passwords, tokens, form content or search terms. The pipeline checks sample logs for these.

## Go deeper

The [full paper]({{ '/observability-security-monitoring/' | relative_url }}) covers the one-way signal path, resilience, common tools, examples and questions for Security and the NOC.
