---
layout: single
title: "Application Reference Architecture, Updated: A Modern View"
date: 2026-10-25 01:00:00 -0400
description: "A short, modern reference for building government applications: what still holds from the 2022 article, what changed, and the defaults to use today."
excerpt: "A short, modern reference for building government applications: what still holds from the 2022 article, what changed, and the defaults to use today."
theme: digital
author_profile: false
classes: full-width
toc: true
toc_label: "Contents"
tags: [architecture, ai, government]
---

In 2022 I wrote a long [Application Reference Architecture (ARA)]({{ '/architecture/application-reference-architecture/' | relative_url }}). It is a 53-minute read. It is still a good library of definitions, principles and references. But it is dated. It cites a strategic plan that has since been replaced, treats MACH as new, sets WCAG 2.1 as the target, and says nothing about AI, sovereignty or platform teams.

This article is the short, modern version. Read this first. Open the [2022 article]({{ '/architecture/application-reference-architecture/' | relative_url }}) when you need the depth.

**A note on what is policy and what is my view.** Where I name a Government of Canada policy or plan, the link is in the sources at the end. The "defaults" are my architecture advice. Check them against your own department's rules.

## What changed since 2022

| Topic | The 2022 view | Today |
|---|---|---|
| Strategy | Digital Operations Strategic Plan 2021–2024 | The CIO's three-year plan is now published as the **Digital Ambition**, updated each year. |
| Application health | An aging portfolio is a risk | It is now measured. The 2024–25 Digital Ambition reports that only 38% of applications are healthy. |
| Cloud | Cloud first: SaaS, then PaaS, then IaaS | Cloud **with control**. Hybrid and portable designs, and a live sovereignty debate. |
| AI | Not covered | A federal AI strategy for 2025–2027. AI is now a component to design for. |
| Style | Microservices, SOA and MACH | **Right-sized**. Start modular. Split only for a real reason. |
| Delivery | "Adopt DevOps" | One pipeline with gates, on a shared platform with paved roads. |
| Security | Shift left | Also supply chain: signed images, a list of what is inside, zero trust. |
| Operations | Observability as a quality trait | Send logs once, route many. Tell users on a status page. |
| Accessibility | WCAG 2.1 AA | WCAG 2.2 is the current W3C version. Use the design system and check your required level. |

## What still holds

These parts of the 2022 article have not aged. Keep them.

- **Business first.** Know the service, the owner and the outcome before you pick technology.
- **Reuse, then buy, then build.** Build only what is unique to you.
- **Build less.** Every feature is a future cost.
- **APIs are contracts.** Design them for the people who will call them.
- **Criticality sets effort.** A critical service needs a tested backup and recovery plan.
- **The 12 factors.** Config in the environment, stateless processes, logs as streams.
- **Accessible and bilingual from day one.** It is cheaper than a retrofit.
- **Test at the lowest level you can.**

## The modern model in seven layers

One page to put on a wall. Each layer asks one question and has one default.

| Layer | The question | The modern default |
|---|---|---|
| 1. Service and business | Which service, which outcome, who owns it? | A capability map, a named owner, outcome measures. |
| 2. Experience | How do people use it? | The federal design system. Accessible and bilingual. Front end separate from back end where it helps. |
| 3. Application | How is it built? | Modular. One deployable unit until there is a real reason to split. |
| 4. Integration | How does it talk to others? | API first, with a catalog and versioned contracts. Events only where asynchronous work fits. |
| 5. Data and AI | What data and what models? | Clear systems of record. Data contracts. AI behind controls (see below). |
| 6. Platform | Where does it run? | Containers described as Kubernetes YAML. Runs on Podman today, a cluster later, on premises or in a cloud. |
| 7. Trust and operations | How do we stay safe and healthy? | One pipeline with gates. Signed images. Logs sent once. A status page. A product owner after launch. |

## Ten defaults

1. **Start modular.** Keep clear boundaries in the code. Split into services when teams or scale force it.
2. **The API is the contract.** Write it first. Publish it in a catalog.
3. **Config lives in the environment.** Never in the image.
4. **Build once, promote the same artifact.** The image you tested is the image you ship.
5. **Sign what you ship.** Keep a list of what is inside it.
6. **Test low.** Many unit tests, fewer integration tests, very few end-to-end tests.
7. **Accessibility is a gate,** not a late audit.
8. **Log in one common format** and send it once. Use open standards such as OpenTelemetry.
9. **Treat AI as a component with controls,** not magic.
10. **Plan the exit.** Know how you would move this application in a year.

## Choosing a style

No style is best. Pick by the quality you need most.

