# User-Specific Vendor Journal Integration

**Purpose:** To enable external systems, such as Power Apps or custom integrations, to access and manage vendor journal entries, facilitating scenarios where journal data needs to be viewed or processed based on the user responsible for the transaction.

## Overview

This feature provides an OData entity for integrating and managing vendor journal entries, specifically allowing for user-centric filtering or processing of these financial transactions.

- **Object Count:** 1
- **Cohesion Score:** 0.00

## Entry Points

- OData endpoint (e.g., /data/AKAVendJournalByUsers)
- Data Management Framework (DMF) import/export projects
- Power Apps
- Power BI

## Business Logic

The core business logic of this feature is encapsulated within the `AKAVendJournalByUserEntity` AxDataEntityView. This entity aggregates and exposes a structured view of vendor journal entries, likely joining data from underlying tables such as `LedgerJournalTable` and `LedgerJournalTrans`. The 'ByUser' aspect indicates that the entity incorporates logic to filter or associate these journal entries with specific users, potentially based on fields like `CreatedBy`, `ModifiedBy`, or a custom user assignment. This allows external applications to interact with vendor journals in a user-specific context, supporting workflows for user-assigned payment processing, invoice entry, or reconciliation, while leveraging D365's financial posting rules and ensuring data integrity.

## Objects in This Feature

| Object Name | Type | Extension | Description |
|-------------|------|-----------|-------------|
| [AKAVendJournalByUserEntity](Objects/AKAVendJournalByUserEntity.md) | AxDataEntityView |  |  |

---

*[← Back to Index](../../index.md)*
