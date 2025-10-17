# Vendor Invoice Status and Details Inquiry

**Purpose:** To enable users to efficiently inquire about the status and details of vendor invoices, facilitating tracking, reconciliation, and auditing of vendor payment processes.

## Overview

This feature provides a consolidated view of vendor invoice information, encompassing general details, open journal entries, and posted journal entries for comprehensive tracking.

- **Object Count:** 4
- **Cohesion Score:** 1.00

## Entry Points

- Likely consumed by a custom form (e.g., 'AKA Vendor Invoice Inquiry') or a report that utilizes AKAVendInvoiceQuery.

## Business Logic

The core business logic centers on aggregating and presenting a holistic view of vendor invoices. The AKAVendInvoiceQuery serves as the central mechanism, joining data from three specialized views: AKAVendInvoiceInfoView (providing general invoice header and line details), AKAVendInvoiceOpenJournalView (displaying invoices that are still in a pending or unposted state within journals), and AKAVendInvoicePostedJournalView (showing invoices that have been finalized and posted to the ledger). This structure allows for a complete lifecycle view of a vendor invoice, enabling users to quickly ascertain an invoice's current status and access all relevant details, whether it's still being processed or has already been accounted for.

## Objects in This Feature

| Object Name | Type | Extension | Description |
|-------------|------|-----------|-------------|
| [AKAVendInvoiceQuery](Objects/AKAVendInvoiceQuery.md) | AxQuery |  |  |
| [AKAVendInvoiceInfoView](Objects/AKAVendInvoiceInfoView.md) | AxView |  |  |
| [AKAVendInvoiceOpenJournalView](Objects/AKAVendInvoiceOpenJournalView.md) | AxView |  |  |
| [AKAVendInvoicePostedJournalView](Objects/AKAVendInvoicePostedJournalView.md) | AxView |  |  |

## Object Relationships

```mermaid
graph LR
    N_AKAVendInvoiceQuery[AKAVendInvoiceQuery]
    N_AKAVendInvoiceInfoView[AKAVendInvoiceInfoView]
    N_AKAVendInvoiceOpenJournalView[AKAVendInvoiceOpenJournalView]
    N_AKAVendInvoicePostedJournalView[AKAVendInvoicePostedJournalView]
    N_AKAVendInvoiceQuery -->|FormDataSource| N_AKAVendInvoicePostedJournalView
    N_AKAVendInvoiceQuery -->|FormDataSource| N_AKAVendInvoiceInfoView
    N_AKAVendInvoiceQuery -->|FormDataSource| N_AKAVendInvoiceOpenJournalView
    classDef table fill:#90EE90
    classDef form fill:#87CEEB
    classDef class fill:#FFD700
    classDef note fill:#F0F0F0
```


---

*[← Back to Index](../../index.md)*
