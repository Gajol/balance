---
permalink: /application/devops/AZ-400-CI-Azure-Pipelines-GH-Actions
title: "Azure GitHub Actions"
excerpt: "Create Azure Pipelines, configure jobs sequencing dependencies, and scale build environment using YAML."
last_modified_at: 2023-01-07T10:23:16-04:00
toc: true
---

# AZ-400 Implement CI with Azure Pipelines and GitHub Actions

# DevOps Pipeline Concepts

- create a repeatable, reliable, and incrementally-improving process for taking software from concept to customer.
- The goal is to enable a constant flow of changes into production via an automated software production line.

The pipeline:

- The pipeline breaks down the software delivery process into stage

- Each stage aims to verify the quality of new features from a different angle to validate the new functionality and prevent errors from affecting your users.
- The pipeline should provide transparency (visibility) and feedback to the team
- A delivery pipeline enables the flow of more minor changes more frequently, with a focus on flow.
  - DevOps teams can concentrate on optimizing the delivery of changes that bring quantifiable value to the business.
- The pipeline is the focus of your continuous improvement loop.

Pipeline stages:

- build automation
- continuous integration
- test automation
- deployment automation

Pipeline needs and dependencies:

- These automated pipelines need infrastructure to run on. The efficiency of this infrastructure will have a direct impact on the effectiveness of the pipeline
  - platform provisioning:
  - platform configuration management

Pipeline orchestration

- different stages of the pipeline involve different groups of people (collaborating, supervisor the release)
- orchestration provides top-level view of the entire pipeline.
- orchestration allows you to define and control the stages and gain insight into the overall software delivery process
-  value stream mappings on your releases: highlight any remaining inefficiencies and hot spots and pinpoint opportunities to improve your pipeline by conducting value stream mapping of your releases

# Azure Pipelines

Azure Pipelines are cross-platform CI and CD service compatible with any Git provider and most cloud services.

- Language support: Python, Java, PHP, Ruby, C#, Go, ...
- Version Control Systems (VCS): GitHub, GitLab, Azure Repos, Bitbucket, Subversion
- Application Types: Java, JS, Python, .NET, PHP, Go, XCod, C++
- Deployment Targets: Container registry, Virtual machine, Azure services, on-premise, cloud (Azure, GCP, AWS)
- Package Formats: produces packages NuuGet, npm, or Maven packages published to Azure Pipelines.  Can also use any package management repository.

| CI                                               | CD                                              |
| ------------------------------------------------ | ----------------------------------------------- |
| Increase code coverage                           | Automatically deploy code to production         |
| Build faster by splitting test and build runs.   | Ensure deployment targets have the latest code. |
| Automatically ensure you don't ship broken code. | Use tested code from the CI process.            |
| Run-tests continually                            |                                                 |

## Azure Pipeline Key Terms

- Agent: When your build or deployment runs, the system begins one or more jobs. An agent is installable software that runs a build or deployment job.
- Artifact: An artifact is a collection of files or packages published by a build. Artifacts are made available for the tasks, such as distribution or deployment.
- Build: A build represents one execution of a pipeline. It collects the logs associated with running the steps and the test results.
- Continuous delivery: Continuous delivery (CD) (also known as Continuous Deployment) is a process by which code is built, tested, and deployed to one or more test and production stages. Deploying and testing in multiple stages helps drive quality. Continuous integration systems produce deployable artifacts, which include infrastructure and apps. Automated release pipelines consume these artifacts to release new versions and fix existing systems. Monitoring and alerting systems constantly run to drive visibility into the entire CD process. This process ensures that errors are caught often and early.

- Continuous integration: Continuous integration (CI) is the practice used by development teams to simplify the testing and building of code. CI helps to catch bugs or problems early in the development cycle, making them more accessible and faster to fix. Automated tests and builds are run as part of the CI process. The process can run on a schedule, whenever code is pushed, or both. Items known as artifacts are produced from CI systems. The continuous delivery release pipelines use them to drive automatic deployments.
- Deployment target: A deployment target is a virtual machine, container, web app, or any service used to host the developed application. A pipeline might deploy the app to one or more deployment targets after the build is completed and tests are run.
- Job: A build contains one or more jobs. Most jobs run on an agent. A job represents an execution boundary of a set of steps. All the steps run together on the same agent. For example, you might build two configurations - x86 and x64. In this case, you have one build and two jobs.
- Pipeline: A pipeline defines the continuous integration and deployment process for your app. It's made up of steps called tasks. It can be thought of as a script that describes how your test, build, and deployment steps are run.
- Release: When you use the visual designer, you can create a release or a build pipeline. A release is a term used to describe one execution of a release pipeline. It's made up of deployments to multiple stages.
- Stage: Stages are the primary divisions in a pipeline: "build the app," "run integration tests," and "deploy to user acceptance testing" are good examples of stages.
- Task: A task is the building block of a pipeline. For example, a build pipeline might consist of build and test tasks. A release pipeline consists of deployment tasks. Each task runs a specific job in the pipeline.
- Trigger: A trigger is set up to tell the pipeline when to run. You can configure a pipeline to run upon a push to a repository at scheduled times or upon completing another build. All these actions are known as triggers.

# Agents and Pools

Agents:

- To build your code or deploy your software, you generally need at least one agent.
- As you add more code and people, you'll eventually need more.
- When your build or deployment runs, the system begins one or more jobs.
- An agent is an installable software that runs one build or deployment job at a time.

