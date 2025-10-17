# AxClass: VendInvoiceJourAKA_Extension

[← Back to Vendor Invoice Processing Extension](../README.md)

## Description

<summary> Augmented class for the table <c>VendInvoiceJour</c> </summary>

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| initFromVendTrans |  | void | none |
| AKATrackingIDJumpRef | ✓ | void | none |

## Declaration Code

```xpp

/// <summary>
/// Augmented class for the table <c>VendInvoiceJour</c>
/// </summary>
/// AKA_2730_ProjectAdjustmentTrackingID , apendli, 1-dec-2020
[ExtensionOf(tableStr(VendInvoiceJour))]
final class VendInvoiceJourAKA_Extension
{
}

```

## Key Methods Source

### initFromVendTrans

```xpp

    /// <summary>
    /// Assign tracking Id details for the table buffer
    /// </summary>
    /// <param name = "vendTrans">
    /// Table buffer
    /// </param>
    void initFromVendTrans(VendTrans vendTrans)
    {
        next initFromVendTrans(vendTrans);

        this.AKATrackingID          = vendTrans.AKATrackingID;
        this.AKATrackingIDCompany   = vendTrans.AKATrackingIDCompany;
    }


```

### AKATrackingIDJumpRef

```xpp

    /// <summary>
    /// Centralized jumpRef to open the journal lines form based on tracking Id
    /// </summary>
    /// <param name = "_trackingId">
    /// AKATRackingId
    /// </param>
    /// <param name = "_trackingIdCompany">
    /// AKATrackingId company
    /// </param>
    static void AKATrackingIDJumpRef(AKATrackingID _trackingId, AKATrackingIDCompany _trackingIdCompany)
    {
        Args                        args, transArgs;
        FormRun                     formRun, transFormRun;
        LedgerJournalTrans          ledgerJournalTrans;
        LedgerJournalTable          ledgerJournaltable;
        ;
        

        changecompany (_trackingIdCompany)
        {
            select firstonly ledgerJournalTrans
               where ledgerJournalTrans.Voucher == _trackingId;

            ledgerJournaltable = LedgerJournalTable::find(ledgerJournaltrans.JournalNum);
        }

        //Open form
        args = new Args();
        args.name(formStr(LedgerJournalTable));
        args.record(ledgerJournaltable);

        formRun = classfactory.formRunClass(args);
        formRun.init();
        
        LedgerJournalFormTable journalFormTable = formRun.journalForm();
        journalFormTable.journalTableData(JournalTableData::newTable(ledgerJournalTable));

        transArgs = new Args();
        transArgs.caller(formRun);
        transArgs.parm("TrackingIDJumpRef");

        if (ledgerJournaltable.JournalType == LedgerJournalType::Daily)
        {
            transArgs.name(formStr(LedgerJournalTransDaily));
        }
        else if (ledgerJournaltable.JournalType == LedgerJournalType::VendInvoiceRegister)
        {
            transArgs.name(formStr(LedgerJournalTransVendInvoice));
        }

// ... (truncated)
```

---

*Generated on 2025-10-17 15:42*
