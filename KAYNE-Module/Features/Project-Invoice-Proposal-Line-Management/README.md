# Project Invoice Proposal Line Management

**Purpose:** To enhance the accuracy and efficiency of project billing by providing tailored logic for selecting, creating, and validating lines on project invoice proposals, ensuring compliance with project contracts and business-specific requirements.

## Overview

This feature extends and customizes the process of generating and managing individual billing lines for project invoice proposals within Dynamics 365 Finance & Operations.

- **Object Count:** 1
- **Cohesion Score:** 0.00

## Entry Points

- Form: ProjInvoiceProposalCreateLinesForm (accessed via Project Invoice Proposals list page or directly from a project)
- Menu Item: ProjInvoiceProposalCreateLines (or similar, which opens the form)

## Business Logic

The ProjInvoiceProposalCreateLinesFormAKA_Extension class introduces custom business logic to the standard form responsible for creating lines on project invoice proposals. This extension typically includes modifications to how project transactions (e.g., time, expenses, items) are selected and transformed into invoice proposal lines. This could involve applying specific filtering criteria, defaulting advanced billing parameters, implementing custom pricing or funding rules, or adding validation checks to ensure adherence to project contracts, funding limits, and customer-specific billing agreements. The goal is to streamline the proposal generation process and ensure that the resulting invoice proposal accurately reflects the services rendered and complies with all relevant billing terms.

## Objects in This Feature

| Object Name | Type | Extension | Description |
|-------------|------|-----------|-------------|
| [ProjInvoiceProposalCreateLinesFormAKA_Extension](Objects/ProjInvoiceProposalCreateLinesFormAKA_Extension.md) | AxClass |  | <summary> Augmented class for the form <c>ProjI... |

---

*[← Back to Index](../../index.md)*
