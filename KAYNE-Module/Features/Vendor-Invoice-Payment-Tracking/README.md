# Vendor Invoice Payment Tracking

**Purpose:** The primary purpose is to enable users to track the payment status of vendor invoices, reconcile vendor accounts, and generate reports or inquiries related to vendor payment activities. This helps in managing accounts payable efficiently, ensuring timely payments, and understanding outstanding liabilities.

## Overview

This feature provides a structured query to retrieve and analyze vendor transactions, specifically focusing on the relationship between vendor invoices and their corresponding payments.

- **Object Count:** 1
- **Cohesion Score:** 0.00

## Entry Points

- Custom Reports (e.g., SSRS reports based on this query)
- Custom Inquiry Forms (displaying data from this query)
- Data Entities (potentially consuming this query for integrations or Power BI)
- Classes (utilizing this query for specific business logic)

## Business Logic

The core business logic encapsulated by the AKAVendTransInvoicePaymentQuery involves joining and filtering vendor transaction data. It typically selects records from the VendTrans table, distinguishing between invoice and payment types. The query is designed to link payments to the specific invoices they settle, likely through tables like VendSettlement, to provide a comprehensive view of the payment lifecycle for each vendor invoice. This allows for detailed analysis of paid, partially paid, and outstanding invoices, potentially including details like payment dates, amounts, and settlement references. The query serves as a foundational data source for various analytical and reporting needs within accounts payable.

## Objects in This Feature

| Object Name | Type | Extension | Description |
|-------------|------|-----------|-------------|
| [AKAVendTransInvoicePaymentQuery](Objects/AKAVendTransInvoicePaymentQuery.md) | AxQuery |  |  |

---

*[← Back to Index](../../index.md)*
