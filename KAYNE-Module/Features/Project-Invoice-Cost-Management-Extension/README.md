# Project Invoice Cost Management Extension

**Purpose:** To enable businesses to apply custom rules and calculations for project costs during the invoicing phase, ensuring that invoices accurately reflect specific cost components, adjustments, or reconciliation requirements beyond standard functionality.

## Overview

This feature extends the standard Dynamics 365 Finance & Operations project invoicing process to incorporate specialized handling and adjustments of project costs, potentially related to specific cost categories or reconciliation logic.

- **Object Count:** 1
- **Cohesion Score:** 0.00

## Entry Points

- Project invoices (form)
- Invoice proposals (form)
- Post invoice (process)

## Business Logic

The `ProjInvoiceCostAKA_Extension` class would contain custom business logic that hooks into the existing project invoicing framework. This logic could involve overriding or augmenting methods responsible for retrieving, calculating, validating, or posting project costs on an invoice. For instance, it might introduce specific cost allocation rules, apply unique markups or discounts based on cost types, or implement reconciliation logic to compare different cost values (e.g., actual vs. estimated, or different cost categories) before the invoice is finalized. The 'AKA' in the name suggests a focus on specific cost definitions or a comparison/adjustment mechanism, implying a need for specialized cost treatment during the project invoicing lifecycle.

## Objects in This Feature

| Object Name | Type | Extension | Description |
|-------------|------|-----------|-------------|
| [ProjInvoiceCostAKA_Extension](Objects/ProjInvoiceCostAKA_Extension.md) | AxClass |  | <summary> Augmented class for the table <c>Proj... |

---

*[← Back to Index](../../index.md)*