| Style | Use it when | Watch out for |
|---|---|---|
| Modular monolith **(default)** | One team, one domain | Boundaries erode unless you enforce them. |
| Microservices | Several teams must deploy on their own | Cost and operations load. You need a platform first. |
| Event driven | Many consumers, audit trail, async work | Harder to test and to trace. |
| SaaS or off the shelf | A common capability | Data residency, extension limits, exit. |
| Low code | Simple forms and workflows | Lock-in and weak governance. |
| Serverless | Spiky, small jobs | Limits and ties to one provider. |

The 2022 article leaned on MACH (microservices, API, cloud, headless). The ideas are fine: modular, API based, front end separate. Use them as ideas, not as a shopping list.

Also keep the warning from 2022: a *big ball of mud* is still the most common style. Most of this page is about not building another one.

## AI in the architecture

The federal AI Strategy for 2025–2027 treats AI as something departments will adopt, with trust and transparency as conditions. For an application architect, that means:

- **Put models behind one gateway.** Log requests, set limits, swap models without code changes.
- **Pin and test.** A model has a version. Outputs vary, so keep a set of test questions and re-run it on every change.
- **Keep data where policy says.** On an isolated network, that means a model you host yourself.
- **Keep a human in the loop** for anything that affects a person.
- **Check the Directive on Automated Decision-Making.** If the system makes or supports decisions about clients, an Algorithmic Impact Assessment applies.
- **Show your work.** Tell users when AI is used. Record it in your application inventory.

## Cloud and sovereignty

The old question was "cloud or on premises?" The better question is "who controls it, and can we move?"

Shared Services Canada has launched a procurement for sovereign Canadian cloud capability. What "sovereign" means in practice is still being worked out. So avoid designs that depend on one provider's special services. Classify your data. Keep deployments portable. Write the exit plan now.

## Application health

An application is a product with a life cycle, not a project that ends.

- **Owner and tier.** Every application has a named owner and a criticality tier.
- **One list.** Keep one trusted inventory. Do not keep five.
- **Review dates.** Review each application at least yearly.
- **Retire on purpose.** Name what comes next and by when.

A portfolio where most applications are unhealthy is not fixed by new projects. It is fixed by owning, funding and retiring.

## The go-live gates

Before release, check:

- [ ] A named owner and a criticality tier
- [ ] Backup and recovery written down and *exercised*
- [ ] Accessibility tested, with real assistive tools
- [ ] English and French complete
- [ ] A privacy review done where personal information is used
- [ ] Security scan clean and image signed
- [ ] Logs reaching the enterprise collector, with a heartbeat
- [ ] A status page entry
- [ ] An API entry in the catalog
- [ ] An exit plan, in one paragraph

## What to do next

1. Pick one application and score it against the seven layers.
2. Write down its owner, tier and review date.
3. Put its API in the catalog.
4. Add one missing gate to its pipeline.
5. Write its exit plan.

## Related reading

- [Application Reference Architecture (2022)]({{ '/architecture/application-reference-architecture/' | relative_url }}): the original and long version. Go there for definitions, domain-driven design, SOLID, the 12 factors, event patterns, systems thinking and the full reference list.
- [Creating a Government Website: How the Pieces Fit]({{ '/creating-a-government-website/' | relative_url }}): the map of design, architecture, delivery, hosting, operations and ownership.
- [Intranet Architecture Pattern Catalog]({{ '/architecture/pattern-catalog/' | relative_url }}): repeatable patterns for new features.
- [CI/CD for a Web Platform: The Short Version]({{ '/cicd-for-a-web-platform/' | relative_url }}): the pipeline and its gates.
- [Podman Now, Kubernetes Later]({{ '/podman-now-kubernetes-later/' | relative_url }}): the portable platform rule.
- [Send Logs Once, Route Many]({{ '/send-logs-once-route-many/' | relative_url }}): operations and security monitoring.
- [Running a Web Platform as a Product: A Reading Guide]({{ '/running-a-web-platform-as-a-product/' | relative_url }}): who looks after it after launch.

## Sources

- [Canada's Digital Ambition 2024–25](https://www.canada.ca/en/government/system/digital-government/canada-digital-ambition/canada-digital-ambition-2024-25.html)
- [Government of Canada Enterprise Architecture Framework](https://www.canada.ca/en/government/system/digital-government/policies-standards/government-canada-enterprise-architecture-framework.html)
- [Strategic plans, policies, standards and guidelines related to government digital services](https://www.canada.ca/en/government/system/digital-government/policies-standards.html) (includes the Cloud Strategy 2024 update and the Standards on APIs)
- [Government of Canada Digital Standards](https://www.canada.ca/en/government/system/digital-government/government-canada-digital-standards.html)
- [AI Strategy for the Federal Public Service 2025–2027](https://www.canada.ca/en/government/system/digital-government/digital-government-innovations/responsible-use-ai/gc-ai-strategy-full-text.html)
- [Request for Information: Sovereign Public Cloud Capability](https://canadabuys.canada.ca/en/tender-opportunities/tender-notice/cb-416-17296820)
