# Project Transaction Posting Enhancement

**Purpose:** To tailor the standard project posting process to meet unique business requirements, such as enforcing specialized validation rules, applying custom accounting treatments, or integrating with other systems during the financial update of project transactions.

## Overview

This feature extends the core project posting functionality within Dynamics 365 Finance & Operations, introducing custom logic or modifications to how specific project-related financial transactions are processed and recorded.

- **Object Count:** 1
- **Cohesion Score:** 0.00

## Entry Points

- Posting project journals (e.g., hour journals, expense journals, item journals)
- Posting project invoices
- Running project estimates or WIP calculations
- Any system process that triggers project transaction posting

## Business Logic

The `ProjPostAKA_Extension` class likely utilizes Dynamics 365 Finance & Operations' extension capabilities, such as Chain of Command or event handlers, to inject custom logic into the project posting lifecycle. This could involve performing additional data validation specific to the 'AKA' context before a project transaction is posted, modifying financial dimensions, ledger accounts, or other financial attributes based on custom rules during the posting process, or updating custom fields on project transactions or related master data. It may also trigger external integrations or notifications upon successful project posting, or implement specific business logic for a particular type of project transaction or project accounting scenario not covered by standard functionality.

## Objects in This Feature

| Object Name | Type | Extension | Description |
|-------------|------|-----------|-------------|
| [ProjPostAKA_Extension](Objects/ProjPostAKA_Extension.md) | AxClass |  |  |

---

*[← Back to Index](../../index.md)*
