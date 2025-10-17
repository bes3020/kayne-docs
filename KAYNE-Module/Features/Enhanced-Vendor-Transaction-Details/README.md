# Enhanced Vendor Transaction Details

**Purpose:** To provide Accounts Payable users with additional information or specialized processing options directly within the Vendor Transactions form, streamlining specific workflows or ensuring compliance with unique business rules related to vendor financial activities.

## Overview

This feature extends the standard Vendor Transactions form (`VendTransForm`) in Dynamics 365 Finance & Operations, adding custom logic and potentially new data fields or actions.

- **Object Count:** 1
- **Cohesion Score:** 0.00

## Entry Points

- Accounts payable > Vendors > All vendors > (select vendor) > Transactions > Vendor transactions
- Accounts payable > Inquiries and reports > Vendor transactions > Vendor transactions (via menu item VendTrans)

## Business Logic

The `VendTransForm_AKA_Extension` class likely contains event handlers or new methods that augment the behavior of the `VendTransForm`. This could involve custom validation logic when creating or modifying vendor transactions, displaying calculated fields based on existing transaction data, integrating with external systems to fetch or update transaction-related information, or adding custom actions to process selected vendor transactions according to specific business rules. The exact logic would depend on the specific business requirement it addresses, but it operates within the context of displaying and managing individual vendor financial transactions, enhancing the user experience and data integrity.

## Objects in This Feature

| Object Name | Type | Extension | Description |
|-------------|------|-----------|-------------|
| [VendTransForm_AKA_Extension](Objects/VendTransForm_AKA_Extension.md) | AxClass |  |  |

---

*[← Back to Index](../../index.md)*
