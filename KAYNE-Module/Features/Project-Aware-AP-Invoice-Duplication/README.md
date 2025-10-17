# Project-Aware AP Invoice Duplication

**Purpose:** To efficiently generate new AP invoices based on existing templates, particularly for recurring project-related expenses or when similar invoices are needed for different periods or project categories, thereby reducing manual data entry and ensuring data consistency.

## Overview

This feature enables the duplication of existing Accounts Payable invoices, allowing for the assignment of a new invoice date and the specification of a project type for the newly created invoice.

- **Object Count:** 2
- **Cohesion Score:** 1.00

## Entry Points

- A custom dialog form or a button on an existing Accounts Payable invoice form (e.g., 'Pending vendor invoices' or 'Vendor invoice journal') that triggers the invoice duplication process.

## Business Logic

The `AKAAPInvoiceCopyNewDateContract` class serves as a data contract, defining the parameters necessary for the AP invoice duplication process. These parameters would typically include the identifier of the source AP invoice, the desired new invoice date, and a selection for the `AKA_ProjectType` enumeration. This `AKA_ProjectType` enum allows users to categorize the new invoice according to its associated project, potentially influencing subsequent processing, accounting dimensions, or approval workflows. The core logic, likely implemented in a separate controller or service class (not provided), would consume this contract, retrieve the details of the source invoice, and then create a new AP invoice record, copying relevant header and line information while applying the specified new date and project type. This mechanism streamlines the creation of similar invoices, especially for project-based accounting scenarios.

## Objects in This Feature

| Object Name | Type | Extension | Description |
|-------------|------|-----------|-------------|
| [AKAAPInvoiceCopyNewDateContract](Objects/AKAAPInvoiceCopyNewDateContract.md) | AxClass |  | <summary> Data Contract class for AP open invoi... |
| [AKA_ProjectType](Objects/AKA_ProjectType.md) | AxEnum |  |  |

## Object Relationships

```mermaid
graph LR
    N_AKAAPInvoiceCopyNewDateContract[AKAAPInvoiceCopyNewDateContract]
    N_AKA_ProjectType[AKA_ProjectType]
    N_AKAAPInvoiceCopyNewDateContract -->|TableReference| N_AKA_ProjectType
    classDef table fill:#90EE90
    classDef form fill:#87CEEB
    classDef class fill:#FFD700
    classDef note fill:#F0F0F0
```


---

*[← Back to Index](../../index.md)*
