# Vendor Journal Inquiry and Filtering

**Purpose:** To enable users to efficiently search, view, and analyze specific vendor journal transactions, thereby supporting tasks such as reconciliation, auditing, and transaction tracking within the vendor ledger.

## Overview

This feature provides the underlying data query mechanism for retrieving and filtering vendor journal entries based on user-defined criteria.

- **Object Count:** 1
- **Cohesion Score:** 0.00

## Entry Points

- Forms displaying vendor journal data (e.g., 'Vendor journal lines' form)
- Reports related to vendor journals
- Data entities consuming vendor journal information

## Business Logic

The AKAVendJournalByUserQuery defines the data sources and relationships necessary to retrieve vendor journal information. It typically involves joining tables like LedgerJournalTable (for journal headers) and LedgerJournalTrans (for journal lines), specifically filtered for vendor-related transactions. The 'ByUserQuery' suffix indicates that this query is designed to accept dynamic filtering parameters from a user interface, allowing users to specify criteria such as journal number, vendor account, transaction date range, voucher number, or journal status. This enables targeted data retrieval for specific inquiries, reporting, or data analysis purposes, ensuring that users can quickly find and review relevant vendor journal entries.

## Objects in This Feature

| Object Name | Type | Extension | Description |
|-------------|------|-----------|-------------|
| [AKAVendJournalByUserQuery](Objects/AKAVendJournalByUserQuery.md) | AxQuery |  |  |

---

*[← Back to Index](../../index.md)*
