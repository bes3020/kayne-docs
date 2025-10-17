# Alternate Ledger Account Configuration

**Purpose:** To provide a centralized mechanism within the General Ledger parameters for defining and controlling the behavior of alternate ledger accounts. This allows businesses to manage different representations or mappings of their standard ledger accounts for purposes such as specific reporting requirements, integration with external systems, or adherence to various accounting standards.

## Overview

This feature extends the core General Ledger parameters to include settings related to alternate ledger accounts, enabling flexible account mapping and usage within the system.

- **Object Count:** 1
- **Cohesion Score:** 0.00

## Entry Points

- General ledger parameters form (General ledger > Ledger setup > General ledger parameters)

## Business Logic

The `LedgerParametersAKA_Extension` class is an extension to the core `LedgerParameters` functionality, specifically targeting 'Also Known As' (AKA) or alternate ledger accounts. This class likely introduces new fields or methods to the `LedgerParameters` table and its associated form, allowing users to configure global settings related to alternate ledger accounts. The business logic within this class would handle the validation, storage, and retrieval of these specific parameters. This could include enabling or disabling the alternate account functionality, defining rules for how alternate accounts are used in transactions or reports, or specifying how they interact with the standard chart of accounts. The extension ensures that the system can adapt to diverse accounting and reporting needs by providing configurable options for managing alternate ledger account definitions.

## Objects in This Feature

| Object Name | Type | Extension | Description |
|-------------|------|-----------|-------------|
| [LedgerParametersAKA_Extension](Objects/LedgerParametersAKA_Extension.md) | AxClass |  |  |

---

*[← Back to Index](../../index.md)*
