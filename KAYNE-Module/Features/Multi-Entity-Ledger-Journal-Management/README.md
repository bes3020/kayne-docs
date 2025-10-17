# Multi-Entity Ledger Journal Management

**Purpose:** To enable the efficient creation, processing, and integration of financial journal entries that involve transactions between different legal entities within the same Dynamics 365 environment, supporting intercompany accounting and consolidated financial reporting.

## Overview

This feature extends the data entity for ledger journals to support scenarios involving multiple legal entities, facilitating intercompany transactions and centralized journal processing.

- **Object Count:** 1
- **Cohesion Score:** 0.00

## Entry Points

- Data Management Framework (DMF) for importing/exporting multi-entity ledger journals
- OData APIs for programmatic integration of journal data
- Standard Ledger Journal forms (e.g., General journal, Daily journals) when configured for intercompany or multi-entity postings

## Business Logic

The core business logic of this feature revolves around extending the data model for ledger journals to accommodate transactions spanning multiple legal entities. As an AxDataEntityViewExtension, it likely adds specific fields or modifies the structure of an existing data entity view related to ledger journals to expose or handle attributes necessary for multi-entity processing. This could include fields for identifying the originating and destination legal entities, intercompany account relationships, or specific dimensions required for cross-company postings. The extension supports the integration of journal entries that span multiple companies, allowing for centralized processing or automated creation of corresponding entries in related legal entities, which is crucial for accurate intercompany accounting, reconciliation, and ultimately, consolidated financial statements. It ensures that data operations (import/export) involving ledger journals can correctly handle and validate entries across different legal entities.

## Objects in This Feature

| Object Name | Type | Extension | Description |
|-------------|------|-----------|-------------|
| [LedgerJournalMultiEntity.AKA](Objects/LedgerJournalMultiEntity.AKA.md) | AxDataEntityViewExtension | ✓ |  |

---

*[← Back to Index](../../index.md)*
