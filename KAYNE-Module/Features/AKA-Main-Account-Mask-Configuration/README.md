# AKA Main Account Mask Configuration

**Purpose:** To maintain the integrity and consistency of the financial chart of accounts by standardizing the structure and validation of main account numbers, and to control access to viewing these critical financial setup details.

## Overview

This feature enables the definition and viewing of main account masks, which are used to enforce structural and validation rules for main accounts within the chart of accounts. The provided privilege specifically grants read-only access to these configurations.

- **Object Count:** 1
- **Cohesion Score:** 0.00

## Entry Points

- Main account masks form (e.g., accessible via General Ledger > Chart of accounts > Setup)

## Business Logic

The core business logic of this feature revolves around defining alphanumeric patterns (masks) that main account numbers must conform to. These masks specify the structure, length, and character types allowed for main accounts, ensuring consistency and preventing data entry errors. When main accounts are created or modified, the system validates the input against these active masks. This ensures that all main accounts adhere to predefined organizational standards, which is crucial for accurate financial reporting, analysis, and integration with other modules. The `AKAMainAccountMaskView` privilege specifically governs the ability to view these configured main account masks and their associated validation rules, without allowing modification.

## Objects in This Feature

| Object Name | Type | Extension | Description |
|-------------|------|-----------|-------------|
| [AKAMainAccountMaskView](Objects/AKAMainAccountMaskView.md) | AxSecurityPrivilege |  |  |

---

*[← Back to Index](../../index.md)*
