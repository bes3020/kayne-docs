# Ledger Journal Daily Form Customization

**Purpose:** To extend and adapt the core daily journal entry process in Dynamics 365 Finance & Operations, enabling specialized validations, data handling, or user experience improvements that are not available in the standard system.

## Overview

This feature provides custom enhancements and modifications to the standard Ledger Journal Daily Lines form, tailoring its functionality to specific business requirements.

- **Object Count:** 1
- **Cohesion Score:** 0.00

## Entry Points

- General ledger > Journal entries > General journals > Journal lines (LedgerJournalTransDaily form)

## Business Logic

The `LedgerJournalTransDailyFormDSAKA_Extension` class likely implements event handlers or method extensions on the `LedgerJournalTransDaily` form. This could involve adding custom validation rules for journal lines (e.g., specific account combinations, project validations, or budget checks), defaulting specific field values, integrating with other modules or external systems, or modifying the user interface and behavior of existing controls. The primary goal is to inject company-specific business logic into the daily journal entry process, ensuring data integrity and compliance with internal policies beyond standard D365 functionality, potentially streamlining data entry or enforcing complex business rules.

## Objects in This Feature

| Object Name | Type | Extension | Description |
|-------------|------|-----------|-------------|
| [LedgerJournalTransDailyFormDSAKA_Extension](Objects/LedgerJournalTransDailyFormDSAKA_Extension.md) | AxClass |  |  |

---

*[← Back to Index](../../index.md)*
