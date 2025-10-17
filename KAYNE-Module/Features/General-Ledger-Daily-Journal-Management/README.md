# General Ledger Daily Journal Management

**Purpose:** To provide enhanced or customized capabilities for users to create, modify, and post general ledger journal entries efficiently, ensuring data integrity and adherence to specific business rules within the daily journal process.

## Overview

This feature extends the standard functionality of the Daily Journal form in Dynamics 365 Finance & Operations, which is used for recording various general ledger transactions.

- **Object Count:** 1
- **Cohesion Score:** 0.00

## Entry Points

- General Ledger > Journal entries > Daily journal (Form: LedgerJournalTransDaily)

## Business Logic

The `LedgerJournalTransDailyFormAKA_Extension` class likely contains business logic that customizes the behavior of the `LedgerJournalTrans` lines within the Daily Journal form. This could involve event handlers for form controls, methods to override standard logic, or post-event handlers for data source operations. Specific functionalities might include custom validations before posting, defaulting specific account dimensions, integrating with external systems, or implementing unique calculation rules for journal lines. The extension aims to streamline the daily journal entry process and enforce specific organizational requirements beyond the standard system capabilities.

## Objects in This Feature

| Object Name | Type | Extension | Description |
|-------------|------|-----------|-------------|
| [LedgerJournalTransDailyFormAKA_Extension](Objects/LedgerJournalTransDailyFormAKA_Extension.md) | AxClass |  | <summary> Augmented class for the form <c>Ledge... |

---

*[← Back to Index](../../index.md)*
