---
permalink: /application/devops/AZ-400-IaC-using-Azure-and-DSC
title: "Azure IaC and DSC"
excerpt: "DevOps needs to treat infrastructure like cattle.  The ability to create environments that are consistent is critical to DevOps success.  Infrastructure as Code (IaC) and Desired State Configuration (DSC) and key DevOps aims."
last_modified_at: 2023-01-07T10:23:16-04:00
toc: true
---
# AZ-400 IaC using Azure and DSC

# Introduction

IaC: infrastructure as code is the concept of managing your operations environment like you do applications or other code for general release.  

- pet and cattle analogy: If you adopt infrastructure as a code approach, you can more easily provision another machine without adversely impacting your entire infrastructure (cattle) if a single machine goes down.  Compared to manual deployments where, like pets, care and attention are involved.
- Treats infrastructure as a flexible resource that can be provisioned, de-provisioned, and reprovisioned as and when needed.

DSC: Desired State Configuration

## Infrastructure as Code: Environment Deployment

| Manual Deployment                                       | Infrastructure as Code                               |
| ------------------------------------------------------- | ---------------------------------------------------- |
| Snowflake servers                                       | Consistent Server between environments               |
| Deployment steps vary by environment                    | Environments are created and scale easily            |
| More and manual verification steps                      | Automated creation of environment updates            |
| Documentation to account for differences                | Immutable infrastructure requires less documentation |
| Weekend deployments for maintenance window and recovery | Blue/green primetime deployments                     |
| Slower release cadence to reduce pain and weekend work  | Servers are cattle not pets                          |

### Benefits of infrastructure as code

The following list is benefits of infrastructure as code:

- Promotes auditing by making it easier to trace what was deployed, when, and how. (In other words, it improves traceability.)
- Provides consistent environments from release to release.
- Greater consistency across development, test, and production environments.
- Automates scale-up and scale-out processes.
- Allows configurations to be version-controlled.
- Provides code review and unit-testing capabilities to help manage infrastructure changes.
- Uses *immutable* service processes, meaning if a change is needed to an environment, a new service is deployed, and the old one was taken down; it isn't updated.
- Allows *blue/green* deployments. This release methodology minimizes downtime, where two identical environments exist—one is live, and the other isn't. Updates are applied to the server that isn't live. When testing is verified and complete, it's swapped with the different live servers. It becomes the new live environment, and the previous live environment is no longer the live. This methodology is also referred to as *A/B deployments*.
- Treats infrastructure as a flexible resource that can be provisioned, de-provisioned, and reprovisioned as and when needed.

## Configuration Management

**Configuration management** refers to automated configuration management, typically in version-controlled scripts, for an application and all the environments needed to support it.

| Manual Configuration                                         | Configuration as Code                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Configuration bugs are challenging to identify.              | Bugs are easily reproducible.                                |
| Error-prone.                                                 | Consistent configuration.                                    |
| More verification steps and more elaborate manual processes. | Increase deployment cadence to reduce the amount of incremental change. |
| Increased documentation.                                     | Treat environment and configuration as executable documentation. |
| Deployment on weekends to allow time to recover from errors. |                                                              |

### Benefits of configuration management

The following list is benefits of configuration management:

- Bugs are more easily reproduced, audit help, and improve traceability.
- Provides consistency across environments such as dev, test, and release.
- It increased deployment cadence.
- Less documentation is needed and needs to be maintained as all configuration is available in scripts.
- Enables automated scale-up and scale out.
- Allows version-controlled configuration.
- Helps detect and correct configuration drift.
- Provides code-review and unit-testing capabilities to help manage infrastructure changes.
- Treats infrastructure as a flexible resource.
- Promotes automation.

### Imperative & Declarative Configuration

- **Declarative** (functional). The declarative approach states *what* the final state should be. When run, the script or definition will initialize or configure the machine to have the finished state declared without defining *how* that final state should be achieved.
- **Imperative** (procedural). In the imperative approach, the script states the *how* for the final state of the machine by executing the steps to get to the finished state. It defines what the final state needs to be but also includes how to achieve that final state. It also can consist of coding concepts such as *for*, **if-then*, *loops*, and matrices.

