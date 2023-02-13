---
permalink: /application/devops/Azure-DevOps-AZ-400-Training
title: "Azure DevOps Training"
excerpt: "The Microsoft course to help prepare for the Microsoft Certified: DevOps Engineer Expert certification."
last_modified_at: 2023-01-07T10:23:16-04:00
toc: true
---
#  DevOps

As part of preparing for the [AZ-400 - Designing and Implementing Microsoft DevOps Solutions](https://learn.microsoft.com/en-us/learn/certifications/exams/az-400) certification exam.  [AZ-400 Journey](https://learn.microsoft.com/training/paths/az-400-get-started-devops-transformation-journey/).   The following notes are a summary (or copy) of the training material.

- [AZ-400 Study Guide](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE3VP8d)
- [AZ-400 Exam Prep videos](https://learn.microsoft.com/en-us/shows/exam-readiness-zone/preparing-for-az-400-configure-processes-and-communications-1-of-5)
- [Exam Sandbox](https://aka.ms/examdemo)

Two Paths

- AZ-400 DevOps Transformation Journey
- Application Lifecycle Management for the Power Platform [application-lifecycle-management-architect](https://learn.microsoft.com/training/modules/application-lifecycle-management-architect/)
- Other [Microsoft Learning Paths](https://learn.microsoft.com/en-gb/training/browse/)

# AZ-400 Learning Path:

Learn to design, develop and implement a:

- [x] DevOps Transformation Journey
- [x] Enterprise DevOps
- [x] CI with Azure Pipelines and GitHub Actions
- [x] [Release Strategy](/application/devops/AZ-400-CI-Azure-Release-Strategy)
- [x] Secure Continuous Deployment using Azure Pipelines
- [x] Manage IaC using Azure and DSC
- [x] Dependency Management Strategy
- [x] Continuous Feedback
- [x] Security and validate codes bases for compliance

# What is DevOps

Development and Operations

- multidisciplinary teams
- shared and efficient practices and tools
- agile planning, continuous integration, continuous delivery
- monitoring of applications
- a journey

## DevOps Cycle

Plan, Build, CI, Deploy, Operation, Continuous Feedback

## Cycle Time

OODA: Observe, Orient, Decide, Act : Similar to Deming's Plan, Do, Check, Act, but ground in military fighter pilot training.

- Observe: business, market, needs, user behaviour, telemetry data
- Orient: enumerate options on what you can delivery, perhaps with experiments
- Decide: decide on what options to pursue
- Act: Delivery working software to real users

Power of Thirds: What We Can Do, What We Want To Do, What We Did

Sports Rule of Thirds: [The Rule of Thirds | Alexi Pappas - YouTube](https://www.youtube.com/watch?v=cKndqq0CsRc).   That wass o.k. Chasing a Dream.  Try hard, push yourself.

- Feel Good
- Feel OK: A third of the time.
- Crappy: A third of the time.  Today was the crappy day in the journey towards the dream

Validated learning.  Like the Olympic Swimmer and the rule of thirds used to reflect on performance, you need to gather feedback to determine your next cycle.  Validated learning is feedback that is factual and actionable data.

Adopting DevOps practices should lead to:

- working in smaller batches to shorten the cycle time
- using more automation
- hardening the release pipeline
- improving your [telemetry](https://en.wikipedia.org/wiki/Telemetry) (your ability to measure and observe performance with meaningful dataj insights)
- deploying more frequently

# Select the Project

From residential urban planning the terms greenfield and brownfield were created:

- Greenfield:  A greenfield project is one done on a green field, undeveloped land.
- Brownfield: A brownfield project is done on the used ground for other purposes. Because of the land use that has once occurred, there could be challenges reusing the land. Like existing buildings, some would be obvious but less obvious, like polluted soil.

For DevOps, greenfield seems easier since there is no existing codebase and no existing team dynamics (politics and rigid processes).  Brownfield projects have the debt of the existing codebase and embedded business and technical processes and culture.

How to decide on candidate systems for DevOps.  

- Bimodal IT:  Two separate coherent modes of IT delivery.  One focused on stability and predictability and the other on agility

## Identify System

| System Type          | Characteristics                                              |
| -------------------- | ------------------------------------------------------------ |
| System of Record     | Systems that provide the truth about data elements are often-called systems of record. These systems have historically evolved slowly and carefully. For example, it is crucial that a banking system accurately reflects your bank balance. Systems of record emphasize accuracy and security. |
| System of Engagement | Systems of engagement are modified regularly.  It is a priority to make quick changes over ensuring that the changes are correct. |

DevOps work for both system types.  Transforming systems of records to follow a DevOps practice can lead to significant outcomes.   However, it is easier to start with a system of engagement when first beginning a DevOps transformation.

## Identify Groups

Identify the people who can join the DevOps transformation.  These people must be willing and receptive to change.  For continuous delivery (CD) users can be categorized into these groups:

- canary: users voluntarily test need features
- early adopters: users voluntarily test new releases
- users: consumers of products once it is expected to be stable

## Target Improvements

Identify improvement goals that:

- used to gain momentum (early wins)
- small enough to be achievable in short timeframe
- significant enough to be evident to key stakeholders

## Project Metrics and KPI

DevOps specific KPIs should be agreed upon by the DevOps team.  Agile primary measure is working software, and DevOps KPIs should embrace this agile principle.  DevOps KPIs could include:

- faster outcomes: deployment frequency, speed, size (features, story-points, bug-fixes), lead-time
- efficiency: server:admin ration, developer:pm ratio, devops-team:client ratio, application usage (observability), application performance (responsiveness)
- quality and security: deployment success rate, application uptime, mean-time-to-recover, bug-report rate
- culture: employee morale, retention rates

## References

Select the Project:

- [About teams and Agile tools](https://learn.microsoft.com/en-us/azure/devops/organizations/settings/about-teams-and-settings)
- [Best practices for "light-weight" Agile project management](https://learn.microsoft.com/en-us/azure/devops/boards/best-practices-agile-project-management)

Team Structure

- [DevOps vs. Agile | Microsoft Azure](https://azure.microsoft.com/overview/devops-vs-agile/).
- [Best practices for Agile project management - Azure Boards | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/boards/best-practices-agile-project-management).
- [Agile Manifesto for Software Development | Agile Alliance](https://www.agilealliance.org/agile101/the-agile-manifesto).
- [12 Principles Behind the Agile Manifesto | Agile Alliance](https://www.agilealliance.org/agile101/12-principles-behind-the-agile-manifesto).

# Team Structures

Agile Development Practices

Waterfall: Software development practice is a sequential order with the concept of "there is no going back".

- Determining a problem.
- Analysing the requirements.
- Building and testing the required code.
- The delivery outcome to users.

The challenge with the traditional waterfall, assuming you follow this process rigidly is:

- project takes a long time to delivery and the customer requirements may change
- customer requirements are likely inaccurate as there is no opportunity for the customer to experience the development of the product
- customers have difficultly explain what they need, and the waterfall process does not help surface customer needs

>  Agile promises to solve everything.  If agile does not solve your problems, then you did need to iterate on your agile implementation.   — unknown

The [agile manifesto](https://en.wikipedia.org/wiki/Agile_software_development) was created in 2001 from 17 software developers (Extreme Programming, Ruby, Scrum, OOD, UML, TDD and OOA leaders).   Some values are:

- ***Individuals and interactions** over processes and tools*
- ***Working software** over comprehensive documentation*
- ***Customer collaboration** over contract negotiation*
- ***Responding to change** over following a plan*

Agile software development methods are based on releases and iterations:

- One release might consist of several iterations.
- Each iteration is like a small independent project.
- After being estimated and prioritization:
  - Features, bug fixes, enhancements, and refactoring width are assigned to a release.
  - And then assigned again to a specific iteration within the release, generally on a priority basis.
- At the end of each iteration, there should be tested working code.
- In each iteration, the team must focus on the outcomes of the previous iteration and learn from them.

## Agile and Waterfall Compared

| Agile                                        | Waterfall                                                    |
| -------------------------------------------- | ------------------------------------------------------------ |
| Sprints separate project development         | Phases separate development                                  |
| Flexible                                     | Rigid                                                        |
| Iterative.  A phase may occur several times. | Sequential.  A phase occurs once, and transitions to the next phase. |
| Requirements expected to change.             | Requirements should not change.                              |
| Values meeting customer needs.               | Values completing project.                                   |

## Agile Principles

 See the Manifesto for [Agile Software Development](https://www.agilealliance.org/agile101/the-agile-manifesto/).  Summarized briefly:

1. prioritize satisfying customer with continuous delivery
2. embrace changing requirements
3. deliver frequently
4. business & developer work together; daily
5. trust & support project team
6. face-to-face conversations is efficient and effective
7. primary progress measure is working software
8. Agile is sustainable; constant pace
9. Simplicity; optimize work-not-done.
10. Self-Organizing Teams lead to best architectures, requirements and design: Team chooses how to accomplish work ([Scrum Teams](https://www.scrum.org/resources/blog/about-self-organizing-teams))
11. Reflect, adjust as a team

## Organizing to Be Agile

Existing organization culture, mindset and governance are often barriers to adapting agile practices.

- horizontal teams:  teams divided into software architecture (UI, SOA, data teams)
- vertical teams; aligned with skillsets or disciplines (email, voice, ...)

Vertical teams, full-stack developers, are proven to provide better outcomes in agile projects.  Each product must have an identified owner.  This can be scaled to feature-teams (shopping cart, customer profile, email, ..).

## Mentoring Team Members

Agile course help, but practicing agile and giving and receiving feedback are key.

- hire external coaches, mentors
- identify agents of change
- coach, teach, mentor

## Collaboration:

Cultural Changes:  Agile relies on effect collaboration within the team and across teams.  Agile prefers face-to-face meetings, but collaboration via email and platforms (Confluence, Jira, Slack, Skype, Teams) are common.   Setting expectations on collaboration is important:

- team members should focus on primary tasks
- limit disrupts
- do not expect immediate responses from asynchronous/unplanned requests (messaging, email, asynchronous tasking, ...)

## Agile Tool Selection

Physical:  Whiteobards, index cards, sticky notes

Collaboration Tools:  Jira, Confluence, Slack, Teams, Mattermost, ...

Project Management Tools

- project planning and execution monitoring
- management and tracking of releases
- records work with outcomes and retrospectives
- kanban boards
- sprint planning

### Azure DevOps and GitHub

- Flexibility in Kanban boards.
- Traceability through Backlogs.
- Customizability in dashboards.
- Built-in scrum boards.
- Integrability directly with code repositories.
- Code changes can be linked directly to tasks or bugs.

# Choose DevOps Tools

Azure DevOps: Azure DevOps is a Software as a service (SaaS) platform from Microsoft that provides an end-to-end DevOps toolchain for developing and deploying software.

## Azure DevOps

Azure DevOps includes a range of services covering the complete development life cycle.

- Azure Boards: agile planning, work item tracking, visualization, and reporting tool.
- Azure Pipelines: a language, platform, and cloud-agnostic CI/CD platform-supporting containers or Kubernetes.
- Azure Repos: provides cloud-hosted private git repos.
- Azure Artifacts: provides integrated package management with support for Maven, npm, Python, and NuGet package feeds from public or private sources.
- Azure Test Plans: provides an integrated planned and exploratory testing solution.

Also, you can use Azure DevOps to orchestrate third-party tools.

Azure DevOps provides a platform that is:

- **Flexible**: you do not have to go 'all in' on Azure DevOps. It is possible to adopt each of the services independently and integrate them with your existing toolchain; most popular tools are supported.
- **Cross-Platform**: designed to work with any platform (Linux, macOS, and Windows). Or language (including Node.js, Python, Java, PHP, Ruby, C/C++, .NET, Android, and iOS apps). Azure DevOps is not aimed at organizations building and shipping on the Microsoft technology stack.
- **Cloud Agnostic**: continuous delivery is supported to AWS, GCP, and Azure.

## Github

GitHub is a Software as a service (SaaS) platform from Microsoft that provides Git-based repositories and DevOps tooling for developing and deploying software.  GitHub provides a range of services for software development and deployment.

- **Codespaces:** Provides a cloud-hosted development environment (based on Visual Studio Code) that can be operated from within a browser or external tools. Eases cross-platform development.
- **Repos:** Public and private repositories based upon industry-standard Git commands.
- **Actions:** Allows for the creation of automation workflows. These workflows can include environment variables and customized scripts.
- **Packages:** The majority of the world's open-source projects are already contained in GitHub repositories. GitHub makes it easy to integrate with this code and with other third-party offerings.
- **Security:** Provides detailed code scanning and review features, including automated code review assignment.

## Authorization and Access

Azure DevOps Services uses enterprise-grade authentication. To protect and secure your data, you can use:

- Microsoft account.
- GitHub account.
- Azure Active Directory (Azure AD).

## Personal access tokens

Use personal access tokens (PAT) for tools that don't directly support Microsoft accounts or Azure AD for authentication. You can use it if you want them to integrate with Azure DevOps.

For example, tools like:

- Git-based repositories.
- NuGet.
- Xcode.

These tokens can be set up using Git Credential managers, or you can create them manually. Personal access tokens are also helpful when establishing access to command-line tools, external tools, and tasks in build pipelines.  Also, when calling REST-based APIs, you don't have a UI popping out to do the authentication. When access is no longer required, you can revoke the personal access token.

## Security groups

Azure DevOps is pre-configured with default security groups.

Default permissions are assigned to the default security groups. You can also configure access at the organization, collection, and project or object levels.

In the organization settings in Azure DevOps, you can configure app access policies. Based on your security policies, you might allow alternate authentication methods, enable third-party applications to access via OAuth, or even allow anonymous access to some projects.

For even tighter control, you can use Conditional Access policies. These offer simple ways to help secure resources such as Azure DevOps when using Azure Active Directory for authentication.

## Multifactor authentication

Conditional Access policies such as multifactor authentication can help to minimize the risk of compromised credentials.

As part of a Conditional Access policy, you might require:

- Security group membership.
- A location or network identity.
- A specific operating system.
- A managed device or other criteria.

## Work Management Tools

Migration: This section seems to suggest to migrate from Jira to Azure DevOps [Azure Boards](https://learn.microsoft.com/en-us/azure/devops/boards/extensions/migrate-integrate?view=azure-devops).   A tool by [Solidify](https://solidify.dev/blog/jira-azure-devops-migration) is suggested which is complex and migrates Feature, Epic, Story, Bug, Task and Sub-Task to Azure.

Integration:  Microsoft Azure supports integration with Trello integration tool

## Test Management Tools

Azure Test Plans track manual testing for sprints and milestones.

[Azure Load Testing](https://learn.microsoft.com/en-us/azure/load-testing/overview-what-is-azure-load-testing)

## License Management Strategy

You journey in the DevOps implementation will affect your licensing.  As DevOps matures licensing is impacted:

- build licenses to allow parallel builds
- package management and storage for build artifacts
- which users roles have access to what licensed features
- as team grows each DevOps feature may need more seat or job licenses.

Pricing Information:

- [Azure DevOps Pricing](https://azure.microsoft.com/pricing/details/devops/azure-devops-services/)
- [GitHub Pricing](https://github.com/pricing/)
- [Azure Pricing Calculator](https://azure.microsoft.com/pricing/calculator/)
- [Azure DevOps Services](https://azure.microsoft.com/en-us/products/devops/)
  - Azure Boards, Pipelines, Repos, Test Plans, Artifacts
  - [Azure Extensions Marketplace](https://marketplace.visualstudio.com/azuredevops?culture=en-us&country=us)

# Azure Boards

## GitHub Projects & Project Boards

### Project Boards

Project Boards: Project boards are made up of issues, pull requests, and notes categorized as cards you can drag and drop into your chosen columns. The cards contain relevant metadata for issues and pull requests, like labels, assignees, the status, and who opened it.  See [Creating a Project Board](https://docs.github.com/articles/creating-a-project-board).

There are different types of project boards:

- **User-owned project boards:** Can contain issues and pull requests from any personal repository.
- **Organization-wide project boards:** Can contain issues and pull requests from any repository that belongs to an organization.
- **Repository project boards:** Are scoped to issues and pull requests within a single repository.

### Projects

A project is a customizable spreadsheet in which you can configure the layout by filtering, sorting, grouping your issues and PRs, and adding custom fields to track metadata.   Projects are a new, customizable and flexible tool version of projects for planning and tracking work on GitHub.  You can use different views such as Board or spreadsheet/table.

## Azure Boards

- supports Agile, Scrum and Kanban processes
- track work, issues and code defects associated to a project
- kanban: filter user stories, bugs, features and epics
- standard fields, plus discussion to track comments, history, links and attachments

Delivery Plans: Visual a feature roadmap:

Delivery plans are fully interactive, supporting the following tasks:

- View up to 15 team backlogs, including a mix of backlogs and teams from different projects.
- View custom portfolio backlogs and epics.
- View work that spans several iterations.
- Add backlog items from a plan.
- View rollup progress of features, epics, and other portfolio items.
- View dependencies that exist between work items.

### Link GitHub and Azure Boards

Use Azure Boards to plan and track your work and GitHub as source control for software development.  The Azure Boards App integrates between Azure Boards and GitHub.  GitHub authentication and be UN/PW or PAT.

Integration Scenarios Supported:

- From GitHub:  By GitHub account integrate all repositories.   Configurable on which repos integrate to what projects.
- From Azure Boards: Connect to a GitHub repository

Features:

- links to GitHub commits, pull requests, issues based on [GitHub mentions](https://docs.github.com/en/account-and-profile/managing-subscriptions-and-notifications-on-github/setting-up-notifications/configuring-notifications).
- transition work based on GitHub metion fix, fixes, fixed
- traceability, posts discussion comment to GitHub
- link to GitHub code artifacts, shown as annotations on Kanban board
- status badges of Kanban board columnsadded to GitHub repositories

## Configure GitHub Projects

Fairly straight forward.   New Project, Add Issues, Settings & Permissions, Invite Collaborators

Manage Work:  Control project delverables, release dates and iterations to plan upcoming work.  Iterations can be repeating blocks of time (3 week sprints), any length, include breaks.

Project Views: Change layout, grouping, sorting and filtering your work.  Create different visualizations based on your needs.  Use the [GitHub Command Palette](https://docs.github.com/get-started/using-github/github-command-palette) to switch layouts, show milestones, sort by fields, filter, ....

## Collaborate Using Teams

With team discussions, you can:

- Post on your team's page or participate in a public discussion.
- Link to any team discussion to reference it elsewhere.
- Pin important posts to your team's page.
- Receive email or web notifications.

## Agile Plan and Portfolio Management

- Manage teams, areas, and iterations.
- Manage work items.
- Manage sprints and capacity.
- Customize Kanban boards.
- Define dashboards.
- Customize team process.

Need [Azure Organization ($$$)](https://learn.microsoft.com/en-us/azure/devops/organizations/accounts/create-organization?view=azure-devops).

## References

- [Quickstart for projects (beta) - GitHub Docs](https://docs.github.com/issues/trying-out-the-new-projects-experience/quickstart).
- [About project boards - GitHub Docs](https://docs.github.com/issues/organizing-your-work-with-project-boards/managing-project-boards/about-project-boards).
- [What is Azure Boards? Tools to manage software development projects. - Azure Boards | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/boards/get-started/what-is-azure-boards).
- [Azure Boards-GitHub integration - Azure Boards | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/boards/github).
- [Managing iterations in projects (beta) - GitHub Docs](https://docs.github.com/issues/trying-out-the-new-projects-experience/managing-iterations).
- [Quickstart for projects (beta) - GitHub Docs](https://docs.github.com/issues/trying-out-the-new-projects-experience/quickstart).
- [Best practices for managing projects (beta) - GitHub Docs](https://docs.github.com/issues/trying-out-the-new-projects-experience/best-practices-for-managing-projects).
- [Customizing your project (beta) views - GitHub Docs](https://docs.github.com/issues/trying-out-the-new-projects-experience/customizing-your-project-views).
- [About team discussions - GitHub Docs](https://docs.github.com/organizations/collaborating-with-your-team/about-team-discussions).



# Source Control

Puppet's Five Stages of DevOps Evolution:

0. Build the Foundation
1. Normalize the Technology Stack
2. Standardize and Reduce Variability
3. Expand DevOps Practices
4. Automate Infrastructure Delivery
5. Provide Self-Service Capabilities

Puppet in their  [Puppet - State of DevOps Report 2021](https://puppet.com/resources/report/2021-state-of-devops-report)\ identify that version control is needed in all stages of DevOps evolution.   Application configuration, software, system configuration all require version control.

## What is Source Control?

A Source control system (or version control system) allows developers to collaborate on code and track changes. Use version control to save your work and coordinate code changes across your team. Source control is an essential tool for multi-developer projects.  The version control system saves a snapshot of your files (history) so that you can review and even roll back to any version of your code with ease. Also, it helps to resolve conflicts when merging contributions from multiple sources.

There are several perspectives on version control.

- For developers, it's a daily enabler for work and collaboration to happen. It's part of the daily job, one of the most-used tools.
- For management, the critical value of version control is in:
  - IP security.
  - Risk management.
  - Time-to-market speed through Continuous Delivery, where version control is a fundamental enabler.

## Benefits of Source Control

Whether writing code professionally or personally, you should always version your code using a source control management system. Some of the advantages of using source control are,

- **Create workflows**. Version control workflows prevent the chaos of everyone using their development process with different and incompatible tools. Version control systems provide process enforcement and permissions, so everyone stays on the same page.
- **Work with versions**. Every version has a description in the form of a comment. These descriptions help you follow changes in your code by version instead of by individual file changes. Code stored in versions can be viewed and restored from version control at any time as needed. It makes it easy to base new work on any version of code.
- **Collaboration**. Version control synchronizes versions and makes sure that your changes do not conflict with other changes from your team. Your team relies on version control to help resolve and prevent conflicts, even when people make changes simultaneously.
- **Maintains history of changes**. Version control keeps a record of changes as your team saves new versions of your code. This history can be reviewed to find out who, why, and when changes were made. The history gives you the confidence to experiment since you can roll back to a previous good version at any time. The history lets your base work from any code version, such as fixing a bug in an earlier release.
- **Automate tasks**. Version control automation features save your team time and generate consistent results. Automate testing, code analysis, and deployment when new versions are saved to version control.

## Software Development Values of Source Control

- **Reusability** – why do the same thing twice? Reuse of code is a common practice and makes building on existing assets simpler.
- **Traceability** – Audits are not just for fun; in many industries, it is a legal matter. All activities must be traced, and managers can produce reports when needed. Traceability also makes debugging and identifying root cause easier. Additionally, it helps with feature reuse as developers can link requirements to implementation.
- **Manageability** – Can team leaders define and enforce workflows, review rules, create quality gates and enforce QA throughout the lifecycle?
- **Efficiency** – are we using the right resources for the job, minimizing time and effort? This one is self-explanatory.
- **Collaboration** – When teams work together, quality tends to improve. We catch one another's mistakes and can build on each other's strengths.
- **Learning** – Organizations benefit when they invest in employees learning and growing. It is important for onboarding new team members, the lifelong learning of seasoned members, and the opportunity for workers to contribute to the bottom line and the industry.

## Best Practices for Source Control

- **Make small changes**. In other words, commit early and commit often. Be careful not to commit any unfinished work that could break the build.
- **Do not commit personal files**. It could include application settings or SSH keys. Often personal files are committed accidentally but cause problems later when other team members work on the same code.
- d**Update often and right before pushing to avoid merge conflicts**.
- **Verify your code change before pushing it to a repository**; ensure it compiles and tests are passing.
- **Quality Commit Messages**:  Pay close attention to commit messages, as it will tell you why a change was made. Consider committing messages as a mini form of documentation for the change.
- **Link code changes to work items**. It will concretely link what was created to why it was created—or modified by providing traceability across requirements and code changes.
- **Team Player**:  No matter your background or preferences, be a team player and follow agreed conventions and workflows. Consistency is essential and helps ensure quality, making it easier for team members to pick up where you left off, review your code, debug, and so on.

## References

- [Understand source control - Azure DevOps](https://learn.microsoft.com/en-us/azure/devops/user-guide/source-control).
- [Using source control in your codespace - GitHub Docs](https://docs.github.com/codespaces/developing-in-codespaces/using-source-control-in-your-codespace).

## Source Control Systems

Centralized Source Control: Centralized source control systems are based on the idea that there's a single "central" copy of your project somewhere (probably on a server). Programmers will check in (or commit) their changes to this central copy.

| Benefits                              | Best Usage                                    |
| ------------------------------------- | --------------------------------------------- |
| Easily scales for large organizations | Large integrated codebases                    |
| Granular permission control           | Audit & Access control down to the file level |
| Permits monitoring of usage           | Hard to merge file types                      |
| Allows exclusive file locking         |                                               |

Workflow

1. get latest changes
2. make changes
3. check-in changes

Distributed Source Control

| Benefits                                                 | Best Usage                     |
| -------------------------------------------------------- | ------------------------------ |
| Cross Platform Support                                   | Small & Modular codebases      |
| Open-source friendly code review via pull-requests (PRs) | Evolving through open-source   |
| Complete offline support                                 | Highly distributed teams       |
| Portable history                                         | Teams working across platforms |
| Enthusiastic growing user base                           | Green field code bases         |

Popular distributed version control systems:

- Git
- Mercurial
- Bazaar

DVCS's:

- systems don't necessarily rely on a central server to store all the versions of a project's files
- every developer "clones" a repository copy and has the project's complete history on their local storage
- copy (or "clone") has all the original metadata

Common terms of DVCS's:

- Pulling: getting new changes from a repository
- Pushing: pushing changes to the repository
- changesets: changes to a group of files

Comparison of DVCS to Centralized Source Control

| DVCS Advantages                                              | Disadvantages                                            |
| ------------------------------------------------------------ | -------------------------------------------------------- |
| Actions are quick since repository is local                  | Large binary files                                       |
| Commit changes can be local.  A group of changes (changeset) can be pushed as once. | Large history (and therefore large changset to download) |
| Work without internet (until you need to push/pull)          | No exclusive file locking                                |
| Share Changes before sharing with everyone                   |                                                          |

Git:

- distributed version control system
- branches are lightweight.
- switch contexts, an create a private local branch.
- switch from one branch to another to pivot among different variations of your codebase.
- merge, publish, or dispose of the branch

Team Foundation Version Control (TFVC)

- two workflow models : server workspaces, local workspaces

Git Branching

- cheap and easy to merge
- pull requests:  source code management tools, like GitHub and Azure Repos, enhance Git with pull requests.

Pull Request:

- A pull request is a way to ask another developer to merge one of your branches into their repository.
- It makes it easier for project leads to keep track of changes
- Lets developers start discussions around their work before integrating it with the rest of the codebase.

### Large Files Issue

Distribute systems perform poorly if large files are version controlled in the DVCS.  As a result use an artifact repository.

- [Git Large File Storage](https://git-lfs.com/)
- Package Management Tool to store binaries: [Azure Artifacts](https://azure.microsoft.com/services/devops/artifacts/).

## Git Learning Resources

Visual Studio Code:

- [Git Lens](https://gitlens.amod.io/): This extension brings visualization for code history by using Git blame annotations and code lens. The extension enables you to seamlessly navigate and explore the history of a file or branch. Also, the extension allows you to gain valuable insights via powerful comparison commands and much more.
- [Git History](https://github.com/DonJayamanne/gitHistoryVSCode/blob/master/README.md): Brings visualization and interaction capabilities to view the Git log, file history and compare branches or commits.

Sample Git Commands

- `git branch feature-devops-home-page`
- `git checkout feature-devops-home-page`
- `git branch --list`
- `git status`
- `git add`
- `git commit -m "update welcome page:"`
- `git checkout main`
- `git merge feature-devops-home-page`
- `git log -v  # check history`
- `git log -p # check changes`
- `git reset -hard xyz # back-out, undo changes`

References:

- [Git and TFVC version control - Azure Repos | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/repos/tfvc/comparison-git-tfvc).
- [Get started with Git and Visual Studio - Azure Repos | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/repos/git/gitquickstart).

# Azure Repos & GitHub

[Azure Repos](https://learn.microsoft.com/en-us/azure/devops/repos) two types of version control:

- Git: distributed version control
- Team Foundation Version Control (TFVC): centralized version control

## Azure Repos Features

- Use free private Git repositories, pull requests, and code search: Get unlimited private Git repository hosting and support for TFVC that scales from a hobby project to the world’s largest repository.
- Support for any Git client: Securely connect with and push code into your Git repository from any IDE, editor, or Git client.
- Web hooks and API integration: Add validations and extensions from the marketplace or build your own-using web hooks and REST APIs.
- Semantic code search: Quickly find what you are looking for with a code-aware search that understands classes and variables.
- Collab to build better code: Do more effective Git code reviews with threaded discussion and continuous integration for each change. Use forks to promote collaboration with inner source workflows.
- Automation with built-in CI/CD: Set up continuous integration/continuous delivery (CI/CD) to automatically trigger builds, tests, and deployments. Including every completed pull request using Azure Pipelines or your tools.
- Protection of your code quality with branch policies: Keep code quality high by requiring code reviewer sign-out, successful builds, and passing tests before merging pull requests. Customize your branch policies to maintain your team’s high standards.
- Usage of your favorite tools: Use Git and TFVC repositories on Azure Repos with your favorite editor and IDE.

## GitHub Features

- Automate from code to cloud: Cycle your production code faster and simplify your workflow with GitHub Packages and built-in CI/CD using GitHub Actions.
  - Automate your workflows: Build, test, deploy, and run CI/CD the way you want in the same place you manage code. Trigger Actions from any GitHub event to any available API. Build your Actions in the language of your choice, or choose from thousands of workflows and Actions created by the community.
  - Packages at home with their code: Use Actions to publish new package versions to GitHub Packages automatically. Install packages and images hosted on GitHub Packages or your preferred packages registry in your CI/CD workflows. It is always free for open source, and data transfer within Actions is unlimited for everyone.
- Securing software together: GitHub plays a role in securing the world's code—developers, maintainers, researchers, and security teams. On GitHub, development teams everywhere can work together to secure the world's software supply chain, from fork to finish.
  - Get alerts about vulnerabilities in your code: GitHub continuously scans security advisories for popular languages. Also, it sends security alerts to maintainers of affected repositories with details so they can remediate risks.
  - Automatically update vulnerabilities: GitHub monitors your project dependencies and automatically opens pull requests to update dependencies to the minimum version that resolves known vulnerabilities.
  - Stay on top of CVEs: Stay up to date with the latest Common Vulnerabilities and Exposures (CVEs), and learn how they affect you with the GitHub Advisory Database.
  - Find vulnerabilities that other tools miss: CodeQL is the industry's leading semantic code analysis engine. GitHub's revolutionary approach treats code as data to identify security vulnerabilities faster.
  - Eliminate variants: Never make the same mistake twice. Proactive vulnerability scanning prevents vulnerabilities from ever reaching production.
  - Keep your tokens safe: Accidentally commit a token to a public repository? GitHub got you. With support from 20 service providers, GitHub takes steps to keep you safe.
- Seamless code review: Code review is the surest path to better code and is fundamental to how GitHub works. Built-in review tools make code review an essential part of your team's process.
  - Propose changes: Better code starts with a Pull Request, a living conversation about changes where you can talk through ideas, assign tasks, discuss details, and conduct reviews.
  - Request reviews: If you are on the other side of a review, you can request reviews from your peers to get the detailed feedback you need.
  - See the difference: Reviews happen faster when you know exactly what changes. Diffs compare versions of your source code side by side, highlighting the new, edited, or deleted parts.
  - Comment in context: Discussions happen in comment threads within your code—bundle comments into one review or reply to someone else who is in line to start a conversation.
  - Give clear feedback: Your teammates should not have to think too hard about what a thumbs-up emoji means. Specify whether your comments are required changes or just a few suggestions.
  - Protect branches: Only merge the highest-quality code. You can configure repositories to require status checks, reducing human error and administrative overhead.
- All your code and documentation in one place: Hundreds of millions of private, public, and open-source repositories are hosted on GitHub. Every repository has tools to help your host, version, and release code and documentation.
  - Code where you collaborate: Repositories keep code in one place and help your teams collaborate with the tools they love, even if you work with large files using Git LFS. You can create or import as many projects as possible with unlimited private repositories for individuals and groups.
  - Documentation alongside your code: Host your documentation directly from your repositories with GitHub Pages. Use Jekyll as a static site generator and publish your Pages from the /docs folder on your main branch.
- Manage your ideas: Coordinate early, stay aligned, and get more done with GitHub's project management tools.
  - See your project's large picture: See everything happening in your project and choose where to focus your team's efforts with Projects and task boards that live right where they belong: close to your code.
  - Track and assign tasks: Issues help you identify, assign, and keep track of tasks within your team. You can open an Issue to track a bug, discuss an idea with an @mention, or start distributing work.
- The human side of software: Building software is more about managing teams and communities than coding. Whether on a group of two or 2000, GitHub has the support your people need.
  - Manage and grow teams: Help people organize with GitHub teams, level up to access administrative roles, and fine-tune your permissions with nested teams.
  - Keep conversations: Moderation tools, like issue and pull request locking, help your team stay focused on code. And if you maintain an open-source project, user blocking reduces noise and ensures productive conversations.
  - Set community guidelines: Set roles and expectations without starting from scratch. Customize standard codes of conduct to create the perfect one for your project. Then choose a pre-written license right from your repository.

## GitHub Skills

- [GitHub Skills Site](https://skills.github.com/)

## GitHub Codespaces

Codespaces addresses these common developer challenges:

- developers are working with old hardware and software systems, which are not refreshed.
- developers are often tied to individual development systems. Moving from location to location or system to system is inconvenient or slow to configure.
- a problem for the developers' organizations is the proliferation of intellectual property across all these machines.

## What is Codespaces?

Codespaces is a cloud-based development environment that GitHub hosts. It is essentially an online implementation of Visual Studio Code.

Codespaces allows developers to work entirely in the cloud.

Codespaces even will enable developers to contribute from tablets and Chromebooks.

Because it is based on Visual Studio Code, the development environment is still rich with:

- Syntax highlighting.
- Autocomplete.
- Integrated debugging.
- Direct Git integration.

Developers can create a codespace (or multiple codespaces) for a repository. Each codespace is associated with a specific branch of a repository.

- You can do all your work in codespaces within a browser.
- For an even more responsive experience, you can connect to a codespace from a local copy of Visual Studio Code.

## References

- [Integration of Azure Repos and Git Repositories](https://azure.microsoft.com/services/devops/repos/).
- [Integration of Azure Boards and GitHub](https://learn.microsoft.com/en-us/azure/devops/boards/github/).
- [GitHub Codespaces](https://github.com/features/codespaces).
