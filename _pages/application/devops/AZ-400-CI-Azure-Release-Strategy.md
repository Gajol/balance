---
permalink: /application/devops/AZ-400-CI-Azure-Release-Strategy
title: "Azure Release Strategy"
excerpt: "A release strategy embraces pushing software to production using the continuous delivery pipeline.  Feature flags enable various releases strategies."
last_modified_at: 2023-01-07T10:23:16-04:00
toc: true
---
# AZ-400 - Release Strategy

Goals:

- Explain continuous delivery (CD).
- Implement continuous delivery in your development cycle.
- Understand releases and deployment.
- Identify project opportunities to apply CD.

# Traditional IT Development Cycle

IT supports the business, software changes had bad quality and disrupted the business.   Software changes were a risk.  Therefore, change management had tight control of software changes.

- IT operations responsible for stability of the system
- IT development responsible for creating value

IT is not motivated to change, since change is risk.  Keeping everything stable is rewarded.  The result is long release cycles.  Silo'd development; plan->realize->release->value.

# Continuous Delivery

Continuous delivery (CD) is a set of processes, tools, and techniques for rapid, reliable, and continuous software development and delivery. CD goes beyond the release of software through a pipeline. The pipeline is a crucial component, but continuous delivery is more; automation and a strategy are required.

Principles of Continuous Delivery

- The process for releasing/deploying software must be repeatable and reliable.
- Automate everything!
- If something is difficult or painful, do it more often.
- Keep everything in source control.
- Done means "released."
- Build quality in!
- Everybody has responsibility for the release process.
- Improve continuously.   Find bottlenecks in process, solve it, learn, repeat.

A pipeline is one component, but the pipeline relies on software designed to be delivered continuously since:

