---
permalink: /application/devops/AZ-400-Continuous-Feedback
title: "Continuous Feedback"
excerpt: "Feedback to the DevOps team using various tools capturing telemetry metrics and presenting dashboards and alerts."
last_modified_at: 2023-01-07T10:23:16-04:00
toc: true
---

# AZ-400 Continuous Feedback

Inner Loop: a software engineering term.

- the inner loop is the iterative process that a developer does when writing, building, and debugging code.
- the right set of steps done repeatedly before sharing their work with their team or the rest of the world.
  - C# loop might be Code, Build, Test
  - WebDev loop might be: Code, Run Webpack, Refresh Browser

Categorize inner loop steps:

- Coding (Experimentation)
- Building (Feedback Collection)
- Testing / Debugging (Feedback Collection)
- Committing (Tax)

Loop optimization

- loop execution time should be proportional to changes, and the desire is to execute the loop as quickly as possible
- minimize time to get feedback (from build & test steps)
- minimize waste (tax steps - time to commit)
- code complexity increase the size of the inner loop (increasing time and waste)

Optimization steps:

- modularize monoliths (reduce code complexity)
- Only build and test what was changed.
- Cache intermediate build results to speed up to complete builds.
- Break up the codebase into small units and share binaries.

Monolith Decouping:  A huge challenge at Microsoft

- Tangled Loops: decoupling frameworks, new features require framework changes; now the solution relies on two separate repositories.  Friction.

## Continuous Monitoring

Continuous monitoring refers to the process and technology required to incorporate monitoring across each phase of your DevOps and IT operations lifecycles.

- Migrate, Secure, Protect, Monitor, Configure, Govern

Enable monitoring to gain observability.  Enabling monitoring allows visualization of end-to-end transactions:

