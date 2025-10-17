# Project Extensible Data Security (XDS) Management

**Purpose:** To enhance data security within the Project Management and Accounting module by applying XDS policies, ensuring that users only access project data they are authorized for, and providing mechanisms to track the application of these policies at runtime. This addresses the business need for stricter data governance and compliance for project-specific information.

## Overview

This feature implements and manages Extensible Data Security (XDS) policies specifically for project-related data, allowing for fine-grained control over data access and tracking its application.

- **Object Count:** 4
- **Cohesion Score:** 1.00

## Entry Points

- Project management and accounting > Setup > Project management and accounting parameters (via ProjParametersFormAKA_Extension)

## Business Logic

This feature implements and manages Extensible Data Security (XDS) specifically for project-related data within Dynamics 365 Finance & Operations. The AKAXDSProjMetadataProvider class is responsible for defining or retrieving the necessary metadata that underpins these XDS policies, outlining the rules for data access restrictions. The AKAXDSProjUtilities class acts as the core logic component, leveraging this metadata to apply and manage the XDS policies during runtime. A key aspect of this utility class is its interaction with the AKAXDSProjModelSecPolRuntimeTracking table, which is used to log and track the application and evaluation of these security policies, providing visibility into how data access is being enforced for projects. Configuration and administrative control over this XDS functionality are provided through the ProjParametersFormAKA_Extension, which extends the standard Project Management and Accounting parameters form, allowing users to set up, enable, or modify the project-specific data security rules. This comprehensive setup ensures robust data governance and compliance for sensitive project information.

## Objects in This Feature

| Object Name | Type | Extension | Description |
|-------------|------|-----------|-------------|
| [AKAXDSProjMetadataProvider](Objects/AKAXDSProjMetadataProvider.md) | AxClass |  |  |
| [AKAXDSProjUtilities](Objects/AKAXDSProjUtilities.md) | AxClass |  |  |
| [ProjParametersFormAKA_Extension](Objects/ProjParametersFormAKA_Extension.md) | AxClass |  |  |
| [AKAXDSProjModelSecPolRuntimeTracking](Objects/AKAXDSProjModelSecPolRuntimeTracking.md) | AxTable |  |  |

## Object Relationships

```mermaid
graph LR
    N_AKAXDSProjMetadataProvider[AKAXDSProjMetadataProvider]
    N_AKAXDSProjUtilities[AKAXDSProjUtilities]
    N_ProjParametersFormAKA_Extension[ProjParametersFormAKA_Extension]
    N_AKAXDSProjModelSecPolRuntimeTracking[AKAXDSProjModelSecPolRuntimeTracking]
    N_AKAXDSProjMetadataProvider -->|MethodCall| N_AKAXDSProjMetadataProvider
    N_AKAXDSProjUtilities -->|TableReference| N_AKAXDSProjModelSecPolRuntimeTracking
    N_AKAXDSProjUtilities -->|MethodCall| N_AKAXDSProjUtilities
    N_AKAXDSProjUtilities -->|MethodCall| N_AKAXDSProjMetadataProvider
    N_ProjParametersFormAKA_Extension -->|MethodCall| N_AKAXDSProjUtilities
    classDef table fill:#90EE90
    classDef form fill:#87CEEB
    classDef class fill:#FFD700
    classDef note fill:#F0F0F0
```


---

*[← Back to Index](../../index.md)*
