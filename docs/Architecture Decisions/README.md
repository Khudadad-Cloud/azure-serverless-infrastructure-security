## Architecture Decisions

The project architecture was designed to deploy a secure, manageable, and cost-conscious Azure Function App environment. The following technologies and services were selected based on their functionality, security capabilities, automation support, and integration with Microsoft Azure.

| Technology / Service                       | Architecture Decision                                                                                                                                   |
| ------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Microsoft Azure**                        | Selected as the cloud platform to host, manage, secure, and monitor the application infrastructure.                                                     |
| **Azure Function App**                     | Selected as the serverless compute service to execute application functions without managing dedicated virtual machines.                                |
| **Azure Resource Manager (ARM) Templates** | Used to define and deploy Azure resources through Infrastructure as Code (IaC), supporting consistent and repeatable deployments.                       |
| **Azure Cloud Shell**                      | Selected as a browser-based administration environment to execute Azure CLI and PowerShell commands without requiring local command-line configuration. |
| **Azure Virtual Network (VNet)**           | Used to provide a private network environment and support secure communication between connected Azure resources.                                       |
| **Network Security Groups (NSGs)**         | Implemented to control inbound and outbound network traffic using security rules based on source, destination, port, and protocol.                      |
| **Azure Key Vault**                        | Selected to securely store and manage sensitive information, including secrets, cryptographic keys, and certificates.                                   |
| **Azure Cost Management**                  | Used to monitor cloud spending, review resource costs, and identify opportunities to optimize Azure resource consumption.                               |
| **Azure Portal**                           | Used as the graphical management interface to deploy, configure, monitor, and troubleshoot Azure resources.                                             |
| **Azure CLI and PowerShell**               | Used where applicable to automate administrative operations, manage resources, and execute deployment and configuration commands.                       |

### Key Architectural Considerations

**1. Serverless Computing**

Azure Function App was selected to reduce infrastructure management overhead and support event-driven application execution.

**2. Infrastructure as Code**

ARM templates provide a repeatable deployment approach, reducing manual configuration and improving infrastructure consistency.

**3. Network Security**

Azure Virtual Network and Network Security Groups provide network isolation and traffic filtering to help protect Azure resources.

**4. Secrets Management**

Azure Key Vault provides centralized and secure management of sensitive application information, reducing the need to store secrets directly in application code.

**5. Cost Optimization**

Azure Cost Management supports spending visibility and helps identify unnecessary resource consumption and potential cost savings.

**6. Administrative Flexibility**

Azure Portal, Cloud Shell, Azure CLI, and PowerShell provide both graphical and command-line management capabilities.

### Design Outcome

The selected architecture supports the following objectives:

* **Scalability:** Serverless application hosting through Azure Functions.
* **Automation:** Repeatable infrastructure deployment using ARM templates.
* **Security:** Network traffic filtering and centralized secrets management.
* **Manageability:** Centralized administration through Azure Portal and Cloud Shell.
* **Cost Awareness:** Monitoring and optimization of cloud resource spending.
* **Documentation:** Recording implementation steps and deployment evidence for future reference.

