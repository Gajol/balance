---
permalink: /application/devops/AZ-400-Dependency-Management-Strategy
title: "Dependency Management Strategy"
excerpt: "Understanding and managing dependencies is key, especially in large complex projects.  Package Feeds (Aftifact Repositories) and scanning tools help manage dependencies."
last_modified_at: 2023-01-07T10:23:16-04:00
toc: true
---
# AZ-400 Dependency Management Strategy

Dependencies in software:

- Projects have dependencies on other projects, and solutions aren't single pieces of software.
- As codebases are expanding and evolving, it needs to be componentized to be maintainable.
- Each component can have its maintainers, speed of change, and distribution, giving both the creators and consumers of the components autonomy.

The need for dependency management:

- dependencies must be declared and resolved
- over composition of project must be managed; including dependencies
- dependency management helps control all components of a solution
- software team is more efficient in working with dependencies using dependency management
- governance and security scanning can be managed

## Dependency Management Strategy

- **Standardization** Managing dependencies benefit from a standardized way of declaring and resolving them in your codebase. Standardization allows a repeatable, predictable process and usage that can be automated as well.

- **Package formats and sources** The distribution of dependencies can be performed by a packaging method suited for your solution's dependency type.

  - Each dependency is packaged using its usable format and stored in a centralized source.
  - Your dependency management strategy should include the selection of package formats and corresponding sources where to store and retrieve packages.

- **Versioning** Just like your own code and components, the dependencies in your solution usually evolve.
  While your codebase grows and changes, you need to consider the changes in your dependencies as well.
  It requires a versioning mechanism for the dependencies to be selective of the version of a dependency you want to use.

### Componentization

There are two ways of componentization commonly used.

1. **Source componentization** The first way of componentization is focused on source code. It refers to splitting the source code in the codebase into separate parts and organizing it around the identified components.
   It works if the source code isn't shared outside of the project. Once the components need to be shared, it requires distributing the source code or the produced binary artifacts created from it.

2. **Package componentization** The second way uses packages. Distributing software components is performed utilizing packages as a formal way of wrapping and handling the components.
   A shift to packages adds characteristics needed for proper dependency management, like tracking and versioning packages in your solution.

### Decompose System

- first gather information about the system
- remove components of system and centralize them; this process creates dependencies
- refactoring, creating new solution artifacts, replace code with open-source code, etc
- use code design patterns to isolate and include component code (interfaces, dependency inject, inversion of control)

### Scan Code for Dependencies

- **Duplicate code** When certain pieces of code appear in several places, it's a good indication that this code can be reused.
- **High cohesion and low coupling** A second approach is to find code that might define components in your solution. You'll look for code elements that have high cohesion and low coupling with other parts of code.
- **Individual lifecycle** Related to high cohesion, you can look for parts of the code that have a similar lifecycle and can be deployed and released individually. If such code can be maintained by a team separate from the codebase that it's currently in, it's an indication that it could be a component outside of the solution.
- **Stable parts** Some parts of your codebase might have a slow rate of change. That code is stable and isn't altered often. You can check your code repository to find the code with a low change frequency.
- **Independent code and components** Whenever code and components are independent and unrelated to other parts of the system, they can be isolated to a separate component and dependency.

Tools: These range from tools that scan for duplicate code and draw solution dependency graphs to tools that compute metrics for coupling and cohesion.

See also:

