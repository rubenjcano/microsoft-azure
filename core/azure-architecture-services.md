# 🏗️ Azure Architecture and Services

> 📖 Based on: [Microsoft Learn — Describe Azure Architecture and Services](https://learn.microsoft.com/en-us/training/paths/azure-fundamentals-describe-azure-architecture-services/)
> Part 2 of 4 in the Azure Fundamentals series (AZ-900)

---

## Module 1 — Core Architectural Components of Azure

### Physical Infrastructure

Azure is built on a global network of datacenters, organized into:

- **Regions** — a geographic area containing one or more datacenters. When you deploy a resource, you choose a region (e.g. West Europe, East US). Always pick the region closest to your users.
- **Region Pairs** — every Azure region is paired with another region in the same geography (e.g. West Europe ↔ North Europe). If one goes down, the paired region takes over. This ensures business continuity.
- **Sovereign Regions** — isolated instances of Azure for government or country-specific compliance requirements (e.g. Azure Government for the US, Azure China).
- **Availability Zones** — physically separate datacenters within a single region, each with independent power, cooling, and networking. Deploying across zones protects you from datacenter-level failures.

### Management Infrastructure

How Azure organizes and manages resources:

- **Resources** — the basic building block. A VM, a storage account, a database — all are resources.
- **Resource Groups** — a logical container for resources. Every resource must belong to exactly one resource group. Deleting a resource group deletes everything in it.
- **Subscriptions** — a billing and access boundary. One account can have multiple subscriptions (e.g. one for dev, one for production).
- **Management Groups** — containers for multiple subscriptions, allowing you to apply governance policies at scale.

```
Management Groups
  └── Subscriptions
        └── Resource Groups
              └── Resources
```

---

## Module 2 — Azure Compute Services

Compute = running applications and workloads in the cloud.

### Virtual Machines (VMs)
Full control over an OS and everything running on it. You manage patching, scaling, and configuration. Best for lift-and-shift migrations or when you need a specific OS setup.

- **VM Scale Sets** — automatically create and manage a group of identical VMs that scale in/out based on demand.
- **Availability Sets** — group VMs across fault and update domains to protect from hardware failures and planned maintenance.

### Azure App Service
A fully managed platform for building and hosting web apps, APIs, and mobile backends. No server management — just deploy your code.
- Supports: .NET, Python, Java, Node.js, PHP, Ruby
- Built-in CI/CD, custom domains, autoscaling

### Azure Container Instances (ACI)
Run containers in Azure without managing any VMs. Fast, lightweight, good for short-lived tasks.

### Azure Kubernetes Service (AKS)
Managed Kubernetes — orchestrate and scale containerized applications. Azure handles the control plane; you manage your workloads.

### Azure Functions
Serverless compute — run small pieces of code triggered by events (HTTP request, timer, queue message). You only pay when the code runs.

### Azure Virtual Desktop
Cloud-hosted Windows desktop and apps. Users access it remotely from any device.

---

## Module 3 — Azure Networking Services

### Azure Virtual Network (VNet)
The foundation of networking in Azure. A VNet lets Azure resources communicate securely with each other, with on-premises environments, and with the internet.

- **Subnets** — divide a VNet into segments for better organization and security.
- **Peering** — connect two VNets so resources in each can communicate privately.

### Connectivity Options
| Option | What it does |
|---|---|
| **VPN Gateway** | Encrypts traffic between Azure and on-premises over the internet |
| **ExpressRoute** | Private, dedicated connection to Azure (not over the internet — faster and more reliable) |
| **Azure DNS** | Hosts your DNS domains in Azure |

### Protecting Network Traffic
- **Network Security Groups (NSGs)** — filter inbound and outbound traffic to resources using rules (allow/deny by port, protocol, IP).
- **Azure Firewall** — fully managed, stateful firewall for VNet traffic.
- **Azure DDoS Protection** — protects against distributed denial-of-service attacks.

---

## Module 4 — Azure Storage Services

### Storage Account Types

| Service | What it stores |
|---|---|
| **Blob Storage** | Unstructured data — files, images, videos, backups |
| **Azure Files** | Fully managed file shares (like a network drive in the cloud) |
| **Queue Storage** | Messages between app components (up to 64 KB per message) |
| **Table Storage** | NoSQL key-value data |
| **Disk Storage** | Managed disks for VMs |

### Blob Access Tiers
Choose based on how often you access the data:

| Tier | Use case | Cost |
|---|---|---|
| **Hot** | Frequently accessed data | Higher storage cost, lower access cost |
| **Cool** | Infrequently accessed (min 30 days) | Lower storage cost, higher access cost |
| **Cold** | Rarely accessed (min 90 days) | Even lower storage cost |
| **Archive** | Long-term backup (min 180 days) | Lowest storage cost, highest retrieval cost |

### Azure Data Lake Storage Gen2 (ADLS Gen2)
Built on top of Blob Storage with a hierarchical namespace — the go-to storage for big data analytics workloads in Azure. Used by ADF, Databricks, Synapse, and Fabric.

### Redundancy Options
How Azure keeps your data safe from hardware failure:

| Option | Copies | Scope |
|---|---|---|
| **LRS** (Locally Redundant Storage) | 3 | Same datacenter |
| **ZRS** (Zone Redundant Storage) | 3 | Different availability zones |
| **GRS** (Geo Redundant Storage) | 6 | Two regions |
| **GZRS** | 6 | Zones + regions |

---

## Module 5 — Azure Identity, Access, and Security

### Microsoft Entra ID (formerly Azure Active Directory)
Azure's cloud-based identity and access management service. It handles authentication (who you are) and authorization (what you can do).

- **Users** — individual accounts
- **Groups** — collections of users to assign permissions in bulk
- **Service Principals** — identities for applications and services (not humans)
- **Managed Identities** — automatically managed service principals for Azure resources. No passwords to manage — Azure handles it. Use this instead of storing credentials in code.

### Authentication Methods
- **SSO (Single Sign-On)** — log in once, access multiple apps
- **MFA (Multi-Factor Authentication)** — requires a second form of verification (phone, authenticator app)
- **Passwordless** — use biometrics or a device instead of a password

### Azure RBAC (Role-Based Access Control)
Control who can do what on which resource:
- **Role** — a collection of permissions (e.g. Reader, Contributor, Owner)
- **Scope** — where the role applies (management group, subscription, resource group, or resource)
- **Assignment** — attaching a role to a user/group/service principal at a scope

**Principle of least privilege** — always grant the minimum permissions needed.

### Zero Trust Model
Never assume trust — verify every request regardless of where it comes from. Key principles: verify explicitly, use least privilege access, assume breach.

### Microsoft Defender for Cloud
Unified security management — monitors your Azure resources for vulnerabilities and provides a security score with recommendations.

---

## Key Takeaways

- Azure organizes resources in a hierarchy: Management Groups → Subscriptions → Resource Groups → Resources
- Availability Zones and Region Pairs protect against failures at different levels
- Compute options range from full control (VMs) to zero management (Functions)
- ADLS Gen2 is the standard for big data storage in Azure
- Managed Identities are the best way to give Azure services access to other services — no credentials in code
- RBAC + least privilege is the foundation of Azure security

---

## Open Questions

- [ ] When should I use AKS vs ACI vs App Service?
- [ ] What is the difference between ADLS Gen2 and standard Blob Storage in practice?
- [ ] How does Managed Identity work end-to-end in an ADF pipeline?
