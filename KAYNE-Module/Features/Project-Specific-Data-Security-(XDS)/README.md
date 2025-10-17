# Project-Specific Data Security (XDS)

**Purpose:** To enhance data privacy and compliance by enforcing granular data access control, preventing unauthorized users from viewing sensitive or irrelevant project-related information within the system.

## Overview

This feature implements extensible data security (XDS) to restrict user access to data records based on project-specific values. It ensures that users can only view or modify data relevant to their assigned projects or scope.

- **Object Count:** 1
- **Cohesion Score:** 1.00

## Entry Points

- Security configuration (assigning XDS policies to roles)
- AKAXDSMyProjValues Setup Form (hypothetical form for managing values in the table, if applicable)

## Business Logic

The core business logic revolves around the application of Extensible Data Security (XDS) policies. The AKAXDSMyProjValues table serves as a crucial component, storing the specific criteria (e.g., project IDs, user-to-project mappings) that define what data a user is permitted to access. When a user interacts with data (e.g., viewing a list of projects, transactions), the associated XDS policy dynamically filters the records based on the values configured in AKAXDSMyProjValues for that user's context. This ensures that only data matching the user's authorized 'project values' is displayed, effectively segmenting data access and maintaining data integrity and confidentiality across the system. Management of the values in AKAXDSMyProjValues would typically involve administrators defining which users or roles are associated with which project values, thereby controlling the scope of their data visibility.

## Objects in This Feature

| Object Name | Type | Extension | Description |
|-------------|------|-----------|-------------|
| [AKAXDSMyProjValues](Objects/AKAXDSMyProjValues.md) | AxTable |  |  |

## Object Relationships

```mermaid
graph LR
    N_AKAXDSMyProjValues[AKAXDSMyProjValues]
    N_AKAXDSMyProjValues -->|TableReference| N_AKAXDSMyProjValues
    classDef table fill:#90EE90
    classDef form fill:#87CEEB
    classDef class fill:#FFD700
    classDef note fill:#F0F0F0
```


---

*[← Back to Index](../../index.md)*
