# Azure Data Factory (ADF) — ARM Template Deployment

## 📌 Project Overview

This project contains Azure Resource Manager (ARM) templates exported from Azure Data Factory (ADF) to support infrastructure deployment, configuration management, and environment replication.

The templates define the Data Factory resources and linked services used in a data engineering workflow involving Azure Data Lake Storage, Azure Blob Storage, Azure Databricks, and Azure SQL Database.

The goal is to make the deployment configuration reusable, easier to maintain, and suitable for version control.

## 🏗️ Architecture & Services

The project includes configuration for the following Azure services:

- **Azure Data Factory** — Orchestrates data integration and pipeline execution.
- **Azure Data Lake Storage Gen2** — Stores data in a lake-based storage environment.
- **Azure Blob Storage** — Provides object storage for pipeline-related data.
- **Azure Databricks** — Supports distributed data processing and transformation.
- **Azure SQL Database** — Serves as a relational data source or reporting destination.
- **ARM Templates** — Define Azure resources and deployment parameters as JSON.

## 📂 Project Structure

```text
arm_template/
├── ARMTemplateForFactory.json
├── ARMTemplateParametersForFactory.json
├── factory/
│   ├── usamakifactory_ARMTemplateForFactory.json
│   └── usamakifactory_ARMTemplateParametersForFactory.json
└── linkedTemplates/
    ├── ArmTemplate_0.json
    ├── ArmTemplate_1.json
    ├── ArmTemplate_master.json
    └── ArmTemplateParameters_master.json
```

## ⚙️ Key Features

- **Infrastructure as Code (IaC):** Defines deployment configuration using ARM templates.
- **Reusable Parameters:** Uses parameters for factory names, storage endpoints, SQL connection settings, and other environment-specific values.
- **Linked Template Deployment:** Organizes resources into linked templates for modular deployment.
- **Secure Configuration:** Uses secure parameters for sensitive values such as passwords, access tokens, storage account keys, and connection strings.
- **Environment Portability:** Uses placeholders for environment-specific identifiers and resource names.
- **Version Control:** Keeps infrastructure configuration in JSON files for review, tracking, and collaboration.

## 🚀 Deployment Guide

### Prerequisites

Before deploying, ensure you have:

- An Azure subscription.
- An Azure Data Factory instance or the permissions required to create one.
- The necessary Azure resources, including storage, Databricks, and SQL Database, where applicable.
- Appropriate Azure permissions to deploy the resources.
- Azure CLI or access to the Azure Portal.

### Step 1: Configure Parameters

Review the relevant parameters files:

- `ARMTemplateParametersForFactory.json`
- `linkedTemplates/ArmTemplateParameters_master.json`
- `factory/usamakifactory_ARMTemplateParametersForFactory.json`

Replace the example placeholders with values appropriate for your own Azure environment.

Supply passwords, access tokens, account keys, and connection strings securely during deployment. Do not commit real credentials to source control.

### Step 2: Review the Templates

Check that:

- Factory names and resource identifiers match your environment.
- Storage URLs and SQL server/database settings are correct.
- Linked-template references point to accessible template files or valid deployment URLs.
- Required parameters are supplied.
- Azure resources and permissions are configured correctly.

### Step 3: Deploy

The templates can be deployed using the Azure Portal, Azure CLI, or an appropriate Azure DevOps release pipeline.

For example, deploying the main template with Azure CLI:

```bash
az deployment group create \
  --resource-group <RESOURCE_GROUP> \
  --template-file ARMTemplateForFactory.json \
  --parameters @ARMTemplateParametersForFactory.json
```

Replace `<RESOURCE_GROUP>` with your resource group name and ensure all required parameter values are provided.

**Note:** This command is an example. If the exported template uses linked templates, additional parameters or accessible template URLs may be required. Review the template structure before deployment.

## 🔐 Security Considerations

This repository is intended to demonstrate sanitized infrastructure configuration.

- Never commit actual passwords, access tokens, storage keys, or connection strings.
- Use Azure Key Vault or another approved secrets-management solution for production deployments.
- Use Azure role-based access control (RBAC) and least-privilege permissions.
- Replace example placeholders with your own environment-specific values.
- Review all template and parameter files before publishing or deploying.

## 🧪 Validation

The JSON files were validated using PowerShell's `ConvertFrom-Json` to check for JSON syntax errors.

Successful JSON parsing confirms syntax validity, but does not guarantee that an ARM deployment will succeed. Deployment compatibility, parameter completeness, resource permissions, and linked-template references must also be verified.

## 🎯 Learning Outcomes

This project demonstrates practical experience with:

- Azure Data Factory configuration and deployment.
- Infrastructure as Code using ARM templates.
- Parameterized cloud resource configuration.
- Integration between Azure data services.
- Secure handling of deployment parameters.
- JSON validation and version-controlled infrastructure.

## ⚠️ Disclaimer

This repository contains sanitized example configuration. It is not guaranteed to deploy without modification. Resource names, parameters, linked-template references, credentials, and Azure permissions must be configured for the target environment.
