# Customer/Vendor Voucher Alias Management

**Purpose:** To provide a flexible way to reference and identify customer and vendor vouchers using an 'Also Known As' (AKA) identifier, facilitating easier cross-referencing, integration with external systems, or specific internal reporting requirements that go beyond the standard voucher numbering sequence.

## Overview

This feature extends the standard customer and vendor voucher functionality by introducing and managing alternative identifiers or aliases for these financial transactions.

- **Object Count:** 1
- **Cohesion Score:** 0.00

## Entry Points

- Customer Voucher Inquiry forms (e.g., CustVoucher)
- Vendor Voucher Inquiry forms (e.g., VendVoucher)
- General Journal forms (for posting and viewing)
- Potentially a dedicated setup form for AKA definitions (if configurable)

## Business Logic

The `CustVendVoucherAKA_Extension` class suggests logic for handling alternative identifiers for customer and vendor vouchers. This could involve methods to retrieve, validate, or display these 'Also Known As' identifiers. The logic might extend existing voucher posting or inquiry processes to include the AKA field, allowing users to search by or view this alternative reference. It likely interacts with underlying tables (possibly a new one for AKA storage or an extension of existing voucher tables) to store the mapping between standard voucher IDs and their aliases. The primary goal is to enhance traceability and usability of financial vouchers by providing an additional, user-defined identifier.

## Objects in This Feature

| Object Name | Type | Extension | Description |
|-------------|------|-----------|-------------|
| [CustVendVoucherAKA_Extension](Objects/CustVendVoucherAKA_Extension.md) | AxClass |  |  |

---

*[← Back to Index](../../index.md)*
