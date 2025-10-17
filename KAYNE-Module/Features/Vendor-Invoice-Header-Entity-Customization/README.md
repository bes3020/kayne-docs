# Vendor Invoice Header Entity Customization

**Purpose:** To allow organizations to tailor the standard vendor invoice header data entity to meet specific business requirements, such as integrating custom data fields, enforcing unique validation rules, or implementing specialized data mapping during import/export processes.

## Overview

This feature extends the standard Vendor Invoice Header data entity, enabling custom fields, validations, or logic for vendor invoice data integration and management.

- **Object Count:** 1
- **Cohesion Score:** 0.00

## Entry Points

- Data Management Framework (DMF) for import/export operations
- OData APIs for external system integration
- Custom X++ integrations interacting with the VendorInvoiceHeaderEntity

## Business Logic

The VendorInvoiceHeaderEntityAKA_Extension class contains custom X++ logic that modifies or enhances the behavior of the standard VendorInvoiceHeaderEntity. This typically involves adding computed columns, overriding data mapping methods (e.g., mapEntityToDataSource, mapDataSourceToEntity) to handle custom fields, or implementing event handlers (e.g., postLoad, preInsert, validateWrite) to enforce specific business rules, perform data transformations, or integrate with other custom logic during the lifecycle of vendor invoice header data. The exact business logic is dependent on the specific customizations applied to the base entity's structure or operational flow.

## Objects in This Feature

| Object Name | Type | Extension | Description |
|-------------|------|-----------|-------------|
| [VendorInvoiceHeaderEntityAKA_Extension](Objects/VendorInvoiceHeaderEntityAKA_Extension.md) | AxClass |  | <summary> Extension class for the data entity <... |

---

*[← Back to Index](../../index.md)*
