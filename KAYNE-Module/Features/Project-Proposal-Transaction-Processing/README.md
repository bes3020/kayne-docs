# Project Proposal Transaction Processing

**Purpose:** To provide custom or extended business logic for the temporary data used in project proposals, ensuring accurate estimates, calculations, or reporting before a project proposal is finalized or presented.

## Overview

This feature extends the core logic for handling temporary project proposal transactions within the Professional Services Automation (PSA) module, likely enhancing calculations or data preparation for project proposals.

- **Object Count:** 1
- **Cohesion Score:** 0.00

## Entry Points

- Project proposals form (ProjProposalTable)
- Project contracts form (ProjTable)
- Project management workspaces
- Reports related to project profitability or estimates

## Business Logic

The PSATmpProjProposalTransAKA_Extension class would contain methods that augment the standard processing of temporary project proposal transaction data. This could involve applying specific pricing rules, calculating estimated costs or revenues based on custom logic, populating additional fields for reporting, or performing data validations unique to a specific business requirement. It acts as a hook to inject custom logic into the project proposal generation or display process, ensuring that temporary data accurately reflects the desired business rules before being used for final proposal generation or reporting.

## Objects in This Feature

| Object Name | Type | Extension | Description |
|-------------|------|-----------|-------------|
| [PSATmpProjProposalTransAKA_Extension](Objects/PSATmpProjProposalTransAKA_Extension.md) | AxClass |  | <summary> Augmented class for the table <c>PSAT... |

---

*[← Back to Index](../../index.md)*
