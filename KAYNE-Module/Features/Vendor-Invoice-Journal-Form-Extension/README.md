# Vendor Invoice Journal Form Extension

**Purpose:** To customize and enhance the user experience and business logic for entering and managing vendor invoices through the journal interface, addressing specific organizational requirements or handling alternative identifiers (implied by 'AKA').

## Overview

This feature extends the standard functionality of the vendor invoice journal form, likely adding specific business logic or UI enhancements related to vendor invoice processing, potentially involving alternative identification or custom data points.

- **Object Count:** 1
- **Cohesion Score:** 0.00

## Entry Points

- Accounts payable > Journals > Invoices > Vendor invoice journal (form: LedgerJournalTransVendInvoice)

## Business Logic

The `LedgerJournalTransVendInvoiceFormAKA_Extension` class likely contains event handlers or methods that modify the behavior of the `LedgerJournalTransVendInvoice` form. This could include custom validation rules for vendor invoice lines, defaulting of specific fields, or logic to handle alternative vendor or invoice identifiers (the 'AKA' aspect). It aims to streamline or enforce specific business processes during the creation or modification of vendor invoice journal entries, ensuring data integrity and compliance with custom business rules.

## Objects in This Feature

| Object Name | Type | Extension | Description |
|-------------|------|-----------|-------------|
| [LedgerJournalTransVendInvoiceFormAKA_Extension](Objects/LedgerJournalTransVendInvoiceFormAKA_Extension.md) | AxClass |  |  |

---

*[← Back to Index](../../index.md)*
