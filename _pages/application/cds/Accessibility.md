---
permalink: /application/cds/Accessibility
title: "Accessibility"
excerpt: "Accessibility basics for digital design, what the Accessible Canada Act means for websites (including a public feedback process), and links to standards and sources."
last_modified_at: 2026-10-23T16:00:00-04:00
toc: true
theme: digital
tags: [accessibility, ux, government]
classes: full-width
author_profile: false
---

# Accessibility

The goal is simple: **recognize exclusion and design it out.** Accessibility is not an extra step at the end. It is part of the basics of every design system and every release.

## Design system basics

Build accessibility into the basics[^LogRocket]:

- **Colour contrast:** enough contrast between text and background.
- **Typography:** a large, clear typeface.
- **Images:** meaningful alt text.
- **Iconography:** icons that do not rely on colour alone, with text labels.
- **Spacing and elevation:** clear space, and a clear visual order.
- **Test the system:** check the visuals above, check the keyboard (tab order, no endless loops), and check with a screen reader.

For the stage-by-stage view, from discovery to live, see [CDS Accessibility]({{ '/application/cds/CDS-Accessibility' | relative_url }}).

## WCAG: the standard to measure against

The [Web Content Accessibility Guidelines (WCAG)](https://www.w3.org/WAI/standards-guidelines/wcag/) have three levels:

1. **Level A:** the basic level of accessibility.
2. **Level AA:** everything in Level A plus extra requirements. This is the usual benchmark in industry and in government.
3. **Level AAA:** the highest level. It includes A and AA, plus more.

## The Accessible Canada Act and your website

The [Accessible Canada Act](https://laws-lois.justice.gc.ca/eng/acts/a-0.6/) aims for a Canada without barriers by 2040. It applies to federally regulated organizations, including federal government bodies, the Canadian Forces, the RCMP, certain Parliamentary entities, and some businesses such as banks and airlines.[^ACA]

It sets out **seven priority areas**. Two matter most for digital teams:

- **[Information and communication technologies (ICT)](https://accessible.canada.ca/node/228):** websites, applications, documents and tools.
- **[Design and delivery of programs and services](https://accessible.canada.ca/priority-areas-guide-our-work/design-and-delivery-programs-and-services):** the online service itself, not only the technology under it. Accessibility Standards Canada also publishes a [technical guide](https://accessible.canada.ca/creating-accessibility-standards/design-and-delivery-accessible-programs-and-services-including-customer-services) for this area.

**The ICT standard: CAN/ASC - EN 301 549:2024.** Accessibility Standards Canada adopted the European standard EN 301 549:2021 as the Canadian standard for ICT, [published in May 2024](https://accessible.canada.ca/creating-accessibility-standards/summary-can-asc-en-301-5492024-accessibility-requirements-ict-products-and-services-en-301-5492021-idt). It covers web content, non-web documents, software and hardware, plus functional performance, two-way voice and video, support services and relay services. It is aimed at private and public organizations in federally regulated sectors. The summary does not say whether it is already required by regulation, so confirm that with your accessibility or legal advisors. The Standards Council of Canada also has a [notice for the standard](https://scc-ccn.ca/standards/notices-of-intent/accessibility-standards-canada/accessibility-requirements-ict-products).

The other areas are employment, the built environment, communication other than ICT, procurement, and transportation. Procurement matters too: what you buy should be accessible.

### Three things organizations must do

1. **Accessibility plan.** Describe how you will find, remove and prevent barriers. Update and publish it every three years. Prepare it with input from people with disabilities.
2. **Feedback process.** Let people tell you about barriers and about your plan. Describe the process on your website, and name the position responsible for receiving feedback. Acknowledge feedback through the same channel it came in on (anonymous feedback is the exception).
3. **Progress reports.** Show how the plan is going, how you used the feedback, and how you consulted people with disabilities.

First plans were due on 31 December 2022 for the federal government, Crown corporations, Parliamentary entities, the RCMP and the Canadian Forces. Large businesses (100 or more employees) were due on 1 June 2023, and small businesses (10 to 99) on 1 June 2024.[^ACA]

### What this means for a digital site

- **Every site needs a way to give accessibility feedback.** Put a clear link in a place people can find, such as the footer and the contact page. Make it easy to use with a form, an email address and a phone number.
- **The feedback description must itself be accessible.** The guidance says the digital version must meet WCAG 2.1 Level AA, be written in simple, clear and concise language, and be available on request in print, large print, Braille, audio and electronic formats.[^Feedback]
- **Someone must own the feedback.** Name the role, not just the inbox. Acknowledge each message and track it like any other product issue.
- **Feedback should drive the backlog.** Barriers reported by real users feed the accessibility plan and the next progress report. This links to the idea of [content owners acting on flags]({{ '/automation-flags-people-decide/' | relative_url }}): route each barrier to the person who can fix it.
- **Plans and progress reports must be accessible too,** and must be updated on schedule.
- **Procurement counts.** Ask vendors for accessible products and evidence, and test what you buy.

For Government of Canada sites, also check the Treasury Board [Standard on Web Accessibility](https://www.tbs-sct.canada.ca/pol/doc-eng.aspx?id=23601) for the current technical requirements, and the Canada.ca [accessibility standards and guidance](https://a11y.canada.ca/en/accessibility-standards/).

# References

## Standards and law

- [Web Content Accessibility Guidelines](https://www.w3.org/WAI/standards-guidelines/wcag/)
- [Accessible Canada Act](https://laws-lois.justice.gc.ca/eng/acts/a-0.6/)
- [Summary of the Accessible Canada Regulations](https://www.canada.ca/en/employment-social-development/programs/accessible-canada/regulations-summary-act.html)
- [Feedback process descriptions: publishing and handling](https://www.canada.ca/en/employment-social-development/programs/accessible-canada-regulations-guidance/feedback-process/publishing-handling.html)
- [CAN/ASC - EN 301 549:2024 summary (Accessibility Standards Canada)](https://accessible.canada.ca/creating-accessibility-standards/summary-can-asc-en-301-5492024-accessibility-requirements-ict-products-and-services-en-301-5492021-idt)
- [Standard on Web Accessibility (Treasury Board)](https://www.tbs-sct.canada.ca/pol/doc-eng.aspx?id=23601)
- USA: [Section 508](https://www.section508.gov/), *Accessibility of Federal Electronic and Information Technology*, reported to Congress and the President.

## Toolkits

- [Microsoft Inclusive Design Toolkit](https://www.microsoft.com/design/inclusive/)
- [IBM Equal Access Toolkit](https://www.ibm.com/able/toolkit/design/overview/)

## Digital government standards

- [Australia Digital Government](https://www.dta.gov.au/)
- [New Zealand Digital Government](https://www.digital.govt.nz/)
- [UK Government Digital Service](https://gds.blog.gov.uk/)
- [USA Digital Service](https://www.usds.gov/)

## Background: the Canadian Digital Service (CDS)

- [CDS](https://digital.canada.ca/) was created in response to the 2013 and [2016 Auditor General](https://www.oag-bvg.gc.ca/internet/English/parl_oag_201611_00_e_41829.html) reports. They found that online services were not focused on the needs of Canadians, and were complex and time-consuming. The reports used the Standish Group's annual [Chaos reports](https://standishgroup.myshopify.com/) as a reference. The made-in-Canada design of CDS was based on a review of its international predecessors (especially in the United States and the United Kingdom) and on [a public engagement process across Canada](https://digital.canada.ca/beginning-the-conversation/).
  - Note: Canada no longer has a Minister of Digital Government. The last minister was Joyce Murray, whose term ended in 2021. The minister was responsible for Shared Services Canada (SSC), which has since returned to the Minister of Public Services and Procurement.
  - [How CDS Started (2017)](https://digital.canada.ca/how-cds-started/full-report/) describes the case for digital government. It refers to the Organisation for Economic Co-operation and Development (OECD)[^Digital]. The case points to the UK, USA and Australia, which focused on user-centric service innovation, rapid prototyping, procurement reform and better use of data. In Canada, Ontario was recognized as a pathfinder with the [Ontario Digital Service](https://ontario.ca/digital).
- **CDS mandate:** CDS was launched in July 2017 to change the way the government designs and delivers services. It was asked to:
  - deliver services by partnering with departments and building prototypes of user-centric services;
  - build the capacity of departments to apply modern service design and technology methods and tools; and
  - provide advice on key technology and service investments.
- [TBS evaluation of CDS by Goss Gilroy Inc.](https://www.canada.ca/en/treasury-board-secretariat/corporate/reports/evaluation-canadian-digital-service.html) Goss Gilroy also did the [Phoenix Lessons Learned](https://www.canada.ca/en/treasury-board-secretariat/corporate/reports/lessons-learned-transformation-pay-administration-initiative.html). Results:
  - effective at agile digital delivery based on continuous improvement;
  - less effective at meeting departments' needs, because it relied on partners embracing change;
  - product partnerships increased capacity, but post-partnership challenges remain;
  - tension exists in applying user-centred methods; and
  - constraining factors were limited partnerships, legacy partner systems, a lack of expertise and skills in departments, the need for government-wide culture change, and a lack of clarity on the CDS mandate.
- [Canada's Digital Ambition](https://www.canada.ca/en/government/system/digital-government/government-canada-digital-operations-strategic-plans/canada-digital-ambition.html) recognizes CDS for developing tools following GOV.UK, including GC Notify and GC Forms.

[^LogRocket]: LogRocket, [How to build accessible design](https://blog.logrocket.com/ux-design/how-to-build-accessible-design-system/). Accessibility guidelines give designers the tools and knowledge to make designs usable by everyone, regardless of ability.
[^ACA]: Employment and Social Development Canada, [Summary of the Accessible Canada Regulations](https://www.canada.ca/en/employment-social-development/programs/accessible-canada/regulations-summary-act.html).
[^Feedback]: Employment and Social Development Canada, [Descriptions of feedback processes: publishing and handling your feedback process description](https://www.canada.ca/en/employment-social-development/programs/accessible-canada-regulations-guidance/feedback-process/publishing-handling.html).
[^Digital]: The OECD defines digital government as *the rethinking of government policy, program and service delivery through digital enablers, as an integrated part of governments' modernization strategies, to create public value. [Digital government] relies on and enables an ecosystem that connects government, non-governmental organizations, businesses, citizens' associations and individuals to support the production of and access to data, services and content through interactions with the government.*