- Software architecture (monoliths are hard to deploy).
- Testing strategy (manual tests don't scale well).
- Organization (separated business and IT departments don't work smoothly)

## Move to Continuous Delivery

Move to where value is release through a pipeline.

- plan, realize, release, monitor & learn to deliver value

Feedback loops at various aspects:

- unit test on code
- automated build to validate source code
- automated test in a test environment
- telemetry: metrics on a server
- telemetry: usage of a feature, code

Continuous Delivery:

- delivery products as fast as possible
- quality should be higher
- production should be faster
- technical debt should be lower

Ways to improve software development practices:

- agile and scrum: sprints create working software.    The value is not realized until it is delivered.  The value is piling up almost like the traditional waterfall IT cycle.  The challenge was how to delivery the software.
- CD tries to deploy value often so software quality can be evaluated and improved in smaller batches

## Releases and Deployments

Separate deployments from releases.  Also phase releases; functional release and technical release.

**Release**: A release is a package or container containing a versioned set of artifacts specified in a release pipeline in your CI/CD process. It includes a snapshot of all the information required to carry out all the tasks and actions in the release pipeline, such as:

- The stages or environments.
- The tasks for each one.
- The values of task parameters and variables.
- The release policies such as triggers, approvers, and release queuing options.

**Deployment**: Deployment is the action of running the tasks for one stage, which results in a tested and deployed application and other activities specified for that stage.

- Technical Release (Deployment)
- Functional Release (Enable Feature)

[Microsoft Release and Deployment](https://learn.microsoft.com/en-us/azure/devops/pipelines/release/releases?view=azure-devops)

- Release {versioned set of artifacts} -> run tasks tests/deploy/actions -> Deployment

A **release** is a construct that holds a versioned set of artifacts specified in a CI/CD pipeline. It includes a snapshot of all the information required to carry out all the tasks and actions in the release pipeline, such as stages, tasks, policies such as triggers and approvers, and deployment options. There can be multiple releases from one release pipeline, and information about each one is stored and displayed in Azure Pipelines for the specified [retention period](https://learn.microsoft.com/en-us/azure/devops/pipelines/policies/retention?view=azure-devops#release).

A **deployment** is the action of running the tasks for one stage, which can include running automated tests, deploying build artifacts, and whatever other actions are specified for that stage. Initiating a release starts each deployment based on the settings and policies defined in the original release pipeline. There can be multiple deployments of each release even for one stage. When a deployment of a release fails for a stage, you can redeploy the same release to that stage. To redeploy a release, simply navigate to the release you want to deploy and select deploy.

## Feature Flags

Feature Toggles: The simplest form of a Feature Toggle is an if statement that either executes or doesn't execute a certain piece of code. By making the if-statement configurable, you can implement the Feature Toggle. Toggles can help roll-back features efficiently.  ([Azure Phase Features with Feature Tags](https://learn.microsoft.com/en-us/azure/devops/articles/phase-features-with-feature-flags)) — [LaunchDarkly: Feature Flag & Toggle Management](https://launchdarkly.com).  Azure App Connect can manage application settings and feature flags.

- Deploy: Put the software into the environment.  The new software is available, but not active, so should not impact the system that already works.
- Release: Flip a switch so people can use it

## Release Process

Release Process (also called a Release Pipeline): The release pipeline contains all the steps you walk through when you move your artifact from one of the artifact sources discussed earlier through the stages or environments.   Stage examples {development, test, production}.   Approvals, triggers, schedules are part of how a release executes through gates.

Release: The release is an instance of the release pipeline. You can compare it with object instantiation.

## See Also

- [What is continuous delivery?](https://learn.microsoft.com/en-us/devops/deliver/what-is-continuous-delivery).
- [Continuous Delivery vs. Continuous Deployment | Microsoft Azure](https://azure.microsoft.com/overview/continuous-delivery-vs-continuous-deployment).
- [Release pipelines](https://learn.microsoft.com/en-us/azure/devops/pipelines/release/?view=azure-devops).
- [Define your Classic pipeline](https://learn.microsoft.com/en-us/azure/devops/pipelines/release/define-multistage-release-process).

# Create a Release Pipeline

Pipelines as code support via YAML in Azure DevOps:

- agents, approvals, artifacts, caching, conditions, container jobs, demands, dependencies, deployment groups/jobs, service connections, service containers, stages, task groups, tasks, templates, triggers, variables, variable groups

A [release pipeline](https://learn.microsoft.com/en-us/azure/devops/pipelines/release) takes artifacts and release them through stages and finally into production.

Components of a release pipeline:

- artifact: can come from different sources (usually a build pipeline, or source control)
- trigger: manual, scheduled, CD trigger (on build complete)
- stages (or environments): where the artefact will be installed
- approval: sign a release before installing it

Artifact Sources:

- most common way is with a build artifact. Build produces a versioned artifact, link to the build (traceability).  Build versioning should use [semantic versioning](https://semver.org/).
- traceability and auditability are key in tracing sources.  

Artifact: The artifact should be a stable package.  The contents of the package should never change. It's what we call [immutability](https://learn.microsoft.com/en-us/azure/devops/artifacts/artifacts-key-concepts). We should be 100% sure that the package that we build, the artifact, remains unchanged.

# Deployment Stages Consideration

What is our target deployment frequency? Considerations include:

- Do we want to deploy our application?
- Do we want to deploy multiple times a day?
- Can we deploy to a stage? Is it used?

What should trigger a deployment?  Considerations include:

- What is your target environment?
- Does one team use it, or do multiple teams use it?  If a single team uses it, you can deploy it frequently.
- Who are the users? Do they want a new version multiple times a day?
- How long does it take to deploy?
- Is there downtime? What happens to performance? Are users affected?

## Build and Release Tasks

Build and release repeatable actions: extract files, FTP upload, create a GitHub release, Install SSH key, ....:

- [Task types & usage](https://learn.microsoft.com/en-us/azure/devops/pipelines/process/tasks)
- [Tasks for Azure](https://github.com/microsoft/azure-pipelines-tasks)
- [Atlassian marketplace](https://marketplace.atlassian.com/addons/app/bamboo/trending)
- [Jenkins Plugins](https://plugins.jenkins.io/)

## Release Jobs

Orgnize build or release pipeline into jobs.   Every pipeline has at least one job.

## See also

- [Release pipelines - Azure Pipelines | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/pipelines/release).
- [Build and Release Tasks - Azure Pipelines | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/pipelines/process/tasks).
- [Jobs in Azure Pipelines and TFS - Azure Pipelines | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/pipelines/process/phases).
- [Configure and pay for parallel jobs - Azure DevOps | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/pipelines/licensing/concurrent-jobs).

# Release Considerations

- Explain things to consider when designing your release strategy
- Define the components of a release pipeline and use artifact sources
- Create a release approval plan
- Implement release gates

Three trigger types; continuous deployment (on build complete), scheduled and manual.

Release approvals: Approvals help establish trust in organizations moving to DevOps CD.  Approvals should consider:

- goal of the approval: what does the approval accomplish?  Is it for compliance or security or business reasons (Security Officer, Product Owner)
- who needs to approval?
- what are consequences and responsibilities on failed deployments?

Release Gates: Can be used as a pre/post deployment condition.  Automated approvals with release gates can also be used for:

- incident and issues management
- inform compliance, security through collaborate platforms like Teams and Slack
- quality validation, query metrics
- security scan
- user experience relative to baseline using product telemetry
- change management complete (integration to ServiceNow)
- infrastructure health: target environment is ready for a change

## Learn more:

- [How Microsoft plans efficient workloads with DevOps - Azure DevOps | Microsoft Docs](https://learn.microsoft.com/en-us/devops/plan/how-microsoft-plans-devops).
- [Release engineering app development - Azure Architecture Center | Microsoft Docs](https://learn.microsoft.com/en-us/azure/architecture/framework/devops/release-engineering-app-dev).
- [How Microsoft develops modern software with DevOps - Azure DevOps | Microsoft Docs](https://learn.microsoft.com/en-us/devops/develop/how-microsoft-develops-devops).
- [Control deployments by using approvals - Azure Pipelines | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/pipelines/release/approvals/approvals).
- [Control deployments by using gates - Azure Pipelines | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/pipelines/release/approvals/gates).

# Provision and Test Environments

Target environments: on-premise servers, cloud servers and IaaS, PaaS and FaaS, clusters, service connections

- IaaS: lift-and-shift.  less use of cloud-power, but the application is in the cloud
- IaC: infrastructure as code.  Scripts create SQL databases, network and IP addresses.  Azure Resource Manager for creating infrastructure on demand.
- PaaS: For example a web-application, and the cloud provider creates the server, network , public IP, storage and webserver.
- Clusters: A cluster is a group of servers that work together to host high-scale applications.
- Server Connections: en a pipeline needs access to resources, you'll often need to create service connections.

See:

- [Desired State Configuration Overview](https://learn.microsoft.com/en-us/powershell/dsc/overview/dscforengineers?view=dsc-1.1).
- [Azure Functions](https://azure.microsoft.com/services/functions).
- [Azure Resource Manager](https://learn.microsoft.com/en-us/azure/azure-resource-manager/resource-group-overview).

## Automated Integration and Functional Test Automation

Agile Testing ([Lisa Crispin Agile Testing - 2011](https://lisacrispin.com/2011/11/08/using-the-agile-testing-quadrants/)) describes four testing targets; based on business/technology facing, and support/critique.:

- Business facing - the tests are more functional and often executed by end users of the system or by specialized testers that know the problem domain well.
- Supporting the Team - it helps a development team get constant feedback on the product to find bugs fast and deliver a product with quality build-in.
- Technology facing - the tests are rather technical and non-meaningful to business people. They're typical tests written and executed by the developers in a development team.
- Critique Product - tests that are there to validate the workings of a product on its functional and non-functional requirements.

Automation principles: ( [reference](https://learn.microsoft.com/en-gb/training/modules/configure-provision-environments/5-understand-shift-left) , [shift-left testing article](https://learn.microsoft.com/en-us/devops/develop/shift-left-make-testing-fast-reliable))

- Tests should be written at the lowest level possible.
- Write once, run anywhere, including the production system.
- The product is designed for testability.
- Test code is product code; only reliable tests survive.
- Test ownership follows product ownership.

## Shift-Left Quality

Push quality upstream.  [Microsoft Shift-Left Testing - Fast & Reliable](https://learn.microsoft.com/en-us/devops/develop/shift-left-make-testing-fast-reliable).

Characteristics of tests:

Unit Tests: must be fast and reliable (think running 1,000's of tests in minutes)

Functional Tests: must be independent (a failed test should not impact other test's ability to execute)

Test Taxonomy: Types of test for different scenarios:

- L0 tests are fast in-memory tests; code is the only dependency.  Execute in 0.5 to 2 seconds.
- L1 tests might rely on a file system or SQL  Functional Tests
- L2 tests are functional tests that run in testable service deployments.  It's a functional test category that requires a service deployment but may have critical service dependencies stubbed out somehow.  See [Fowler - Mocks Aren't Stubs](https://martinfowler.com/articles/mocksArentStubs.html)).
- L3 tests are a restricted class of integration tests that run against production. They require a complete product deployment.

### Shift Left Testing with Unit Tests

Refence: [Shift Left Testing with Unit Tests](https://learn.microsoft.com/en-us/devops/develop/shift-left-make-testing-fast-reliable)

This article shows 5 levels (L0..L4).

Functional Tests: (simple, but with SQL/file system): Functional tests must be independent. The key concept for L2 tests is isolation. Properly isolated tests can run reliably in any sequence, because they have complete control over the environment they run in. The state must be known at the beginning of the test. If one test created data and left it in the database, it could corrupt the run of another test that relies on a different database state.

- Challenge of Isolation Example: Legacy tests that need a user identity might have called external authentication providers to get the identity. This practice introduces several challenges. The external dependency could be unreliable or unavailable momentarily, breaking the test. This practice also violates the test isolation principle, because a test could change the state of an identity, such as permission, resulting in an unexpected default state for other tests. Consider preventing these issues by investing in identity support within the test framework.

Track progress:  Track testing process health, debt and velocity.

Live Site Metrics:

- time to detect
- time to mitigate
- team repair backlog: repair item is work the team identifies in a retrospective to prevent similar incidents from occurring.

Engineering Health Metrics:

- bugs per developer  (5:1 ratio is the team switches to priorities bug-fixes)
- bug age in key categories (security, UI responsiveness, )

Engineering Velocity Metrics measure CI/CD pipeline:

- time from idea to code in production (value stream)
- deploy to feedback time (customer experience)

### Shirt Right to Test in Production

Article: [Shift right to test in production](https://learn.microsoft.com/en-us/devops/deliver/shift-right-test-production).

*Shift right* is the practice of moving some testing later in the DevOps process to *test in production*. Testing in production uses real deployments to validate and measure an application's behavior and performance in the production environment.

Testing in production provides:

- The full breadth and diversity of the production environment.
- The real workload of customer traffic.
- Profiles and behaviors as production demand evolves over time.

Shifting right to test in production is especially important for the following scenarios:

- microservice deployments: large number of microservices results in different versions and configurations in production.  Testing compatibility in production is mandatory as it is impossible to test all variations in test environments.
- post-deployment quality assurance: After release to production, the ability of the release to support the real-world workload must be assured.  Test data (observability, metrics, telemetry) must be captured and assessed.  Tracking failures, exceptions, performance and security events post-deployment.
- deployment rings:  Progressive deployments to wider audiences, regions through [deployment rings](https://learn.microsoft.com/en-us/devops/operate/safe-deployment-practices#ring-based-deployment) and [feature flags](https://learn.microsoft.com/en-us/devops/operate/progressive-experimentation-feature-flags).  First ring is smallest possible so as to not impact customers, expanding with each ring as confidence builds based on observed behaviours.
- fault injection: employ *fault injection* and *chaos engineering* to see how a system behaves under failure conditions:  Validate resiliency mechanisms, failures are contained, prove repair work (test failure paths in production), create training drills for site reliability engineers.
- failover testing: test business continuity and disaster recover
- circuit breaker fault testing:
- A *circuit breaker* mechanism cuts off a given component from a larger system, usually to prevent failures in that component from spreading outside its boundaries.

See also:

- [What are microservices?](https://learn.microsoft.com/en-us/devops/deliver/what-are-microservices)
- [Run a test failover (disaster recovery drill) to Azure](https://learn.microsoft.com/en-us/azure/site-recovery/site-recovery-test-failover-to-azure)
- [Safe deployment practices](https://learn.microsoft.com/en-us/devops/operate/safe-deployment-practices)
- [What is monitoring?](https://learn.microsoft.com/en-us/devops/operate/what-is-monitoring)

## Run Availability Tests

Create and set-up tests to monitor an application's availability and responsiveness.  See [Azure Web Resource and Web Test](https://azure.microsoft.com/blog/creating-a-web-test-alert-programmatically-with-application-insights/).

## Load Testing

Azure Load Testing:  A fully managed load-testing service.  Use Apache JMeter.  Azure Load Testing abstracts the infrastructure.

Use [Selenium](http://www.seleniumhq.org/) for functional tests.

## See Also

- [Create target environment - Azure Pipelines | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/pipelines/process/environments).
- [Integrate DevTest Labs environments into Azure Pipelines - Azure DevTest Labs | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devtest-labs/integrate-environments-devops-pipeline).
- [Connect to Microsoft Azure - Azure Pipelines | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/pipelines/library/connect-to-azure).
- [Service connections in Azure Pipelines - Azure Pipelines | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/pipelines/library/service-endpoints).
- [Run Functional Tests task - Azure Pipelines | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/pipelines/tasks/test/run-functional-tests).
- [Monitor availability with URL ping tests - Azure Monitor | Microsoft Docs](https://learn.microsoft.com/en-us/azure/azure-monitor/app/monitor-web-app-availability).
- [Testing your app and Azure environment - Azure Architecture Center | Microsoft Docs](https://learn.microsoft.com/en-us/azure/architecture/framework/devops/release-engineering-testing).

# Manage & Modularize Tasks & Templates

Goal:

- Use and manage task and variable groups.
- Use release variables and stage variables in your release pipeline.
- Use variables in release pipelines.
- Create custom build and release tasks.

## Task Groups

A task group allows you to encapsulate a sequence of tasks, already defined in a build or a release pipeline, into a single reusable task that can be added to a build or release pipeline, just like any other task.

## Variables in Release Pipelines

See [Release variables and debugging](https://learn.microsoft.com/en-us/azure/devops/pipelines/release/variables).

- predefined variables
- stage variables: share values across tasks
- variable groups: share values across a project, across multiple builds or release pipelines.  Examples: username/password, shared connection string, geolocation of application, settings for an application.  See [Variable Groups](https://learn.microsoft.com/en-us/azure/devops/pipelines/library/variable-groups).
- normal and secret variables

Learn more:

- [Variable groups for Azure Pipelines - Azure Pipelines | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/pipelines/library/variable-groups).
- [Define variables - Azure Pipelines | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/pipelines/process/variables).
- [Add a build or release task in an extension - Azure DevOps | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/extend/develop/add-build-task).

# Health Inspection Automation

Goal:

- Implement automated inspection of health
- Create and configure events
- Configure notifications in Azure DevOps and GitHub
- Create service hooks to monitor pipeline
- Classify a release versus a release process, and outline how to control the quality of both
- Choose a release management tool

## Overview:

Inspection of the release pipeline and release is should be considered from the start. When you run multiple deployments a day, you want to:

- Stay informed.
- Know whether a release passed or failed.
- Know the quality of the release.
- Know details about the release and how it has been done.
- Stop releases when you detect something suspicious.
- Visualize some of these things on a dashboard.

Key components of release health:

- release gates: allow automatic collection of health signals from external services.  Promotes release or stops deployment on timeout.   Data collected from incident management problem management, change management, monitoring and external approval systems.
- events, subscriptions and notifications: Events are raised when events occurs (release started, build complete, ...).  Notification subscription, usually emails you receive.
- service hooks: allow tasks on other services to be performed when an event happens
- reporting: change a dashboard based on status of build and release

## Events and notifications

- alerts: consideration to ensure the alerts are meaningful and mailboxes are not overwhelmed with alerts
- target audience & delivery: alerts should be for action (not for information purposes).  Use query and filters to ensure quality of alerts.

Service hooks allow hooks into different other platforms:

- build and release: AppVeyor, Bamboo, Jenkins, Slack
- collaborate: Campfire, Flowdock, HipChat, Hubot
- customer support: UserVoice, Zendesk
- Plan and track: Trello
- Integrate: Azure Service Bus, Azure Storage, Web Hooks, Zapier

###  Notifications

Azure DevOps

- Notifications when items change {work items, code reviews, PRs, source control files, builds, releases}
- Notification types: {personal, team, project, global}

GitHub Notifications

- Notifications for issues, PR, gist, repository activity, CI activity, security alerts, discussion

## Release Quality

Use a dashboard on the build pipeline across all environments.

## Release Notes and Documentation

Communicate what has changed to your customer with release notes.   Release notes can be:

- document store: create text notes manually.  No connection to release management tool.
- wiki: Store notes in a wiki (Confluence, SharePoint, SlimWiki, Wiki in Azure DevOps).  Use hyperlinks to associate to builds and artifacts.
- code base: release notes belong in the code base.  Team completes feature, product owner creates release notes and saves them with the code.  The build process generates the release notes documentation.
- work item: work items can be bugs, tasks, backlog items, or user stories.  A field in the work item can be a release.  Scripts can generate the release note.

# Release Management Tools Choice

The tools in the marketplace can be divided into two categories.

- Tools that can do Build and Continuous Integration and Deployment.
- Tools that can do Release Management.

Release Management that requires approvals, quality gates, and different stages needs a different kind of tool that tightly integrates with the build and CI tools isn't the same.  Companies sometimes only require the deployment part of Release Management since their existing build or release toolset can perform deployment and installation.

Artifacts & Artifacts Source

Artifacts are versioned packages that are stored somewhere.  The artifact is stored before a pipeline consumes it.  Artifact storage considerations:

- Which Source Control systems are supported?
- Can you've one or more artifact sources in your release pipeline? In other words, can you combine artifacts from different sources into one release?
- Does it integrate with your build server?
- Does it support other build servers?
- Does it support container registries?
- How do you secure the connection to the artifact source?
- Can you extend the artifact sources?

Features in these following key areas may affect your release management tool choice:

1. triggers & schedules: Support for CD triggers, trigger releases via API, schedule releases, trigger stages independently

2. approvals & gates[^approvalworkflow]: Release Approval Workflow is the critical component that differentiates a release management tool from a build tool.  Approval characteristics, features and considerations include; external approvals, licensing costs, manual/automatic approvals, API approval, workflow features, per stage approvals, voting (all, majority, ...).

3. stages: a release management tool should extend the abilities of a CI pipeline that builds and deploys to a single environment.  Features include deploy artifact to different stages, configuration/stage, unique steps per stage, traceability of release between stages.

4. build and release tasks:  How is work done in the pipeline and what flexibility, security and control do you have.  Considerations include ability to author steps in shell, python, authentication to secure sources, multi-platform execution, task re-use, task control

5. traceability, auditability and security:

   - four-eyes principle
     - Does at least one other person review the deployed artifact?
     - Is the person that deploys another person the one that writes the code?
   - Traceability
     - Can we see where the released software originates from (which code)?
     - Can we see the requirements that led to this change?
     - Can we follow the requirements through the code, build, and release?

   - Auditability
     - Can we see who, when, and why the release process changed?
       - Can we see who, when, and why a new release has been deployed?

   ## Common Release Management Tools

   | Tool                                                         | Notes                                                        |
   | ------------------------------------------------------------ | ------------------------------------------------------------ |
   | GitHub Actions                                               | GitHub Actions help you build, test, and deploy your code. You can implement continuous integration and continuous delivery (CI/CD) that allows you to make code reviews, branch management, and issue triaging work the way you want.<br />[GitHub Actions](https://docs.github.com/en/actions).<br />[Understanding GitHub Actions](https://docs.github.com/en/actions/learn-github-actions/understanding-github-actions). <br />[Essential features of GitHub Actions](https://docs.github.com/en/actions/learn-github-actions/essential-features-of-github-actions). <br />[Deploying with GitHub Actions](https://docs.github.com/en/actions/deployment/about-deployments/deploying-with-github-actions). |
   | Azure Pipelines                                              | Azure Pipelines helps you implement a build, test, and deployment pipeline for any app.<br />[Azure Pipelines](https://azure.microsoft.com/services/devops/pipelines/). <br />[Building and Deploying your Code with Azure Pipelines](https://www.youtube.com/watch?v=NuYDAs3kNV8). |
   | Jenkins                                                      | Jenkins's leading open-source automation server provides hundreds of plugins to support building, deploying, and automating any project.<br />[Jenkins](https://jenkins.io/). <br />[Tutorial: Jenkins CI/CD to deploy an ASP.NET Core application to Azure Web App service](https://cloudblogs.microsoft.com/opensource/2018/09/21/configure-jenkins-cicd-pipeline-deploy-asp-net-core-application/). <br />[Azure Friday - Jenkins CI/CD with Service Fabric](https://www.youtube.com/watch?v=5RYmooIZqS4). |
   | [CircleCI](https://circleci.com/)                            | CircleCI's continuous integration and delivery platform help software teams rapidly release code with confidence by automating the build, test, and deploy process. |
   | [GitLab Pipelines](https://about.gitlab.com/stages-devops-lifecycle/release/) | GitLab helps teams automate the release and delivery of their applications to shorten the delivery lifecycle, streamline manual processes and accelerate team velocity. |
   | [Atlassian Bamboo](https://www.atlassian.com/software/bamboo/features) | Bamboo is a continuous integration (CI) server that can automate the release management for a software application, creating a Continuous Delivery pipeline. |

   Learn more:

   - [DevOps checklist - Azure Design Review Framework | Microsoft Docs](https://learn.microsoft.com/en-us/azure/architecture/checklist/dev-ops).
   - [Events, subscriptions, and notifications - Azure DevOps | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/notifications/concepts-events-and-notifications).
   - [Integrate with service hooks - Azure DevOps | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/service-hooks/overview).
   - [Build Quality Indicators report - Azure DevOps Server | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/report/sql-reports/build-quality-indicators-report).

# Footnotes

[^approvalworkflow]: Triggering a release from technical-events like a script, executable or deployable artifact is a basic CI-build-tool capability.  A release management tools incorporates an approval workflow in the pipeline.