- [Azure Artifacts overview - Azure Artifacts | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/artifacts/start-using-azure-artifacts).
- [NuGet documentation | Microsoft Docs](https://learn.microsoft.com/en-us/nuget/).
- [npm Docs (npmjs.com)](https://docs.npmjs.com/).
- [Maven – Welcome to Apache Maven](https://maven.apache.org/).

# Package Management

Package: A package is a formalized way of creating a distributable unit of software artifacts that can be consumed from another software solution.

Types of packages; The range from frontend components, such as JavaScript code files, to backend components like .NET assemblies or Java components, complete self-contained solutions, or reusable files in general.

- **NuGet** packages (pronounced "new get") are a standard used for .NET code artifacts. It includes .NET assemblies and related files, tooling, and sometimes only metadata. NuGet defines the way packages are created, stored, and consumed. A NuGet package is essentially a compressed folder structure with files in ZIP format and has the `.nupkg` extension. See also [An introduction to NuGet](https://learn.microsoft.com/en-us/nuget/what-is-nuget).
- **NPM** An NPM package is used for JavaScript development. It originates from node.js development, where it's the default packaging format. An NPM package is a file or folder containing JavaScript files and a `package.json` file describing the package's metadata. For node.js, the package usually includes one or more modules that can be loaded once the package is consumed. See also [About packages and modules](https://docs.npmjs.com/about-packages-and-modules).
- **Maven** is used for Java-based projects. Each package has a Project Object Model file describing the project's metadata and is the basic unit for defining a package and working with it.
- **PyPi** The Python Package Index, abbreviated as PyPI and known as the Cheese Shop, is the official third-party software repository for Python.
- **Docker** packages are called images and contain complete and self-contained deployments of components. A Docker image commonly represents a software component that can be hosted and executed by itself without any dependencies on other images. Docker images are layered and might be dependent on other images as their basis. Such images are referred to as base images.

Package Feeds

- packages are stored in a central place commonly called a `package feed`, `repository` or `registry`

Package Feed Managers:

- Installation and removal of local packages
- Pushing packages to a remote package feed
- Consuming packages from a remote package feed
- Searching feeds for packages

Package Sources

- NuGet: NuGet Gallery [https://nuget.org](https://nuget.org/)
- NPM: NPMjs [https://npmjs.org](https://npmjs.org/)
- Maven: Maven [https://search.maven.org](https://search.maven.org/)
- Docker: Docker Hub [https://hub.docker.com](https://hub.docker.com/)
- Python: Python Package Index: [https://pypi.org](https://pypi.org/)

Self-Hosted Options:

- NuGet Packages: NuGet server
- NPM Packages: Sinopia, CNPMjs, Verdaccio
- Maven Packages: Nexus, Artifactory, Archivia
- Docker Packages: Portus, Quay, Harbor
- Python Packages: PyPI server

Consume packages flow:

1. Identify a required dependency in your codebase.
2. Find a component that satisfies the requirements for the project.
3. Search the package sources for a package offering a correct component version.
4. Install the package into the codebase and development machine.
5. Create the software implementation that uses the new components from the package.

## Azure Artifacts

Azure Artifacts currently supports feeds that can store five different package types:

- NuGet packages
- NPM packages
- Maven
- Universal packages
- Python

## Migrating Package Feeds / Artifact REpos

An **artifact** is a deployable component of your application. Azure Pipelines can work with a wide variety of artifact sources and repositories.

Migrating artifacts to a common manager has advantages.  

- [Get started with NuGet packages in Azure DevOps Services and TFS](https://learn.microsoft.com/en-us/azure/devops/artifacts/get-started-nuget).
- [Use npm to store JavaScript packages in Azure DevOps Services or TFS](https://learn.microsoft.com/en-us/azure/devops/artifacts/get-started-npm).
- [Get started with Maven packages in Azure DevOps Services and TFS](https://learn.microsoft.com/en-us/azure/devops/artifacts/get-started-maven).
- [Get started with Python packages in Azure Artifacts](https://learn.microsoft.com/en-us/azure/devops/artifacts/quickstarts/python-packages).
- [Publish and then download a Universal Package](https://learn.microsoft.com/en-us/azure/devops/artifacts/quickstarts/universal-packages).

Package Feeder roles:

- Reader: Can list and restore (or install) packages from the feed.
- Collaborator: Can save packages from upstream sources.
- Contributor: Can push and unlist packages in the feed.
- Owner: has all available permissions for a package feed.

Permissions: List, restore, install, save, push, unlist, deprecate, delete/unpublish, edit permissions

See also:

- [Azure Artifacts overview](https://learn.microsoft.com/en-us/azure/devops/artifacts/start-using-azure-artifacts).
- [Azure Artifacts: best practices](https://learn.microsoft.com/en-us/azure/devops/artifacts/concepts/best-practices).
- [Configure permissions](https://learn.microsoft.com/en-us/azure/devops/artifacts/feeds/feed-permissions).

# Versioning Strategy

Immutable packages: packages should always have a new version when they change.

- As packages get new versions, your codebase can choose when to use a new version of the packages it consumes.
- Once a package is published it cannot change

[Semantic Version](https://semver.org/) `major.minor.patch`:

- **Major change** Major indicates that the package and its contents have changed significantly. It often occurs at the introduction of a new version of the package. It can be a redesign of the component. Major changes aren't guaranteed to be compatible and usually have breaking changes from older versions. Major changes might require a large amount of work to adopt the consuming codebase to the new version.
- **Minor change** Minor indicates that the package and its contents have extensive modifications but are smaller than a major change. These changes can be backward compatible with the previous version, although they aren't guaranteed to be.
- **Patch** A patch or revision is used to indicate that a flaw, bug, or malfunctioning part of the component has been fixed. Usually, It's a backward-compatible version compared to the previous version.

## Paradox and Views

a package needs a version before being consumed and tested, but only after testing is the quality of a package known.  Many iterations before the desired quality is reached can result in many package-versions

- a `descriptor` is used in parallel with the semantic version to identify the quality.  This metadata allows for a different view.  Default views are Local, Prerelease, Release.  Alpha and Beta are good view options.
  - **Local.** The `@Local` view contains all release and prerelease packages and the packages downloaded from upstream sources.
  - **Prerelease.** The `@Prerelease` view contains all packages that have a label in their version number.
  - **Release.** The `@Release` view contains all packages that are considered official releases.

## Promote Packages

Azure Artifacts has the notion of promoting packages to views to indicate that a version is of a certain quality level.

## Versioning Best Practices

- Have a documented versioning strategy.
- Adopt SemVer 2.0 for your versioning scheme.
- Each repository should only reference one feed.
- On package creation, automatically publish packages back to the feed.

See also:

- [Key concepts for Azure Artifacts](https://learn.microsoft.com/en-us/azure/devops/artifacts/artifacts-key-concepts#immutability).
- [Publish and download universal packages - Azure Artifacts | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/artifacts/quickstarts/universal-packages).
- [Get started with NuGet packages - Azure Artifacts | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/artifacts/get-started-nuget).

# GitHub Packages

GitHub Packages can host:

- npm.
- RubyGems.
- Apache Maven.
- Gradle.
- Docker.
- NuGet.
- GitHub's Container registry is optimized for containers and supports Docker and OCI images.

Flows:

Install, delete and restore a package

Manage package access control and visibility: read, write, admin



See also:

- [Quickstart for GitHub Packages - GitHub Docs](https://docs.github.com/packages/quickstart).
- [Learn GitHub Packages - GitHub Docs](https://docs.github.com/packages/learn-github-packages).
- [Working with the Container registry](https://docs.github.com/packages/working-with-a-github-packages-registry/working-with-the-container-registry).
- [Working with a GitHub Packages registry](https://docs.github.com/packages/working-with-a-github-packages-registry).
- [About GitHub Security Advisories](https://docs.github.com/github/managing-security-vulnerabilities/about-github-security-advisories).
- [Working with the NuGet registry](https://docs.github.com/packages/working-with-a-github-packages-registry/working-with-the-nuget-registry).
- [Working with the npm registry](https://docs.github.com/packages/working-with-a-github-packages-registry/working-with-the-npm-registry).
