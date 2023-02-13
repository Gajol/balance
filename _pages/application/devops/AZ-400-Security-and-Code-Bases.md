---
permalink: /application/devops/AZ-400-Security-and-Code-Bases
title: "Open Source Security"
excerpt: "Managing open source software, using static application security testing (SAST) and keeping informed of latest security concerns are key to using open-source securely."
last_modified_at: 2023-01-07T10:23:16-04:00
toc: true
---
# AZ-400 Security and Code Bases

# DevOps & Impacts to Security

- DevOps teams have access to unprecedented infrastructure and scale thanks to the cloud.
- Threats: Members can be approached by some of the most nefarious actors on the internet
- Risk: risk the security of their business with every application deployment

Perimeter-class security is no longer viable in such a distributed environment

Securing Applications requires layered security:

- application architecture
- continuous validation
- monitoring
- infrastructure

## Attacks

Example: SQL Injection Attack: SQL Injection is an attack that makes it possible to execute malicious SQL statements

Resources:

- [OWASP organization](https://owasp.org/) (Open Web Application Security Project)
- [Azure Defender for Cloud Playbooks](https://learn.microsoft.com/en-us/azure/defender-for-cloud/workflow-automation)

## DevSecOps

[Microsoft Security Defense Report - 2022](https://www.microsoft.com/en-us/security/business/microsoft-digital-defense-report-2022).

- 2018: only 7% of data was encrypted at rest, only 4% of SaaS applications used HTTP session header protection

Traditional security methodologies:

- Access control.
- Environment hardening.
- Perimeter protection.

SecDevOps

- includes traditional methodologies
- involves securing the pipeline
- involves determining where to add protection to the elements that plug into your build and release pipelines
- considers broad questions such as:
  - Is my pipeline consuming third-party components, and are they secure?
  - Are there known vulnerabilities within any of the third-party software we use?
  - How quickly can I detect vulnerabilities (also called *time to detect*)?
  - How quickly can I remediate identified vulnerabilities (also known as *time to remediate*)?

### SecDevOps Pipeline

DevOps broadly refers to securing the pipeline.  Two essential features of Secure DevOps Pipelines that aren't found in standard DevOps Pipelines are:

- Package management and the approval process associated with it. The previous workflow diagram details other steps for adding software packages to the Pipeline and the approval processes that packages must go through before they're used. These steps should be enacted early in the Pipeline to identify issues sooner in the cycle.
- Source Scanner is also an extra step for scanning the source code. This step allows for security scanning and checking for vulnerabilities that aren't present in the application code. The scanning occurs *after* the app is built *before* release and pre-release testing. Source scanning can identify security vulnerabilities earlier in the cycle.

Key validation points: IDE / Pull Request: Static code analys tools (SAST)

Tool options:

- SonarQube.
- Visual Studio Code Analysis and the Roslyn Security Analyzers.
- Checkmarx - A Static Application Security Testing (SAST) tool.
- BinSkim - A binary static analysis tool that provides security and correctness results for Windows portable executables and many more.

## Threat Modelling

There are five major threat modeling steps:

1. Defining security requirements.
2. Creating an application diagram.
3. Identifying threats.
4. Mitigating threats.
5. Validating that threats have been mitigated.

Microsoft Threat Modelling tool:

- [Threat Modeling Tool feature overview](https://learn.microsoft.com/en-us/azure/security/azure-security-threat-modeling-tool-feature-overview).
- [Microsoft Threat Modeling Tool](https://blogs.msdn.microsoft.com/secdevblog/2018/09/12/microsoft-threat-modeling-tool-ga-release/).

# Open Source Software

> *"Open-source software is a type of computer software in which source code is released under a license in which the copyright holder grants users the rights to study, change, and distribute the software to anyone and for any purpose."* — Wikipedia

Corporate concerns with Open Source Software

- **Are of low quality.** It would impact the maintainability, reliability, and performance of the overall solution.
- **Have no active maintenance.** The code wouldn't evolve or be alterable without copying the source code, effectively forking away from the origin.
- **Contain malicious code.** The entire system that includes and uses the code will be compromised. Potentially the whole company's IT and infrastructure is affected.
- **Have security vulnerabilities.** The security of a software system is as good as its weakest part. Using source code with vulnerabilities makes the entire system susceptible to attack by hackers and misuse.
- **Have unfavorable licensing restrictions.** The effect of a license can affect the entire solution that uses the open-source software.

## Open source licenses:

According to the open-source definition of [OpenSource.org](http://opensource.org/), a license shouldn't:

- Discriminate against persons or groups.
- Discriminate against fields of endeavor.
- Be specific to a product.
- Restrict other software.
- And more - See the [Open Source Definition](http://opensource.org/osd).

Types of Licenses:  Spectrum:

- Attribution BSD, MIT, Apache (Permissive)
- Downstream: MPL, EPL, MS-RL
- Copyleft: GPF, LGPL, AGPL (Restricitve)

Licensie rating based on the impact they have.  For compliance reasons, a high license rating can be considered a risk for compliance, intellectual property, and exclusive rights.

Viral: Copyleft licenses are considered viral, as the use of the source code and its components, and distribution of the complete software, implies that all source code using it should follow the same license form.

# Software Composition Analysis

SBOM: SBOMs are a standardized, machine-readable inventory of software components and dependencies. They’re designed to track the details and supply chain relationships of software components, their dependencies, and their hierarchical relationships.

PBOM

## Compliance: Insepct Code Bases

Breaches: We need to make sure we properly authenticate who is accessing the data and that they have the correct permissions to do so. We need to find evidence when something has gone wrong through historical or archival data or logs.

Aspects to building and deploying secure applications.

- **General knowledge** problem. Many developers and other staff assume they understand security, but they don't. Cybersecurity is a constantly evolving discipline. A program of ongoing education and training is essential.
- **Design with Security in Mind**: Ensure that the code is created correctly and securely implements the required features, and we need to make sure that the features were designed with security in mind in the first place.
- **Compliance**: Ensure that the application follows the rules and regulations required to meet. We need to test it while building the code and retest it periodically, even after deployment.

## Software Composition Analysis

Software Composition Analysis (SCA) is the process of analyzing open-source software (OSS) to identify potential security vulnerabilities and provide validation that the software meets a defined criterion to use in your pipeline.

Package Management

- keep artifacts organized
- protect packages
- integrate seamless package handling

Tool: Mend: The Mend extension is available on the Azure DevOps Marketplace. Using Mend, you can integrate extensions with your CI/CD pipeline to address Secure DevOps security-related issues.

- Mend detects usage of open-source and builds an inventory.  [Mend SBOM support](https://www.mend.io/sbom/).
- Receive alerts on open source vulnerabilities
- Enforce open-source security and license-compliance policies

GitHub Dependabot:

- detects volnerable dependencies and sends alerts
- create pull requests on security updates

Integrate SAST (software composition analysis checks) in pipelines.

- integrate PR into analysis (manage noise on PR)
- Tool options in Azure:
  - [Mend](https://www.mend.io/). Helps validate dependencies with its binary fingerprinting.
  - [Checkmarx](https://www.checkmarx.com/). Provides an incremental scan of changes.
  - [Veracode](https://www.veracode.com/). Implements the concept of a developer sandbox.
  - [Black Duck by Synopsis](https://www.blackducksoftware.com/). An auditing tool for open-source code to help identify, fix, and manage compliance.

Alerts interpretation

- **False positives** It's essential to verify the findings to be real positives in the scan results. The tooling is an automated way to scan and might be misinterpreting specific vulnerabilities. In the triaging of the finding in the scan results, you should be aware that some findings might not be correct. Such results are called `false positives`, established by human interpretation and expertise. One must not declare a result a false positive too quickly. On the other hand, scan results aren't guaranteed to be 100% accurate.  Ensure alerts are not repeated sent (can be flagged as assessed and filtered afterwards)
- **Security bug bar** Most likely, many security vulnerabilities will be detected—some of these `false positives`, but still many findings. More findings can often be handled or mitigated, given a certain amount of time and money. In such cases, there must be a security bug bar indicating the level of vulnerabilities that must be fixed before the security risks are acceptable enough to take the software into production. The bug bar makes sure that it's clear what must be taken care of and what might be done if time and resources are left.

Tools for Package assessment and license rate:

# Static Analyzers

SonarCloud and CodeQL in GitHub

- CodeQL: query code as if it were data
- SonarCloud: SAST
- BinSkim: SAST on binary files

Technical debt can be classified as the measure between the codebase's current state and an optimal state.

- Technical debt saps productivity by making code hard to understand, easy to break, and difficult to validate, creating unplanned work and ultimately blocking progress.
- Technical debt is inevitable! It starts small and grows over time through rushed changes, lack of context, and discipline.

# Dynamic Analyzers

[OWASP](http://owasp.org/) regularly publishes a set of Secure Coding Practices. Their guidelines currently cover advice in the following areas:

- Input Validation
- Output Encoding
- Authentication and Password Management
- Session Management
- Access Control
- Cryptographic Practices
- Error Handling and Logging
- Data Protection
- Communication Security
- System Configuration
- Database Security
- File Management
- Memory Management
- General Coding Practices

[OWASP Top 10 vulnerabilities](https://owasp.org/www-project-top-ten/).

- [Book Writing Secure Code](https://www.booktopia.com.au/writing-secure-code-david-leblanc/ebook/2370006179962.html) —  David LeBlanc, Michael Howard
- [OWASP Secure Coding Practices Quick Reference Guide](https://owasp.org/www-pdf-archive/OWASP_SCP_Quick_Reference_Guide_v2.pdf).
- [OWASP Code Review Guide](https://owasp.org/www-project-code-review-guide/assets/OWASP_Code_Review_Guide_v2.pdf). 2017
- [OWASP Top 10](https://owasp.org/www-project-top-ten/).
- [Vulnerability Scanning Tools | OWASP Foundation](https://owasp.org/www-community/Vulnerability_Scanning_Tools).

ZAP: free penetration test tool.  [OSWA ZAP VSTS Extension](https://github.com/deliveron/owasp-zap-vsts-extension) : ZAP includes an API and a weekly docker container image to integrate into your deployment process.

# Security Monitoring and Governance'

Goal:

- Configure Microsoft Defender for Cloud
- Understand Azure policies
- Describe initiatives, resource locks and Azure Blueprints
- Work with Microsoft Defender for Identity

## Implement Pipeline Security

It's fundamental to protect your code protecting credentials, and secrets. Phishing is becoming ever more sophisticated. The following list is several operational practices that a team ought to apply to protect itself:

- Authentication and authorization. Use multifactor authentication (MFA), even across internal domains, and just-in-time administration tools such as Azure PowerShell [Just Enough Administration (JEA)](https://aka.ms/jea), to protect against privilege escalations. Using different passwords for different user accounts will limit the damage if a set of access credentials is stolen.
- The CI/CD Release Pipeline. If the release pipeline and cadence are damaged, use this pipeline to rebuild infrastructure. Manage Infrastructure as Code (IaC) with Azure Resource Manager or use the Azure platform as a service (PaaS) or a similar service. Your pipeline will automatically create new instances and then destroy them. It limits the places where attackers can hide malicious code inside your infrastructure. Azure DevOps will encrypt the secrets in your pipeline. As a best practice, rotate the passwords just as you would with other credentials.
- Permissions management. You can manage permissions to secure the pipeline with role-based access control (RBAC), just as you would for your source code. It keeps you in control of editing the build and releases definitions that you use for production.
- Dynamic scanning. It's the process of testing the running application with known attack patterns. You could implement penetration testing as part of your release. You also could keep up to date on security projects such as the Open Web Application Security Project ([OWASP](https://www.owasp.org/)) Foundation, then adopt these projects into your processes.
- Production monitoring. It's a critical DevOps practice. The specialized services for detecting anomalies related to intrusion are known as *Security Information and Event Management*. [Microsoft Defender for Cloud](https://azure.microsoft.com/services/defender-for-cloud) focuses on the security incidents related to the Azure cloud.

## Microsoft Defender for Cloud

**Microsoft Defender for Cloud** is a monitoring service that provides threat protection across all your services both in Azure and on-premises. Microsoft Defender can:

- Provide security recommendations based on your configurations, resources, and networks.
- Monitor security settings across on-premises and cloud workloads and automatically apply required security to new services as they come online.
- Continuously monitor all your services and do automatic security assessments to identify potential vulnerabilities before they can be exploited.
- Use Azure Machine Learning to detect and block malicious software from being installed on your virtual machines (VMs) and services. You can also define a list of allowed applications to ensure that only the validated apps can execute.
- Analyze and identify potential inbound attacks and help investigate threats and any post-breach activity that might have occurred.
- Provide just-in-time (JIT) access control for ports by reducing your attack surface by ensuring the network only allows traffic that you require.

### Defend Cloud usage scenarios

Incident Response Plan: incident response plan is required before a response occurs: Detect - Assess - Diagnose - Stablize - Close

- Detect. Review the first indication of an event investigation. For example, use the Microsoft Defender for Cloud dashboard to review a high-priority security alert's initial verification.
- Assess. Do the initial assessment to obtain more information about suspicious activity. For example, you can get more information about a security alert from Microsoft Defender for Cloud.
- Diagnose. Conduct a technical investigation and identify containment, mitigation, and workaround strategies. For example, you can follow the remediation steps described by Microsoft Defender for Cloud for a particular security alert.
- Use Microsoft Defender for Cloud recommendations to enhance security.

## Azure Policy

Policies enforce different rules and effects over your Azure resources, ensuring that your resources stay compliant with your standards and SLAs. Azure Policy uses policies and initiatives to provide policy enforcement capabilities.

- CI/CD pipeline: Azure policies, Check gate provides security and compliance assessment on the resources with an Azure resource group or subscription that you can specify.

Policies:

- Policy definition. Create a policy definition.
- Policy assignment. Assign the definition to a scope of resources.
- Remediation. Review the policy evaluation results and address any non-compliances.

Initiatives:

- An *initiative definition* is a set of policy definitions to help track your compliance state for meeting large-scale compliance goals
- Applying an initiative definition to a specific scope is called an *initiative assignment*.
- Example:
- For example, you can create an initiative named *Enable Monitoring in Azure Security Center* to monitor security recommendations from Azure Security Center.  Under this example initiative, you would have the following policy definitions:
  - Monitor unencrypted SQL Database in Security Center. This policy definition monitors unencrypted SQL databases and servers.
  - Monitor OS vulnerabilities in Security Center. This policy definition monitors servers that don't satisfy a specified OS baseline configuration.
  - Monitor missing Endpoint Protection in Security Center. This policy definition monitors servers without an endpoint protection agent installed.

## Azure Blueprints

Azure Blueprints enables cloud architects to define a repeatable set of Azure resources that implement and adhere to an organization's standards, patterns, and requirements.

Azure Blueprints provides a declarative way to orchestrate deployment for various resource templates and artifacts, including:

- Role assignments
- Policy assignments
- Azure Resource Manager templates
- Resource groups

To implement Azure Blueprints, complete the following high-level steps:

1. Create a blueprint.
2. Assign the blueprint.
3. Track the blueprint assignments.

## Microsoft Defender for Identity

Microsoft Defender for Identity (formerly Azure Advanced Threat Protection, also known as Azure ATP) is a cloud-based security solution that identifies and detects:

- Advanced threats.
- Compromised identities.
- Malicious insider actions directed at your organization.
-
