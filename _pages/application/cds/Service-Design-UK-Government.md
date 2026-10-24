---
title: "Service Design UK Government"
excerpt: "How the UK government designs and runs public services: the Service Standard, the delivery phases, the Design System, and where it is heading."
permalink: /application/cds/Service-Design-UK-Government
layout: single
author_profile: false
classes: wide-text
toc: true
toc_sticky: true
toc_label: "Contents"
theme: digital
tags: ["service design", government, ux]
classes: full-width
author_profile: false
---

The UK Government Digital Service (GDS) is widely seen as a leader in making service design a normal part of public service delivery, and many other governments, including Canada, draw on its approach. This page explains how the UK approach works, what has changed recently, and what is worth taking from it.

It is based on public GDS material (listed under Sources). The Service Standard is being reworked at the time of writing, so check the original sources before relying on any detail.

## The short version

- **One standard.** Every UK government service is expected to meet the same 14-point Service Standard.
- **One method.** Teams work in four phases: discovery, alpha, beta and live. Each phase ends with a decision.
- **One kit.** The Service Manual explains how, and the GOV.UK Design System supplies tested components so teams do not redesign a date field.
- **A change in direction (2026).** GDS is moving the Standard from a one-off test to a "living system" for the whole life of a service, including the non-digital parts.

## Journey, service and transaction

Three words are used precisely in UK guidance, and mixing them up causes most scoping arguments.

- A **user journey** follows a person from the moment a need arises to the moment they stop using the service. It can cross many services and many departments.
- A **service** is what an organization provides to meet part of that need.
- A **transaction** is one task inside a service, such as filling in a form or paying a fee.

A **user journey map** shows the journey over time. GDS has used them across government since at least 2016, because the person's problem rarely matches the organization chart. GOV.UK guidance on [scoping your service](https://www.gov.uk/service-manual/design/scoping-your-service) covers how transactions join up with the wider journey.

<div markdown="0" class="diagram">
<svg viewBox="0 0 900 250" role="img" aria-labelledby="d1t" style="width:100%;height:auto;max-width:900px">
<title id="d1t">A user journey contains services, and each service contains transactions</title>
<rect x="10" y="10" width="880" height="230" rx="8" fill="#f4f4f4" stroke="#8c8c8c" stroke-width="2"/>
<text x="26" y="36" font-size="15" font-weight="700" fill="#333">User journey</text>
<text x="124" y="36" font-size="13" fill="#595959">from the moment a need arises to the moment they stop using the service</text>
<rect x="30" y="56" width="410" height="150" rx="6" fill="#ffffff" stroke="#8c8c8c" stroke-width="1.5"/>
<text x="44" y="80" font-size="14" font-weight="700" fill="#333">Service A</text>
<rect x="44" y="96" width="110" height="46" rx="4" fill="#e9e9e9" stroke="#8c8c8c"/><text x="99" y="124" font-size="12" text-anchor="middle" fill="#333">Transaction</text>
<rect x="166" y="96" width="110" height="46" rx="4" fill="#e9e9e9" stroke="#8c8c8c"/><text x="221" y="124" font-size="12" text-anchor="middle" fill="#333">Transaction</text>
<rect x="288" y="96" width="140" height="46" rx="4" fill="#e9e9e9" stroke="#8c8c8c"/><text x="358" y="124" font-size="12" text-anchor="middle" fill="#333">Transaction</text>
<text x="44" y="176" font-size="12" fill="#595959">Owned by one team or department</text>
<rect x="470" y="56" width="400" height="150" rx="6" fill="#ffffff" stroke="#8c8c8c" stroke-width="1.5"/>
<text x="484" y="80" font-size="14" font-weight="700" fill="#333">Service B</text>
<rect x="484" y="96" width="120" height="46" rx="4" fill="#e9e9e9" stroke="#8c8c8c"/><text x="544" y="124" font-size="12" text-anchor="middle" fill="#333">Transaction</text>
<rect x="616" y="96" width="120" height="46" rx="4" fill="#e9e9e9" stroke="#8c8c8c"/><text x="676" y="124" font-size="12" text-anchor="middle" fill="#333">Transaction</text>
<text x="484" y="176" font-size="12" fill="#595959">Often a different department</text>
<path d="M440 131 H470" stroke="#333" stroke-width="2" stroke-dasharray="5 4"/>
<text x="455" y="196" font-size="11" text-anchor="middle" fill="#595959">hand-off</text>
<text x="880" y="230" font-size="11" text-anchor="end" fill="#595959">Illustrative structure, not an official map</text>
</svg>
</div>

