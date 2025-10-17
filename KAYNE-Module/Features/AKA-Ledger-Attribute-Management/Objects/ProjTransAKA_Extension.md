# AxClass: ProjTransAKA_Extension

[← Back to AKA Ledger Attribute Management](../README.md)

## Description

<summary> Augmented class for the class <c>ProjTrans</c> </summary>

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| AKATrackingID |  | void | none |
| AKATrackingIDCompany |  | void | none |

## Declaration Code

```xpp

/// <summary>
/// Augmented class for the class <c>ProjTrans</c>
/// </summary>
/// AKA_2730_ProjectAdjustmentTrackingID , apendli, 1-dec-2020
[Extensionof(classStr(ProjTrans))]
final class ProjTransAKA_Extension
{
}

```

## Key Methods Source

### AKATrackingID

```xpp

    /// <summary>
    /// Finds the tracking Id
    /// </summary>
    /// <returns>
    /// AKATrackingId
    /// </returns>
    public AKATrackingID AKATrackingID()
    {
        LedgerJournalTrans          ledgerJournalTrans;
        LedgerJournalTrans_Project  ledgerJournalTrans_Project;
        AKATrackingID               trackingId;

        if (buffer.TableId == tablenum(LedgerJournalTrans))
        {
            ledgerJournalTrans = buffer;

            select firstonly AKATrackingID from LedgerJournalTrans_Project
            where ledgerJournalTrans.RecId == ledgerJournalTrans_Project.RefRecId;

            trackingId = LedgerJournalTrans_Project.AKATrackingID;

            if(!trackingId)
            {
                trackingId = ledgerJournalTrans.Voucher;
            }
        }

        else if (buffer.TableId == tablenum(projcostTrans))
        {
            ProjCostTrans               projCostTrans;
            projCostTrans = buffer;

            trackingId = projCostTrans.AKATrackingID;
        }
        else if (buffer.TableId == tablenum(ProjProposalCost))
        {
            ProjProposalCost projProposalCost;
            projProposalCost = buffer;

            trackingId = projProposalCost.AKATrackingID;
        }

        return trackingId;
    }


```

### AKATrackingIDCompany

```xpp

    /// <summary>
    /// Finds the tracking Id company
    /// </summary>
    /// <returns>
    /// AKATrackingIdCompany
    /// </returns>
    public AKATrackingIDCompany AKATrackingIDCompany ()
    {
        LedgerJournalTrans          ledgerJournalTrans;        
        LedgerJournalTrans_Project  ledgerJournalTrans_Project;
        AKATrackingIDCompany        trackingIdCompany;

        if (buffer.TableId == tablenum(LedgerJournalTrans))
        {
            ledgerJournalTrans = buffer;

            select firstonly AKATrackingIDCompany from LedgerJournalTrans_Project
            where ledgerJournalTrans.RecId == ledgerJournalTrans_Project.RefRecId;

            trackingIdCompany = LedgerJournalTrans_Project.AKATrackingIDCompany;

            if(!trackingIdCompany)
            {
                trackingIdCompany = ledgerJournalTrans.DataAreaId;
            }
        }
        else if (buffer.TableId == tablenum(projcostTrans))
        {
            ProjCostTrans               projCostTrans;
            projCostTrans = buffer;

            trackingIdCompany = projCostTrans.AKATrackingIDCompany;
        }
        else if (buffer.TableId == tablenum(ProjProposalCost))
        {
            ProjProposalCost projProposalCost;
            projProposalCost = buffer;

            trackingIdCompany = projProposalCost.AKATrackingIDCompany;
        }

        return trackingIdCompany;
    }


```

---

*Generated on 2025-10-17 15:42*