### Best practices

The **declarative** approach abstracts away the methodology of how a state is achieved. As such, it can be easier to read and understand what is being done.

- It also makes it easier to write and define. Declarative approaches also separate the final desired state and the coding required to achieve that state.
- So, it doesn't force you to use a particular approach, allowing for optimization.

- A **declarative** approach would generally be the preferred option where ease of use is the primary goal. Azure Resource Manager template files are an example of a declarative automation approach.

An **imperative** approach may have some advantages in complex scenarios where changes in the environment occur relatively frequently, which need to be accounted for in your code.

There's no absolute on which is the best approach to take, and individual tools may be used in either *declarative* or *imperative* forms. The best approach for you to take will depend on your needs.

## Idempotent Configuration

**Idempotence** is a mathematical term that can be used in Infrastructure as Code and Configuration as Code. It can apply one or more operations against a resource, resulting in the same outcome.

- re-run script without and the result is the same
- You can achieve idempotency by:
  - Automatically configuring and reconfiguring an existing set of resources.
  - Discarding the existing resources and recreating a new environment.

## See Also

- [Create and target an environment](https://learn.microsoft.com/en-us/azure/devops/pipelines/process/environments).
- [Integrate DevTest Labs environments into Azure Pipelines](https://learn.microsoft.com/en-us/azure/devtest-labs/integrate-environments-devops-pipeline).
- [What is infrastructure as code (IaC)?](https://learn.microsoft.com/en-us/devops/deliver/what-is-infrastructure-as-code).
- [Repeatable Infrastructure](https://learn.microsoft.com/en-us/azure/architecture/framework/devops/automation-infrastructure).
- [Infrastructure as code](https://learn.microsoft.com/en-us/dotnet/architecture/cloud-native/infrastructure-as-code).

# Azure Resources and Azure Resource Manager Templates

## Templates

Templates make your deployments faster and more repeatable:

- Templates improve consistency. Resource Manager templates provide a common language for you and others to describe your deployments. Despite the tool or SDK that you use to deploy the template, the template's structure, format, and expressions remain the same.
- Templates help express complex deployments. Templates enable you to deploy multiple resources in the correct order. For example, you wouldn't want to deploy a VM before creating an operating system (OS) disk or network interface. Resource Manager maps out each resource and its dependent resources and creates dependent resources first. Dependency mapping helps ensure that the deployment is carried out in the correct order.
- Templates reduce manual, error-prone tasks. Manually creating and connecting resources can be time-consuming, and it's easy to make mistakes. The Resource Manager ensures that the deployment happens the same way every time.
- Templates are code. Templates express your requirements through code. Think of a template as a type of Infrastructure as Code that can be shared, tested, and versioned like any other piece of software. Also, because templates are code, you can create a record that you can follow. The template code documents the deployment. Also, most users maintain their templates under revision control, such as GIT. Its revision history also records how the template (and your deployment) has evolved when you change the template.
- Templates promote reuse. Your template can contain parameters that are filled in when the template runs. A parameter can define a username or password, a domain name, and other necessary items. Template parameters also enable you to create multiple versions of your infrastructure, such as staging and production, while still using the same template.
- Templates are linkable. You can link Resource Manager templates together to make the templates themselves modular. You can write small templates that define a solution and then combine them to create a complete system.

Template Components

- written in JSON
- parameters: where you specify which values are configurable when the template runs
- variables: where you define values that are used throughout the template
- functions: where you define procedures for re-use throughout the template
- resources: define the Azure resources that make up your deployment
- outputs: define any information to be provided when the template runs

Usage:

- manage Dependencies with the `dependsOn` element
- modularize templates with `linked-to` and `templateLink`.  External templates can be accessible via a shared access signature (SAS)
- nest templates

## Deploy Resources

Deploy resources using the following deployment modes:

- **validate**. This option compiles the templates, validates the deployment, ensures the template is functional (for example, no circular dependencies), and correct syntax.
- **incremental mode (default)**. This option only deploys whatever is defined in the template. It doesn't remove or modify any resources that aren't defined in the template. For example, if you've deployed a VM via template and then renamed the VM in the template, the first VM deployed will remain after the template is rerun. It's the default mode.
- **complete mode**: Resource Manager deletes resources that exist in the resource group but isn't specified in the template. For example, only resources defined in the template will be present in the resource group after the template deploys. As a best practice, use this mode for production environments to achieve idempotency in your deployment templates.

Manage secrets in templates, manage access to the secret and reference the secret with a static ID.

## See Also

- [Connect to Microsoft Azure - Azure Pipelines | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/pipelines/library/connect-to-azure).
- [CI/CD with Azure Pipelines and templates - Azure Resource Manager | Microsoft Docs](https://learn.microsoft.com/en-us/azure/azure-resource-manager/templates/add-template-to-azure-pipelines).
- [Security through templates - Azure Pipelines | Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/pipelines/security/templates).

# Create Azure Resources using Azure CLI

Using Azure CLI to:

- create Azure Resources
- Run templates

Example commands:

```sh
# restart VM
az vm restart -g MyResourceGroup -n MyVm

# find commands
az find blob

# get list of commands for managing blob storage
az storage blob --help

# connect to Azure subscription "login"
az login

# create a resource group
az group create --name <name> --location <location>

# verify resource group
az group list
az group list --output table
az group list --query "[?name == '<rg name>']"
```

See also:

- [Azure CLI task](https://learn.microsoft.com/en-us/azure/devops/pipelines/tasks/deploy/azure-cli).
- [How to install the Azure CLI](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli).
- [Get started with Azure CLI](https://learn.microsoft.com/en-us/cli/azure/get-started-with-azure-cli).

# Azure Automation with DevOps

## Introduction

Some Azure Automation capabilities are:

- Process automation. Azure Automation provides you with the ability to automate frequent, time-consuming, and error-prone cloud management tasks.
- Azure Automation State Configuration. It's an Azure service that allows you to write, manage, and compile Windows PowerShell DSC configurations, import DSC Resources, and assign configurations to target nodes, all in the cloud. For more information, visit [Azure Automation State Configuration Overview](https://learn.microsoft.com/en-us/azure/automation/automation-dsc-overview).
- Update management. Manage operating system updates for Windows and Linux computers in Azure, on-premises environments, or other cloud providers. Get update compliance visibility across Azure, on-premises, and for other cloud services. You can create scheduled deployments to orchestrate update installations within a defined maintenance window. For more information, visit [Azure Automation Update Management Deployment Plan](https://learn.microsoft.com/en-us/azure/automation/update-management/plan-deployment).
- Start and stop virtual machines (VMs). Azure Automation provides an integrated Start/Stop VM–related resource that enables you to start and stop VMs on user-defined schedules. It also provides insights through **Azure Log Analytics** and can send emails by using action groups. For more information, go to [Start/Stop VMs during off-hours solution in Azure Automation](https://learn.microsoft.com/en-us/azure/automation/automation-solution-vm-management).
- Integration with GitHub, Azure DevOps, Git, or Team Foundation Version Control repositories. For more information, go to [Source control integration in Azure Automation](https://learn.microsoft.com/en-us/azure/automation/source-control-integration).
- Automate Amazon Web Services (AWS) Resources. Automate common tasks with resources in AWS using Automation runbooks in Azure. For more information, go to [Authenticate Runbooks with Amazon Web Services](https://learn.microsoft.com/en-us/azure/automation/automation-config-aws-account).
- Manage Shared resources. Azure Automation consists of a set of shared resources (such as *connections*, *credentials*, *modules*, *schedules*, and *variables*) that make it easier to automate and configure your environments at scale.
- Run backups. Azure Automation allows you to run regular backups of non-database systems, such as backing up Azure Blob Storage at certain intervals.

## runbook

**Runbooks** serve as repositories for your custom scripts and workflows.  Types:

- graphical runbooks
- PowerShell runbooks
- PowerShell workflow runbooks: run in Windows PowerShell Workflow
- Python runbooks (Python-2)

## Automation - Shared Resources

Azure Automation contains shared resources that are globally available to be associated with or used in a runbook. There are currently eight shared resources categories:

- **Schedules**: It allows you to define a one-off or recurring schedule.
- **Modules**: Contains Azure PowerShell modules.
- **Modules gallery**: It allows you to identify and import PowerShell modules into your Azure automation account.
- **Python packages**. Allows you to import a Python package by uploading: **.whl** or **tar.gz** packages.
- **Credentials**: It allows you to create username and password credentials.
- **Connections**: It allows you to specify Azure, Azure classic certificate, or Azure Service principal connections.
- **Certificates**: It allows you to upload certificates in .cer or pfx format.
- **Variables**: It allows you to define encrypted or unencrypted variables of types—for example, *String*, *Boolean*, *DateTime*, *Integer*, or no specific type.

## webhooks

A **webhook** allows you to start a particular runbook in Azure Automation through a single HTTPS request.

Post codes:

- 202 Accepted:  request accepted and the runbook was queued
- 400 Bad Request: runbook has expired, runbook is disabled, bad token URL or invalid
- 404 Not Found: webhook, runbook or account not found
- 500 Internal Server Error

Response

- contains JSON with job id

```JSON
{"JobIds":["< JobId >"]}
```

## Source Control Integration

Azure Automation supports source control integration.  This allows runbooks to be up to date with scripts in GitHub or Azure DevOps source control repository.

## PowerShell Workflows

Activity: A task that the workflow does

Workflow characteristics, a workflow can:

- Be long-running.
- Be repeated over and over.
- Run tasks in parallel.
- Be interrupted—can be stopped and restarted, suspended, and resumed.
- Continue after an unexpected interruption, such as a network outage or computer/server restart.

## Workflow benefits

A workflow offers many benefits, including:

- Windows PowerShell scripting syntax. Is built on PowerShell.
- Multidevice management. Simultaneously apply workflow tasks to hundreds of managed nodes.
- Single task runs multiple scripts and commands.
- Automated failure recovery.
- Connection and activity retries.
- Connect and disconnect from workflows.
- Task scheduling.

Checkpoints: A snapshot of the current state of a workflow.

Parallel Processing:

```sh
    Parallel
    {
        Start-AzureRmVM -Name $vm0 -ResourceGroupName $rg
        Start-AzureRmVM -Name $vm1 -ResourceGroupName $rg
    }
```

See also

- [Manage runbooks in Azure Automation](https://learn.microsoft.com/en-us/azure/automation/manage-runbooks).
- [Use source control integration](https://learn.microsoft.com/en-us/azure/automation/source-control-integration).
- [Webhooks](https://learn.microsoft.com/en-us/azure/devops/service-hooks/services/webhooks).
- [Learn PowerShell Workflow for Azure Automation](https://learn.microsoft.com/en-us/azure/automation/automation-powershell-workflow).

# Desired State Configuration

## Introduction

**Desired State Configuration** (DSC) is a configuration management approach that you can use for configuration, deployment, and management of systems to ensure that an environment is maintained in a state that you specify (*defined state*) and doesn't deviate from that state.

- **Configuration drift** is the process of a set of resources changing over time from their original deployment state.
- Security considerations. Configuration drift can also introduce security vulnerabilities into your environment. For example:
  - Ports might be opened that should be kept closed.
  - Updates and security patches might not be applied across environments consistently.
  - The software might be installed that doesn't meet compliance requirements.
- Use Desired State Configuration and Policy (Azure DSC, Azure Policy) to manage configuration drift

DSC components:

- Configurations. These are declarative PowerShell scripts that define and configure instances of resources. Upon running the configuration, DSC (and the resources being called by the configuration) will apply the configuration, ensuring that the system exists in the state laid out by the configuration. DSC configurations are also *idempotent*: The Local Configuration Manager (LCM) will ensure that machines are configured in whatever state the configuration declares.
- Resources. They contain the code that puts and keeps the target of a configuration in the specified state. Resources are in PowerShell modules and can be written to a model as generic as a file or a Windows process or as specific as a Microsoft Internet Information Services (IIS) server or a VM running in Azure.
- Local Configuration Manager (LCM). The LCM runs on the nodes or machines you wish to configure. It's the engine by which DSC facilitates the interaction between resources and configurations. The LCM regularly polls the system using the control flow implemented by resources to maintain the state defined by a configuration. If the system is out of state, the LCM calls the code in resources to apply the configuration according to specified.

Two DSC models:

- Push: a user actively pushes configuration to a tartget
- Pull: the target pulls configuration

## Pull Model

- Pull mode is where pull clients are automatically configured to get their desired state configurations from a remote pull service. This remote pull service is provided by a *pull server* that acts as central control and manager for the configurations, ensures that nodes conform to the desired state, and reports on their compliance status. The pull server can be set up as an SMB-based pull server or an HTTPS-based server. HTTPS-based pull-server uses the Open Data Protocol (OData) with the OData Web service to communicate using REST APIs. It's the model we're most interested in, as it can be centrally managed and controlled. The following diagram provides an outline of the workflow of DSC pull mode.

## Azure Automation DSC (PowerShell)

The following outlines some of the reasons why we would consider using Azure Automation DSC ([Managed Object Format](https://learn.microsoft.com/en-us/windows/win32/wmisdk/managed-object-format--mof-)):

- Built-in pull server. Provides a DSC pull server like the Windows Feature DSC service so that target nodes automatically receive configurations, conform to the desired state, and report back on their compliance. The built-in pull server in Azure Automation eliminates the need to set up and maintain your pull server.
- Management of all your DSC artifacts. You can manage all your DSC configurations, resources, and target nodes from the Azure portal or PowerShell.
- Import reporting data into Log Analytics. Nodes managed with Azure Automation state configuration send detailed reporting status data to the built-in pull server. You can configure Azure Automation state configuration to send this data to your Log Analytics workspace.

DSC configuration elements:

- configuration block
- node block: defines the nodes (computers and VMs) that you're configuring
- resource blocks: where the configuration sets the properties for the resources (see [DSC resources](https://learn.microsoft.com/en-us/powershell/scripting/dsc/resources/resources))

DSC's are imported and compiled.

- [Enable Azure Automation State Configuration.](https://learn.microsoft.com/en-us/azure/automation/automation-dsc-onboarding)
- [Configuring the Local Configuration Manager](https://learn.microsoft.com/en-us/powershell/scripting/dsc/managing-nodes/metaconfig)

Hybrid Management: Hybrid Worker feature in Azure Automation allows runbooks to manage local resources in a private data center.

Linux Automation: Linux OS is supported CentOS, Debian, Oract, RHEL, SUSE and Ubuntu.

See Also

- [Building a Continuous Integration and Continuous Deployment pipeline with DSC](https://learn.microsoft.com/en-us/azure/devops/pipelines/release/dsc-cicd?view=azure-devops).
- [Azure Automation State Configuration overview](https://learn.microsoft.com/en-us/azure/automation/automation-dsc-overview).
- [Introduction to the Azure Desired State Configuration extension handler](https://learn.microsoft.com/en-us/azure/virtual-machines/extensions/dsc-overview).

# Bicep

**Azure Bicep** is the next revision of **ARM templates** designed to solve some of the issues developers were facing when deploying their resources to Azure. It's an Open Source tool and, in fact, a domain-specific language (DSL) that provides a means to declaratively codify infrastructure, which describes the topology of cloud resources such as VMs, Web Apps, and networking interfaces. It also encourages code reuse and modularity in designing the infrastructure as code files.

- [Bicep](https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/overview?tabs=bicep) is a domain specific language (DSL) for deploying resources to Azure.
- Bicep provides the following advantages:
  - **Support for all resource types and API versions**: Bicep immediately supports all preview and GA versions for Azure services. As soon as a resource provider introduces new resources types and API versions, you can use them in your Bicep file. You don't have to wait for tools to be updated before using the new services.
  - **Simple syntax**: When compared to the equivalent JSON template, Bicep files are more concise and easier to read. Bicep requires no previous knowledge of programming languages. Bicep syntax is declarative and specifies which resources and resource properties you want to deploy.

Bicep file `.bicep` components: scope, parameters, variable, modules and outputs

- [What is Bicep? | Azure Bicep documentation](https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/overview).
- [Bicep on Microsoft Learn](https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/learn-bicep).
- [Best practices for Bicep | Microsoft documentation](https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/best-practices).
- [Migrate to Bicep | Microsoft documentation](https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/migrate).





s
