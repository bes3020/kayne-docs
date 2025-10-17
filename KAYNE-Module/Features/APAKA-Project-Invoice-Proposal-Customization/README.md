# APAKA Project Invoice Proposal Customization

**Purpose:** To enable the generation of project invoice proposals that adhere to unique business rules, data requirements, or calculation methodologies mandated by the APAKA customization, thereby ensuring accurate and compliant project billing.

## Overview

This feature extends the standard Project Invoice Proposal generation process within Dynamics 365 Finance & Operations to incorporate specific business logic and requirements for the APAKA module or client.

- **Object Count:** 1
- **Cohesion Score:** 0.00

## Entry Points

- Project management and accounting > Project invoices > Project invoice proposals (Form)
- Project management and accounting > Project invoices > Create invoice proposal (Menu Item)

## Business Logic

The `ProjInvoiceProposalGenAPAKA_Extension` class modifies the standard logic of the `ProjInvoiceProposalGen` class, which is responsible for creating project invoice proposals. As an extension, it likely uses event handlers or method extensions to inject custom code at various stages of the proposal generation process. This custom logic could involve altering the selection criteria for project transactions (e.g., hours, expenses, items), applying specific pricing or discount rules, populating additional custom fields on the invoice proposal header or lines, performing unique validations, or integrating with APAKA-specific data structures. The core objective is to tailor the out-of-the-box project invoice proposal functionality to meet the distinct business processes and data requirements defined by the APAKA customization.

## Objects in This Feature

| Object Name | Type | Extension | Description |
|-------------|------|-----------|-------------|
| [ProjInvoiceProposalGenAPAKA_Extension](Objects/ProjInvoiceProposalGenAPAKA_Extension.md) | AxClass |  | <summary> This class <c>ProjInvoiceProposalGenA... |

---

*[← Back to Index](../../index.md)*
