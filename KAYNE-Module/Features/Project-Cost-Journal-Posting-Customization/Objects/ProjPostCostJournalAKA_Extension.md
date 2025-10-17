# AxClass: ProjPostCostJournalAKA_Extension

[← Back to Project Cost Journal Posting Customization](../README.md)

## Description

<summary> Augmented class for the calss <c>ProjPostCostJournal</c> </summary>

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| populateProjCostTrans |  | void | none |

## Declaration Code

```xpp

/// <summary>
/// Augmented class for the calss <c>ProjPostCostJournal</c>
/// </summary>
/// AKA_2730_ProjectAdjustmentTrackingID , apendli, 1-dec-2020
[ExtensionOf(classStr(ProjPostCostJournal))]
final class ProjPostCostJournalAKA_Extension
{
}

```

## Key Methods Source

### populateProjCostTrans

```xpp

    /// <summary>
    /// Assign tracking Id details to buffer projCostTrans
    /// </summary>
    /// <param name = "_multiplier">
    /// Integer
    /// </param>
    protected void populateProjCostTrans(int _multiplier)
    {
        next populateProjCostTrans(_multiplier);

        switch (buffer.TableId)
        {
            case tableNum(LedgerJournalTrans):

                if (!this.parmAdjustment())
                {
                    projCostTrans.AKATrackingID         = ledgerJournalTrans_Project.AKATrackingID ? ledgerJournalTrans_Project.AKATrackingID : ProjCostTrans.VoucherJournal;
                    projCostTrans.AKATrackingIDCompany  = ledgerJournalTrans_Project.AKATrackingIDCompany ? ledgerJournalTrans_Project.AKATrackingIDCompany : curExt();
                }
                else
                {
                    ProjCostTrans origProjCostTrans = ProjCostTrans::find(this.parmAdjRefTransId());
                    
                    projCostTrans.AKATrackingID         = origProjCostTrans.AKATrackingID;
                    projCostTrans.AKATrackingIDCompany  = origProjCostTrans.AKATrackingIDCompany;
                }

                break;
        }
    }


```

---

*Generated on 2025-10-17 15:42*
