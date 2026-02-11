# Azure Operations: Governance & Cost Management

Documenting operational controls for enterprise cloud environments.

## 1. Governance & Compliance
**Objective:** Enforce internal standards and regulatory compliance automatically.
*   **Resource Locks:** Configured `CanNotDelete` locks on critical production resource groups to prevent accidental data loss.
*   **Azure Policy:** Understanding how to enforce tagging rules (e.g., requiring a "CostCenter" tag on all new resources) for audit trails.

## 2. Cost Management (FinOps)
**Objective:** Monitoring cloud spend to ensure ROI and prevent budget overruns.
*   **CapEx vs. OpEx:** Transitioning from upfront hardware costs (CapEx) to consumption-based operating costs (OpEx).
*   **Budgets & Alerts:** Configuring thresholds (e.g., "Alert me when 80% of budget is reached") to proactively manage client spend.
*   **TCO (Total Cost of Ownership):** Analyzing the long-term cost savings of cloud migration vs. on-premise data centers.

## 3. Virtual Machine Deployment & Lifecycle Management
**Objective:** Deployed and secured a Windows Server 2019 VM to understand infrastructure components and attack surfaces.

- **Resource Grouping:** Created `IntroAzureRG` to manage the lifecycle of dependent resources (Network, Compute, Storage).
- **Network Security:** Configured Network Security Group (NSG) to allow inbound HTTP (Port 80) and RDP (Port 3389) traffic.
- **Web Server Configuration:** Installed IIS via PowerShell to simulate a production web workload.
- **Lifecycle Cleanup:** Executed full resource deletion to prevent "zombie resource" costs and adhere to FinOps principles.

---
_Status: Microsoft Learn Modules & Hands-on Labs Completed._
