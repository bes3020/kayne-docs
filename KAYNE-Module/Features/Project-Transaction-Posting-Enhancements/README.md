# Project Transaction Posting Enhancements

**Purpose:** To enable organizations to implement specific accounting rules, validations, or data updates for project transactions that deviate from or enhance the standard system behavior, ensuring compliance with unique business requirements not covered by out-of-the-box functionality.

## Overview

This feature extends the standard project transaction posting process in Dynamics 365 Finance & Operations, allowing for custom business logic to be applied during the recording and financial update of project-related transactions.

- **Object Count:** 1
- **Cohesion Score:** 0.00

## Entry Points

- Posting of Project Hour Journals
- Posting of Project Expense Journals
- Posting of Project Item Journals
- Posting of Project Fee Journals
- Project Invoice Posting
- Timesheet Posting
- Expense Report Posting

## Business Logic

The ProjTransPostingAKA_Extension class intercepts or modifies the standard project transaction posting flow. Its methods would contain custom logic executed at various stages of the posting process, such as before, during, or after the creation of ledger entries or sub-ledger updates for project transactions. This could involve additional data validations, custom financial dimension derivations, updates to project-specific fields, integration with external systems, or the application of unique business rules for specific project types or transaction categories. The 'AKA' likely denotes the specific context or type of customization implemented within this extension, tailoring the posting behavior to meet particular business needs.

## Objects in This Feature

| Object Name | Type | Extension | Description |
|-------------|------|-----------|-------------|
| [ProjTransPostingAKA_Extension](Objects/ProjTransPostingAKA_Extension.md) | AxClass |  | <summary> Augmented class for table <c>ProjTran... |

---

*[← Back to Index](../../index.md)*
