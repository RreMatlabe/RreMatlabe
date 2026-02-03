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

*Status: Modules Completed via Microsoft Learn.*
