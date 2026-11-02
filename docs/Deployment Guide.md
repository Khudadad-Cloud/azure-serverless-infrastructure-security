# Deployment Guide

## 1. Microsoft Azure – Environment Preparation

Before deploying the infrastructure, prepare the Azure environment.

### Steps

1. Sign in to the [Microsoft Azure Portal](https://portal.azure.com/).
2. Navigate to **Resource Groups**.
3. Select **Create**.
4. Choose the appropriate subscription.
5. Enter a resource group name (e.g., `rg-functionapp-project`).
6. Select an Azure region.
7. Review the configuration and select **Create**.

The resource group provides a centralized location for managing all project resources.

---

## 2. Azure Virtual Network (VNet)

Create a Virtual Network to provide a private networking environment for Azure resources.

### Steps

1. Navigate to **Virtual Networks** in the Azure Portal.
2. Select **Create**.
3. Select the project resource group.
4. Enter a VNet name (e.g., `vnet-functionapp`).
5. Select the deployment region.
6. Configure the IPv4 address space (e.g., `10.0.0.0/16`).
7. Create an application subnet (e.g., `10.0.1.0/24`).
8. Review the configuration and deploy.

**Purpose:** Provides network isolation and a foundation for secure connectivity between supported Azure resources.

---

## 3. Network Security Groups (NSGs)

Configure Network Security Groups to control inbound and outbound network traffic.

### Steps

1. Search for **Network Security Groups** in the Azure Portal.
2. Select **Create**.
3. Select the project resource group and region.
4. Enter an NSG name (e.g., `nsg-functionapp`).
5. Deploy the NSG.
6. Open the NSG and navigate to **Inbound security rules**.
7. Add rules based on the application's networking requirements.
8. Review **Outbound security rules**.
9. Associate the NSG with the appropriate subnet or network interface.

**Purpose:** Controls network traffic using source, destination, port, protocol, and priority-based security rules.

---

## 4. Azure Key Vault

Deploy Azure Key Vault to securely manage application secrets, encryption keys, and certificates.

### Steps

1. Search for **Key Vaults** in the Azure Portal.
2. Select **Create**.
3. Select the project resource group and region.
4. Enter a unique Key Vault name (e.g., `kv-functionapp-project`).
5. Select the appropriate pricing tier.
6. Configure the permission model using Azure RBAC.
7. Configure networking and access settings.
8. Review and create the Key Vault.
9. Open the Key Vault and navigate to **Objects → Secrets**.
10. Select **Generate/Import** to create a secret.
11. Configure the Function App's managed identity and grant it the required Key Vault permissions.

**Purpose:** Centralizes sensitive information management and reduces the need to store credentials directly in application code.

---

## 5. Azure Function App

Deploy an Azure Function App to provide serverless application hosting.

### Steps

1. Search for **Function App** in the Azure Portal.
2. Select **Create**.
3. Choose the project resource group.
4. Enter a globally unique Function App name.
5. Select the appropriate runtime stack (e.g., .NET or Python).
6. Select the runtime version.
7. Choose an appropriate hosting plan.
8. Configure the operating system and deployment region.
9. Configure or create the required storage account.
10. Review networking and monitoring settings.
11. Select **Review + Create**.
12. Deploy the Function App.
13. Open the Function App and verify its deployment status.
14. Configure VNet integration if supported by the selected hosting plan and required by the architecture.
15. Enable the Function App's managed identity if it needs to access Key Vault.

**Purpose:** Hosts and executes serverless functions without requiring direct management of virtual machines.

---

## 6. Azure Resource Manager (ARM) Templates

Use ARM templates to deploy and manage Azure resources through Infrastructure as Code (IaC).

### Steps

1. Create an ARM template in JSON format.
2. Define the required Azure resources.
3. Configure resource names, locations, properties, and dependencies.
4. Define parameters for reusable deployment configurations.
5. Save the template as `azuredeploy.json`.
6. Open Azure Cloud Shell.
7. Select the Bash environment.
8. Upload or access the ARM template.
9. Validate the template.
10. Deploy the template to the project resource group.

### ARM Template Validation

```bash
az deployment group validate \
  --resource-group rg-functionapp-project \
  --template-file azuredeploy.json
```

### Deploy ARM Template

```bash
az deployment group create \
  --resource-group rg-functionapp-project \
  --template-file azuredeploy.json
```

### Verify Deployment

```bash
az deployment group list \
  --resource-group rg-functionapp-project \
  --output table
```

**Purpose:** Automates infrastructure deployment and improves consistency, repeatability, and resource management.

---

## 7. Azure Cloud Shell

Use Azure Cloud Shell to execute administrative commands and manage Azure resources.

### Steps

1. Sign in to the Azure Portal.
2. Select the Cloud Shell icon in the portal toolbar.
3. Choose **Bash** or **PowerShell**.
4. Authenticate using your Azure account if prompted.
5. Select the appropriate subscription.
6. Execute Azure CLI or PowerShell commands.
7. Validate resource configurations and deployment results.

### Verify Azure Account

```bash
az account show
```

### List Available Subscriptions

```bash
az account list --output table
```

### Select Subscription

```bash
az account set --subscription "SUBSCRIPTION_ID"
```

### List Resource Groups

```bash
az group list --output table
```

**Purpose:** Provides a browser-based command-line environment for Azure administration without requiring local installation.

---

## 8. Azure Cost Management

Use Azure Cost Management to monitor spending and identify cost optimization opportunities.

### Steps

1. Navigate to **Cost Management + Billing** in the Azure Portal.
2. Open **Cost Management**.
3. Select **Cost analysis**.
4. Select the appropriate subscription or resource group scope.
5. Review actual spending and cost trends.
6. Analyze spending by resource, service, and location.
7. Identify unused or unnecessary resources.
8. Review available budget options.
9. Configure a budget and spending alerts if required.
10. Implement appropriate cost optimization measures.

**Purpose:** Improves cost visibility, helps control cloud spending, and supports efficient resource utilization.

---

## 9. Azure Portal

Use the Azure Portal as the central graphical interface for managing and monitoring deployed resources.

### Steps

1. Sign in to the Azure Portal.
2. Open the project resource group.
3. Review the deployed resources.
4. Open the Function App and verify its configuration.
5. Review networking and NSG settings.
6. Verify Key Vault configuration and access permissions.
7. Review deployment history.
8. Monitor application performance and available logs.
9. Review resource health and configuration settings.

**Purpose:** Provides centralized visibility and management of the Azure infrastructure.

---

## 10. Azure CLI and PowerShell

Use Azure CLI and PowerShell to perform administrative tasks and automate resource management.

### Azure CLI – List Azure Resources

```bash
az resource list \
  --resource-group rg-functionapp-project \
  --output table
```

### Azure CLI – Verify Function Apps

```bash
az functionapp list \
  --resource-group rg-functionapp-project \
  --output table
```

### Azure CLI – Verify Network Security Groups

```bash
az network nsg list \
  --resource-group rg-functionapp-project \
  --output table
```

### Azure CLI – Verify Key Vaults

```bash
az keyvault list \
  --resource-group rg-functionapp-project \
  --output table
```

### PowerShell – Connect to Azure

```powershell
Connect-AzAccount
```

### PowerShell – List Resource Groups

```powershell
Get-AzResourceGroup
```

### PowerShell – List Resources

```powershell
Get-AzResource -ResourceGroupName "rg-functionapp-project"
```

**Purpose:** Supports command-line administration, resource verification, automation, and repeatable management operations.

---

## 11. Deployment Verification

After completing the deployment, verify that all resources are configured correctly.

| Resource                | Verification                                               |
| ----------------------- | ---------------------------------------------------------- |
| Azure Resource Group    | Confirm the resource group exists.                         |
| Azure Function App      | Verify deployment and application configuration.           |
| ARM Templates           | Confirm successful template validation and deployment.     |
| Azure Cloud Shell       | Verify successful execution of administrative commands.    |
| Azure Virtual Network   | Confirm address space and subnet configuration.            |
| Network Security Groups | Verify security rules and subnet associations.             |
| Azure Key Vault         | Confirm vault deployment, secrets, and access permissions. |
| Azure Cost Management   | Review spending and cost analysis.                         |
| Azure Portal            | Confirm resource visibility and deployment status.         |
| Azure CLI / PowerShell  | Verify resource information through command-line tools.    |

---

## 12. Project Documentation

Document the deployment process to demonstrate the implementation and configuration of the Azure environment.

Recommended screenshots:

* Azure Resource Group deployment.
* Azure Function App configuration.
* ARM template deployment results.
* Azure Cloud Shell commands.
* Virtual Network and subnet configuration.
* Network Security Group security rules.
* Azure Key Vault configuration.
* Azure Cost Management dashboard.
* Azure Portal resource overview.

Store the screenshots in the project's `screenshots/` directory and the architecture diagram in the `images/` directory.

---

## Deployment Outcome

The completed implementation demonstrates practical experience with:

* Azure resource deployment and administration.
* Infrastructure as Code using ARM templates.
* Serverless computing with Azure Functions.
* Cloud networking and network security.
* Secure secrets and key management.
* Azure CLI and PowerShell administration.
* Cloud spending analysis and cost optimization.
* Technical documentation and architecture design.
