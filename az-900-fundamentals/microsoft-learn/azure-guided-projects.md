# 🛠️ Apply Azure Skills — Guided Projects

> 📖 Based on: [Microsoft Learn — Apply Azure Skills in Guided Projects](https://learn.microsoft.com/en-us/training/paths/introduction-cloud-infrastructure-apply-azure-skills-guided-projects/)
> Part 4 of 4 in the Azure Fundamentals series (AZ-900)

This part is hands-on — no theory, just practice. Each project below is a step-by-step exercise you complete in a real Azure environment. Use the links to do them directly on Microsoft Learn.

---

## Projects Overview

| # | Project | What you practice |
|---|---|---|
| 1 | Deploy a static website with Blob Storage | Blob storage, static website hosting |
| 2 | Organize and protect resources with tags and locks | Tags, resource locks |
| 3 | Build a simple website endpoint with Azure Functions | Serverless, function triggers |
| 4 | Set up new employee access (Entra ID + RBAC) | Identity, role assignments |
| 5 | Share files securely | Blob storage, SAS tokens, access policies |
| 6 | Set up cost guardrails | Budgets, cost alerts |
| 7 | Monitor Azure with Service Health and Activity Log alerts | Azure Monitor, alerting |
| 8 | Manage resources with Cloud Shell and Azure CLI | CLI, scripting |

---

## Project 1 — Deploy a Static Website with Azure Blob Storage

🔗 [Start project](https://learn.microsoft.com/en-us/training/modules/guided-project-deploy-static-website-blob-storage/)

**What you do:** upload HTML files to a Blob Storage container and enable static website hosting so the files are publicly accessible via a URL.

**Key concepts practiced:**
- Creating a Storage Account
- Enabling static website hosting on a container
- Uploading files via Azure portal
- Accessing the public URL

**My notes:**
> _(fill in after completing the project)_

---

## Project 2 — Organize and Protect Resources with Tags and Locks

🔗 [Start project](https://learn.microsoft.com/en-us/training/modules/guided-project-organize-resources-tags-locks/)

**What you do:** tag Azure resources for organization and apply resource locks to prevent accidental deletion.

**Key concepts practiced:**
- Adding tags (key-value pairs) to resources
- Applying Delete and ReadOnly locks
- Verifying that a locked resource cannot be deleted

**My notes:**
> _(fill in after completing the project)_

---

## Project 3 — Build a Simple Website Endpoint with Azure Functions

🔗 [Start project](https://learn.microsoft.com/en-us/training/modules/guided-project-build-basic-website-endpoint-with-functions/)

**What you do:** create an Azure Function triggered by HTTP requests and validate its response.

**Key concepts practiced:**
- Creating a Function App
- Writing a simple HTTP-triggered function
- Testing the endpoint

**My notes:**
> _(fill in after completing the project)_

---

## Project 4 — Set Up New Employee Access (Entra ID + RBAC)

🔗 [Start project](https://learn.microsoft.com/en-us/training/modules/guided-project-new-employee-access/)

**What you do:** create a new user in Microsoft Entra ID and assign them the minimum permissions needed for their role.

**Key concepts practiced:**
- Creating users in Entra ID
- Assigning RBAC roles at the right scope
- Principle of least privilege in practice

**My notes:**
> _(fill in after completing the project)_

---

## Project 5 — Share Files Securely

🔗 [Start project](https://learn.microsoft.com/en-us/training/modules/guided-project-share-files-securely/)

**What you do:** share a file temporarily and securely using Blob Storage, stored access policies, and SAS (Shared Access Signature) tokens.

**Key concepts practiced:**
- Stored access policies on containers
- Generating SAS tokens with expiry and permission scopes
- Secure temporary file sharing without exposing storage keys

**My notes:**
> _(fill in after completing the project)_

---

## Project 6 — Set Up Cost Guardrails in Azure

🔗 [Start project](https://learn.microsoft.com/en-us/training/modules/guided-project-cost-guardrails/)

**What you do:** set budgets and cost alerts to avoid unexpected Azure spending.

**Key concepts practiced:**
- Creating budgets in Azure Cost Management
- Setting alert thresholds (e.g. notify at 80% and 100% of budget)
- Reviewing spending forecasts

**My notes:**
> _(fill in after completing the project)_

---

## Project 7 — Monitor Azure with Service Health and Activity Log Alerts

🔗 [Start project](https://learn.microsoft.com/en-us/training/modules/guided-project-monitor-service-health-activity-alerts/)

**What you do:** configure alerts based on Azure Service Health events and Activity Log entries.

**Key concepts practiced:**
- Setting up Service Health alerts
- Creating Activity Log alert rules
- Choosing action groups (email, SMS, webhook)

**My notes:**
> _(fill in after completing the project)_

---

## Project 8 — Manage Resources with Cloud Shell and Azure CLI

🔗 [Start project](https://learn.microsoft.com/en-us/training/modules/guided-project-manage-resources-cloud-shell-cli/)

**What you do:** use Azure Cloud Shell and CLI commands to create and manage resources without touching the portal UI.

**Key concepts practiced:**
- Opening and using Cloud Shell (Bash)
- Basic Azure CLI commands: `az group create`, `az storage account create`, `az vm create`
- Scripting resource creation

**Useful CLI commands:**
```bash
# Login
az login

# List subscriptions
az account list --output table

# Create a resource group
az group create --name myResourceGroup --location westeurope

# List resources in a group
az resource list --resource-group myResourceGroup --output table

# Create a storage account
az storage account create \
  --name mystorageaccount \
  --resource-group myResourceGroup \
  --location westeurope \
  --sku Standard_LRS
```

**My notes:**
> _(fill in after completing the project)_

---

## Key Takeaways

- Hands-on practice is the fastest way to solidify Azure concepts
- SAS tokens are the right way to share storage access temporarily — never share account keys
- Azure CLI is essential for automation — get comfortable with it early
- Budgets + alerts are a must for any Azure environment to avoid bill surprises
- RBAC assignments at the right scope (not too broad, not too narrow) is a skill worth practicing

---

## Completed Projects

- [ ] Project 1 — Static website with Blob Storage
- [ ] Project 2 — Tags and locks
- [ ] Project 3 — Azure Functions endpoint
- [ ] Project 4 — Entra ID + RBAC
- [ ] Project 5 — Secure file sharing
- [ ] Project 6 — Cost guardrails
- [ ] Project 7 — Service Health alerts
- [ ] Project 8 — Cloud Shell + Azure CLI
