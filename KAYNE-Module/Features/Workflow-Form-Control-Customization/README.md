# Workflow Form Control Customization

**Purpose:** To enable specific business rules for user interface interaction within workflow-enabled forms, ensuring that controls (like buttons, fields) are appropriately visible, enabled, or mandatory based on the workflow's current state, user roles, or other business criteria.

## Overview

This feature provides custom logic to manage the behavior and appearance of controls on forms that are part of a workflow process in Dynamics 365 Finance & Operations.

- **Object Count:** 1
- **Cohesion Score:** 0.00

## Entry Points

- Forms that are part of a configured workflow process (e.g., Purchase Order, Expense Report, Journal forms) where this extension's logic is applied to their controls.

## Business Logic

The SysWorkflowFormControlsAKA_Extension class extends the standard framework for managing workflow-related form controls. It introduces custom business logic that dynamically adjusts the properties (e.g., visibility, enabled state, mandatory status) of controls on forms participating in a workflow. This logic is typically executed when a workflow form is initialized or when the workflow state changes, allowing for tailored user experiences. The 'AKA' suffix suggests this is a specific, potentially module- or client-specific, set of rules designed to meet unique business requirements for how users interact with workflow-driven forms.

## Objects in This Feature

| Object Name | Type | Extension | Description |
|-------------|------|-----------|-------------|
| [SysWorkflowFormControlsAKA_Extension](Objects/SysWorkflowFormControlsAKA_Extension.md) | AxClass |  |  |

---

*[← Back to Index](../../index.md)*
