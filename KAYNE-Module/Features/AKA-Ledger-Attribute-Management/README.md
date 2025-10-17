# AKA Ledger Attribute Management

**Purpose:** The primary business purpose is to provide enhanced traceability and granular attribute management for financial and project transactions. By extending core transaction tables with unique tracking identifiers, businesses can gain deeper insights, facilitate specific reporting requirements, and support internal control or compliance needs related to these custom attributes.

## Overview

This feature introduces a robust framework for assigning and managing custom tracking IDs and associated ledger attributes across various financial and project transactions within Dynamics 365 Finance & Operations.

- **Object Count:** 22
- **Cohesion Score:** 0.97

## Entry Points

- While no direct user interface objects (forms, menu items) are provided in the object list, it is highly probable that a dedicated form exists for the AKALedgerAttributeTrans table to manage the attribute definitions and their review status.
- The ProjTransAKA_Extension class suggests programmatic integration into project transaction posting and processing workflows.

## Business Logic

The core logic revolves around two new Extended Data Types, AKATrackingID and AKATrackingIDCompany, which are added to a wide array of critical transaction tables including CustTrans, VendTrans, ProjCostTrans, GeneralJournalAccountEntry, and various temporary project tables via table extensions. These EDTs serve as unique identifiers to link transactions to a central AKALedgerAttributeTrans table. This table stores detailed, custom attributes associated with each AKATrackingID and AKATrackingIDCompany combination, along with a AKALedgerReviewStatus to manage their lifecycle. The ProjTransAKA_Extension class is responsible for populating these tracking IDs during project transaction processing. Furthermore, several views (AKADefaultDimensionNameValueView, AKAGeneralJournalAccountEntryMaskView, AKAVendTransInvoicePaymentView) are defined to enable comprehensive reporting and analysis by joining these custom attributes with standard financial dimensions, general ledger entries, and vendor invoice/payment details, providing a holistic view of transactions enriched with AKA-specific attributes.

## Objects in This Feature

| Object Name | Type | Extension | Description |
|-------------|------|-----------|-------------|
| [ProjTransAKA_Extension](Objects/ProjTransAKA_Extension.md) | AxClass |  | <summary> Augmented class for the class <c>Proj... |
| [AKATrackingID](Objects/AKATrackingID.md) | AxEdt |  |  |
| [AKATrackingIDCompany](Objects/AKATrackingIDCompany.md) | AxEdt |  |  |
| [AKALedgerReviewStatus](Objects/AKALedgerReviewStatus.md) | AxEnum |  |  |
| [AKALedgerAttributeTrans](Objects/AKALedgerAttributeTrans.md) | AxTable |  |  |
| [AccountingSourceExplorerTmp.AKA](Objects/AccountingSourceExplorerTmp.AKA.md) | AxTableExtension | ✓ |  |
| [CustTrans.AKA](Objects/CustTrans.AKA.md) | AxTableExtension | ✓ |  |
| [GeneralJournalAccountEntry.AKA](Objects/GeneralJournalAccountEntry.AKA.md) | AxTableExtension | ✓ |  |
| [LedgerJournalTrans_Project.AKA](Objects/LedgerJournalTrans_Project.AKA.md) | AxTableExtension | ✓ |  |
| [LedgerPostingTransactionTmp.AKA](Objects/LedgerPostingTransactionTmp.AKA.md) | AxTableExtension | ✓ |  |
| [ProjCostTrans.AKA](Objects/ProjCostTrans.AKA.md) | AxTableExtension | ✓ |  |
| [ProjInvoiceCost.AKA](Objects/ProjInvoiceCost.AKA.md) | AxTableExtension | ✓ |  |
| [ProjProposalCost.AKA](Objects/ProjProposalCost.AKA.md) | AxTableExtension | ✓ |  |
| [ProjTransPosting.AKA](Objects/ProjTransPosting.AKA.md) | AxTableExtension | ✓ |  |
| [PSATmpProjProposalTrans.AKA](Objects/PSATmpProjProposalTrans.AKA.md) | AxTableExtension | ✓ |  |
| [TmpProjAdjustment.AKA](Objects/TmpProjAdjustment.AKA.md) | AxTableExtension | ✓ |  |
| [TmpProjAdjustmentCreate.AKA](Objects/TmpProjAdjustmentCreate.AKA.md) | AxTableExtension | ✓ |  |
| [VendInvoiceJour.AKA](Objects/VendInvoiceJour.AKA.md) | AxTableExtension | ✓ |  |
| [VendTrans.AKA](Objects/VendTrans.AKA.md) | AxTableExtension | ✓ |  |
| [AKADefaultDimensionNameValueView](Objects/AKADefaultDimensionNameValueView.md) | AxView |  |  |
| [AKAGeneralJournalAccountEntryMaskView](Objects/AKAGeneralJournalAccountEntryMaskView.md) | AxView |  |  |
| [AKAVendTransInvoicePaymentView](Objects/AKAVendTransInvoicePaymentView.md) | AxView |  |  |