The practical lesson: scope the service around the person's problem, then find out which organizations and channels it crosses. A service blueprint (see [From strawman to blueprint]({{ '/journey-map-and-service-blueprint/' | relative_url }})) is the tool for showing the staff work and systems behind each step.

## The Service Standard

The Service Standard says what good looks like. It started in 2013 as the Digital by Default Service Standard, alongside the first Service Design Manual, and came into force across government in 2014. It has been revised several times since. GDS describes the Standard, the Service Manual and the Service Toolkit as a set: the Standard defines good, the Manual explains how to get there, and the Toolkit helps teams find tools and resources.

The 14 points are:

1. Understand users and their needs
2. Solve a whole problem for users
3. Provide a joined-up experience across channels
4. Make the service simple to use
5. Make sure everyone can use the service
6. Have a multidisciplinary team
7. Use agile ways of working
8. Iterate and improve frequently
9. Create a secure service which protects users' privacy
10. Define what success looks like and publish performance data
11. Choose the right tools and technology
12. Make new source code open
13. Use and contribute to open standards, common components and patterns
14. Operate a reliable service

The diagram groups them by theme. The grouping is mine, not GDS's. It shows that most of the points are about people and ways of working, not technology.

<div markdown="0" class="diagram">
<svg viewBox="0 0 900 360" role="img" aria-labelledby="d3t" style="width:100%;height:auto;max-width:900px">
<title id="d3t">The 14 Service Standard points grouped into four themes</title>
<rect x="10" y="10" width="435" height="180" rx="6" fill="#f4f4f4" stroke="#8c8c8c" stroke-width="1.5"/>
<text x="26" y="36" font-size="15" font-weight="700" fill="#333">Design for people</text>
<text x="26" y="62" font-size="13" fill="#333">1  Understand users and their needs</text>
<text x="26" y="86" font-size="13" fill="#333">2  Solve a whole problem for users</text>
<text x="26" y="110" font-size="13" fill="#333">3  Joined-up experience across channels</text>
<text x="26" y="134" font-size="13" fill="#333">4  Make the service simple to use</text>
<text x="26" y="158" font-size="13" fill="#333">5  Make sure everyone can use the service</text>
<rect x="455" y="10" width="435" height="180" rx="6" fill="#f4f4f4" stroke="#8c8c8c" stroke-width="1.5"/>
<text x="471" y="36" font-size="15" font-weight="700" fill="#333">Work as a team</text>
<text x="471" y="62" font-size="13" fill="#333">6  Have a multidisciplinary team</text>
<text x="471" y="86" font-size="13" fill="#333">7  Use agile ways of working</text>
<text x="471" y="110" font-size="13" fill="#333">8  Iterate and improve frequently</text>
<text x="471" y="150" font-size="12" fill="#595959">Skills and cadence, not just tools.</text>
<rect x="10" y="200" width="435" height="150" rx="6" fill="#f4f4f4" stroke="#8c8c8c" stroke-width="1.5"/>
<text x="26" y="226" font-size="15" font-weight="700" fill="#333">Build and run it well</text>
<text x="26" y="252" font-size="13" fill="#333">9   Secure, and protects users' privacy</text>
<text x="26" y="276" font-size="13" fill="#333">11  Choose the right tools and technology</text>
<text x="26" y="300" font-size="13" fill="#333">14  Operate a reliable service</text>
<rect x="455" y="200" width="435" height="150" rx="6" fill="#f4f4f4" stroke="#8c8c8c" stroke-width="1.5"/>
<text x="471" y="226" font-size="15" font-weight="700" fill="#333">Measure and be open</text>
<text x="471" y="252" font-size="13" fill="#333">10  Define success, publish performance data</text>
<text x="471" y="276" font-size="13" fill="#333">12  Make new source code open</text>
<text x="471" y="300" font-size="13" fill="#333">13  Open standards, common components, patterns</text>
</svg>
</div>

