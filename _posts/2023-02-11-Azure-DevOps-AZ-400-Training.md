---
layout: single
title: "Azure DevOps (AZ-400): A Guide to My Course Notes"
date: 2023-02-11 14:55:59 -0500
description: "A guide to nine sets of notes from the Microsoft AZ-400 DevOps course: pipelines, releases, infrastructure as code, dependencies, feedback and security."
excerpt: "A guide to nine sets of notes from the Microsoft AZ-400 DevOps course: pipelines, releases, infrastructure as code, dependencies, feedback and security."
header.image: /assets/images/bridge-generated-og.jpeg
theme: digital
author_profile: false
classes: full-width
tags: [azure, devops, engineering, training]
---

Microsoft's [AZ-400: Designing and Implementing Microsoft DevOps Solutions](https://learn.microsoft.com/en-us/learn/certifications/exams/az-400) prepares you for the DevOps Engineer Expert certification exam. The course explains why Agile and DevOps are a good way to deliver software to the business, and how to build a working delivery pipeline.

These are my notes. Each topic has its own page, so you can read only what you need. They follow the order of the course, and they build on each other: first how code is managed, then how it is built, released and run, then how it is kept secure.

## The course in nine steps

1. [DevOps Transformation Journey]({{ '/application/devops/Azure-DevOps-AZ-400-Training' | relative_url }}) &mdash; Why DevOps, how to pick a first project, and how to measure improvement with cycle time and KPIs. Start here.
2. [Development in Enterprise DevOps]({{ '/application/devops/AZ-400-Development-Enterprise-DevOps' | relative_url }}) &mdash; Git repository structure, branching strategies and pull requests, so teams can work together safely.
3. [CI with Azure Pipelines and GitHub Actions]({{ '/application/devops/AZ-400-CI-Azure-Pipelines-GH-Actions' | relative_url }}) &mdash; Build pipelines in YAML, agents and pools, and scaling the build environment.
4. [Release Strategy]({{ '/application/devops/AZ-400-CI-Azure-Release-Strategy' | relative_url }}) &mdash; Moving from traditional releases to continuous delivery, with release pipelines, stages and feature flags.
5. [Secure Continuous Deployment]({{ '/application/devops/AZ-400-Secure-Continuous-Deployment' | relative_url }}) &mdash; Deploy in small steps with blue-green, canary, dark launches, A/B testing and deployment rings, and look after secrets and identity.
6. [Infrastructure as Code with Azure and DSC]({{ '/application/devops/AZ-400-IaC-using-Azure-and-DSC' | relative_url }}) &mdash; Treat servers like cattle, not pets: build consistent environments from code with ARM templates and Desired State Configuration.
7. [Dependency Management Strategy]({{ '/application/devops/AZ-400-Dependency-Management-Strategy' | relative_url }}) &mdash; Package feeds, versioning and promoting packages, so large projects keep control of what they depend on.
8. [Continuous Feedback]({{ '/application/devops/AZ-400-Continuous-Feedback' | relative_url }}) &mdash; Telemetry, monitoring, dashboards and alerts that tell the team how the product behaves, plus retrospectives.
9. [Open Source Security and Code Compliance]({{ '/application/devops/AZ-400-Security-and-Code-Bases' | relative_url }}) &mdash; DevSecOps, open source licences, software composition analysis, and static and dynamic code analysis.

## How the pieces fit

- **Steps 1 to 3 (people and code):** agree why you are changing, structure the code, and build it automatically.
- **Steps 4 to 6 (delivery):** release safely in small steps, and make environments repeatable with code.
- **Steps 7 to 9 (control):** manage dependencies, learn from live use, and keep the code base secure.

If you are short of time, read steps 1, 4 and 8. They give the best view of the overall idea.

## Exam resources

- [AZ-400 Study Guide](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE3VP8d)
- [AZ-400 exam prep videos](https://learn.microsoft.com/en-us/shows/exam-readiness-zone/preparing-for-az-400-configure-processes-and-communications-1-of-5)
- [Exam sandbox](https://aka.ms/examdemo)
- [AZ-400 learning path: get started with the DevOps transformation journey](https://learn.microsoft.com/training/paths/az-400-get-started-devops-transformation-journey/)
- Application Lifecycle Management for the Power Platform is a related path: [application lifecycle management architect](https://learn.microsoft.com/training/modules/application-lifecycle-management-architect/)

Other references mentioned in the course:

- Puppet, 5 Stages of DevOps (2018)
- OWASP Code Review Guide (2017)
- Microsoft Digital Defense Report (2022), and its Executive Summary

These notes are a summary, and in places a copy, of the Microsoft training material. The course changes over time, so check the current exam skills outline before relying on them.

> *I wish I had been a little bit more respectful of the pile of poker chips God put in front of me to get started on.  But, you know that's life.  Mistakes and lost poker chips.*  - Duke Montana The Comeback Trail - Tommy Lee Jones.
