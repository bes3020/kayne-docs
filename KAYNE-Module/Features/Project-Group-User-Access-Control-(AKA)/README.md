# Project Group User Access Control (AKA)

**Purpose:** To enhance project security by allowing administrators to define and enforce access restrictions or permissions for projects based on their assigned project group, leveraging a custom 'AKA' access ID.

## Overview

This feature extends project groups to include a reference to a specific user group access ID, enabling custom security and access control for projects.

- **Object Count:** 2
- **Cohesion Score:** 1.00

## Entry Points

- Project groups form (ProjGroup form) in Project Management and Accounting module

## Business Logic

The core logic of this feature involves extending the standard 'ProjGroup' table with a new field, 'AKA', which is an Extended Data Type (EDT) named 'AKAProjUserGroupAccessId'. This field is intended to store an identifier that links a project group to a specific user group access configuration. When a project is created or assigned to a project group, it implicitly inherits this 'AKAProjUserGroupAccessId'. Downstream business processes, forms, or reports would then utilize this ID to implement custom security checks, determining a user's permissions or visibility for projects belonging to that specific project group. This allows for a more granular and customized security model where access to project-related data and functions can be controlled at the project group level, beyond standard Dynamics 365 security roles.

## Objects in This Feature

| Object Name | Type | Extension | Description |
|-------------|------|-----------|-------------|
| [AKAProjUserGroupAccessId](Objects/AKAProjUserGroupAccessId.md) | AxEdt |  |  |
| [ProjGroup.AKA](Objects/ProjGroup.AKA.md) | AxTableExtension | ✓ |  |

## Object Relationships

```mermaid
graph LR
    N_AKAProjUserGroupAccessId[AKAProjUserGroupAccessId]
    N_ProjGroup_AKA[ProjGroup.AKA]
    N_ProjGroup_AKA -->|EdtReference| N_AKAProjUserGroupAccessId
    classDef table fill:#90EE90
    classDef form fill:#87CEEB
    classDef class fill:#FFD700
    classDef note fill:#F0F0F0
```


---

*[← Back to Index](../../index.md)*
