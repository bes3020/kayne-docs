# Accounts Payable Invoice Duplication with Date Override

**Purpose:** The primary purpose is to streamline and expedite the creation of new AP invoices that are largely identical to existing ones but require a different date. This reduces manual data entry, minimizes errors, and is particularly useful for recurring invoices, corrections, or generating similar invoices for different accounting periods.

## Overview

This feature enables users to duplicate existing Accounts Payable invoices, providing an option to specify a new date for the copied invoice.

- **Object Count:** 1
- **Cohesion Score:** 0.00

## Entry Points

- Action button on the 'Pending vendor invoices' form (VendInvoiceInfoTable form)
- Potentially a custom menu item under Accounts Payable inquiries or periodic tasks
- API call if exposed as a data entity or service operation

## Business Logic

The `AKAAPInvoiceCopyNewDateService` class orchestrates the process of copying an Accounts Payable invoice. Its core logic involves retrieving an existing AP invoice (header and lines), then creating a new invoice record. During this creation, it copies most relevant data fields from the source invoice to the new one. A key aspect of its functionality is to accept and apply a user-defined 'new date' to the copied invoice, which could affect fields like the invoice date, document date, or accounting date. The service would also be responsible for ensuring that associated details, such as invoice lines, charges, and potentially tax calculations or payment terms, are correctly replicated and adjusted based on the new date, ensuring the integrity and validity of the newly generated AP invoice for further processing within Dynamics 365 Finance & Operations.

## Objects in This Feature

| Object Name | Type | Extension | Description |
|-------------|------|-----------|-------------|
| [AKAAPInvoiceCopyNewDateService](Objects/AKAAPInvoiceCopyNewDateService.md) | AxClass |  | <summary> This class is use to update the open ... |

---

*[← Back to Index](../../index.md)*
