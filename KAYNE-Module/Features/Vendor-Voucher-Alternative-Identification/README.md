# Vendor Voucher Alternative Identification

**Purpose:** To provide greater flexibility in identifying, linking, and processing vendor vouchers, especially in scenarios where multiple reference numbers or external system IDs are involved, thereby improving data accuracy and integration capabilities.

## Overview

This feature extends the standard vendor voucher processing by introducing mechanisms to manage and utilize alternative identifiers or references for vendor vouchers.

- **Object Count:** 1
- **Cohesion Score:** 0.00

## Entry Points

- Accounts payable > Invoices > Vendor invoices
- Accounts payable > Inquiries and reports > Voucher transactions
- Forms related to vendor invoice entry and posting (e.g., VendInvoiceInfoTable, LedgerJournalTrans)
- Potentially, integration points (APIs) if external systems are involved

## Business Logic

The VendVoucherAKA_Extension class likely contains logic to handle the storage, validation, and retrieval of alternative identifiers associated with vendor vouchers. This could involve adding new fields to existing vendor voucher tables (e.g., VendInvoiceInfoTable, LedgerJournalTrans) via table extensions, which this class would then interact with. It might implement custom validation rules for these alternative identifiers during voucher creation or posting, and provide methods to search for and link vendor vouchers using these alternative keys. Additionally, the class could override or extend standard methods related to voucher matching, reconciliation, or reporting to incorporate the 'AKA' logic, facilitating integration with external systems that use different reference numbers for the same financial transactions.

## Objects in This Feature

| Object Name | Type | Extension | Description |
|-------------|------|-----------|-------------|
| [VendVoucherAKA_Extension](Objects/VendVoucherAKA_Extension.md) | AxClass |  | <summary> Augmented class for the class <c>Vend... |

---

*[← Back to Index](../../index.md)*
