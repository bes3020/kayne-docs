# Document Attachment View Enhancements

**Purpose:** To improve the user experience and functionality when viewing attached documents across various records in D365FO, possibly by providing specialized views, integrating with external document management systems, or handling specific document referencing scenarios.

## Overview

This feature extends the standard document attachment viewing capabilities in Dynamics 365 Finance & Operations, potentially offering alternative display methods or additional information for attached documents.

- **Object Count:** 1
- **Cohesion Score:** 0.00

## Entry Points

- DocuView form (standard document viewer)
- Any D365FO form or record that allows viewing of attached documents (e.g., Sales Order details, Purchase Order details, Journal entries, Master data forms)

## Business Logic

The `DocuViewExtensionAKA` class likely contains business logic to customize or enhance the standard document viewing process. This could involve overriding or extending methods on the `DocuView` form or related document management classes to alter how documents are retrieved, rendered, or interacted with. The 'AKA' suffix might suggest handling 'Also Known As' scenarios for documents, such as displaying alias names, linking to alternative document references, or providing different viewing options based on document type, context, or specific business rules. The class would hook into existing document management events or methods to inject its custom logic, ensuring a modified or extended experience when users access attached files.

## Objects in This Feature

| Object Name | Type | Extension | Description |
|-------------|------|-----------|-------------|
| [DocuViewExtensionAKA](Objects/DocuViewExtensionAKA.md) | AxClass |  |  |

---

*[← Back to Index](../../index.md)*
