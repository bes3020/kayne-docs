# Project Ledger Accounting Extensions

**Purpose:** To enable unique accounting rules, calculations, or data processing for project-related financial transactions that are not covered by standard functionality, ensuring compliance with specific business or industry requirements.

## Overview

This feature provides custom extensions to the standard project ledger accounting processes in Dynamics 365 Finance & Operations, likely introducing specific business logic for project transaction handling.

- **Object Count:** 1
- **Cohesion Score:** 0.00

## Entry Points

- Project management and accounting > Projects > All projects (for project-specific data)
- Project management and accounting > Inquiries and reports > Project transactions (for viewing ledger entries)
- Project management and accounting > Setup > Posting > Ledger posting setup (if it affects how transactions post)
- Any form or process involved in creating or posting project transactions (e.g., timesheets, expense reports, item journals linked to projects)

## Business Logic

The `ProjLedgerAKA_Extension` class is an X++ extension that modifies or enhances the behavior of existing project ledger functionality. This typically involves overriding methods on base project ledger-related classes or tables, implementing event handlers, or adding new business logic. The class likely contains custom validations, calculations, or data manipulations that are applied during the posting or inquiry of project transactions. This could impact how project costs, revenues, or work-in-progress (WIP) are accounted for, potentially affecting ledger accounts, financial dimensions, or specific reporting requirements beyond standard D365 F&O capabilities.

## Objects in This Feature

| Object Name | Type | Extension | Description |
|-------------|------|-----------|-------------|
| [ProjLedgerAKA_Extension](Objects/ProjLedgerAKA_Extension.md) | AxClass |  | <summary> Augmented class for the class <c>Proj... |

---

*[← Back to Index](../../index.md)*