Two points are worth singling out because they are less common elsewhere:

- **Point 10** requires teams to publish how the service performs, so the public and other teams can see it.
- **Points 12 and 13** push teams to open their code and reuse common components. This is why UK government has a shared Design System and shared platforms instead of every department building its own.

The NHS service standard contains the same 14 points, then adds three health and social care points (15 to 17). That is a useful pattern: a shared core with a sector layer on top.

## The delivery phases

The Service Manual describes four phases of agile delivery, plus the end of a service's life.

- **Discovery.** Learn about the problem before building anything. Talk to users, explore policy, technology and budget constraints, define success, and start a high-level roadmap. Funding is small. The question is whether change is justified.
- **Alpha.** Test possible solutions. Build prototypes of different approaches, research with a small group of users, and work out which approaches to keep.
- **Beta.** Build a working service and widen the audience. A private beta runs with a small audience. A public beta is open to anyone and still being improved. Reliability, accessibility and readiness to scale are tested here.
- **Live.** The service is open to everyone. The Manual is clear that agile delivery does not end at go-live: teams track performance, respond to feedback and policy change, and keep improving.
- **Retirement.** Services end too, and the Manual has guidance for retiring one properly.

Each phase ends with a checkpoint so leaders can decide whether to continue, change direction or stop, while teams stay flexible within the phase.

<div markdown="0" class="diagram">
<svg viewBox="0 0 900 300" role="img" aria-labelledby="d2t" style="width:100%;height:auto;max-width:900px">
<title id="d2t">Delivery phases from discovery to retirement, with checkpoints between them</title>
<defs><marker id="a2" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="8" markerHeight="8" orient="auto-start-reverse"><path d="M0,0 L10,5 L0,10 z" fill="#333"/></marker></defs>
<g font-size="12" fill="#333">
<rect x="10" y="30" width="150" height="110" rx="6" fill="#f4f4f4" stroke="#8c8c8c" stroke-width="1.5"/>
<text x="85" y="55" font-size="15" font-weight="700" text-anchor="middle">Discovery</text>
<text x="85" y="78" text-anchor="middle">Understand the problem</text><text x="85" y="94" text-anchor="middle">Talk to users</text><text x="85" y="110" text-anchor="middle">Define success</text>
<rect x="190" y="30" width="150" height="110" rx="6" fill="#f4f4f4" stroke="#8c8c8c" stroke-width="1.5"/>
<text x="265" y="55" font-size="15" font-weight="700" text-anchor="middle">Alpha</text>
<text x="265" y="78" text-anchor="middle">Prototype options</text><text x="265" y="94" text-anchor="middle">Test with a few users</text><text x="265" y="110" text-anchor="middle">Pick what to build</text>
<rect x="370" y="30" width="170" height="110" rx="6" fill="#f4f4f4" stroke="#8c8c8c" stroke-width="1.5"/>
<text x="455" y="55" font-size="15" font-weight="700" text-anchor="middle">Beta</text>
<text x="455" y="78" text-anchor="middle">Build the real service</text><text x="455" y="94" text-anchor="middle">Private, then public beta</text><text x="455" y="110" text-anchor="middle">Make it ready to scale</text>
<rect x="570" y="30" width="150" height="110" rx="6" fill="#f4f4f4" stroke="#8c8c8c" stroke-width="1.5"/>
<text x="645" y="55" font-size="15" font-weight="700" text-anchor="middle">Live</text>
<text x="645" y="78" text-anchor="middle">Open to everyone</text><text x="645" y="94" text-anchor="middle">Measure and improve</text><text x="645" y="110" text-anchor="middle">Respond to change</text>
<rect x="750" y="30" width="140" height="110" rx="6" fill="#ffffff" stroke="#8c8c8c" stroke-width="1.5" stroke-dasharray="6 4"/>
<text x="820" y="55" font-size="15" font-weight="700" text-anchor="middle">Retirement</text>
<text x="820" y="85" text-anchor="middle">Retire the service</text><text x="820" y="101" text-anchor="middle">properly</text>
</g>
<g stroke="#333" stroke-width="2" fill="none">
<line x1="160" y1="85" x2="188" y2="85" marker-end="url(#a2)"/>
<line x1="340" y1="85" x2="368" y2="85" marker-end="url(#a2)"/>
<line x1="540" y1="85" x2="568" y2="85" marker-end="url(#a2)"/>
<line x1="720" y1="85" x2="748" y2="85" marker-end="url(#a2)"/>
</g>
<g fill="#333" font-size="11">
<circle cx="175" cy="168" r="9" fill="#ffffff" stroke="#333" stroke-width="2"/><text x="175" y="172" text-anchor="middle" font-size="10">1</text>
<circle cx="355" cy="168" r="9" fill="#ffffff" stroke="#333" stroke-width="2"/><text x="355" y="172" text-anchor="middle" font-size="10">2</text>
<circle cx="555" cy="168" r="9" fill="#ffffff" stroke="#333" stroke-width="2"/><text x="555" y="172" text-anchor="middle" font-size="10">3</text>
<line x1="175" y1="140" x2="175" y2="159" stroke="#8c8c8c" stroke-dasharray="3 3"/>
<line x1="355" y1="140" x2="355" y2="159" stroke="#8c8c8c" stroke-dasharray="3 3"/>
<line x1="555" y1="140" x2="555" y2="159" stroke="#8c8c8c" stroke-dasharray="3 3"/>
</g>
<g font-size="12" fill="#333">
<text x="20" y="206"><tspan font-weight="700">1</tspan> Is change justified? Fund alpha.</text>
<text x="20" y="226"><tspan font-weight="700">2</tspan> Which solution is worth building? Fund beta.</text>
<text x="20" y="246"><tspan font-weight="700">3</tspan> Is it safe and ready for everyone? Go live (assessed against the Standard).</text>
</g>
<text x="890" y="288" font-size="11" text-anchor="end" fill="#595959">Live is not the end: the team keeps funding and improving.</text>
</svg>
</div>

