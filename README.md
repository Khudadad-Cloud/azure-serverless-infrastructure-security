# Azure Serverless Infrastructure and Security Project

## Project Overview

This project combines multiple Microsoft Azure services to build and manage a cloud environment with a focus on serverless computing, infrastructure deployment, network security, encryption, and cost management.

The project brings together an Azure Function App, Azure Resource Manager (ARM) templates, Azure Cloud Shell, Network Security Groups (NSGs), Azure Key Vault, and Azure Cost Management.

Each component supports a different part of the solution, from deploying and running serverless workloads to controlling network traffic, protecting sensitive information, and reviewing cloud spending.

This project demonstrates hands-on experience with Azure resource management, cloud security, infrastructure as code, and cost optimization.

## Project Objectives

* Deploy and configure an Azure Function App.
* Manage Azure resource deployments using ARM templates.
* Execute Azure administration commands using Azure Cloud Shell.
* Configure Network Security Groups to control network traffic.
* Use Azure Key Vault to manage keys, secrets, and encryption-related resources.
* Review Azure spending and identify opportunities for cost optimization.
* Document the implementation using screenshots and an architecture diagram.

## Technologies and Services

* Microsoft Azure
* Azure Function App
* Azure Resource Manager (ARM) Templates
* Azure Cloud Shell
* Azure Virtual Network
* Network Security Groups (NSGs)
* Azure Key Vault
* Azure Cost Management
* Azure Portal
* Azure CLI and PowerShell, where applicable

## Architecture Overview

The solution combines serverless computing, infrastructure deployment, network security, key and secret management, and cost monitoring within an Azure environment.

ARM templates support repeatable resource deployment, while Azure Cloud Shell provides a browser-based environment for running Azure CLI or PowerShell commands.

Network Security Groups control permitted network traffic according to configured security rules. Azure Key Vault provides centralized management of supported secrets and cryptographic keys. Azure Cost Management helps review cloud expenditure and identify potential savings.

The exact connections between these services depend on the deployed configuration.

**Architecture Diagram**

![Azure Serverless Infrastructure and Security Architecture](diagrams/azure-architecture.png)

## Implementation Details

### 1. Create an Azure Function App

**Objective:** Deploy a serverless application using Azure Functions.

**Implementation:**

* Created and configured an Azure Function App.
* Selected the required runtime and hosting configuration.
* Configured the associated Azure resources required by the application.
* Reviewed the Function App configuration in the Azure Portal.
* Verified the deployment and tested the function where applicable.

**Skills demonstrated:**

* Azure Functions deployment
* Serverless computing fundamentals
* Application configuration
* Azure resource management

**Evidence:** See the screenshots in the `screenshots/` folder.

### 2. Manage Azure Resource Deployment Using ARM Templates

**Objective:** Define and deploy Azure resources using an Azure Resource Manager template.

**Implementation:**

* Worked with ARM templates to describe Azure resource configurations.
* Reviewed the template structure and resource properties.
* Used the Azure deployment process to deploy or manage the required resources.
* Reviewed deployment results and resolved configuration issues where necessary.

**Skills demonstrated:**

* Infrastructure as Code (IaC)
* ARM template structure
* Azure Resource Manager
* Resource deployment and troubleshooting

**Evidence:** See the ARM template and deployment screenshots.

### 3. Run Commands Using Azure Cloud Shell

**Objective:** Perform Azure administration tasks using a browser-based command-line environment.

**Implementation:**

* Opened Azure Cloud Shell through the Azure Portal.
* Used the available command-line environment to manage and inspect Azure resources.
* Worked with Azure CLI or PowerShell, depending on the task.
* Verified resource configurations and command results.

**Skills demonstrated:**

* Azure Cloud Shell
* Azure CLI and/or PowerShell
* Cloud administration
* Resource inspection and troubleshooting

**Evidence:** See the Cloud Shell screenshots.

### 4. Implement a Network Security Group

**Objective:** Control network traffic using Azure Network Security Groups.

**Implementation:**

* Created or configured a Network Security Group.
* Reviewed inbound and outbound security rules.
* Configured traffic permissions according to the intended network requirements.
* Reviewed the NSG configuration and its associated network resources.

**Skills demonstrated:**

* Azure network security
* Inbound and outbound security rules
* Traffic filtering
* Network access control
* Cloud security fundamentals

**Evidence:** See the NSG configuration screenshots.

### 5. Manage Encryption Using Azure Key Vault

**Objective:** Use Azure Key Vault to manage supported cryptographic keys and secrets securely.

**Implementation:**

* Created or configured an Azure Key Vault.
* Reviewed the available key and secret management options.
* Examined access permissions and the configuration required to control access.
* Reviewed the relevant encryption or key-management settings used in the deployment.

**Skills demonstrated:**

* Azure Key Vault
* Key and secret management
* Access control
* Encryption and cryptographic key management
* Cloud security practices

**Evidence:** See the Key Vault screenshots.

### 6. Manage and Review Azure Costs

**Objective:** Understand and monitor cloud spending using Azure Cost Management.

**Implementation:**

* Opened Azure Cost Management in the Azure Portal.
* Reviewed available cost and usage information.
* Examined the available cost analysis and budgeting features.
* Identified opportunities to manage resource usage and reduce unnecessary spending.

**Skills demonstrated:**

* Azure Cost Management
* Cloud cost analysis
* Budgeting fundamentals
* Resource utilization awareness
* Cost optimization

**Evidence:** See the Cost Management screenshots.

## Screenshots

The following screenshots document the configuration and deployment of the project's Azure components.

### 1. Azure Function App

![Azure Function App](screenshots/01-function-app.png)

### 2. ARM Template Deployment

![ARM Template Deployment](screenshots/02-arm-template.png)

### 3. Azure Cloud Shell

![Azure Cloud Shell](screenshots/03-cloud-shell.png)

### 4. Network Security Group

![Network Security Group](screenshots/04-network-security-group.png)

### 5. Azure Key Vault

![Azure Key Vault](screenshots/05-key-vault.png)

### 6. Azure Cost Management

![Azure Cost Management](screenshots/06-cost-management.png)

## Security Considerations

* Apply the principle of least privilege when granting access to Azure resources.
* Configure NSG rules to allow only the traffic required by the workload.
* Store sensitive application information in appropriate secure services rather than source code.
* Review Key Vault access permissions and relevant cryptographic settings.
* Monitor resource usage and cloud spending.
* Avoid publishing credentials, access keys, tokens, or other confidential configuration details.

## Skills Demonstrated

* Microsoft Azure administration
* Serverless computing
* Infrastructure as Code
* Azure CLI and PowerShell
* Network security
* Key and secret management
* Cloud resource deployment
* Cost management
* Technical documentation
* Cloud troubleshooting

## Project Outcome

This project brought together several Azure services to explore cloud application deployment, infrastructure management, network security, cryptographic key and secret management, and cost monitoring.

It demonstrates practical exposure to Azure administration and cloud infrastructure concepts relevant to junior IT support, cloud support, and Azure administration roles.

## Disclaimer

This project was completed in a personal learning environment. Resource configurations, service availability, and costs depend on the Azure subscription, region, selected service tiers, and deployment settings.
