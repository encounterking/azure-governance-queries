# ðŸ“¦ 01 â€” Resource Inventory

Queries in this folder produce structured inventories of Azure resources and installed software. They are designed to support **asset management**, **configuration baseline**, and **lifecycle monitoring** activities under GRC frameworks including ISO 27001.

---

## Queries

### ARG-001 Â· `all-azure-resources.kql`
**Complete Azure Resource Inventory**

Returns one row per Azure resource across all subscriptions in the selected scope. Includes resource type, name, location, resource group, SKU, and tags.

**Use for:** Asset register population, subscription-wide resource discovery, tag compliance review.

---

### ARG-002 Â· `vm-infrastructure-baseline.kql`
**Azure Virtual Machine Infrastructure Baseline**

Returns one row per virtual machine with OS type, VM size, Azure region, and source image details (publisher, offer, SKU, version).

**Use for:** VM configuration baseline, OS inventory, image currency review, infrastructure exposure assessment.

---

### ARG-003 Â· `defender-software-inventory.kql`
**Complete Defender Software Inventory**

Extracts all software packages detected on Azure VMs by Microsoft Defender for Cloud. Returns vendor, software name, version, and end-of-support status per VM.

**Use for:** Software asset inventory, licence review, end-of-support pre-screening.

> **Note:** A single VM can return hundreds of package-level records. Apply filters as needed when exporting.

---

### ARG-004 Â· `eos-eol-software.kql`
**End-of-Support / End-of-Life Software Detection**

Filters Defender software inventory to surface only components with a non-empty `endOfSupportStatus`. Includes pre-populated **finding write-up**, **suggested remediation**, and **validation guidance** fields â€” ready to paste directly into a risk register or audit finding.

**Use for:** EOS/EOL risk identification, audit evidence, risk register entries, remediation planning.

---

## Data Handling

- Export results only to your **approved evidence storage location**
- Do **not** commit CSV exports, screenshots, or subscription identifiers to this repository
- Results are scoped to your selected subscriptions and your Azure RBAC permissions

---

## Prerequisites

| Query | Requirement |
|-------|------------|
| ARG-001, ARG-002 | Reader role on target subscriptions |
| ARG-003, ARG-004 | Reader role + Microsoft Defender for Cloud enabled on VMs |