### Assessments

Services are assessed against the Standard at key points between alpha, beta and live. The assessment report gives feedback, not just a result: praise for what works, suggested improvements, and comments on ways of working. In 2020 GDS said a service that passed public beta should get its live assessment soon, with a default of 6 to 12 months, so legacy services could be switched off with more confidence. It also proposed pilot reviews of services already live, using a half-day session and a multidisciplinary panel of assessors from other departments, to catch problems after launch.

The weakness of this model is the one GDS now names itself: it can turn the Standard into a test to pass rather than a way of working.

## The team

Point 6 asks for a multidisciplinary team. GDS careers list the disciplines that service work draws on:

- Content design
- Design
- User research
- Data science
- Software engineering
- Technical architecture
- Delivery management
- Product management

The idea is that no single discipline can own a service. A product manager owns the problem and priorities, a user researcher brings the evidence, a designer and content designer make it understandable, engineers and architects make it work and keep it secure, and a delivery manager keeps the team moving.

## Reusable parts: the Design System and shared platforms

The Standard asks teams to reuse common components and patterns. In practice that means the GOV.UK Design System, a set of tested components (buttons, forms, date fields, error messages) and patterns (such as asking for an address), delivered through GOV.UK Frontend code. A team starts from something that already works for people with different needs, instead of designing and testing its own.

The Design System keeps moving. GOV.UK Frontend had a major release (v6.0.0) in February 2026 with changes to the Sass architecture, type scale, colours and page template layout. Releases since then added a generic header component for services outside the GOV.UK proposition (June 2026), an interruption variant of the Panel component (July 2026), and new Feedback and Language navigation components released as trial components (August 2026). New components start as "trial", so they can be tried in real services before they are called stable.

Beyond components there are shared platforms. GDS's January 2026 roadmap lists the GOV.UK app, GOV.UK Wallet and GOV.UK One Login among the things that join services up. At that point it reported One Login used by more than 13 million people for more than 120 services, and the GOV.UK app in public beta since July 2025.

