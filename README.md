# azure-governance-queries
Version-controlled Azure Resource Graph and Defender queries for infrastructure inventory, lifecycle monitoring and audit evidence.
Azure Governance Queries
This repository contains version-controlled Azure Resource Graph and Microsoft Defender for Cloud queries used for infrastructure inventory, software inventory, lifecycle monitoring and audit evidence.

Purpose
The queries support:

Azure resource inventory
Virtual-machine inventory
Microsoft Defender software inventory
End-of-support and end-of-life monitoring
Technology-component reporting
Infrastructure exposure reviews
ISO 27001 asset and configuration-management evidence
Information-handling rules
This repository contains query definitions only.

Do not commit:

Azure Resource Graph CSV exports
Defender software-inventory exports
Subscription or tenant identifiers in documentation
Credentials, secrets or access tokens
Internal screenshots
Audit evidence
Customer or personal information
How to use a query
Open Azure Resource Graph Explorer.
Select the approved directory and subscription scope.
Open the required .kql file from this repository.
Copy the query.
Paste it into Azure Resource Graph Explorer.
Run the query.
Store exported results only in the approved evidence location.
