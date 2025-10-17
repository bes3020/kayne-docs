# AxClass: LedgerJournalTrans_Project_FSAKA_Extension

[← Back to FSAKA Project Ledger Journal Processing](../README.md)

## Description

<summary> Eventhandler class for the class <c>LedgerJournalTrans_Project_FS_Extension</c> </summary>

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| LedgerJournalTrans_Project_FS_Extension_Post_initFromProjInvoiceCost | ✓ | void | none |

## Declaration Code

```xpp

/// <summary>
/// Eventhandler class for the class <c>LedgerJournalTrans_Project_FS_Extension</c>
/// </summary>
/// AKA_2730_ProjectAdjustmentTrackingID , apendli, 1-dec-2020
static final class LedgerJournalTrans_Project_FSAKA_Extension
{
}

```

## Key Methods Source

### LedgerJournalTrans_Project_FS_Extension_Post_initFromProjInvoiceCost

```xpp

    /// <summary>
    /// PostEventHandler for the method 'initFromProjInvoiceCost'
    /// </summary>
    /// <param name="args">
    /// args
    /// </param>
    [PostHandlerFor(classStr(LedgerJournalTrans_Project_FS_Extension), staticMethodStr(LedgerJournalTrans_Project_FS_Extension, initFromProjInvoiceCost))]
    public static void LedgerJournalTrans_Project_FS_Extension_Post_initFromProjInvoiceCost(XppPrePostArgs args)
    {
        ProjInvoiceCost             projInvoiceCost = args.getArg('_projInvoiceCost');
        LedgerJournalTrans_Project  ledgerJournalTrans_Project = args.getArg('_this');

        ledgerJournalTrans_Project.AKATrackingID        = projInvoiceCost.AKATrackingID;
        ledgerJournalTrans_Project.AKATrackingIDCompany = projInvoiceCost.AKATrackingIDCompany;
    }


```

---

*Generated on 2025-10-17 15:42*