<div markdown="0" class="diagram">
<svg viewBox="0 0 900 330" role="img" aria-labelledby="d6t" style="width:100%;height:auto;max-width:900px">
<title id="d6t">The family of UK government service design products, from the Standard down to shared platforms</title>
<g font-size="13" fill="#333">
<rect x="10" y="10" width="880" height="62" rx="6" fill="#f4f4f4" stroke="#8c8c8c" stroke-width="1.5"/>
<text x="26" y="36" font-size="15" font-weight="700">Service Standard</text><text x="26" y="58">What good looks like: the 14 points</text>
<rect x="10" y="82" width="880" height="62" rx="6" fill="#f4f4f4" stroke="#8c8c8c" stroke-width="1.5"/>
<text x="26" y="108" font-size="15" font-weight="700">Service Manual</text><text x="26" y="130">How to do it: delivery phases, user research, design, technology guidance</text>
<rect x="10" y="154" width="880" height="62" rx="6" fill="#f4f4f4" stroke="#8c8c8c" stroke-width="1.5"/>
<text x="26" y="180" font-size="15" font-weight="700">Service Toolkit</text><text x="26" y="202">Tools and resources teams can find and use</text>
<rect x="10" y="226" width="430" height="94" rx="6" fill="#ffffff" stroke="#8c8c8c" stroke-width="1.5"/>
<text x="26" y="252" font-size="15" font-weight="700">Design System and GOV.UK Frontend</text><text x="26" y="274">Tested components and patterns</text><text x="26" y="294">Reuse instead of redesign</text>
<rect x="460" y="226" width="430" height="94" rx="6" fill="#ffffff" stroke="#8c8c8c" stroke-width="1.5"/>
<text x="476" y="252" font-size="15" font-weight="700">Shared platforms</text><text x="476" y="274">GOV.UK One Login, GOV.UK app, GOV.UK Wallet</text><text x="476" y="294">Build once, use across services</text>
</g>
</svg>
</div>

## Joining services up

The 2025 blueprint and the January 2026 roadmap push in one direction: services should join up around the person's life events, not the organization chart. Examples in the roadmap include a digital Veteran Card (the first credential in the GOV.UK Wallet, with a digital driving licence in testing) and CustomerFirst, a GDS unit launched in January 2026 that combines AI and service design to reduce waiting times and backlogs, starting with the Driver and Vehicle Licensing Agency (DVLA). The roadmap also states a target that one in ten civil servants work in tech and digital roles by 2030, and a move from short funding cycles to continuous funding for product teams.

That last point matters for service design. A service funded as a project stops being designed when the project ends. A service funded as a product keeps a team.

## Designing for everyone

GDS's inclusive services work (reported December 2025) starts from the fact that a digital-first service can exclude people who are not confident online or cannot get the right device or connection. It sits under the services pillar of the February 2025 Digital Inclusion Action Plan, which has four pillars: skills, access, services and trust. The workstream has three goals:

- Update the Service Manual and Service Standard with more practical guidance on inclusive design.
- Create a consistent measure of whether digital services reach and work for the people who need them.
- Build a cross-government community of practice.

Early findings were practical: teams want blueprints and shared language for digital exclusion, case studies with overlapping needs, and designed alternative routes for people who cannot use digital channels. A public comment on the post made a fair point worth keeping in mind: pushing everything online can increase repeat contact when people struggle to describe a complex situation in a form, so services need both digital and direct channels.

## Where it is heading (2026)

In July 2026 GDS announced it will evolve the Service Standard "from a one-off test into a living standard for modern, end-to-end public services". It says the current Standard is a successful baseline, and gives four reasons for the change:

- It is closely tied to assessments at delivery stages, not to continuous improvement of operations.
- It is hard to apply consistently to services that span organizations and channels.
- It was designed for an earlier era and does less to support modernizing legacy services.
- It was developed with limited co-design, so there is no shared cross-government view of "good".

The direction has four parts. A shared, evolving standards framework replaces a single standard. Standards are developed with more input from departments, local government and partners. A new service helps organizations apply the standards in practice, not only assess against them. And the Service Manual, Standard and tools are more closely connected.

GDS says the work is at an early stage, with no dates yet, and that it will share a roadmap. Readers commented that small, niche business services face the same assessment burden as large citizen services, and GDS replied that looking beyond the citizen lens is in scope.

