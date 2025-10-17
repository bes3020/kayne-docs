# Intercompany Ledger Account Mapping

**Purpose:** To automate and correctly post intercompany ledger transactions by dynamically determining the appropriate ledger accounts in each participating legal entity based on predefined mappings, thereby simplifying intercompany reconciliation and improving financial data accuracy.

## Overview

This feature enhances the standard ledger posting process by providing a mechanism to map and resolve 'Also Known As' (AKA) accounts for intercompany transactions, ensuring accurate financial recording across legal entities.

- **Object Count:** 1
- **Cohesion Score:** 0.00

## Entry Points

- General Ledger > Chart of accounts > Main accounts (for AKA account configuration)
- General Ledger > Setup > Intercompany accounting (for intercompany setup)
- General Ledger > Journal entries > General journals (when posting intercompany transactions)

## Business Logic

The LedgerTransAccountAKA_Extension class likely extends the core logic responsible for determining and validating ledger accounts during the posting of financial transactions. Specifically, it would contain logic to identify transactions that require intercompany account resolution. When an intercompany scenario is detected, the class would consult predefined 'Also Known As' (AKA) account mappings to substitute the original account with the correct corresponding account for the target legal entity. This ensures that a transaction originating in one company, but impacting another, is recorded using the appropriate chart of accounts and financial dimensions in both entities. This automated mapping is crucial for maintaining data integrity, streamlining intercompany reconciliation, and facilitating accurate consolidated financial reporting.

## Objects in This Feature

| Object Name | Type | Extension | Description |
|-------------|------|-----------|-------------|
| [LedgerTransAccountAKA_Extension](Objects/LedgerTransAccountAKA_Extension.md) | AxClass |  |  |

---

*[← Back to Index](../../index.md)*
