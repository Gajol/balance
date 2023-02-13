---
permalink: /application/devops/AZ-400-Development-Enterprise DevOps
title: "Development in DevOps"
excerpt: "A software branching strategy allows developer flexibility, transparency and collaboration during code development phase."
last_modified_at: 2023-01-07T10:23:16-04:00
toc: true
---
# AZ-400: Development for Enterprise DevOps

# Structure Git Repo

Objectives:  Understand Git repos, mono or multiple repos, how to structure a Git Repos, implement a changelog

## Repos: Mono vs Multiple

Goal:

- manageable repos clear of bloat and unrelated code
- keep a clear separation of concerns

Mono repos:all the source code is kept in a single repository

Multiple repos: organizing your projects into their separate repository

## ChangeLog Tools:

Changelog:  a file with a list of the changes.

[gitchangelog](https://pypi.org/project/gitchangelog/): python based tool. *Use your commit log to make beautifull and configurable changelog file.*

[github-changelog-generator](https://github.com/github-changelog-generator/github-changelog-generator): ruby based

See also:

- [Understand source control - Azure DevOps](https://learn.microsoft.com/en-us/azure/devops/user-guide/source-control).
- [Build Azure Repos Git repositories - Azure Pipelines | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/pipelines/repos/azure-repos-git).
- [Check out multiple repositories in your pipeline - Azure Pipelines | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/pipelines/repos/multi-repo-checkout).

# Git branches and Workflows

Goals:

- Describe Git branching workflows
- Implement feature branches
- Implement GitHub Flow
- Fork a repo

Git branch workflows:

When evaluating a workflow for your team, you must consider your team's culture. You want the workflow to enhance your team's effectiveness and not be a burden that limits productivity. Some things to consider when evaluating a Git workflow are:

- Does this workflow scale with team size?
- Is it easy to undo mistakes and errors with this workflow?
- Does this workflow impose any new unnecessary cognitive overhead on the team?

## Popular Workflows

Trunk-based development: Feature development on a dedicated branch (not the main branch).  Developers can work on a feature (branch) without impacting the main codebase.  The main branch is always a working branch.

Forking Workflow: Different from a single-server repository.  A developer has their own private local repo (a forked repo)

Feature Branch Workflow

- Pull requests allow for team to common on work
- Feature branches pushed to central repo allows sharing feature with others
- Feature branches should have descriptive names

Process

1. create a branch
2. commit to branch
3. open a pull request: starts a discussion with your team.  Use the @mention in the PR to request feedback
4. fork & pull model:  maintainers are notified of changes to consider via the PR
5. discuss and review the code
6. deploy: prior to merging, deploy and vlaidate changes
7. merge: merge code to main branch

## Git branch model & Continuous Delivery

Git principles;

- The main branch:
  - The main branch is the only way to release anything to production.
  - The main branch should always be in a ready-to-release state.
  - Protect the main branch with branch policies.
  - Any changes to the main branch flow through pull requests only.
  - Tag all releases in the main branch with Git tags.
- The feature branch:
  - Use feature branches for all new features and bug fixes.
  - Use feature flags to manage long-running feature branches.
  - Changes from feature branches to the main only flow through pull requests.
  - Name your feature to reflect its purpose.
- Pull requests:
  - Review and merge code with pull requests.
  - Automate what you inspect and validate as part of pull requests.
  - Tracks pull request completion duration and set goals to reduce the time it takes.

Azure Marketplace: Tools for branch model

- [Azure CLI](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli): is a command-line interface for Azure.
- [Azure DevOps CLI](https://learn.microsoft.com/en-us/azure/devops/cli): It's an extension of the Azure CLI for working with Azure DevOps and Azure DevOps Server designed to seamlessly integrate with Git, CI pipelines, and Agile tools. With the Azure DevOps CLI, you can contribute to your projects without leaving the command line. CLI runs on Windows, Linux, and Mac.
- [Git Pull Request Merge Conflict](https://marketplace.visualstudio.com/items?itemName=ms-devlabs.conflicts-tab): This open-source extension created by Microsoft DevLabs allows you to review and resolve the pull request merge conflicts on the web. Any conflicts with the target branch must be resolved before a Git pull request can complete. With this extension, you can resolve these conflicts on the web as part of the pull request merge instead of doing the merge and resolving conflicts in a local clone.

## GitHub flow

[GitHub flow](https://docs.github.com/en/get-started/quickstart/github-flow) is a branch-based workflow suggested for GitHub.

1. Create a branch
2. Make changes
3. Create a PR
4. Address review comments
5. Merge your PR
6. Delete your branch: After you merge your pull request, delete your branch. This indicates that the work on the branch is complete and prevents you or others from accidentally using old branches

[GitHub About Branches](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-branches)

## Fork Workflow

The forking workflow is fundamentally different than other popular Git workflows.   Commonly used in public open-source projects.

Instead of using a single server-side repository to act as the "central" codebase, it gives every developer their server-side repository.

It means that each contributor has two Git repositories:

- A private local.
- A public server-side.

### Key points

- only the project maintainer can push to the official repository
- forking workflow typically will be intended for merging into the original project maintainer's repository
- a distributed workflow that provides you a flexible way for large, organic teams (including untrusted third parties) to collaborate securely
- Forked repositories are created using the standard `git clone` command

### Flow

The following is a step-by-step example of this workflow:

- A developer 'forks' an 'official' server-side repository. It creates their server-side copy.
- The new server-side copy is cloned to their local system.
- A Git remote path for the 'official' repository is added to the local clone.
- A new local feature branch is created.
- The developer makes changes to the new branch.
- New commits are created for the changes.
- The branch gets pushed to the developer's server-side copy.
- The developer opens a pull request from the new branch to the 'official' repository.
- The pull request gets approved for merge and is merged into the original server-side repository.

To integrate the feature into the official codebase:

- The maintainer pulls the contributor's changes into their local repository.
- Checks to make sure it doesn't break the project.
- Merges it into their local main branch.
- Pushes the main branch to the official repository on the server.

## Version Control with Git in Azure Repos

Two version control systems (VCS) are supported; Team Foundation Version Control (TFVC) and Git.

## Learn more

- [Git branching guidance - Azure Repos | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/repos/git/git-branching-guidance).
- [Create a new Git branch from the web - Azure Repos | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/repos/git/create-branch).
- [How Microsoft develops modern software with DevOps - Azure DevOps | Microsoft Docs](https://learn.microsoft.com/en-us/devops/develop/how-microsoft-develops-devops).
- [Fork your repository - Azure Repos | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/repos/git/forks).

# Pull Request and Azure Repos: Collaboration

Goals:

- Leverages pull requests for collaboration and code reviews
- Give feedback using pull requests
- Configure branch policies
- Use GitHub mobile for pull requests approvals

Branches & Policies

- can be protected by policies; require PR to be approved, reject pushes to protected branches, add conditions to a PR to enforce a higher level of quality
- require a minimum number of reviewers, prohibit approving own changes, vote/wait/reject, block while comments active

Pull Request Resources:

- [About pull requests and permissions - Azure Repos | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/repos/git/about-pull-requests).
- [Create a pull request to review and merge code - Azure Repos | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/repos/git/pull-requests).
- [Review and comment on pull requests - Azure Repos | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/repos/git/review-pull-requests).
- [Protect your Git branches with policies - Azure Repos | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/repos/git/branch-policies).
- [Creating an issue or pull request - GitHub Docs](https://docs.github.com/desktop/contributing-and-collaborating-using-github-desktop/working-with-your-remote-repository-on-github-or-github-enterprise/creating-an-issue-or-pull-request).

# Identify Technical Debt

This module examines technical debt, complexity, quality metrics, and plans for effective code reviews and code quality validation.

- Identify and manage technical debt
- Integrate code quality tools
- Plan code reviews
- Describe complexity and quality metrics

## Code Quality

Five key traits to measure for code quality:

1. Reliability: Probability that a system will run without failure over a specific period of operation. Software availability can be measured using the mean time between failures (MTBF). Low defect counts are crucial for developing a reliable codebase.
2. Maintainability: Maintainability measures how easily software can be maintained.  Factors include; codebase size, consistency, structure, complexity.  Metrics to measure stylistic warnings, Halstead complexity[^Halstead].  Automated and human (subjective) measures.
3. Testability: Testability measures how well the software supports testing efforts.  How does the software allow control, observe, isolate and automate testing.   How many test cases are needed to find potential faults in a system. The size and complexity of the software can impact testability.
4. Portability: Portability measures how usable the same software is in different environments; the platform independence of the software.  Test code on different platforms, compile with at least two compilers (and set warning levels at highest level)
5. Reusability: Reusability measures whether existing assets—such as code—can be used again. Assets are more easily reused if they have modularity or loose coupling characteristics. The number of interdependencies can measure reusability. Running a static analyzer can help you identify these interdependencies.

Software Development

- establish quality goals ([SonarQube Quality Gates](https://docs.sonarqube.org/latest/user-guide/quality-gates/))
- establish quality gates

## Code Complexity & Quality Metrics

### Code Complexity

Complexity metrics can help in measuring quality. [Cyclomatic complexity](https://en.wikipedia.org/wiki/Cyclomatic_complexit) measures the number of linearly independent paths through a program's source code. Another way to understand quality is through calculating Halstead complexity measures.

This measure:

- Program vocabulary.
- Program length.
- Calculated program length.
- Volume.
- Difficulty.
- Effort.

### Quality Metrics

The following is a list of metrics that directly relate to the quality of the code being produced and the build and deployment processes.

- **Failed builds percentage** - Overall, what percentage of builds are failing?
- **Failed deployments percentage** - Overall, what percentage of deployments are failing?
- **Ticket volume** - What is the overall volume of customer or bug tickets?
- **Bug bounce percentage** - What percentage of customer or bug tickets are reopened?
- **Unplanned work percentage** - What percentage of the overall work is unplanned?

## Technical Debt

Technical debt[^debt] is a term that describes the future cost that will be incurred by choosing an easy solution today instead of using better practices because they would take longer to complete.

Common sources of technical debt:

- Lack of coding style and standards.
- Lack of or poor design of unit test cases.
- Ignoring or not understanding object oriented design principles.
- Monolithic classes and code libraries.
- Poorly envisioned the use of technology, architecture, and approach. (Forgetting that all system attributes, affecting maintenance, user experience, scalability, and others, need to be considered).
- Over-engineering code (adding or creating code that isn't required, adding custom code when existing libraries are sufficient, or creating layers or components that aren't needed).
- Insufficient comments and documentation.
- Not writing self-documenting code (including class, method, and variable names that are descriptive or indicate intent).
- Taking shortcuts to meet deadlines.
- Leaving dead code in place.

### Measure and Manage Technical Debt

Integrating the assessment and measurement of technical debt and code quality overall is essential as part of your Continuous Integration and Deployment pipelines in Azure DevOps.

### Code Quality Tools

NDepend: for .Net developers. Visual Studio extension that assesses the amount of technical debt a developer has added during a recent development period, typically in the last hour.

Resharper Code Quality Analysis: Resharper can make a code quality analysis from the command line. Also, be set to fail builds when code quality issues are found automatically. Rules can be configured for enforcement across teams.  Resharper is Visual Studio and .Net focused.

Code Quality vs Vulnerabilities:  Code Quality tools like SonarQube and Resharper are not vulnerability scanners of code.   Fority Static Code Analyze - Micro Focus provides Static Application Security Testing (SAST)[^SAST].

### Plan Code Reviews: Effective Ones

Code reviews improve quality, but only if the process is effective:

- no single best way for a code review
- developers should not be over protective of code
- knowledge-sharing is a key benefit and one of the most important outcomes
- effective code reviews help the development team learn; similar to pair-programming concepts
- improving code quality (code reviews enhances code quality) reduces the cost of the code
- team leaders need to establish and foster a code review culture

## Learn More

- [Technical Debt – The Anti-DevOps Culture - Developer Support (microsoft.com)](https://devblogs.microsoft.com/premier-developer/technical-debt-the-anti-devops-culture/).
- [Microsoft Security Code Analysis documentation overview | Microsoft Docs](https://learn.microsoft.com/en-us/azure/security/develop/security-code-analysis-overview).
- [Build Quality Indicators report - Azure DevOps Server | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/report/sql-reports/build-quality-indicators-report).

# Git Hooks

Goals:

- Understand Git hooks
- Identify when used Git hooks
- Implement Git hooks for automation
- Explain Git hooks' behavior

## Introduction

Git hooks are a mechanism that allows code to be run before or after certain Git lifecycle events.  For example, one could hook into the commit-msg event to validate that the commit message structure follows the recommended format. The hooks can be any executable code, including shell, PowerShell, Python, or other scripts. Or they may be a binary executable. Anything goes!

The only criteria are that hooks must be stored in the .git/hooks folder in the repo root. Also, they must be named to match the related events (Git 2.x):

- applypatch-msg
- pre-applypatch
- post-applypatch
- pre-commit
- prepare-commit-msg
- commit-msg
- post-commit
- pre-rebase
- post-checkout
- post-merge
- pre-receive
- update
- post-receive
- post-update
- pre-auto-gc
- post-rewrite
- pre-push

### Git hook use cases

Some examples of where you can use hooks to enforce policies, ensure consistency, and control your environment:

- Enforcing preconditions for merging
- Verifying work Item ID association in your commit message
- Preventing you & your team from committing faulty code
- Sending notifications to your team's chat room (Teams, Slack, HipChat, etc.)

Git hooks allow you to run custom scripts whenever certain important events occur in the Git life cycle—for example, committing, merging, and pushing.

#### Pre-commit script:  To ensure no access keys are included:

```sh
#!C:/Program\ Files/Git/usr/bin/sh.exe
matches=$(git diff-index --patch HEAD | grep '^+' | grep -Pi 'password|keyword2|keyword3')
if [ ! -z "$matches" ]
then
    cat <<\EOT
Error: Words from the blocked list were present in the diff:
EOT
    echo $matches
    exit 1
fi
```

How script works:

1. `git diff-index`: identifies the code increment committed in the script.
2. This increment is then compared against the list of specified keywords.
3. If any matches are found, an error is raised to block the commit;
4. the script returns an error message with the list of matches.
5. The pre-commit script doesn't return 0 (zero), which means the commit fails.

### Git hooks - Shared in Repo

- Place scripts in `~/.githooks` folder.  Named to match the corresponding events like post-checkout, pre-commit, post-commit, update, ...
- You can override git hooks (bad practice) with `git commit --no-verify`

See also:

- [Creating a pre-receive hook script - GitHub Docs](https://docs.github.com/enterprise-server@3.1/admin/policies/enforcing-policy-with-pre-receive-hooks/creating-a-pre-receive-hook-script).
- [Service hooks event reference - Azure DevOps | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/service-hooks/events).

# Foster Inner Source

Goals:

- Use Git to foster inner source across the organization
- Implement fork workflow
- Choose between branches and forks
- Share code between forks

Fork-based pull request (common in open source) can also be used within an organization.

- opens software development process to allow developers to collaborate across projects and the enterprise (Microsoft uses inner source - e.g., fork-based pulls)

Benefits

- all developers can see the enterprises code (e.g., prior to this only Outlook developers @ Microsoft could see Outlook sofware).  
- Allows developers to investigate sources of errors (e.g., a SharePoint coder looking at the Outlook code on an integration issue)

What is in a fork?

- all the contents from the upstream repo
- can include branches
- no permissions or policies are included
- PR's can go in either direction (up or down stream)

## The forking workflow

- Create a fork.
- Clone it locally.
- Make your changes locally and push them to a branch.
- Create and complete a PR to upstream.
- Sync your fork to the latest from upstream.

See:

- [Fork your repository - Azure Repos | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/repos/git/forks).
- [Clone an existing Git repo - Azure Repos | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/repos/git/clone).

# Manage Git Repos

Goal:

- Understand large Git repositories
- Explain Virtual File System (VFS) for Git
- Use Git Large File Storage (LFS)
- Purge repository data
- Manage and Automate Release Notes with GitHub

## Git & Large Repos

Git is a great version control system widely adopted and recommended, but a few concerns should be made and taken care of when working with large repositories.  There are two primary causes for large repositories:

- Long history
- Large binary files

Recommendation:  When cloning repos do a shallow clone.   `git clone --depth [depth] [clone-url] `

CFS for Git: VFS for Git helps with large repositories. It requires a Git LFS client.

-  [Working with large files](https://docs.github.com/repositories/working-with-files/managing-large-files) and
- [Virtual File System for Git: Enable Git at Enterprise Scale](https://github.com/microsoft/VFSForGit)

### Scalar

Scalar is a .NET Core application available for Windows and macOS. With tools and extensions for Git to allow very large repositories to maximize your Git command performance. Microsoft uses it for Windows and Office repositories. If Azure Repos hosts your repository, you can clone a repository using the [GVFS protocol](https://github.com/microsoft/VFSForGit/blob/master/Protocol.md#the-gvfs-protocol-v1).  

It achieves by enabling some advanced Git features, such as:

- *Partial clone:* reduces time to get a working repository by not downloading all Git objects right away.
- *Background prefetch:* downloads Git object data from all remotes every hour, reducing the time for foreground git fetch calls.
- *Sparse-checkout:* limits the size of your working directory.
- *File system monitor:* tracks the recently modified files and eliminates the need for Git to scan the entire work tree.
- *Commit-graph:* accelerates commit walks and reachability calculations, speeding up commands like git log.
- *Multi-pack-index:* enables fast object lookups across many pack files.
- *Incremental repack:* Repacks the packed Git data into fewer pack files without disrupting concurrent commands using the multi-pack-index.

## Purge Repo Data

While one of the benefits of Git is its ability to hold long histories for repositories efficiently, there are times when you need to purge data.

The most common situations are where you want to:

- Significantly reduce the size of a repository by removing history.
- Remove a large file that was accidentally uploaded.
- Remove a sensitive file that shouldn't have been uploaded.

Tools:

- [git filter-repo](https://github.com/newren/git-filter-repo) is a tool for rewriting history
- https://rtyley.github.io/bfg-repo-cleaner: Cleaner is a commonly used open-source tool for deleting or "fixing" content in repositories. It's easier to use than the git filter-branch command.

See also:

- [Quickly rewrite git repository history](https://github.com/newren/git-filter-repo/).
- [Removing files from Git Large File Storage](https://docs.github.com/repositories/working-with-files/managing-large-files/removing-files-from-git-large-file-storage).
- [Removing sensitive data from a repository](https://docs.github.com/authentication/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository).
- [BFG Repo Cleaner](https://rtyley.github.io/bfg-repo-cleaner).

## Manage Releases with GitHub Repos

Releases in GitHub are based on [Git tags](https://git-scm.com/book/en/Git-Basics-Tagging).  See [Viewing your repository's releases and tags.](https://docs.github.com/repositories/releasing-projects-on-github/viewing-your-repositorys-releases-and-tags)

- When creating new releases with release notes, it's possible to @mentions contributors, add links to binary files and edit or delete existing releases.
- Publish an action from a specific release in GitHub Marketplace.
- Choose whether Git LFS objects are included in the ZIP files and tarballs GitHub creates for each release.
- Receive notifications when new releases are published in a repository.

Steps:

- Creating a release:  `gh release create tag`.  Ceate a pre-release with specified title and notes `gh release create v1.2.1 --title`

- Edit a release: Must use GitHub (GH) UI on the Release tab
- Delete a release: `gh release delete tag -y`

See:

- [Managing releases in a repository - GitHub Docs](https://docs.github.com/repositories/releasing-projects-on-github/managing-releases-in-a-repository) - If you want to perform the same steps from Web Browser instead of GitHub CLI.
- [Publishing an action in the GitHub Marketplace](https://docs.github.com/actions/creating-actions/publishing-actions-in-github-marketplace).
- [Managing Git LFS objects in archives of your repository](https://docs.github.com/github/administering-a-repository/managing-git-lfs-objects-in-archives-of-your-repository).
- [Viewing your subscriptions](https://docs.github.com/github/managing-subscriptions-and-notifications-on-github/viewing-your-subscriptions).

## Release Note Automation

- option for release note automation when creating a release
- use `.github/release.yml` to customize release notes

release.yml: Specify in YAML the pull request labels and authors you want to exclude from this release. You can also create new categories and list the pull request labels in each.  See [GitHub - Auto-generated Release Notes](https://docs.github.com/en/repositories/releasing-projects-on-github/automatically-generated-release-notes#configuration-options).

```yml
# .github/release.yml

changelog:
  exclude:
    labels:
    - ignore-for-release
    authors:
    - octocat
  categories:
    - title: Breaking Changes 🛠
      labels:
        - Semver-Major
        - breaking-change
    - title: Exciting New Features 🎉
      labels:
        - Semver-Minor
        - enhancement
    - title: Other Changes
      labels:
        - *

```

See also:

- [About releases - GitHub Docs](https://docs.github.com/repositories/releasing-projects-on-github/about-releases)
- [Linking to releases - GitHub Docs](https://docs.github.com/repositories/releasing-projects-on-github/linking-to-releases)
- [Automation for release forms with query parameters - GitHub Docs](https://docs.github.com/repositories/releasing-projects-on-github/automation-for-release-forms-with-query-parameters)

# Footnotes

[^Halstead]: Halstead complexity measures - Wikipedia are software metrics, from 1977, to establish empirical science for software development.  The goal is to identify measurable properties of software (operators, operands, distinct/total).   With the measures, calculations on difficulty, time to program and delivered bugs is possible.  See [Cyclomatic complexity](https://en.wikipedia.org/wiki/Cyclomatic_complexity) which measures number linearly independent paths through code.
[^debt]: [Technical debt](https://en.wikipedia.org/wiki/Technical_debt) (also known as [design debt](https://en.wikipedia.org/wiki/Technical_debt#cite_note-Girish_2014-1) or **code debt** is the implied cost of additional rework caused by choosing an easy (limited) solution now instead of using a better approach that would take longer.
[^SAST]: [Static application security testing - Wikipedia](https://en.wikipedia.org/wiki/Static_application_security_testing) is a frequently used Application Security (AppSec) tool, which scans an application’s source, binary, or byte code. A white-box testing tool, it identifies the root cause of vulnerabilities and helps remediate the underlying security flaws. SAST solutions analyze an application from the “inside out” and do not reed a running system to perform a scan.   SASTs test and scan at the fuction file/class and application level.  SAST is difficult in Agile as developers must address many false-positives and productivity and developer experience is impacted.  SAST scans can generate 1,000's of items to investigate.