<div markdown="0" class="diagram">
<svg viewBox="0 0 900 270" role="img" aria-labelledby="d5t" style="width:100%;height:auto;max-width:900px">
<title id="d5t">From a static, assessment-led Standard to a living system covering the whole service life cycle</title>
<defs><marker id="a5" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="8" markerHeight="8" orient="auto-start-reverse"><path d="M0,0 L10,5 L0,10 z" fill="#333"/></marker></defs>
<rect x="10" y="10" width="380" height="250" rx="6" fill="#f4f4f4" stroke="#8c8c8c" stroke-width="1.5"/>
<text x="26" y="36" font-size="15" font-weight="700" fill="#333">Today: assessment-led</text>
<g font-size="13" fill="#333">
<text x="26" y="64">One standard, one set of criteria</text>
<text x="26" y="86">Checked at delivery stages</text>
<text x="26" y="108">Focus on the digital build</text>
<text x="26" y="130">Something you pass</text>
</g>
<line x1="30" y1="190" x2="370" y2="190" stroke="#8c8c8c" stroke-width="2"/>
<g fill="#ffffff" stroke="#333" stroke-width="2"><circle cx="100" cy="190" r="9"/><circle cx="200" cy="190" r="9"/><circle cx="300" cy="190" r="9"/></g>
<text x="100" y="222" font-size="11" text-anchor="middle" fill="#333">gate</text><text x="200" y="222" font-size="11" text-anchor="middle" fill="#333">gate</text><text x="300" y="222" font-size="11" text-anchor="middle" fill="#333">gate</text>
<line x1="400" y1="135" x2="500" y2="135" stroke="#333" stroke-width="3" marker-end="url(#a5)"/>
<rect x="510" y="10" width="380" height="250" rx="6" fill="#ffffff" stroke="#8c8c8c" stroke-width="1.5"/>
<text x="526" y="36" font-size="15" font-weight="700" fill="#333">Direction: a living system</text>
<g font-size="13" fill="#333">
<text x="526" y="64">A framework of standards that evolves</text>
<text x="526" y="86">Continuous improvement, whole life cycle</text>
<text x="526" y="108">End-to-end, including non-digital parts</text>
<text x="526" y="130">Something you demonstrate every day</text>
</g>
<path d="M600 205 A60 40 0 1 1 800 205" fill="none" stroke="#8c8c8c" stroke-width="2"/>
<path d="M800 205 A60 40 0 1 1 600 205" fill="none" stroke="#333" stroke-width="2" marker-end="url(#a5)"/>
<text x="700" y="200" font-size="12" text-anchor="middle" fill="#333">measure, learn, improve</text>
</svg>
</div>

In late September 2026 GDS also updated the Government Functional Standard for Digital (its biggest update since it took effect in 2023) to include proportionate references to AI. References to AI went from one to more than 60. It asks organizations to explain how AI will be used safely and lawfully, to keep human oversight, and to use AI only where there is clear evidence that it meets user needs.

## How the standard has changed over time

