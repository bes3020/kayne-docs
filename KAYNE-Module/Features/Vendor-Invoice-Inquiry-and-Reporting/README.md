# Vendor Invoice Inquiry and Reporting

**Purpose:** To offer a single, easily accessible source of truth for all vendor invoice data, enabling users to quickly find, analyze, and report on vendor invoices without needing to navigate multiple forms or perform complex data joins. This supports financial reconciliation, payment tracking, and audit processes.

## Overview

This feature provides a consolidated view of all vendor invoices, aggregating key information from various related tables to facilitate comprehensive inquiry and reporting.

- **Object Count:** 1
- **Cohesion Score:** 0.00

## Entry Points

- Menu items leading to custom inquiry forms (e.g., 'All Vendor Invoices Inquiry')
- Menu items leading to custom reports (e.g., 'Vendor Invoice Summary Report')
- Potentially consumed by data entities for external integrations or Power BI dashboards

## Business Logic

While the AKAVendInvoiceAllView itself is a data aggregation layer and does not contain executable business logic, it is a crucial component of the broader vendor invoice management process. The underlying business logic, which this view exposes, includes the creation and posting of vendor invoices, matching invoices to purchase orders and product receipts, tracking payment status, and potentially incorporating approval workflows. The view's 'logic' is in its definition: joining relevant tables (such as VendInvoiceInfoTable, VendInvoiceTrans, VendTable, PurchTable, and LedgerJournalTrans for payments) and potentially applying filters or calculated fields to present a holistic view of each vendor invoice, its lines, associated vendor, and payment status. This consolidated data is then used by forms and reports to provide insights into the financial obligations and payment history related to vendors.

## Objects in This Feature

| Object Name | Type | Extension | Description |
|-------------|------|-----------|-------------|
| [AKAVendInvoiceAllView](Objects/AKAVendInvoiceAllView.md) | AxView |  |  |

---

*[← Back to Index](../../index.md)*
