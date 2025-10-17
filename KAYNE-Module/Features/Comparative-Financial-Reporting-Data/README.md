# Comparative Financial Reporting Data

**Purpose:** To enable financial analysts and controllers to retrieve and analyze comparative financial data, facilitating performance evaluation, variance analysis, and informed decision-making.

## Overview

This feature provides the underlying data structures and logic for generating financial reports that involve comparisons, such as actuals versus budget or current period versus prior period.

- **Object Count:** 1
- **Cohesion Score:** 0.00

## Entry Points

- Menu items for standard SSRS financial reports (e.g., 'Trial Balance Comparison', 'Income Statement Comparison')
- Forms displaying comparative financial data
- Integration points for external reporting tools (e.g., Management Reporter, Power BI)

## Business Logic

The AKAFinancialReportsCOMPQuery defines the data selection criteria for comparative financial reports. It is designed to retrieve and structure financial data from the general ledger and potentially budget modules. The query likely includes joins to relevant tables such as GeneralJournalAccountEntry, DimensionAttributeValueCombination, and LedgerTrans, enabling the selection of financial dimensions, accounts, and transaction details. The 'COMP' in the name suggests it incorporates logic to fetch data for multiple scenarios (e.g., actuals, budget, prior year) or different reporting periods, allowing for side-by-side analysis within a single dataset. It would apply filtering based on legal entity, date ranges, and financial dimensions, and might include aggregation logic to summarize financial amounts for various reporting levels.

## Objects in This Feature

| Object Name | Type | Extension | Description |
|-------------|------|-----------|-------------|
| [AKAFinancialReportsCOMPQuery](Objects/AKAFinancialReportsCOMPQuery.md) | AxQuery |  |  |

---

*[← Back to Index](../../index.md)*
