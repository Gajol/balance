---
layout: single
title: "CI/CD for a Web Platform: The Short Version"
date: 2026-10-25 00:00:00 -0400
description: "Every change becomes a tested, secure, traceable release. Start small, add gates as the team matures."
excerpt: "Every change becomes a tested, secure, traceable release. Start small, add gates as the team matures."
theme: digital
author_profile: false
classes: full-width
tags: [devops, ci-cd, web platform]
---
{% include series-nav.html %}

A CI/CD pipeline is one automated path from a code change to production. Every change is built the same way, tested, scanned and recorded. Nobody has to remember the checklist, because the pipeline runs it.

## Why a government team cares

- **Fewer surprises.** Small, tested changes are safer than big, rare ones.
- **Faster fixes.** A security patch can reach production in days, not months.
- **Evidence by default.** Each release shows what changed, who approved it and which tests passed.

## Four levels, one step at a time

| Level | Name | What it looks like |
| :-- | :-- | :-- |
| 1 | Foundation | Code and config in Git. One automated build. Deploys are scripted. |
| 2 | Automated checks | Tests, coding standards, secret and dependency scans run on every change. |
| 3 | Controlled release | Failed gates block the build. Artifacts are versioned and signed. Rollback is one step. |
| 4 | Measured | Production health and usage feed back into planning. |

A new team should aim for Level 2 first. Do not try to jump to Level 4.

## Gates: a few, always enforced

A gate is a rule that can stop a build. Start with code quality, secrets, dependencies and a short list of key journeys. Add search, accessibility and configuration-drift gates at Level 3. Every exception needs an owner, a reason and an expiry date.

Many gates that people learn to ignore are worse than a few that always hold.

## Go deeper

- [CI/CD Pipeline Guide]({{ '/cicd-pipeline-guide/' | relative_url }}) is the full guide, with a gate filter by level.
- [DevOps Definitions]({{ '/devops-definitions/' | relative_url }}) explains the terms in plain language.