- [Azure DevOps Projects gives you a simplified experience with your existing code and Git repository or chooses](https://learn.microsoft.com/en-us/azure/devops-project/overview) from one of the sample applications to create a Continuous Integration (CI) and Continuous Delivery (CD) pipeline to Azure.
- [Continuous monitoring in your DevOps release pipeline](https://learn.microsoft.com/en-us/azure/application-insights/app-insights-vsts-continuous-monitoring) allows you to gate or roll back your deployment based on monitoring data.
- [Status Monitor](https://learn.microsoft.com/en-us/azure/application-insights/app-insights-monitor-performance-live-website-now) allows you to instrument a live .NET app on Windows with Azure Application Insights without modifying or redeploying your code.
- If you have access to the code for your application, then enable complete monitoring with [Application Insights](https://learn.microsoft.com/en-us/azure/application-insights/app-insights-overview) by installing the Azure Monitor Application Insights SDK for [.NET](https://learn.microsoft.com/en-us/azure/application-insights/quick-monitor-portal), [Java](https://learn.microsoft.com/en-us/azure/application-insights/app-insights-java-quick-start), [Node.js](https://learn.microsoft.com/en-us/azure/application-insights/app-insights-nodejs-quick-start), or [any other programming language](https://learn.microsoft.com/en-us/azure/application-insights/app-insights-platforms). It allows you to specify custom events, metrics, or page views relevant to your application and business.

Recommendations: Azure Monitor and Analytics:

- enable monitoring for entire infrastructure
- combine resources in Azure Resource Groups
- Use CD to raise quality
- Use Actionable Alerts with actions
- Prepare dashboards and workbooks
- continuously optimize

## Log Analytics:

[Kusto Query Language](https://learn.microsoft.com/en-us/azure/data-explorer/kusto/concepts/) (KQL)

```C++
// What data is being collected?
// List the collected performance counters and object types (Process, Memory, Processor.)
Perf
| summarize by ObjectName, CounterName

// Last heartbeat of each computer
// Show the last heartbeat sent by each computer
Heartbeat
| summarize arg_max(TimeGenerated, *) by Computer
```

## Application Insights

- instrumentation monitors your app and sends telemetry data to the portal
- install a small instrumentation package in your application and set up an Application Insights resource in the Microsoft Azure portal.
- Tracking calls are non-blocking and are batched and sent in a separate thread

Application Insights is aimed at the development team to help you understand how your app is doing and how it's being used. It monitors:

- Request rates, response times, and failure rates - Find out which pages are most popular, at what times of day, and where your users are. See which pages do best. If your response times and failure rates go high with more requests, perhaps you have a resourcing problem.
- Dependency rates, response times, and failure rates - Find out whether external services are slowing you down.
- Exceptions - Analyze the aggregated statistics or pick specific instances and drill into the stack trace and related requests. Both server and browser exceptions are reported.
- Pageviews and load performance - reported by your users' browsers.
- AJAX calls from web pages - rates, response times, and failure rates.
- User and session count.
- Performance counters from your Windows or Linux server machines include CPU, memory, and network usage.
- Host diagnostics from Docker or Azure.
- Diagnostic trace logs from your app - so that you can correlate trace events with requests.
- Custom events and metrics that you write yourself in the client or server code to track business events such as items sold or games won.

Viewing Telemetry ( [article](https://learn.microsoft.com/en-us/azure/application-insights/app-insights-proactive-diagnostics) )

- application map
- profiler: execution profiles
- usage analytics
- diagnostic search: requests, exceptions, dependency calls, logs, traces, page views
- metrics explore for aggregated data
- dashboards
- live metrics stream
- analytics
- jump to code from stack traces
- snapshot debugger
- PowerBI: integrate to BI
- REST API: query metrics and raw data
- continuous export: bulk, raw data to storage

Application Insights Implementation

- monitore: setup [availability web tests](https://learn.microsoft.com/en-us/azure/application-insights/app-insights-monitor-web-app-availability)
- detect, diagnose
- build, measure, learn

# Monitor  and Status Dashboards

## Azure Dashboards

[Azure dashboards](https://learn.microsoft.com/en-us/azure/azure-portal/azure-portal-dashboards) are the primary dashboarding technology for Azure.

- Deep integration into Azure. Visualizations can be pinned to dashboards from multiple Azure pages, including metrics analytics, log analytics, and Application Insights.
- Supports both metrics and logs.
- Combine data from multiple sources, including output from [Metrics explorer](https://learn.microsoft.com/en-us/azure/azure-monitor/platform/metrics-charts), [Log Analytics queries](https://learn.microsoft.com/en-us/azure/azure-monitor/log-query/log-query-overview), and [maps](https://learn.microsoft.com/en-us/azure/azure-monitor/app/app-map) and [availability](https://learn.microsoft.com/en-us/azure/azure-monitor/visualizations) in Application Insights.
- Option for personal or shared dashboards. It's integrated with [Azure role-based authentication (RBAC)](https://learn.microsoft.com/en-us/azure/role-based-access-control/overview).
- Automatic refresh. Metrics refresh depends on the time range with a minimum of five minutes. Logs refresh at one minute.
- Parametrized metrics dashboards with timestamp and custom parameters.
- Flexible layout options.
- Full-screen mode.

Limitations

- Limited control over log visualizations with no support for data tables. The total number of data series is limited to 10, with different data series grouped under another bucket.
- No custom parameters support for log charts.
- Log charts are limited to the last 30 days.
- Log charts can only be pinned to shared dashboards.
- No interactivity with dashboard data.
- Limited contextual drill-down.

## Azure Monitor Workbooks

Advantages

- Supports both metrics and logs.
- Supports parameters enabling interactive reports selecting an element in a table will dynamically update associated charts and visualizations.
- Document-like flow.
- Option for personal or shared workbooks.
- Easy, collaborative-friendly authoring experience.
- Templates support the public GitHub-based template gallery.

Limitations

- No automatic refresh.
- No dense layout like dashboards, which make workbooks less useful as a single pane of glass. It's intended more for providing more profound insights.

## Power BI

Advantages

- Rich visualizations.
- Extensive interactivity, including zoom-in and cross-filtering.
- Easy to share throughout your organization.
- Integration with other data from multiple data sources.
- Better performance with results cached in a cube.

Limitations

- It supports logs but not metrics.
- No Azure RM integration. Can't manage dashboards and models through Azure Resource Manager.
- Need to import query results need into the Power BI model to configure. Limitation on result size and refresh.

## Custom Application Dashboard

Advantages

- Complete flexibility in UI, visualization, interactivity, and features.
- Combine metrics and log data with other data sources.

Disadvantages

- Significant engineering effort is required.

# Knowledge Share with Teams

Use Azure DevOps Wiki.  Supports:

- Markdown: GitHub Flavoured Markdown (GFM) and Mermaid
- Integration with Azure Boards: create work items from Application Insights (features evolving)

See also:

- [Create a project wiki to share information - Azure DevOps | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/project/wiki/wiki-create-repo).
- [Overview of extensions for Azure Boards - Azure DevOps | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/boards/extensions/).

# Automate Application Analytics

log management: augment search

- The analysis algorithm automatically identifies errors, risk factors, and problem indicators while analyzing their severity by combining semantic processing, statistical models, and machine learning to analyze and "understand" the events in the logs. These insights are displayed as intelligence layers on top of the search results, helping the user quickly discover the most relevant and essential information.

integrate telemetry:

- telemetry can offer insights on which features end users use most, detect bugs and issues, and provide better visibility into the performance without asking for feedback directly from users
- Telemetry enables you to answer questions such as:
  - Are your customers using the features you expect? How are they engaging with your product?
  - How frequently are users engaging with your app, and for what duration?
  - What settings options do users select most? Do they prefer certain display types, input modalities, screen orientation, or other device configurations?
  - What happens when crashes occur? Are crashes happening more frequently when certain features or functions are used? What is the context surrounding a crash?

Monitoring options:

- **Synthetic Monitoring:** Developers, testers, and operations staff all need to ensure that their internet and intranet-mobile applications and web applications are tested and operate successfully from different points of presence worldwide.
- **Alert Management:** Developers, testers, and operations staff all need to send notifications via email, voice mail, text, mobile push notifications, and Slack messages when specific situations or events occur in development, testing, or production environments, to get the right people’s attention and to manage their response.
- **Deployment Automation:** Developers, testers, and operations staff use different tools to schedule and deploy complex applications and configure them in development, testing, and production environments. We'll discuss the best practices for these teams to collaborate effectively and efficiently and avoid potential duplication and erroneous information.
- **Analytics:** Developers need to look for patterns in log messages to identify if there's a problem in the code. Operations need to do root cause analysis across multiple log files to identify the source of the problem in complex applications and systems.

# Culture, Retrospectives

## Helpful Alerts and Flow

Manage alert notifications to only when the application has a problem and needs attention:

- Response time degradation - Your app has started responding to requests more slowly than it used to. The change might have been rapid, for example, because there was a regression in your latest deployment. Or it might have been gradual, maybe caused by a memory leak.
- Dependency duration degradation - Your app makes calls to a REST API, database, or other dependencies. The dependency is responding more slowly than it used to.
- Slow performance pattern - Your app appears to have a performance issue that is affecting only some requests. For example, pages are loading more slowly on one type of browser than others; or requests are being served more slowly from one server. Currently, our algorithms look at page load times, request response times, and dependency response times.

Alert flow:

- triage, diagnose, improve

Alert characteristics:

- Alerts that trigger call-out should be urgent, important, actionable, and real.
- They should represent either ongoing or imminent problems with your service.
- Err on the side of removing noisy alerts – over-monitoring is a more-challenging problem to solve under-monitoring.
- You should almost always classify the problem into availability & basic functionality; latency; correctness (completeness, freshness, and durability of data); and feature-specific problems.
- Symptoms are a better way to capture more problems more comprehensively and robustly with less effort.
- Include cause-based information in symptom-based pages or on dashboards but avoid alerting directly on causes.
- The further up your serving stack you go, the more distinct problems you catch in a single rule.
- If you want an on-call rotation, it's imperative to have a system for dealing with things that need a timely response but aren't imminently critical.

## Blameless Retrospectives

Having a "blameless" retrospective process means that engineers whose actions have contributed to an accident can give a detailed account of:dddddddddddd

- What actions do they take at what time.
- What effects do they observe?
- Expectations they had.
- Assumptions they had made.
- Their understanding of the timeline of events as they occurred.

See [Brian Harry's Blog - A good incident postmortem](https://blogs.msdn.microsoft.com/bharry/2018/03/02/a-good-incident-postmortem/)

## Just Culture

Failure happens.  Enthusiasm increases when mistakes are accepted and engineers feel safe.  A "Just Culture":

1. **Learning Culture**: Encourage learning by having these blameless Postmortems on outages and accidents.
2. **Understand How**: The goal is to understand **how **an accident could have happened, to better equip ourselves from it happening in the future.
3. **Diverse Views**: Gather details from multiple perspectives on failures, and don't punish people for making mistakes.
4. **Trust**: Instead of punishing engineers, we give them the requisite authority to improve safety by providing detailed accounts of their contributions to failures.
5. **Share Lessons**: Enable and encourage people who *make mistakes to educate* the rest of the organization on how not to make them in the future.
6. **Manage [Hindsight Bias](https://en.wikipedia.org/wiki/Hindsight_bias)**: Accept that there's always a discretionary space where humans can decide to make actions or not and that the judgment of those decisions lies in hindsight.
   - Accept that the [Hindsight Bias](http://en.wikipedia.org/wiki/Hindsight) will continue to cloud our assessment of past events and work hard to eliminate it.
   - Accept that the [Fundamental Attribution Error](http://en.wikipedia.org/wiki/Fundamental_attribution_error) is also difficult to escape, so we focus on the environment and circumstances people are working in when investigating accidents.
7. **Manage Upwards Expectations**: Strive to make sure that the blunt end of the organization understands how work is getting done (as opposed to how they imagine it's getting done via Gantt charts and procedures) on the sharp end.
8. **Be Professional**: The sharp end is relied upon to inform the organization of the line between appropriate and inappropriate behavior. It isn't something that the blunt end can come up with on its own.
