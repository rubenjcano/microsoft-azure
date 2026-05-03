# ☁️ Cloud Concepts

> 📖 Based on: [Microsoft Learn — Describe Cloud Concepts](https://learn.microsoft.com/en-us/training/paths/microsoft-azure-fundamentals-describe-cloud-concepts/)
> Part 1 of 4 in the Azure Fundamentals series (AZ-900)

---

## Module 1 — What is Cloud Computing?

Cloud computing is the delivery of computing services — servers, storage, databases, networking, software, analytics — over the internet ("the cloud"), on demand and with pay-as-you-go pricing. Instead of owning physical hardware, you rent what you need from a cloud provider like Microsoft Azure.

### Shared Responsibility Model

Not everything in the cloud is managed by the provider. Responsibility is split depending on what service you use:

| Responsibility | On-premises | IaaS | PaaS | SaaS |
|---|---|---|---|---|
| Data & access | You | You | You | You |
| Application | You | You | You | Provider |
| Runtime / OS | You | You | Provider | Provider |
| Hardware / network | You | Provider | Provider | Provider |

**Rule of thumb:** the more managed the service, the more the provider handles.

### Cloud Models

| Model | Description | When to use |
|---|---|---|
| **Public** | Resources owned and operated by a third-party provider (Azure, AWS, GCP), shared across customers | Most workloads, fast deployment, no hardware costs |
| **Private** | Cloud infrastructure dedicated exclusively to one organization, on-premises or hosted | Strict compliance, sensitive data |
| **Hybrid** | Combination of public and private, connected together | Gradual migration, keeping some workloads on-prem |
| **Multi-cloud** | Using services from more than one cloud provider | Avoid vendor lock-in, best-of-breed services |

### Consumption-Based Model

Traditional IT has two types of costs:
- **CapEx (Capital Expenditure)** — upfront investment in physical infrastructure (servers, data centers). You own it.
- **OpEx (Operational Expenditure)** — pay for what you use, as you go. Cloud is OpEx.

The cloud shifts you from CapEx to OpEx: no upfront costs, you only pay for what you consume, and you can scale up or down at any time.

---

## Module 2 — Benefits of Cloud Services

### High Availability & Scalability
- **High availability** means the service keeps running even when something fails. Azure guarantees uptime through SLAs (Service Level Agreements), typically 99.9%+.
- **Scalability** means you can adjust resources based on demand:
  - **Vertical scaling** — adding more power to an existing resource (bigger VM)
  - **Horizontal scaling** — adding more instances of a resource (more VMs)

### Reliability & Predictability
- **Reliability** — the cloud is designed to be resilient. Resources can be deployed across multiple regions so if one goes down, others keep running.
- **Predictability** — you can forecast both performance and costs. Azure tools like Cost Management help you plan and avoid surprises.

### Security & Governance
- **Security** — cloud providers offer tools to protect your data: encryption, firewalls, DDoS protection, identity management. You still control how they're applied.
- **Governance** — policies, auditing, and compliance templates help ensure your cloud resources follow company and regulatory rules.

### Manageability
Two dimensions of manageability in the cloud:

- **Management of the cloud** — scaling resources automatically, deploying from templates, monitoring health, receiving alerts.
- **Management in the cloud** — how you interact with your environment: via web portal, CLI, APIs, or PowerShell.

---

## Module 3 — Cloud Service Types

### IaaS — Infrastructure as a Service
The provider gives you the raw infrastructure: virtual machines, networking, storage. You manage everything on top of it (OS, runtime, apps, data).

- **Most flexible** — maximum control
- **Use cases:** lift-and-shift migrations, dev/test environments, custom configurations
- **Azure examples:** Azure Virtual Machines, Azure Virtual Network, Azure Blob Storage

### PaaS — Platform as a Service
The provider manages the infrastructure AND the underlying platform (OS, middleware, runtime). You focus only on your application and data.

- **Middle ground** — less management overhead, still customizable
- **Use cases:** building and deploying web apps, APIs, databases without managing servers
- **Azure examples:** Azure App Service, Azure SQL Database, Azure Data Factory, Azure Databricks

### SaaS — Software as a Service
The provider manages everything — infrastructure, platform, and the application itself. You just use it.

- **Least control** — but zero maintenance
- **Use cases:** email, collaboration tools, CRM
- **Azure examples:** Microsoft 365, Microsoft Teams, Dynamics 365

### Quick comparison

```
IaaS → you manage: OS, middleware, runtime, app, data
PaaS → you manage: app, data
SaaS → you manage: nothing (just use it)
```

---

## Key Takeaways

- Cloud = renting computing resources over the internet on a pay-as-you-go basis
- Responsibility is shared between you and the provider depending on the service type
- Public, private, hybrid, and multi-cloud each solve different problems
- Cloud shifts costs from CapEx (buy) to OpEx (pay as you use)
- The main benefits: availability, scalability, reliability, security, governance, manageability
- IaaS / PaaS / SaaS differ in how much the provider manages for you

---

## Open Questions

- [ ] What are the SLA differences between Azure services?
- [ ] When exactly does it make sense to choose private over public cloud?
- [ ] How does Azure handle failover across regions in practice?
