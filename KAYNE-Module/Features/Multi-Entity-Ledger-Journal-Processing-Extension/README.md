# Multi-Entity Ledger Journal Processing Extension

**Purpose:** To facilitate and streamline the creation, validation, and posting of ledger journals that impact financial records across different legal entities within a single Dynamics 365 Finance & Operations instance, ensuring proper accounting and balancing.

## Overview

This feature extends the standard ledger journal functionality to support and enhance scenarios involving multiple legal entities, likely for intercompany or cross-company transactions.

- **Object Count:** 1
- **Cohesion Score:** 0.00

## Entry Points

- General ledger > Journal entries > General journals (Form: LedgerJournalTable)
- General ledger > Journal entries > Daily journals (Form: LedgerJournalTransDaily)
- Related journal posting processes

## Business Logic

The LedgerJournalMultiEntityAKA_Extension class likely contains business logic that intercepts or augments standard ledger journal operations when dealing with transactions that span multiple legal entities. This could involve implementing specific validation rules for cross-entity journal lines, automating the generation of offsetting intercompany entries, managing financial dimensions or accounts unique to multi-entity postings, or modifying the user interface to improve the data entry experience for such journals. The primary goal is to ensure data integrity, compliance, and accurate financial reporting across all involved legal entities when a single journal entry affects more than one company.

## Objects in This Feature

| Object Name | Type | Extension | Description |
|-------------|------|-----------|-------------|
| [LedgerJournalMultiEntityAKA_Extension](Objects/LedgerJournalMultiEntityAKA_Extension.md) | AxClass |  |  |

---

*[← Back to Index](../../index.md)*