<div markdown="0" class="diagram">
<svg viewBox="0 0 900 250" role="img" aria-labelledby="d4t" style="width:100%;height:auto;max-width:900px">
<title id="d4t">Timeline of the UK Service Standard and related GDS milestones, 2013 to 2026</title>
<line x1="20" y1="125" x2="880" y2="125" stroke="#8c8c8c" stroke-width="3"/>
<g font-size="12" fill="#333" text-anchor="middle">
<circle cx="50" cy="125" r="7" fill="#333"/><text x="50" y="105" font-weight="700">2013</text><text x="50" y="82" font-size="11">Service Manual and</text><text x="50" y="96" font-size="11">first Standard</text>
<circle cx="150" cy="125" r="7" fill="#333"/><text x="150" y="155" font-weight="700">2014</text><text x="150" y="172" font-size="11">In force across</text><text x="150" y="186" font-size="11">government</text>
<circle cx="250" cy="125" r="7" fill="#333"/><text x="250" y="105" font-weight="700">2015</text><text x="250" y="82" font-size="11">Revised and</text><text x="250" y="96" font-size="11">shortened</text>
<circle cx="350" cy="125" r="7" fill="#333"/><text x="350" y="155" font-weight="700">2019</text><text x="350" y="172" font-size="11">Updated to the</text><text x="350" y="186" font-size="11">14 points</text>
<circle cx="450" cy="125" r="7" fill="#333"/><text x="450" y="105" font-weight="700">2020</text><text x="450" y="82" font-size="11">Community-led</text><text x="450" y="96" font-size="11">approach</text>
<circle cx="550" cy="125" r="7" fill="#333"/><text x="550" y="155" font-weight="700">Jan 2025</text><text x="550" y="172" font-size="11">Blueprint for modern</text><text x="550" y="186" font-size="11">digital government</text>
<circle cx="650" cy="125" r="7" fill="#333"/><text x="650" y="105" font-weight="700">Jan 2026</text><text x="650" y="82" font-size="11">Roadmap to 2030,</text><text x="650" y="96" font-size="11">CustomerFirst</text>
<circle cx="750" cy="125" r="7" fill="#333"/><text x="750" y="155" font-weight="700">Jul 2026</text><text x="750" y="172" font-size="11">Standard to become</text><text x="750" y="186" font-size="11">a living system</text>
<circle cx="850" cy="125" r="7" fill="#333"/><text x="850" y="105" font-weight="700">Oct 2026</text><text x="850" y="82" font-size="11">Digital standard</text><text x="850" y="96" font-size="11">updated for AI</text>
</g>
</svg>
</div>

## What to take from it

These are my own judgements, not GDS positions.

1. **Use a standard as a way of working, not a gate.** GDS's own diagnosis is that a test to pass is not enough. A department standard should describe practice teams use every day.
2. **Name the disciplines.** Point 6 works because it lists the roles. A project plan that has no user researcher or content designer does not meet it.
3. **Scope to the person's problem.** Start from the journey, then find the organizations and systems behind it.
4. **Publish performance.** Point 10 is a cheap way to build trust and find problems early.
5. **Reuse before building.** A shared design system and shared platforms stop every team solving the same problem.
6. **Plan for the whole life.** Fund and staff services as products, and plan the end of life.
7. **Design the non-digital parts.** GDS now says services include operational and non-digital elements. Call centres, paper and staff work belong in the design, which is what a service blueprint shows.
8. **Keep a direct channel.** Digital inclusion work shows why.

## Sources

- [Evolving the Service Standard for the future of public services](https://gds.blog.gov.uk/2026/07/02/evolving-the-service-standard-for-the-future-of-public-services/), GDS blog, 2 July 2026
- [GDS to reinvent Service Standard in shift from a static assessment to living system](https://www.civilserviceworld.com/professions/article/gds-to-reinvent-service-standard-in-shift-from-a-static-assessment-to-living-system), Civil Service World
- [GDS makes AI updates to government's digital governance standards](https://www.publictechnology.net/2026/10/05/education-and-skills/gds-makes-ai-updates-to-governments-digital-governance-standards/), PublicTechnology, 5 October 2026
- [Our roadmap for modern digital government](https://gds.blog.gov.uk/2026/01/20/our-roadmap-for-modern-digital-government), GDS blog, January 2026
- [Designing public services that work for everyone](https://gds.blog.gov.uk/2025/12/10/designing-public-services-that-work-for-everyone/), GDS blog, 10 December 2025
- [GOV.UK Design System: what's new](https://design-system.service.gov.uk/community/whats-new)
- [Service assessments: improvements and life after live](https://services.blog.gov.uk/2020/02/05/service-assessments-improvements-life-after-live/), 2020
- [The phases of agile delivery](https://digitalpublicservices.gov.wales/guidance-and-standards/service-manual/delivering-services-agile-way/the-phases-of-agile-delivery), Digital Public Services for Wales, drawing on the GOV.UK Service Manual
- [NHS service standard](https://service-manual.nhs.uk/service-standard)
- [Why we use user journey maps in government](https://designnotes.blog.gov.uk/2016/03/30/why-we-use-user-journey-maps-in-government/), GDS Design Notes, 2016
- [Scoping your service](https://www.gov.uk/service-manual/design/scoping-your-service), GOV.UK Service Manual
- [GDS careers](https://gdscareers.gov.uk/)
