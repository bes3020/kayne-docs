# AKA Ledger Access Configuration

**Purpose:** To provide a centralized setting within the General Ledger module for defining a user group or access ID that governs custom permissions, responsibilities, or feature availability related to financial operations.

## Overview

This feature allows the configuration of a specific user group access identifier within the General Ledger parameters, likely for custom access control or process designation.

- **Object Count:** 2
- **Cohesion Score:** 1.00

## Entry Points

- General ledger parameters form (via the General Ledger module menu)

## Business Logic

The core business logic revolves around the storage and retrieval of a custom user group access ID. An administrator configures this `AKAPeopleUserGroupAccessId` value on the General Ledger parameters form. Subsequently, other parts of the 'AKA' solution would read this parameter to enforce specific business rules. For instance, it might be used to determine if a user belongs to the designated group before allowing them to perform certain ledger transactions, approve journal entries, or access specific financial reports. This enables dynamic control over user permissions and workflow participation based on a globally defined ledger setting.

## Objects in This Feature

| Object Name | Type | Extension | Description |
|-------------|------|-----------|-------------|
| [AKAPeopleUserGroupAccessId](Objects/AKAPeopleUserGroupAccessId.md) | AxEdt |  |  |
| [LedgerParameters.AKA](Objects/LedgerParameters.AKA.md) | AxTableExtension | ✓ |  |

## Object Relationships

```mermaid
graph LR
    N_AKAPeopleUserGroupAccessId[AKAPeopleUserGroupAccessId]
    N_LedgerParameters_AKA[LedgerParameters.AKA]
    N_LedgerParameters_AKA -->|EdtReference| N_AKAPeopleUserGroupAccessId
    classDef table fill:#90EE90
    classDef form fill:#87CEEB
    classDef class fill:#FFD700
    classDef note fill:#F0F0F0
```


---

*[← Back to Index](../../index.md)*
