# AP Invoice Copy with New Date

**Purpose:** To efficiently generate new AP invoices based on existing templates, particularly when only the date needs to be adjusted, thereby reducing manual data entry and ensuring consistency for recurring or similar transactions.

## Overview

This feature enables users to create a new Accounts Payable invoice by copying an existing one, allowing for the specification of a new document or posting date for the duplicated invoice.

- **Object Count:** 1
- **Cohesion Score:** 1.00

## Entry Points

- Menu item (Action button) on an Accounts Payable invoice form or list page
- Dialog form for new date input (invoked by the controller)

## Business Logic

The AKAAPInvoiceCopyNewDateController class orchestrates the process of duplicating an Accounts Payable invoice. It typically takes an existing invoice as a source, presents a user interface (likely a dialog) to prompt for a new date (e.g., document date, invoice date, or posting date) for the new invoice. Upon user confirmation, it copies the relevant data from the original invoice's header and lines, applies the specified new date to the appropriate fields of the newly created invoice, and then persists this new invoice into the system. This process likely includes validation of the new date and ensures that all necessary related information (such as financial dimensions, tax details, and vendor information) is correctly transferred or re-evaluated for the new transaction.

## Objects in This Feature

| Object Name | Type | Extension | Description |
|-------------|------|-----------|-------------|
| [AKAAPInvoiceCopyNewDateController](Objects/AKAAPInvoiceCopyNewDateController.md) | AxClass |  | <summary> The <c>AKAAPInvoiceCopyNewDateControl... |

## Object Relationships

```mermaid
graph LR
    N_AKAAPInvoiceCopyNewDateController[AKAAPInvoiceCopyNewDateController]
    N_AKAAPInvoiceCopyNewDateController -->|MethodCall| N_AKAAPInvoiceCopyNewDateController
    N_AKAAPInvoiceCopyNewDateController -->|TableReference| N_AKAAPInvoiceCopyNewDateController
    classDef table fill:#90EE90
    classDef form fill:#87CEEB
    classDef class fill:#FFD700
    classDef note fill:#F0F0F0
```


---

*[← Back to Index](../../index.md)*