Hosted-agent: Azure pipelines can use Microsoft hosted agents.  Agents have job-time limits and run one-job-at-a-time.

Self-hosted agent: Allows more control.  You can install dependent software needed for your builds and deployments.

## Job  Types

Azure DevOps has four (4) job types:

- Agent pool jobs: run on an agent that is part of a pool.
- Container jobs: run in a container on an agent that is part of a pool
- Deployment group jobs: run on a system in a deployment group
- Agentless jobs: run directly on Azure DevOps.  No agent required.  "Server Jobs"

## Agent Pools

An agent pool defines the sharing boundary for all agents in that pool.\

- In Azure Pipelines, pools are scoped to the entire organization so that you can share the agent machines across projects.
- If you create an Agent pool for a specific project, only that project can use the pool until you add the project pool into another project.
- When creating a build or release pipeline, you can specify which pool it uses, organization, or project scope.
- Pools scoped to a project can only use them across build and release pipelines within a project.
- To share an agent pool with multiple projects, use an organization scope agent pool and add them in each of those projects, add an existing agent pool, and choose the organization agent pool. If you create a new agent pool, you can automatically grant access permission to all pipelines.

### Pre-defined Agent Pools

Azure Pipelines provides a pre-defined agent pool-named **Azure Pipelines** with Microsoft-hosted agents.

It will often be an easy way to run jobs without configuring build infrastructure.

The following virtual machine images are provided by default:

- Windows Server 2022 with Visual Studio 2022.
- Windows Server 2019 with Visual Studio 2019.
- Ubuntu 20.04.
- Ubuntu 18.04.
- macOS 11 Big Sur.
- macOS X Catalina 10.15.

When to Create Agent Pools

Based on a team purpose a new agent pool maybe needed:

- you want to use a set of machines your team owns
- you are an infrastructure team member and you want a pool to support all projects
- you want to share agent machines with a subset of projects

Communication:

- Agents communicate with Azure Pipelines to run and report on jobs.
- Self-hosted agents may be needed to ensure deploy artifacts can reach firewall blocked targets ([reference diagram](https://learn.microsoft.com/en-gb/training/modules/manage-azure-pipeline-agents-pools/8-communicate-to-deploy-to-target-servers))

Other Considerations

- Authentication, Administration, PATs, manual (interactive) vs service

## Agent Pool Security

- organization and project agents
- reader, service account, administrator

## Configure Agent Pools

- YAML-based pipelines:  Pipeline definitions reside in the same repository as the code
- support many features of classic pipelines: PRs, code review, history, branching templates

# Pipelines & Concurrency

Goals:

- Use and estimate parallel jobs.
- Use Azure Pipelines for open-source or private projects.
- Use Visual Designer.
- Work with Azure Pipelines and YAML.

## Parallel Jobs

The term job can refer to multiple concepts, and its meaning depends on the context:

- When you define a build or release, you can define it as a collection of jobs. When a build or release runs, you can run multiple jobs as part of that build or release.
- Each job consumes a parallel job that runs on an agent. When there aren't enough parallel jobs available for your organization, then the jobs are queued up and run one after the other.

Estimate Parallel Jobs: A simple rule of thumb: Estimate that you'll need one parallel job for every four to five users in your organization.

- Parallel jobs are purchased at the organization level, and they're shared by all projects in an organization.

## Open Source Projects - Pipelines

Open-source needs to give anonymous users read-access.  Azure DevOps calls this a public project.

Non-members of a public project will have read-only access to a limited set of services, precisely:

- Browse the code base, download code, view commits, branches, and pull requests.
- View and filter work items.
- View a project page or dashboard.
- View the project Wiki.
- Do a semantic search of the code or work items.

# Azure Pipeline and Visual Designer

You can create and configure your build and release pipelines in the Azure DevOps web portal with the visual designer. (Often referred to as "Classic Pipelines").

The visual designer is great for new users in continuous integration (CI) and continuous delivery (CD).

- The visual representation of the pipelines makes it easier to get started.
- The visual designer is in the same hub as the build results. This location makes it easier to switch back and forth and make changes.

If you think the designer workflow is best for you, create your first pipeline using the [visual designer](https://learn.microsoft.com/en-us/azure/devops/pipelines/get-started-designer).

# Azure Pipeline & YAML

Edit Code -> Edit YAML file -> Push to code repo -> Azure Pipelines -> Deploy to Target

The pipeline is versioned and the follows the same branching structure as the code.

# Continuous Integration

A key pillar of DevOps is continuous integration.  Continuous integration (CI) is the process of automating the build and testing of code every time a team member commits changes to version control.

- CI encourages developers to share their code and unit tests by merging their changes into a shared version control repository after every small task completion.
- Committing code triggers an automated build system to grab the latest code from the shared repository and build, test, and validate the entire main branch (also known as the trunk or main).

The four (4) pillars of CI are:

1. Version Control System:  Manages changes to your source code over time (Git, Subversion, TFVC, ..)
2. Package Management System: Installs, uninstall and manage software packages (NuGet, NPM, Chocolately, HomeBrew, RPM, )
3. Continuous Integration System: Merges all developer working copies to a shared mainline several times a day (Azuer DevOps, TeamCity, Jenkins, ...)
4. Automated Build Process: Creates a software build, including compiling, packaging and running automated tests.  (Apache Ant, NAnt, Gradle, ...)

CI benefits:

- Improving code quality based on rapid feedback
- Triggering automated testing for every code change
- Reducing build times for quick feedback and early detection of problems (risk reduction)
- Better managing technical debt and conducting code analysis
- Reducing long, complex, and bug-inducing merges
- Increasing confidence in codebase health long before production deployment

Build Properties

- build number formatting `$(date:yyyy-mm-dd)$(rev:.r)`
- build status: enabled, paused, disabled
- authorization (scope) and timeouts
- badges: provide an image for build state

# Enable CI with Azure Pipelines

Goal:

- Create a basic build pipeline from a template.
- Track and review a build.
- Invoke a continuous integration build.

## Implement a Pipeline Strategy

- Define a build strategy.
- Explain and configure demands.
- Implement multi-agent builds.
- Use different source control types available in Azure Pipelines.

## Configure Agent Demands

Agents have different properities, based on different OS's and installed dependencies.  

- every agent has a set of capabilities as name-value pairs (NVP); system and user-defined capabilities

Multi-Agent Builds

An organization will have multiple build-agents to support multiple build machines.

- distribute load
- run builds in parallel
- use different agent capabilities

Adding multiple jobs to a pipeline lets you:

- Break your pipeline into sections that need different agent pools or self-hosted agents.
- Publish artifacts in one job and consume them in one or more subsequent jobs.
- Build faster by running multiple jobs in parallel.
- Enable conditional execution of tasks.

Source Control Type Support by Azure Pipelines

- Azure Pipelines (YAML) supports a subset of the repository types; Azure Repos Git, GitHub, GitHub Enterprise, Bitbucket Cloud.   Subversion is not supported.

# Integrate with Azure Pipelines

## Hello World YAML Pipeline

```YAML
name: 1.0$(Rev:.r)

# simplified trigger (implied branch)
trigger:

- main

# equivalents trigger
# trigger:
#  branches:
#    include:
#    - main

variables:
  name: John

pool:
  vmImage: ubuntu-latest

jobs:

- job: helloworld
  steps:
    - checkout: self
    - script: echo "Hello, $(name)"
```

**Name**: The variable name is a bit misleading since the name is in the build number format. tA monotonically increasing number of runs triggered off this pipeline, starting at 1. This number is stored in Azure DevOps. You can make use of this number by referencing $(Rev).

- To make a date-based number, you can use the format `$(Date:yyyyMMdd)` to get a build number like 20221003.
- To get a semantic number like 1.0.x, you can use something like `1.0.$(Rev:.r)`

**Triggers**: by branch, path, PR, schedule, when another pipeline completes (chaining)

**Jobs**: A job is a set of steps executed by an agent in a queue (or pool). Jobs are atomic – they're performed wholly on a single agent. A job has the following attributes besides its name:

- displayName – a friendly name.
- dependsOn - a way to specify dependencies and ordering of multiple jobs.
- condition – a binary expression: if it evaluates to true, the job runs; if false, the job is skipped.
- strategy - used to control how jobs are parallelized.
- continueOnError - to specify if the rest of the pipeline should continue or not if this job fails.
- pool – the name of the pool (queue) to run this job on.
- workspace - managing the source workspace.
- container - for specifying a container image to execute the job later.
- variables – variables scoped to this job.
- steps – the set of steps to execute.
- timeoutInMinutes and cancelTimeoutInMinutes for controlling timeouts.
- services - sidecar services that you can spin up.

Dependencies: You can define dependencies between jobs using the `dependsOn` property

- A sequential dependency is implied if you don't explicitly define a dependency.
- If you want jobs to run parallel, you need to specify `dependsOn: []`.  fan out and fan  is possible.

```YAML
jobs:

- job: A
  steps:
  # steps omitted for brevity

- job: B
  dependsOn: [] # this removes the implicit dependency on previous stage and causes this to run in parallel
  steps:
  # steps omitted for brevity
```

Checkout: ipelines require you to be more explicit using the checkout keyword

Download:  Downloading artifacts requires you to use the download keyword

Resources: Resources let you reference things needed elsewhere:

- other repositories
- pipelines
- builds (classic builds)
- containers (for container jobs)
- packages

Steps: Steps are the tasks in the YAML file.  Each step is a task.  Many out-of-the-box (OOTB) tasks come with Azure DevOps.

Variables: Every variable is a key: value pair

```YAML
variables:
  name: John
steps:

- script: echo "Hello, $(name)!"
```

## Pipeline Structure

A pipeline is one or more stages of a CI/CD process.  Stages are primary divisions in a pipeline.

- a pipeline is one or more stages
- a stage is one or more jobs
- a job is one or more tasks

### Pipeline

```YAML
# pipeline schema
name: string  # build numbering format
resources:
  pipelines: [ pipelineResource ]
  containers: [ containerResource ]
  repositories: [ repositoryResource ]
variables: # several syntaxes
trigger: trigger
pr: pr
stages: [ stage | templateReference ]
```

### Stage

```YAML
# stage schmea
stages:

- stage: Build
  jobs:

  - job: BuildJob
    steps:

    - script: echo Building!
- stage: Test
  jobs:

  - job: TestOnWindows
    steps:

    - script: echo Testing on Windows!
  - job: TestOnLinux
    steps:

    - script: echo Testing on Linux!
- stage: Deploy
  jobs:

  - job: Deploy
    steps:

    - script: echo Deploying the code!
```

Job

```YAML
# job schema
jobs:

- job: MyJob
  displayName: My First Job
  continueOnError: true
  workspace:
    clean: outputs
  steps:

  - script: echo My first job
```

## Deployment Strategies

Deployment strategies allow you to use specific techniques to deliver updates when deploying your application.  Techniques examples:

- Enable initialization.
- Deploy the update.
- Route traffic to the updated version.
- Test the updated version after routing traffic.
- If there's a failure, run steps to restore to the last known good version.

See [Pipeline - Deployment Jobs](https://learn.microsoft.com/en-us/azure/devops/pipelines/process/deployment-jobs).

### Run Once

```YAML
# runOnce - straightforward deployment strategy
# - presnted in lifecycle hooks
strategy:
    runOnce:
        preDeploy:
            pool: [ server | pool ] # See pool schema.
            steps:
            - script: [ script | bash | pwsh | powershell | checkout | task | templateReference ]
        deploy:
            pool: [ server | pool ] # See pool schema.
            steps: ...
        routeTraffic:
            pool: [ server | pool ]
            steps:
            ...
        postRouteTraffic:
            pool: [ server | pool ]
            steps:
            ...
        on:
            failure:
                pool: [ server | pool ]
                steps:
                ...
            success:
                pool: [ server | pool ]
                steps:
                ...
```

### Rolling

```YAML
# Rolling Deployment Strategy
strategy:
    rolling:
        maxParallel: [ number or percentage as x% ]
        preDeploy:       
            steps:
            - script: [ script | bash | pwsh | powershell | checkout | task | templateReference ]
        deploy:         
            steps:
            ...
        routeTraffic:       
            steps:
            ...       
        postRouteTraffic:         
            steps:
            ...
        on:
            failure:       
                steps:
                ...
            success:         
                steps:
                ...

```

### Canary

```YAML
# Canary Deployment Strategy
strategy:
    canary:
        increments: [ number ]
        preDeploy:       
            pool: [ server | pool ] # See pool schema.       
            steps:
            - script: [ script | bash | pwsh | powershell | checkout | task | templateReference ]
        deploy:         
            pool: [ server | pool ] # See pool schema.       
            steps:
            ...
        routeTraffic:       
            pool: [ server | pool ]       
            steps:
            ...       
        postRouteTraffic:         
            pool: [ server | pool ]       
            steps:
            ...
        on:
            failure:       
                pool: [ server | pool ]         
                steps:
                ...
            success:         
                pool: [ server | pool ]         
                steps:
                ...
```

### Lifecycle Hooks

You can achieve the deployment strategies technique by using lifecycle hooks.  Lifecycle hooks inherit the pool specified by the deployment job. Deployment jobs use the `$(Pipeline.Workspace)` system variable. Available lifecycle hooks:

- **preDeploy:** Used to run steps that initialize resources before application deployment starts.
- **deploy:** Used to run steps that deploy your application. Download artifact task will be auto-injected only in the deploy hook for deployment jobs. To stop downloading artifacts, use - download: none or choose specific artifacts to download by specifying [Download Pipeline Artifact task](https://learn.microsoft.com/en-us/azure/devops/pipelines/yaml-schema/steps-download).
- **routeTraffic:** Used to run steps that serve the traffic to the updated version.
- **postRouteTraffic:** Used to run the steps after the traffic is routed. Typically, these tasks monitor the health of the updated version for a defined interval.
- **on: failure** or **on: success:** Used to run steps for rollback actions or

Steps: A step is a linear sequence of operations that make up a job. Each step runs its process on an agent and accesses the pipeline workspace on a local hard drive. This behavior means environment variables aren't preserved between steps, but file system changes are.

Tasks: Tasks are the building blocks of a pipeline. There's a catalog of tasks available to choose from.

## Templates

Azure Pipelines support Stage, Job, Step and Variable templates.

- Stage Template: A stage template can be called with parameters for example as stage.  For example to change the testfile from full to mini based on the stage.
- Job Template: Specify a job once and use it across platforms (Mac, Windows, Linux)
- Steps Template: same concept, variables can then be specified once and reused across multiple pipelines. (e.g., image-name, cpu-architecture, configuration (debug/prod))

## YAML Resources

Resources in YAML represent sources of pipelines, repositories, and containers. For more information on Resources, [see Azure-DevOps-Pipelines-Process-Resources](https://learn.microsoft.com/en-us/azure/devops/pipelines/process/resources).

```YAML
# General Resources Schema
resources:
  pipelines: [ pipeline ]
  repositories: [ repository ]
  containers: [ container ]
```

Container Resource

Container jobs let you isolate your tools and dependencies inside a container.

- The agent launches an instance of your specified container then runs steps inside it.
- The container keyword lets you specify your container images.

```YAML
# Container Reosurce
resources:
  containers:

  - container: linux
    image: ubuntu:16.04

  - container: windows
    image: myprivate.azurecr.io/windowsservercore:1803
    endpoint: my_acr_connection

  - container: my_service
    image: my_service:tag
    ports:

    - 8080:80 # bind container port 80 to 8080 on the host machine
    - 6379 # bind container port 6379 to a random available port on the host machine
    volumes:

    - /src/dir:/dst/dir # mount /src/dir on the host into /dst/dir in the container
```

### Repository Resource

The repository keyword lets you specify an external repository. Let the system know about the repository if:

- If your pipeline has templates in another repository.
- If you want to use multi-repo checkout with a repository that requires a service connection.

```YAML
# Repository Resource
resources:
  repositories:

  - repository: common
    type: github
    name: Contoso/CommonTools
    endpoint: MyContosoServiceConnection
```

## Multiple Repos in Pipeline

How do you reuse git repos across multiple pipelines?  Pipelines often rely on multiple repositories.

- You can have different repositories with sources, tools, scripts, or other items that you need to build your code.
- By using multiple checkout steps in your pipeline, you can fetch and check out other repositories to the one you use to store your YAML pipeline.
- Repositories are now first-class citizens within Azure Pipelines.

Supported Repos: Git< GitHub, BitBucket Cloud

### GitHub Repo

Azure Pipelines can automatically build and validate every pull request and commit to your GitHub repository.  See [Azure GitHub Repos](https://learn.microsoft.com/en-us/azure/devops/pipelines/repos/github).

Granting Access: GitHub App, OAuth, PAT

### Lab: Integrate External Source Control with Azure Pipelines

Azure DevOps: With the introduction of Azure DevOps, Microsoft offers developers a new continuous integration/continuous delivery (CI/CD) service called Azure Pipelines that enables you to build continuously, test, and deploy to any platform or cloud. It has cloud-hosted agents for Linux, macOS, and Windows; powerful workflows with native container support; and flexible deployments to Kubernetes, VMs, and serverless environments.

See also:

- [Azure Pipelines New User Guide - Key concepts - Azure Pipelines | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/pipelines/get-started/key-pipelines-concepts).
- [Azure Pipelines YAML pipeline editor guide - Azure Pipelines | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/pipelines/get-started/yaml-pipeline-editor).
- [Check out multiple repositories in your pipeline - Azure Pipelines | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/pipelines/repos/multi-repo-checkout).
- [Azure Pipelines Agents - Azure Pipelines | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/pipelines/agents/agents).

# GitHub Actions

Actions are the mechanism used to provide workflow automation within the GitHub environment.

They're often used to build continuous integration (CI) and continuous deployment (CD) solutions.

However, they can be used for a wide variety of tasks:

- Automated testing.
- Automatically responding to new issues, mentions.
- Triggering code reviews.
- Handling pull requests.
- Branch management.

They're defined in YAML and stay within GitHub repositories.  Actions are executed on "runners," either hosted by GitHub or self-hosted.  [GitHub Marketplace for Actions](https://github.com/marketplace).

## Actions Flow

Events -> Workflows -> Jobs -> Actions

- Events; GitHub tracks events that occur. Events can trigger the start of workflows.
- Workflows: Workflows can also start on cron-based schedules and can be triggered by events outside of GitHub.
  - Triggers: They can be manually triggered.
  - Automation & Jobs: Workflows are the unit of automation. They contain Jobs.
- Jobs use Actions to get work done.

### Workflows

Workflows define the automation required. It details the events that should trigger the workflow.

- Also, define the jobs that should run when the workflow is triggered.
- The job defines the location in which the actions will run, like which runner to use.
- Workflows are written in YAML and live within a GitHub repository at the place **.github/workflows.**
- [Workflow Syntax](https://docs.github.com/actions/learn-github-actions/workflow-syntax-for-github-actions)

```YAML
# .github/workflows/build.yml
name: Node Build.

on: [push]

jobs:
    mainbuild:

        runs-on: ${{ matrix.os }}

    strategy:
        matrix:
            node-version: [12.x]
            os: [windows-latest]

    steps:

    - uses: actions/checkout@v1
    - name: Run node.js on latest Windows.
      uses: actions/setup-node@v1
      with:
        node-version: ${{ matrix.node-version }}

    - name: Install NPM and build.
      run: |
        npm ci
        npm run build
```

[Workflow Syntax Elements](https://docs.github.com/actions/learn-github-actions/workflow-syntax-for-github-actions):

- **Name:** is the name of the workflow. It's optional but is highly recommended. It appears in several places within the GitHub UI.
- **On:** is the event or list of events that will trigger the workflow.
- **Jobs:** is the list of jobs to be executed. Workflows can contain one or more jobs.
- **Runs-on:** tells Actions which runner to use.
- **Steps:** It's the list of steps for the job. Steps within a job execute on the same runner.
- **Uses:** tells Actions, which predefined action needs to be retrieved. For example, you might have an action that installs node.js.
- **Run:** tells the job to execute a command on the runner. For example, you might execute an NPM command.

### Events

- Events are implemented by the **on** clause in a workflow definition.
- There are several types of events that can [trigger workflows](https://docs.github.com/actions/learn-github-actions/events-that-trigger-workflows).
  - schedule `cron: '0 8-17 * * 1-5'` ( minute, hour, day, month, day-of-week)
  - code: pull_request, push, ..
  - manual: `workflow_dispatch`.  
  - webhook: when a GitHub webhook is called `gollum` (on updating wiki page)
  - external: external systems can fire events

### Jobs

- Workflows contain one or more jobs. A job is a set of steps that will be run in order on a runner.
- Steps within a job execute on the same runner and share the same filesystem.
- The logs produced by jobs are searchable, and artifacts produced can be saved.

```YAML
# jobs run in parallel by default
jobs:
  startup:
    runs-on: ubuntu-latest
    steps:

      - run: ./setup_server_configuration.sh
  build:
    steps:

      - run: ./build_new_server.sh
```

Sequentional uses the `needs` keyword

```YAML
# jobs run in sequential order with "needs"
jobs:
  startup:
    runs-on: ubuntu-latest
    steps:

      - run: ./setup_server_configuration.sh
  build:
    needs: startup
    steps:

      - run: ./build_new_server.sh
```

### Runners

Jobs execute on runners.  The steps can be the execution of a shell script or the execution of a predefined Action.  GitHub provides several hosted runners to avoid you needing to spin up your infrastructure to run actions. Now, the maximum duration of a job is 6 hours, and for a workflow is 72 hours.

For JavaScript code, you have implementations of node.js on:

- Windows
- macOS
- Linux

If you need to use other languages, a Docker container can be used. Now, the Docker container support is only Linux-based. These options allow you to write in whatever language you prefer. JavaScript actions will be faster (no container needs to be used) and more versatile runtime.  The GitHub UI is also better for working with JavaScript actions.

Self-hosted Runners: ([GitHub Self-Hosted Runner Source Code](https://github.com/actions/runner)). Self-hosted runners can be added at different levels within an enterprise:

- Repository-level (single repository).
- Organizational-level (multiple repositories in an organization).
- Enterprise-level (multiple organizations across an enterprise).

### Examine Release and Test an Action

Actions will often produce console output. You don't need to connect directly to the runners to retrieve that output.  On the GitHub UI, the Actions tab lets you see the results of an action.  More logging can be enabled (see [GitHub help](https://docs.github.com/actions/monitoring-and-troubleshooting-workflows/enabling-debug-logging))

### Release Management for Actions

Tags allow you to specify the precise versions that you want to work.  Can use hashes or branches.

- [GitHub Actions Hello-World](https://github.com/skills/hello-github-actions)

### GitHub Actions References

- [Quickstart for GitHub Actions](https://docs.github.com/actions/quickstart).
- [Workflow syntax for GitHub Actions - GitHub Docs](https://docs.github.com/actions/learn-github-actions/workflow-syntax-for-github-actions).
- [Events that trigger workflows - GitHub Docs](https://docs.github.com/actions/learn-github-actions/events-that-trigger-workflows).

# CI with GitHub Actions

Goals:

- Implement Continuous Integration with GitHub Actions.
- Use environment variables.
- Share artifacts between jobs and use Git tags.
- Create and manage secrets.

## CI with Actions

```YAML
name: dotnet Build

on: [push]

jobs:
    build:
        runs-on: ubuntu-latest
        strategy:
            matrix:
                node-version: [10.x]
        steps:

        - uses: actions/checkout@main
        - uses: actions/setup-dotnet@v1
            with:
                dotnet-version: '3.1.x'

        - run: dotnet build awesomeproject
```

- **On:** Specifies what will occur when code is pushed.
- **Jobs:** There's a single job called **build.**
- **Strategy:** It's being used to specify the Node.js version.
- **Steps:** Are doing a checkout of the code and setting up dotnet.
- **Run:** Is building the code.

## Environment Variables

Some built-in variables:

- **GITHUB_WORKFLOW** is the name of the workflow.
- **GITHUB_ACTION** is the unique identifier for the action.
- **GITHUB_REPOSITORY** is the name of the repository (but also includes the name of the owner in owner/repo format)

Setting variables:

```YAML
jobs:
    verify-connection:
        steps:
            - name: Verify Connection to SQL Server
            - run: node testconnection.js
        env:
            PROJECT_SERVER: PH202323V
            PROJECT_DATABASE: HAMaster
```

## Share Artifacts between Jobs

Using the `upload-artifact` and `download-artifact` actions

### Upload

``` YAML
# upload a file
- uses: actions/upload-artifact
  with:
    name: harness-build-log
    path: bin/output/logs/harness.log

# upload a folder
- uses: actions/upload-artifact
  with:
    name: harness-build-logs
    path: bin/output/logs/

# wildcards
- uses: actions/upload-artifact
  with:
    name: harness-build-logs
    path: bin/output/logs/harness[ab]?/*

# several paths
- uses: actions/upload-artifact
  with:
    name: harness-build-logs
    path: |
        bin/output/logs/harness.log
        bin/output/logs/harnessbuild.txt
```

### Download

```YAML
- uses: actions/download-artifact
  with:
    name: harness-build-log
```

### Retention

```YAML
- uses: actions/upload-artifact
  with:
    name: harness-build-log
    path: bin/output/logs/harness.log
    retention-days: 12
```

### Deletion

Done through GitHub UI: [Removing Workflow Artifacts](https://docs.github.com/actions/managing-workflow-runs/removing-workflow-artifacts)

## Badges: Examine Workflow Badges

Badges are adding using URL's ([GitHub Adding Workflow Badges](https://docs.github.com/actions/monitoring-and-troubleshooting-workflows/adding-a-workflow-status-badge)).  Format:
`https://github.com/<OWNER>/<REPOSITORY>/actions/workflows/<WORKFLOW_FILE>/badge.svg`

## Action - Best Practices

- Create chainable actions. Don't create large monolithic actions. Instead, create smaller functional actions that can be chained together.
- Version your actions like other code. Others might take dependencies on various versions of your actions. Allow them to specify versions.
- Provide the **latest** label. If others are happy to use the latest version of your action, make sure you provide the **latest** label that they can specify to get it.
- Add appropriate documentation. As with other codes, documentation helps others use your actions and can help avoid surprises about how they function.
- Add details **action.yml** metadata. At the root of your action, you'll have an **action.yml** file. Ensure it has been populated with author, icon, expected inputs, and outputs.
- Consider contributing to the marketplace. It's easier for us to work with actions when we all contribute to the marketplace. Help to avoid people needing to relearn the same issues endlessly.

## Mark Release with Git tags

In Git, releases are based on Git tags. These tags mark a point in the history of the repository. Tags are commonly assigned as releases are created. (See [GitHub About Releases](https://docs.github.com/repositories/releasing-projects-on-github/about-releases))

## Create Encrypted Secrets

Actions often can use secrets within pipelines. Common examples are passwords or keys.

In GitHub actions, It's called Secrets.  Secrets are similar to environment variables but encrypted. They can be created at two levels:

- Repository
- Organization

If secrets are created at the organization level, access policies can limit the repositories that can use them.

### Using Secrets in Workflow

Secrets aren't passed automatically to the runners when workflows are executed.  Instead, when you include an action that requires access to a secret, you use the **secrets** context to provide it.

```YAML
steps:

  - name: Test Database Connectivity
    with:
      db_username: ${{ secrets.DBUserName }}
      db_password: ${{ secrets.DBPassword }}
```

Use the secrets in command-line arguments:

```YAML
steps:

  - shell: pwsh
    env:
      DB_PASSWORD: ${{ secrets.DBPassword }}
    run: |
      db_test "$env:DB_PASSWORD"
```

Workflows can use up to 100 secrets, and they're limited to 64 KB in size.  See [Encrypted Secrets](https://docs.github.com/actions/security-guides/encrypted-secrets).

## See Also:

- [About continuous integration - GitHub Docs](https://docs.github.com/actions/automating-builds-and-tests/about-continuous-integration).
- [Environment variables - GitHub Docs](https://docs.github.com/actions/learn-github-actions/environment-variables).
- [Storing workflow data as artifacts - GitHub Docs](https://docs.github.com/actions/advanced-guides/storing-workflow-data-as-artifacts).
- [Encrypted secrets - GitHub Docs](https://docs.github.com/actions/security-guides/encrypted-secrets).

# Container Build Strategy

Goals:

- Design a container strategy
- Work with Docker Containers
- Create an Azure Container Registry
- Explain Docker microservices and container

Containers

Containers are the third computing model, after bare metal and virtual machine

- Unlike a VM, which provides hardware virtualization, a container provides operating-system-level virtualization by abstracting the "user space," not the entire operating system. The operating system level architecture is being shared across containers. It's what makes containers so lightweight.
- Docker gives you a simple platform for running apps in containers. Either old or new apps on Windows and Linux, and that simplicity is a powerful enabler for all aspects of modern IT.
- Containers aren't only faster and easier to use than VMs; they also make far more efficient use of computing hardware. Also, they have provided engineering teams with dramatically more flexibility for running cloud-native applications.
- Containers package up the application services and make them portable across different computing environments for dev/test and production use.
- With containers, it's easy to ramp application instances to match spikes in demand quickly. And because containers draw on resources of the host OS, they're much lighter weight than virtual machines. It means containers make highly efficient use of the underlying server infrastructure.
- Though the container runtime APIs are well suited to managing individual containers, they're woefully inadequate for managing applications that might comprise hundreds of containers spread across multiple hosts.
- You need to manage and connect containers to the outside world for scheduling, load balancing, and distribution. It's where a container orchestration tool like Azure Kubernetes Services (AKS) comes into its own.
- AKS handles the work of scheduling containers onto a compute cluster and manages the workloads to ensure they run as the user intended.
- AKS is an open-source system for deploying, scaling and managing containerized applications. Instead of bolting operations as an afterthought, AKS brings software development and operations together by design.
- AKS enables an order-of-magnitude increase in the operability of modern software systems. With declarative, infrastructure-agnostic constructs to describe how applications are composed. Also how they interact and how they're managed.

Container benefits:

- Containers are portable. A container will run wherever Docker is supported.  Containers are a solution to the problem of how to get the software to run reliably when moved from one computing environment to another.  Problems arise when the supporting software environment isn't identical.
- Containers allow you to have a **consistent** development environment. For example, a SQL Server 2019 CU2 container that one developer is working with will be identical to another developer.
- Containers can be lightweight. A container may be only tens of megabytes in size, but a virtual machine with its entire operating system may be several gigabytes. Because of it, a single server can host far more containers than virtual machines.
- Containers can be efficient: fast to deploy, fast to boot, fast to patch, and quick to update.

## Container Structure

Simple terms;

- A container is a thing that runs a little program package
- Docker is the container runtime and orchestrator

A container consists of an entire runtime environment:

- An application, plus all its dependencies.
- Libraries and other binaries.
- Configuration files needed to run it, bundled into one package.

### Containers versus Virtualization

Similarities:  Containers and VMs are similar in their goals: to isolate an application and its dependencies into a self-contained unit that can run anywhere. They remove the need for physical hardware, allowing for:

- More efficient use of computing resources.
- Energy consumption.
- Cost-effectiveness.

Differences:  The architecture approach.

Virtual Machines: emulates a real computer.  VM's run on top of a physical machine.  VM is composed of the Application, Binaries, Libraries and the Guest OS. The VM executes on the Hypervisor, which executes on the Host OS.

| VM Approach            | Container Approach     |
| ---------------------- | ---------------------- |
| App                    | App                    |
| Binaries and Libraries | Binaries and Libraries |
| Guest OS               |                        |
| Hypervisor             | Docker Engine          |
| Host OS                | Host OS                |
| Server                 | Server                 |

### Docker Container

The standard steps when working with containers are:

- **Docker build** - You create an image by executing a Dockerfile.
- **Docker pull** - You retrieve the image, likely from a container registry.
- **Docker run** - You execute the container. An instance is created of the image.

You can often execute the docker run without needing first to do the docker pull.  In that case, Docker will pull the image and then run it. Next time, it won't need to pull it again.

### Dockerfile core concepts

```sh
# example dockerfile
FROM ubuntu
LABEL maintainer="johndoe@contoso.com"
ADD appsetup /
RUN /bin/bash -c 'source $HOME/.bashrc; \
echo $HOME'
CMD ["echo", "Hello World from within the container"]
```

Multi-Stage Docker Files

```sh
# stage 3 takes outputs from previous stages
FROM mcr.microsoft.com/dotnet/core/aspnetcore:3.1 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
WORKDIR /src
COPY ["WebApplication1.csproj", ""]
RUN dotnet restore "./WebApplication1.csproj"
COPY . .
WORKDIR "/src/."
RUN dotnet build "WebApplication1.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "WebApplication1.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "WebApplication1.dll"]
```

### Multi-Stage Build - Considerations

- container modularity: keep containers single purpose
- avoid unnecessary packages
- choose an appropriate base: start with a base image that only contains required packages
- avoid application data: isolate application and its data.  Use docker volume and persistent storage mechanisms that exist outside the lifespan of a container

## Azure Container Services

[Azure Container Instances (ACI)](https://azure.microsoft.com/services/container-instances/)

Running your workloads in Azure Container Instances (ACI) allows you to create your applications rather than provisioning and managing the infrastructure that will run the applications.

ACIs are simple and fast to deploy, and when you're using them, you gain the security of hypervisor isolation for each container group. It ensures that your containers aren't sharing an operating system kernel with other containers.

[Azure Kubernetes Service (AKS)](https://azure.microsoft.com/services/kubernetes-service/)

Kubernetes has quickly become the de-facto standard for container orchestration. This service lets you quickly deploy and manage Kubernetes, to scale and run applications while maintaining overall solid security.

This service started life as Azure Container Services (ACS) and supported Docker Swarm and Mesos/Mesosphere DC/OS at release to manage orchestrations. These original ACS workloads are still supported in Azure, but Kubernetes support was added.

It quickly became so popular that Microsoft changed the acronym for Azure Container Services to AKS and later changed the name of the service to Azure Kubernetes Service (also AKS).

[Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/)

This service lets you store and manage container images in a central registry. It provides you with a Docker private registry as a first-class Azure resource.

All container deployments, including DC/OS, Docker Swarm, and Kubernetes, are supported. The registry is integrated with other Azure services such as the App Service, Batch, Service Fabric, and others.

Importantly, it allows your DevOps team to manage the configuration of apps without being tied to the configuration of the target-hosting environment.

[Azure Container Apps](https://azure.microsoft.com/services/container-apps/)

Azure Container Apps allows you to build and deploy modern apps and microservices using serverless containers. It deploys containerized apps without managing complex infrastructure.

You can write code using your preferred programming language or framework and build microservices with full support for [Distributed Application Runtime (Dapr)](https://dapr.io/). Scale dynamically based on HTTP traffic or events powered by [Kubernetes Event-Driven Autoscaling (KEDA)](https://keda.sh/).

[Azure App Service](https://azure.microsoft.com/services/app-service/)

Azure Web Apps provides a managed service for both Windows and Linux-based web applications and provides the ability to deploy and run containerized applications for both platforms. It provides autoscaling and load balancing options and is easy to integrate with Azure DevOps.

## Deploy Docker Containers to Azuer App Service

[Lab](https://learn.microsoft.com/en-gb/training/modules/design-container-build-strategy/8-deploy-docker-containers-to-azure-app-service-web-apps):  build a custom Docker Image and push it to Azure Container Registry.  From the registry deploy to Azure App Service.

## See Also

- [Container Jobs in Azure Pipelines - Azure Pipelines](https://learn.microsoft.com/en-us/azure/devops/pipelines/process/container-phases).
- [Build an image - Azure Pipelines](https://learn.microsoft.com/en-us/azure/devops/pipelines/ecosystems/containers/build-image).
- [Service Containers - Azure Pipelines](https://learn.microsoft.com/en-us/azure/devops/pipelines/process/service-containers).
- [Quickstart - Create registry in portal - Azure Container Registry](https://learn.microsoft.com/en-us/azure/container-registry/container-registry-get-started-portal).
- [What are Microservices?](https://learn.microsoft.com/en-us/devops/deliver/what-are-microservices).
- [CI/CD for microservices](https://learn.microsoft.com/en-us/azure/architecture/microservices/ci-cd).