## Object Relationships

```mermaid
graph LR
    N_ProjTransAKA_Extension[ProjTransAKA_Extension]
    N_AKATrackingID[AKATrackingID]
    N_AKATrackingIDCompany[AKATrackingIDCompany]
    N_AKALedgerReviewStatus[AKALedgerReviewStatus]
    N_AKALedgerAttributeTrans[AKALedgerAttributeTrans]
    N_AccountingSourceExplorerTmp_AKA[AccountingSourceExplorerTmp.AKA]
    N_CustTrans_AKA[CustTrans.AKA]
    N_GeneralJournalAccountEntry_AKA[GeneralJournalAccountEntry.AKA]
    N_LedgerJournalTrans_Project_AKA[LedgerJournalTrans_Project.AKA]
    N_LedgerPostingTransactionTmp_AKA[LedgerPostingTransactionTmp.AKA]
    N_ProjCostTrans_AKA[ProjCostTrans.AKA]
    N_ProjInvoiceCost_AKA[ProjInvoiceCost.AKA]
    N_ProjProposalCost_AKA[ProjProposalCost.AKA]
    N_ProjTransPosting_AKA[ProjTransPosting.AKA]
    N_PSATmpProjProposalTrans_AKA[PSATmpProjProposalTrans.AKA]
    N_TmpProjAdjustment_AKA[TmpProjAdjustment.AKA]
    N_TmpProjAdjustmentCreate_AKA[TmpProjAdjustmentCreate.AKA]
    N_VendInvoiceJour_AKA[VendInvoiceJour.AKA]
    N_VendTrans_AKA[VendTrans.AKA]
    N_AKADefaultDimensionNameValueView[AKADefaultDimensionNameValueView]
    N_ProjTransAKA_Extension -->|TableReference| N_AKATrackingID
    N_ProjTransAKA_Extension -->|TableReference| N_AKATrackingIDCompany
    N_AKALedgerAttributeTrans -->|EdtReference| N_AKATrackingID
    N_AKALedgerAttributeTrans -->|EdtReference| N_AKATrackingIDCompany
    N_AccountingSourceExplorerTmp_AKA -->|EnumReference| N_AKALedgerReviewStatus
    N_AccountingSourceExplorerTmp_AKA -->|EdtReference| N_AKATrackingID
    N_AccountingSourceExplorerTmp_AKA -->|EdtReference| N_AKATrackingIDCompany
    N_CustTrans_AKA -->|EdtReference| N_AKATrackingIDCompany
    N_CustTrans_AKA -->|EdtReference| N_AKATrackingID
    N_GeneralJournalAccountEntry_AKA -->|RelationRefe...| N_AKALedgerAttributeTrans
    N_LedgerJournalTrans_Project_AKA -->|EdtReference| N_AKATrackingIDCompany
    N_LedgerJournalTrans_Project_AKA -->|EdtReference| N_AKATrackingID
    N_LedgerPostingTransactionTmp_AKA -->|RelationRefe...| N_AKALedgerAttributeTrans
    N_ProjCostTrans_AKA -->|RelationRefe...| N_AKADefaultDimensionNameValueView
    N_ProjCostTrans_AKA -->|EdtReference| N_AKATrackingID
    N_ProjCostTrans_AKA -->|EdtReference| N_AKATrackingIDCompany
    N_ProjInvoiceCost_AKA -->|EdtReference| N_AKATrackingIDCompany
    N_ProjInvoiceCost_AKA -->|EdtReference| N_AKATrackingID
    N_ProjProposalCost_AKA -->|EdtReference| N_AKATrackingIDCompany
    N_ProjProposalCost_AKA -->|EdtReference| N_AKATrackingID
    N_ProjTransPosting_AKA -->|EdtReference| N_AKATrackingID
    N_ProjTransPosting_AKA -->|EdtReference| N_AKATrackingIDCompany
    N_PSATmpProjProposalTrans_AKA -->|EdtReference| N_AKATrackingIDCompany
    N_PSATmpProjProposalTrans_AKA -->|EdtReference| N_AKATrackingID
    N_TmpProjAdjustment_AKA -->|EdtReference| N_AKATrackingIDCompany
    N_TmpProjAdjustment_AKA -->|EdtReference| N_AKATrackingID
    N_TmpProjAdjustmentCreate_AKA -->|EdtReference| N_AKATrackingIDCompany
    N_TmpProjAdjustmentCreate_AKA -->|EdtReference| N_AKATrackingID
    N_VendInvoiceJour_AKA -->|EdtReference| N_AKATrackingIDCompany
    N_VendInvoiceJour_AKA -->|EdtReference| N_AKATrackingID
    More["...and 2 more objects"]:::note
    classDef table fill:#90EE90
    classDef form fill:#87CEEB
    classDef class fill:#FFD700
    classDef note fill:#F0F0F0
```


---

*[← Back to Index](../../index.md)*
