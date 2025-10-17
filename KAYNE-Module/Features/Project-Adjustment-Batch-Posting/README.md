# Project Adjustment Batch Posting

**Purpose:** To ensure the accurate and efficient recording of corrections to project transactions, maintaining up-to-date project financials and enabling scheduled processing of these adjustments.

## Overview

This feature facilitates the automated processing and posting of project-related adjustments, such as cost or revenue corrections, in a batch-oriented manner.

- **Object Count:** 1
- **Cohesion Score:** 0.00

## Entry Points

- Menu item to initiate or schedule the 'Post project adjustments batch' (e.g., under Project management and accounting > Periodic tasks)
- Form for creating and managing project adjustment batches

## Business Logic

The AKAProjAdjustmentBatchPostTask class is a core component responsible for executing the posting of project adjustment batches. Its primary business logic involves identifying and retrieving unposted project adjustment batches, then iterating through the individual adjustments contained within each batch. For each adjustment, the class performs necessary validations to ensure data integrity and adherence to business rules. Subsequently, it generates and posts the corresponding financial and project transactions, which typically involves updating project cost and revenue figures, impacting the general ledger, and marking the adjustments as successfully posted. The class also handles error conditions, logs processing details, and updates the status of the batch job, ensuring that a large volume of adjustments can be processed efficiently and reliably in a background process.

## Objects in This Feature

| Object Name | Type | Extension | Description |
|-------------|------|-----------|-------------|
| [AKAProjAdjustmentBatchPostTask](Objects/AKAProjAdjustmentBatchPostTask.md) | AxClass |  |  |

---

*[← Back to Index](../../index.md)*
