---
permalink: /application/devops/AZ-400-Secure-Continuous-Deployment
title: "Secure Continuous Deployment"
excerpt: "Deliverying smaller components often with observability to help refine solutions enables success.  Feature toggles can help on blue-green, A/B testing, canary and progressive-exposure release strategies."
last_modified_at: 2023-01-07T10:23:16-04:00
toc: true
---
# AZ-400 Secure Continuous Deployment

This section ([learning path](https://learn.microsoft.com/en-us/training/paths/az-400-implement-secure-continuous-deployment/)) you understand automated release gates, secrets, and secret management in your pipeline. Learn how to implement alerting mechanisms, report on your quality, and get notified by using service hooks.

# Deployment Patterns

Embrace that some features will only be tested in production.  End-users always use your application differently. Unexpected events will happen in a data center, multiple events from multiple users will cooccur, triggering some code that hasn't been tested in that way.

Feature toggling can be used with various deployment strategies to allow control and management.  Different patterns include:

- Blue-green deployments.
- Canary releases.
- Dark launching.
- A/B testing.
- Progressive exposure or ring-based deployment.
- Feature toggles.
- Classic: Dev, Test, Staging, and Production deployment.

Assess your architecture as to whether it is suitable for CD.  Questions to consider are:

- Is your software built as one giant monolith, or is it divided into multiple components?
- Can you deliver parts of your application separately?
- Can you guarantee the quality of your software when deploying multiple times a week?
- How do you test your software?
- Do you run one or multiple versions of your software?
- Can you run multiple versions of your software side by side?
- What do you need to improve to implement Continuous Delivery?

## Microservice Architecture

Microservice: A microservice is an autonomous, independently deployable, and scalable software component.  If one microservice changes, it shouldn't impact any other microservices within your landscape.

A microservices architecture creates an environment of services that can be developed, tested, and deployed separately. It introduces other risks and complexity; for example, keeping track of interfaces and application lifecycles.

- traditional architecture: layered, UI, logic, services, data layers.  Each layer is often a separate team.
- microservice: UI, logic, services, data are part of same layer.  A microservice contains one-specific function.  Interaction between services is asynchronous via queues and events.  CD deployments might deploy some microservices within a larger landscape.  These smaller components (microservices) help in implementing a fully automated pipeline.  Note: CD can be done without microservices, but it is more challenging to do so.

See also:

- [Deployment jobs - Azure Pipelines | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/pipelines/process/deployment-jobs).
- [What are Microservices? - Azure DevOps | Microsoft Docs](https://learn.microsoft.com/en-us/devops/deliver/what-are-microservices).
- [Design a CI/CD pipeline-using Azure DevOps - Azure Example Scenarios | Microsoft Docs](https://learn.microsoft.com/en-us/azure/architecture/example-scenario/apps/devops-dotnet-webapp).

# Blue-Green Deployment and Feature Toggles

Two environments are setup with a load-balancer in front of them.  The load balancer directs all production instance; deployments goto the other instance.  Once stable, the load balance swaps traffic to the newly deployed release.  Back-up is done by toggling the load-balancer.  

Cloud environments include deployment slots.  This allows blue-green deployment without setting up infrastructure.  Deployment slots can be Dev, Test, Stage, Production.  

Swap:Swapping changes by internal swapping of IP addresses.   This is the critical difference with Swap, rather than just a typical deployment process from one staged site to another. You have a rapid fallback option by swapping the sites back if needed.

- [Set up Staging Environments in Azure App Service](https://learn.microsoft.com/en-us/azure/app-service/deploy-staging-slots).
- [Considerations on using Deployment Slots in your DevOps Pipeline](https://blogs.msdn.microsoft.com/devops/2017/04/10/considerations-on-using-deployment-slots-in-your-devops-pipeline/).
- [What happens during a swap.](https://learn.microsoft.com/en-us/azure/app-service/deploy-staging-slots)

## Feature Toggles

Feature Flags allow you to change how our system works without making significant changes to the code. Only a small configuration change is required. In many cases, it will also only be for a few users.

- control conditional logic
- canary flags: a flag to allow feature testing for a small set of users
- a/b testing: a flag to offer two service types and the ability to collect metrics on the experience
- simple flags: on/off
- complex flags: intelligent, functions based on role, user, time of day, etc

Feature Flag Maintenance

Flags are code and need to be maintained, and cleaned-up when no longer used.

- flags are short-lived:  they should not be used for license-management, etc
- two dimensions ([Flag Dimensions Fowler](https://www.martinfowler.com/articles/feature-toggles.html)[^fowlerflags]): longevity  (days...months) and dynamism (change with deployment, configuration, release)
- tooling: which flags exist, what are the flag-settings for environments, situations, target environments, target user categories, plan for flag usage, plan for flag lifecycle

See:

-  [Launch Darkly](https://launchdarkly.com/) - *Fundamentally change how you deliver software*.  

- [Release Engineering Continuous deployment - Azure Architecture Center | Microsoft Docs](https://learn.microsoft.com/en-us/azure/architecture/framework/devops/release-engineering-cd).
- [Deployment jobs - Azure Pipelines | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/pipelines/process/deployment-jobs).
- [Configure canary deployments for Azure Linux virtual machines - Azure Virtual Machines | Microsoft Docs](https://learn.microsoft.com/en-us/azure/virtual-machines/linux/tutorial-azure-devops-blue-green-strategy).
- [Progressive experimentation with feature flags - Azure DevOps | Microsoft Docs](https://learn.microsoft.com/en-us/devops/operate/progressive-experimentation-feature-flags).
- [Set up staging environments - Azure App Service | Microsoft Docs](https://learn.microsoft.com/en-us/azure/app-service/deploy-staging-slots).

# Canary Release and Dark Launching

Canary release:

- The term canary release comes from the days that miners took a canary with them into the coal mines.
- The purpose of the canary was to identify the existence of toxic gasses.
- The canary would die much sooner than the miner, giving them enough time to escape the potentially lethal environment.
- A canary release is a way to identify potential problems without exposing all your end users to the issue at once.
- The idea is that you tell a new feature only to a minimal subset of users; ideally users with a high tolerance for issues.

Azure Traffic Management:  (alternatives [Traefik](https://traefik.io/))

- expand on deployment slots (swap between two different versions of an application) and allow the ability to control traffic
- DNS-based traffic load balancer; endpoints are internet-facing
- traffic routing methods
- endpoint monitoring options
- resilient to failure (include Azure region failures)

Traffic Manager currently provides six options to distribute traffic:

- **Priority**: Select Priority when you want to use a primary service endpoint for all traffic and provide backups if the primary or the backup endpoints are unavailable.
- **Weighted**: Select Weighted when you want to distribute traffic across a set of endpoints, either evenly or according to weights, which you define.
- **Performance**: Select Performance when you have endpoints in different geographic locations, and you want end users to use the "closest" endpoint for the lowest network latency.
- **Geographic**: Select Geographic so that users are directed to specific endpoints (Azure, External, or Nested) based on which geographic location their DNS query originates from. It empowers Traffic Manager customers to enable scenarios where knowing a user's geographic region and routing them based on that is necessary. Examples include following data sovereignty mandates, localization of content & user experience, and measuring traffic from different regions.
- **Multivalue**: Select MultiValue for Traffic Manager profiles that can only have IPv4/IPv6 addresses as endpoints. When a query is received for this profile, all healthy endpoints are returned.
- **Subnet**: Select the Subnet traffic-routing method to map sets of end-user IP address ranges to a specific endpoint within a Traffic Manager profile. The endpoint returned will be mapped for that request's source IP address when a request is received.

## Dark Launching

Dark launching is in many ways like canary releases.  The key difference is users are not aware of the release; hence the "dark" launching.   A Elon Mus SpaceX example is provided to show how dark-launching is not just for end-user features:

- SpaceX dark-launches a new sensor with the old sensor.  Launches collect both datasets, and, only upon assessment is the old sensor removed.

## See Also

- [Release Engineering: Deployment](https://learn.microsoft.com/en-us/azure/architecture/framework/devops/release-engineering-cd).
- [Canary deployment strategy for Kubernetes deployments](https://learn.microsoft.com/en-us/azure/devops/pipelines/ecosystems/kubernetes/canary-demo).
- [What is Traffic Manager?](https://learn.microsoft.com/en-us/azure/traffic-manager/traffic-manager-overview).
- [Progressive experimentation with feature flags](https://learn.microsoft.com/en-us/devops/operate/progressive-experimentation-feature-flags).

# A/B Testing and Progressive Exposure Deployment

A/B Testing: A/B testing (also known as split testing or bucket testing) compares two versions of a web page or app against each other to determine which one does better.  A/B testing is mainly an experiment where two or more page variants are shown to users at random. Statistical analysis is used to determine which variation works better for a given conversion goal.

- CD allows you to do A/B testing.  You can deliver minimal viable products (MVPs) to production, experiment with new features (see if adaption increases)

# CI/CD Deployment Rings

Progressive exposure deployment, also called ring-based deployment, was first discussed in [Jez Humble's Continuous Delivery book](https://www.amazon.com/Continuous-Delivery-Deployment-Automation-Addison-Wesley/dp/0321601912).

- Production first mindset of DevOps
- Limit impact on end-users while gradually deploying and validating changes in production
- Impact (blast radius) is evaluated through observation, testing, telemetry analysis and user feedback
- rings would be stages in DevOps: Canaries -> Early Adopters -> Users
- Microsoft rings might have 10-rings spanned over 16-months:
  - Engineering builds
  - Internal Validation
  - Insider Preview
  - Pilot
  - Broad Deployment { ring 1, 2, 3, 4 }

# Integrate with Identity Management

Goal:

- Integrate Azure DevOps with identity management systems.
- Integrate GitHub with single sign-on (SSO).
- Understand and create a service principal.
- Create managed service identities.

## GitHub with SSO

- connect identity provide with GitHub at the organization level.  GitHub supports SAML and SCIM.  [ [Github - Enforcing SAMLSSO](https://docs.github.com/organizations/managing-saml-single-sign-on-for-your-organization/enforcing-saml-single-sign-on-for-your-organization) ]

## Service Principals

Azure AD supports different authentication mechanisms.  Service principal is one of the most important mechanisms.

### Azure AD Applications

- applications are registered with Azure AD tenant within Azure Active Directory (AAD).  
- registering an application creates an identity configuration, and, configuration on who can use it:
  - accounts in same organization directory,
  - accounts in any organization directory,
  - accounts in any organizational directory, and Microsoft Accounts (personal)
  - Microsoft Accounts (Personal Accounts only)

Steps on Application Creation (see [Azure Objects and Service Principals](https://learn.microsoft.com/en-us/azure/active-directory/develop/app-objects-and-service-principals)):

1. Client Secret: Create at least one client secret for an application.
2. Grant Permissions: Grant permissions to the Application ID within services and resources that trust AAD.
3. Service Principal:  To access resources an entity must be represented by a service principal.  The entity must known the TenantID, Application ID and Client Sercret

## Managed Identities

Azure AD is Managed identities is another authentication mechanism.

- use case: You need to connect from Azure Data Factor to Azure SQL Database.  What identity do you use?  Traditionally you use a SQL Authentication (username/password), but this is an other credential to manage.  Answer: use the identify of the service

**Identity of the service**: Many Azure services expose their own identity. It isn't an identity that you need to manage. For example, you don't need to worry about password policies and so on.  Permissions can be assigned to the service.

Types of managed identities:

- System-assigned - It's the types of identities described above. Many, but not all, services expose these identities.
- User-assigned - you can create a managed identity as an Azure resource. It can then be assigned to one or more instances of a service.

## See Also

- [About security, authentication, authorization, and security policies - Azure DevOps | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/organizations/security/about-security-identity).
- [Azure Identity and Access Management Solutions | Microsoft Azure](https://azure.microsoft.com/product-categories/identity/).
- [About authentication with SAML single sign-on - GitHub Docs](https://docs.github.com/authentication/authenticating-with-saml-single-sign-on/about-authentication-with-saml-single-sign-on).
- [Connect to Microsoft Azure - Azure Pipelines | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/pipelines/library/connect-to-azure).

# Management Application Configuration Data

Goals:

- Rethink application configuration data
- Understand separation of concerns
- Integrate Azure Key Vault with Azure Pipelines
- Manage secrets, tokens and certificates
- Describe Azure App Configuration
- Understand Key-value pairs
- Understand app configuration feature management
- Implement application configuration

## Rethink Configuration Data

files deployed with application: edit file to change applicaition behaviour.   Application re-deployed might cause outages and administration overhead.  Sharing configuration across multiple applications is hard.

- sharing DB connection strings
- UI theme information
- URLs of queues and storage
- best practices to not include secrets/keys

DevOps tools for managing configuration:

- Chef, Puppet

## Separation of Concerns

Remove configuration away from source control helps to outline responsibilities.

Roles:

- **Configuration custodian**: Responsible for generating and maintaining the life cycle of configuration values. These include CRUD on keys, ensuring the security of secrets, regeneration of keys and tokens, defining configuration settings such as Log levels for each environment. This role can be owned by operation engineers and security engineering while injecting configuration files through proper DevOps processes and CI/CD implementation. They do not define the actual configuration but are custodians of their management.



- **Configuration consumer**: Responsible for defining the schema (loose term) for the configuration that needs to be in place and then consuming the configuration values in the application or library code. It's the Dev. And Test teams shouldn't be concerned about the value of keys but rather what the key's capability is. For example, a developer may need a different ConnectionString in the application but not know the actual value across different environments.



- **Configuration store**: The underlying store used to store the configuration, while it can be a simple file, but in a distributed application, it needs to be a reliable store that can work across environments. The store is responsible for persisting values that modify the application's behavior per environment but aren't sensitive and don't require any encryption or HSM modules.



- **Secret store**: While you can store configuration and secrets together, it violates our separation of concern principle, so the recommendation is to use a different store for persisting secrets. It allows a secure channel for sensitive configuration data such as ConnectionStrings, enables the operations team to have Credentials, Certificate, Token in one repository, and minimizes the security risk if the Configuration Store gets compromised.

## External Configuration Store Patterns

Configuration is stored external and can be accessed by an interface.  Hosting and runtime affect the external store type.

- cloud hosting would use cloud hosted storage, caching in the event of interface failures, ...
- authorize user's access

## Azure App Configuration

Azure App Configuration is a service for central management of application settings and feature flags.

- Modern programs include distributed components, each that needs its settings.
- It's prevalent with microservice-based applications and with serverless applications.
- Distributed configuration settings can lead to hard-to-troubleshoot deployment errors.
- Azure App Configuration service stores all the settings for your application and secures their access in one place.

Azure App Configuration service provides the following features:

- A fully managed service that can be set up in minutes.
- Flexible key representations and mappings.
- Tagging with labels.
- A point-in-time replay of settings.
- Dedicated UI for feature flag management.
- Comparison of two sets of configurations on custom-defined dimensions.
- Enhanced security through Azure managed identities.
- Complete data encryptions, at rest or in transit.
- Native integration with popular frameworks.

Azure App Configuration complements [Azure Key Vault](https://learn.microsoft.com/en-GB/azure/key-vault/general/basic-concepts) which stores application secrets.  The pair support these scenarios:

- Centralize management and distribution of hierarchical configuration data for different environments and geographies.
- Dynamically change application settings without the need to redeploy or restart an application.
- Control feature availability in real time.

[12-Factor App](http://12factor.net/config) recommends against configuration-files and to user environment variables:

> ... stores config in environment variables. Env vars are easy to change between deploys without changing any code; unlike config files, there is little chance of them being checked into the code repo accidentally; and unlike custom config files, or other config mechanisms such as Java System Properties, they are a language- and OS-agnostic standard.

Key Value Pairs used by App Configuration

- must create your own naming convention; likely with a hierarchy namespace delimited by `/ : or .`
- case-sensitive, examples:
  - by component service `AppName:Service1:ApiEndpoint AppName:Service2:ApiEndpoint `
  - by deployment region `AppName:Region1:DbEndpoint`
- can add labels to separate `Key = AppName:DbEndpoint & Label = Staging`

Feature Management

- flag (binary state on/off), manager (manages lifecycle of flag, caching, updating states), filter
- effective use of feature management includes two components; an application that uses the flag and a repository that stores the feature flags and their states.  Azure App Configuration can store feature flags.
- each flag has two parts; a name and a list of one or more filters to evaluate if the state is on or off
  - filter: defines a use case for when a feature should be turned on

## Integrate Azure Key Vault with Pipelines

Applications contain many secrets, such as:

- Connection strings.
- Passwords.
- Certificates.
- Tokens, which, if leaked to unauthorized users, can lead to a severe security breach.

[Azure Key Vault](https://learn.microsoft.com/en-us/azure/key-vault/key-vault-overview) allows you to manage your organization's secrets and certificates in a centralized repository.

### Manage secrets, tokens and certificates

Azure Key Vault helps solve the following problems:

- **Secrets management** - Azure Key Vault can be used to store securely and tightly control access to tokens, passwords, certificates, API keys, and other secrets.
- **Key management** - Azure Key Vault can also be used as a key management solution. Azure Key Vault makes it easy to create and control the encryption keys used to encrypt your data.
- **Certificate management** - Azure Key Vault is also a service that lets you easily provision, manage, and deploy public and private Secure Sockets Layer/Transport Layer Security (SSL/TLS) certificates for use with Azure. And your internal connected resources.
- **Store secrets backed by hardware security modules** - The secrets and keys can be protected by software or FIPS 140-2 Level 2 validates HSMs.

Microsoft uses Thales hardware security modules. You can use Thales tools to move a key from your HSM to Azure Key Vault.  Azure Key Vault is designed so that Microsoft doesn't see or extract your data.

Monitoring access and use by configuring Azure Key Vault to:

- Archive to a storage account.
- Stream to an Event Hubs.
- Send the logs to Log Analytics.

DevOps Inner and Outer Loops

Problem: Storing secrets and configurations together violates  separation of concern principles.  It is recommended to use a separate store for persisting secrets.

- It allows a secure channel for sensitive configuration data, such as ConnectionStrings.
- It enables the operations team to have credentials, certificates, tokens in one repository and minimizes the security risk if the Configuration Store gets compromised.

Inner Loop: Developer teams iterating over solution in development; code, run, debug, validate.  Consumes configuration from outer loop.

Outer Loop: Ops engineers push configuration changes to Kubernetes and Azure Key Vault using tools like Chef and Puppet.

See also:

- [Use Azure Key Vault secrets in Azure Pipelines - Azure Pipelines | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/pipelines/release/azure-key-vault).
- [Define variables - Azure Pipelines | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/pipelines/process/variables).
- [Integrate Azure App Configuration using a continuous integration and delivery pipeline | Microsoft Docs](https://learn.microsoft.com/en-us/azure/azure-app-configuration/integrate-ci-cd-pipeline).

# Watch: The God Login

[Awesome summary of a 1991 lecture by Randy Paush "The Last Lecture](https://blog.codinghorror.com/the-god-login/)" before he died of cancer. :+1: :smile: - [Randy Pausch](https://en.wikipedia.org/wiki/Randy_Pausch).

- Pausch learned he had [pancreatic cancer](https://en.wikipedia.org/wiki/Pancreatic_cancer) in September 2006. In August 2007, he was given a terminal diagnosis: "three to six months of good health left". He gave an upbeat lecture titled, "[The Last Lecture: Really Achieving Your Childhood Dreams](https://en.wikipedia.org/wiki/Really_Achieving_Your_Childhood_Dreams)" on September 18, 2007 at Carnegie Mellon, which became a popular [YouTube](https://en.wikipedia.org/wiki/YouTube) video and led to other media appearances. He co-authored a book of the same name, *[The Last Lecture](https://en.wikipedia.org/wiki/The_Last_Lecture)*, which became a *[New York Times](https://en.wikipedia.org/wiki/The_New_York_Times)* [best-seller](https://en.wikipedia.org/wiki/The_New_York_Times_Best_Seller_list).  Human-Computer Interaction and Design @ Carnegie Mellon University
- [Famous Positive Quotes by Randy Pausch](https://en.wikiquote.org/wiki/Randy_Pausch).







# Footnotes



[^fowlerflags]: *Toggles introduce complexity. We can keep that complexity in check by using smart toggle implementation practices and appropriate tools to manage our toggle configuration, but we should also aim to constrain the number of toggles in our system.* — [Feature Toggles](https://www.martinfowler.com/articles/feature-toggles.html)
