# Financial Reports Data Security

**Purpose:** To ensure data confidentiality and compliance by preventing unauthorized users from viewing sensitive financial information, typically by filtering data based on legal entity, organizational unit, or user role.

## Overview

This feature implements a security policy to control and restrict user access to financial report data within Dynamics 365 Finance & Operations.

- **Object Count:** 1
- **Cohesion Score:** 0.00

## Entry Points

- All standard and custom financial reports (e.g., 'Trial Balance', 'Balance Sheet', 'Income Statement', 'Cash Flow Statement')
- Financial reporting workspaces and forms

## Business Logic

The AKAFinancialReportsCOMPPolicy is an X++ security policy designed to enforce data access restrictions on financial reports. It likely uses a query to filter records from financial reporting-related tables (e.g., GeneralJournalAccountEntry, MainAccount, DimensionAttributeValueCombination) based on specific criteria such as the user's assigned legal entities, departments, or other organizational hierarchies. This ensures that when a user generates or views a financial report, they only see data for which they have explicit permission, thereby maintaining data segregation and adhering to internal or external compliance requirements. The policy is applied automatically whenever a user attempts to access data covered by its scope.

## Objects in This Feature

| Object Name | Type | Extension | Description |
|-------------|------|-----------|-------------|
| [AKAFinancialReportsCOMPPolicy](Objects/AKAFinancialReportsCOMPPolicy.md) | AxSecurityPolicy |  |  |

---

*[← Back to Index](../../index.md)*
