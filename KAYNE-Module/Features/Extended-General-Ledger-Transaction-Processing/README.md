# Extended General Ledger Transaction Processing

**Purpose:** To enable organizations to implement specific business rules, validations, or data enrichments on general ledger transaction lines, extending the standard system capabilities to meet unique accounting or integration requirements.

## Overview

This feature provides custom enhancements and logic for handling individual general ledger voucher transactions within Dynamics 365 Finance & Operations.

- **Object Count:** 1
- **Cohesion Score:** 0.00

## Entry Points

- General Ledger Journals (e.g., Daily journals, Vendor invoice journals, Customer payment journals)
- Subledger postings (e.g., Sales order invoicing, Purchase order product receipt/invoicing)
- Any process that creates or modifies LedgerVoucherTransObject instances

## Business Logic

The LedgerVoucherTransObjectAKA_Extension class extends the core LedgerVoucherTransObject, which represents a single line in a general ledger voucher. This extension allows for the injection of custom business logic, such as adding new fields, implementing specific validation rules, or modifying data during the creation, update, or posting of ledger transaction lines. The exact nature of the logic depends on the methods and properties extended, but its primary role is to customize the behavior of general ledger entries to accommodate unique business processes, ensuring that custom data is handled correctly and specific accounting rules are enforced at the transaction level.

## Objects in This Feature

| Object Name | Type | Extension | Description |
|-------------|------|-----------|-------------|
| [LedgerVoucherTransObjectAKA_Extension](Objects/LedgerVoucherTransObjectAKA_Extension.md) | AxClass |  |  |

---

*[← Back to Index](../../index.md)*
