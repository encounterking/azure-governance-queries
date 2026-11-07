# Azure Governance Queries

Version-controlled Azure Resource Graph and Microsoft Defender for Cloud queries for infrastructure inventory, lifecycle monitoring, and GRC audit evidence.

---

## Overview

This repository is a curated library of **KQL (Kusto Query Language)** queries designed to support Governance, Risk and Compliance (GRC) activities across Azure environments. Queries are written for **Azure Resource Graph Explorer** and **Microsoft Defender for Cloud** and are intended to be run directly â€” not automated or scheduled.

The queries help answer common GRC questions such as:
- *What Azure resources do we have across all subscriptions?*
- *Which virtual machines are running, and what OS/size are they?*
- *What software is installed on our VMs according to Defender?*
- *Are any components running past their end-of-support or end-of-life date?*

---

## Repository Structure

```
queries/
â””â”€â”€ 01-resource-inventory/     # Azure resource and VM inventory, software inventory, EOS/EOL detection
```

More query categories will be added over time (e.g. vulnerability management, policy compliance, access reviews).

---

## Query Categories

| Folder | Description |
|--------|-------------|
| [`01-resource-inventory`](./queries/01-resource-inventory/) | Full Azure resource inventory, VM baseline, Defender software inventory, end-of-support/end-of-life detection |

---

## How to Run a Query

1. Open [**Azure Resource Graph Explorer**](https://portal.azure.com/#view/HubsExtension/ArgQueryBlade) in the Azure Portal
2. Set your **subscription and directory scope** (top-left of the Explorer)
3. Open the relevant `.kql` file from this repository
4. **Copy** the query content (excluding the comment header)
5. **Paste** it into the Resource Graph Explorer query window
6. Click **Run query**
7. Export results to CSV only to your **approved evidence storage location**

> **âš ï¸ Important:** Query results are scoped to the subscriptions you select and limited to your Azure RBAC permissions. Always confirm scope before running.

---

## Data Handling Rules

This repository contains **query definitions only**. The following must never be committed:

- Azure Resource Graph CSV exports or query results
- Defender software inventory exports
- Subscription IDs, tenant IDs, or management group identifiers in documentation
- Credentials, secrets, access tokens, or API keys
- Internal screenshots or screen recordings
- Audit evidence or evidence packages
- Customer data or personal information

---

## GRC Use Cases

| Use Case | Relevant Queries |
|----------|-----------------|
| Asset inventory (ISO 27001 A.8) | `all-azure-resources.kql`, `vm-infrastructure-baseline.kql` |
| Software inventory | `defender-software-inventory.kql` |
| End-of-support / end-of-life monitoring | `eos-eol-software.kql` |
| Audit evidence generation | All queries â€” export results to approved evidence location |
| Infrastructure exposure review | `vm-infrastructure-baseline.kql`, `all-azure-resources.kql` |

---

## Prerequisites

| Requirement | Details |
|-------------|---------|
| Azure access | Reader role (minimum) on target subscriptions |
| Portal access | Access to [Azure Resource Graph Explorer](https://portal.azure.com/#view/HubsExtension/ArgQueryBlade) |
| Defender for Cloud | Required for `defender-software-inventory.kql` and `eos-eol-software.kql` |

---

## Query Index

| Query ID | File | Description |
|----------|------|-------------|
| ARG-001 | [`all-azure-resources.kql`](./queries/01-resource-inventory/all-azure-resources.kql) | Full inventory of all Azure resources across selected subscriptions |
| ARG-002 | [`vm-infrastructure-baseline.kql`](./queries/01-resource-inventory/vm-infrastructure-baseline.kql) | Virtual machine inventory including OS type, size, and image details |
| ARG-003 | [`defender-software-inventory.kql`](./queries/01-resource-inventory/defender-software-inventory.kql) | Software packages detected on VMs by Microsoft Defender for Cloud |
| ARG-004 | [`eos-eol-software.kql`](./queries/01-resource-inventory/eos-eol-software.kql) | Software flagged as end-of-support or end-of-life by Defender, with finding write-ups |

---

## Contributing

When adding new queries, follow these conventions:

- Place the query in the most relevant subfolder under `queries/`
- Use the filename format: `kebab-case-description.kql`
- Add a comment header block at the top of every `.kql` file:

```kql
// Query ID: ARG-XXX
// Name: Human-readable query name
//
// Purpose:
// Brief description of what this query returns and why it is useful.
//
// Important:
// Any caveats, scope limitations or permissions needed.
//
// Handling:
// Data handling instructions for the output.
```

- Update the Query Index table in this README
- Update the relevant folder `README.md`

---

## Licence

MIT License â€” see [LICENSE](./LICENSE) for full terms.

This project is open source. You are free to use, copy, modify, and distribute these queries, provided the original author is credited.
