# 🔧 Azure Management and Governance

> 📖 Based on: [Microsoft Learn — Describe Azure Management and Governance](https://learn.microsoft.com/en-us/training/paths/describe-azure-management-governance/)
> Part 3 of 4 in the Azure Fundamentals series (AZ-900)

---

## Module 1 — Cost Management in Azure

### What drives Azure costs?

- **Resource type** — some resources cost more than others
- **Consumption** — pay-as-you-go vs reserved capacity
- **Region** — prices vary by geography
- **Bandwidth** — data leaving Azure (egress) is charged; data coming in (ingress) is usually free
- **Subscriptions** — different subscription types may have different pricing

### Saving Money

| Option | How it works |
|---|---|
| **Reserved Instances** | Commit to 1 or 3 years upfront — up to 72% savings vs pay-as-you-go |
| **Spot VMs** | Use unused Azure capacity at a large discount — can be evicted at any time |
| **Hybrid Benefit** | Use existing on-prem Windows Server or SQL Server licenses in Azure |
| **Dev/Test pricing** | Discounted rates for non-production workloads |

### Tools

- **Azure Pricing Calculator** — estimate the cost of a new architecture before you build it. [Try it here](https://azure.microsoft.com/en-us/pricing/calculator/)
- **Total Cost of Ownership (TCO) Calculator** — compare on-premises costs vs Azure. Useful to justify cloud migration. [Try it here](https://azure.microsoft.com/en-us/pricing/tco/calculator/)
- **Azure Cost Management** — monitor actual spending, set budgets, and create alerts when you're close to the limit. Also available in the Azure portal.

### Tags
Tags are key-value pairs you attach to resources for organization and cost tracking.

```
Environment = Production
Team = DataEngineering
CostCenter = Analytics
```

You can use tags to filter the Cost Management dashboard and see exactly how much each team or project is spending.

---

## Module 2 — Governance and Compliance

### Azure Blueprints (being replaced by Deployment Stacks)
Package together policy assignments, role assignments, and ARM templates into a single repeatable unit. Useful for deploying consistent environments across multiple subscriptions.

### Azure Policy
Define rules that resources must follow. Policies can:
- **Audit** — flag non-compliant resources without blocking them
- **Deny** — prevent creation of non-compliant resources
- **Remediate** — automatically fix existing non-compliant resources

Example policies:
- "All storage accounts must use HTTPS"
- "VMs must be in a specific region"
- "All resources must have an `Environment` tag"

**Policy Initiatives** — a group of related policies applied together (e.g. "ISO 27001 compliance" initiative includes dozens of individual policies).

### Microsoft Purview
Data governance platform — gives a unified view of your data across on-premises, Azure, and other clouds. Key features:
- **Data Map** — catalog all your data assets
- **Data Catalog** — make data discoverable by teams
- **Data Lineage** — track where data came from and how it was transformed

Very relevant for data engineering — use it to document pipelines and enforce data classification.

### Resource Locks
Prevent accidental deletion or modification of critical resources:

| Lock Type | What it does |
|---|---|
| **Delete** | Can read and modify, but cannot delete |
| **ReadOnly** | Can only read — cannot modify or delete |

Locks apply to all users regardless of their RBAC role. Even an Owner cannot delete a locked resource without first removing the lock.

---

## Module 3 — Managing and Deploying Azure Resources

### Ways to interact with Azure

| Tool | Best for |
|---|---|
| **Azure Portal** | Visual management, exploring services, one-off tasks |
| **Azure CLI** | Scripting, automation, cross-platform (Windows/Mac/Linux) |
| **Azure PowerShell** | Scripting with cmdlets, Windows-heavy environments |
| **Cloud Shell** | Browser-based CLI/PowerShell — no local install needed |
| **Azure Mobile App** | Monitoring and basic management from your phone |

### Infrastructure as Code (IaC)

Instead of clicking through the portal, define your infrastructure in code — repeatable, version-controlled, and consistent.

- **ARM Templates (Azure Resource Manager)** — JSON-based. Azure's native IaC format. Verbose but very powerful.
- **Bicep** — a cleaner, simpler language that compiles down to ARM. Much easier to read and write than raw JSON.
- **Terraform** — open-source, multi-cloud IaC. Works with Azure, AWS, GCP. Very popular in the industry.

**Why IaC matters for data engineering:** deploying ADF pipelines, Databricks clusters, and storage accounts via code means environments are reproducible and can be deployed in minutes.

### Azure Arc
Extend Azure management to resources outside Azure — on-premises servers, other clouds (AWS, GCP), edge devices. Manage everything from a single control plane.

---

## Module 4 — Monitoring Tools in Azure

### Azure Advisor
Free, personalized recommendations to improve your Azure environment across 5 pillars:
- Reliability
- Security
- Performance
- Cost
- Operational Excellence

Think of it as Azure's built-in consultant — check it regularly.

### Azure Service Health
Three layers of health monitoring:

| Service | What it shows |
|---|---|
| **Azure Status** | Global Azure outages affecting all customers |
| **Service Health** | Outages affecting your specific subscriptions and regions |
| **Resource Health** | Health of your individual resources |

Set up alerts so you get notified when a service you depend on has an issue.

### Azure Monitor
Centralized monitoring platform — collects metrics and logs from all your Azure resources.

- **Metrics** — numerical data over time (CPU %, requests per second)
- **Logs** — detailed event data stored in Log Analytics workspace, queryable with KQL (Kusto Query Language)
- **Alerts** — trigger notifications or automated actions when a threshold is crossed
- **Application Insights** — APM (Application Performance Monitoring) for your apps — track requests, failures, dependencies

**For data engineers:** use Azure Monitor to set alerts on ADF pipeline failures, Databricks job durations, and storage account errors.

---

## Key Takeaways

- Always tag resources — it makes cost tracking and governance much easier
- Use Azure Policy to enforce compliance at scale automatically
- Resource Locks protect critical infrastructure from accidental deletion
- Prefer IaC (Bicep or Terraform) over manual portal deployments for repeatability
- Azure Monitor + Alerts is your first line of defense for catching pipeline failures
- Microsoft Purview is the governance layer on top of your data — important for data engineering

---

## Open Questions

- [ ] How do I write a basic Bicep template for an ADF pipeline?
- [ ] What KQL queries are most useful for monitoring ADF in Log Analytics?
- [ ] How does Microsoft Purview integrate with Azure Data Factory lineage?
