---
layout: single
title: "Send Logs Once, Route Many"
date: 2026-10-25 00:30:00 -0400
description: "One forwarder sends the platform's logs to the enterprise collector. Security and operations each take what they need."
excerpt: "One forwarder sends the platform's logs to the enterprise collector. Security and operations each take what they need."
theme: digital
author_profile: false
classes: full-width
tags: [devops, observability, security]
---

A web platform has to tell two enterprise teams how it is doing: the security operations centre (SOC) and the network operations centre (NOC). The simple way is to send each signal once and let the enterprise route it.

## Three ideas

- **Send once, route many.** The platform writes standard logs. One local forwarder sends them to the enterprise collector. The SIEM and the NOC take what they need.
- **Agree a contract.** A small file in Git lists the required fields, ports, severity names and owners. The team and the enterprise both test against it.
- **Treat silence as a failure.** A heartbeat event every minute means a quiet link raises an alert. Without it, a broken link looks like a calm system.

## Where infrastructure as code fits

The pipeline does not carry the logs. It builds, tests and deploys the settings that do: the log format, the forwarder and the alert rules. Because they live in Git, logging cannot be switched off by accident, and the link can be rebuilt on demand.

## Keep personal information out

The SOC needs a user ID and source address. It does not need passwords, tokens, form content or search terms. The pipeline checks sample logs for these.

## Go deeper

The [full paper]({{ '/observability-security-monitoring/' | relative_url }}) covers the signal path, resilience, common tools, examples and questions for Security and the NOC.
