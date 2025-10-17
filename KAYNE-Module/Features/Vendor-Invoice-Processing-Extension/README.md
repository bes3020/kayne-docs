# Vendor Invoice Processing Extension

**Purpose:** To address specific business requirements for vendor invoice management that are not covered by standard Dynamics 365 functionality, such as handling unique alternative invoice identifiers or implementing custom validation during the invoice lifecycle to ensure compliance with organizational policies.

## Overview

This feature extends the standard vendor invoice journal functionality, likely incorporating custom logic for alternative invoice identification, validation, or processing rules.

- **Object Count:** 1
- **Cohesion Score:** 0.00

## Entry Points

- Vendor Invoice Journal form (VendInvoiceJournal)
- Purchase Order Invoice forms
- Any process or integration that creates or modifies VendInvoiceJour records

## Business Logic

The `VendInvoiceJourAKA_Extension` class likely contains methods that hook into the lifecycle of a vendor invoice, extending the core `VendInvoiceJour` table's capabilities. This could involve custom validation logic executed when an invoice is created, updated, or posted, ensuring data integrity for specific fields related to an 'AKA' (Alternative Key) concept. For example, it might enforce uniqueness for a custom invoice reference, populate additional fields on the `VendInvoiceJour` table based on specific business rules, or implement custom matching logic against purchase orders or receipts using an alternative identifier. The class would override standard methods or introduce new ones to support these custom business rules, ensuring that vendor invoices are processed according to specific organizational requirements beyond the standard system functionality.

## Objects in This Feature

| Object Name | Type | Extension | Description |
|-------------|------|-----------|-------------|
| [VendInvoiceJourAKA_Extension](Objects/VendInvoiceJourAKA_Extension.md) | AxClass |  | <summary> Augmented class for the table <c>Vend... |

---

*[← Back to Index](../../index.md)*
