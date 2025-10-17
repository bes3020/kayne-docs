# AxClass: VendVoucherAKA_Extension

[← Back to Vendor Voucher Alternative Identification](../README.md)

## Description

<summary> Augmented class for the class <c>VendVoucher</c> </summary>

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| initCustVendTrans |  | void | none |

## Declaration Code

```xpp

/// <summary>
/// Augmented class for the class <c>VendVoucher</c>
/// </summary>
/// AKA_2730_ProjectAdjustmentTrackingID , apendli, 1-dec-2020
[ExtensionOf(classStr(VendVoucher))]
final class VendVoucherAKA_Extension
{
}

```

## Key Methods Source

### initCustVendTrans

```xpp

     //<summary>
     //Assign tracking id details to vendTrans
     //</summary>
     //<param name = "_custVendTrans">
     //VendTrans buffer
     //</param>
     //<param name = "_ledgerPostingJournal">
     //ledger posting journal
     //</param>
     //<param name = "_useSubLedger">
     //Yes or no
     //</param>
    protected void initCustVendTrans(
        CustVendTrans _custVendTrans,
        LedgerVoucher _ledgerPostingJournal,
        boolean _useSubLedger)
    {
        VendTrans                   vendTrans;
        LedgerJournalTrans          ledgerJournalTrans;
        LedgerJournalTrans_Project  ledgerJournalTrans_Project;

        next initCustVendTrans(_custVendTrans, _ledgerPostingJournal, _useSubLedger);

        if (common && common.TableId == tableNum(LedgerJournalTrans))
        {
            ledgerJournalTrans  = common;

            vendTrans           = _custVendTrans;

            ledgerJournalTrans_Project = ledgerJournalTrans_Project::find(ledgerJournalTrans.RecId);

            if (ledgerJournalTrans_Project.AKATrackingID)
            {
                vendTrans.AKATrackingID         = ledgerJournalTrans_Project.AKATrackingID;
                vendTrans.AKATrackingIDCompany  = ledgerJournalTrans_Project.AKATrackingIDCompany;
            }
            else
            {
                LedgerJournalTrans ledgerJournalTransLocal;
                select firstonly  ledgerJournalTransLocal
                    where ledgerJournalTransLocal.Voucher == ledgerJournalTrans.Voucher
                    join ledgerJournalTrans_Project
                    where   ledgerJournalTransLocal.RecId == ledgerJournalTrans_Project.RefRecId
                    &&      ledgerJournalTrans_Project.AKATrackingID;

                if (ledgerJournalTrans_Project.AKATrackingID)
                {
                    vendTrans.AKATrackingID         = ledgerJournalTrans_Project.AKATrackingID;
                    vendTrans.AKATrackingIDCompany  = ledgerJournalTrans_Project.AKATrackingIDCompany;

// ... (truncated)
```

---

*Generated on 2025-10-17 15:42*
