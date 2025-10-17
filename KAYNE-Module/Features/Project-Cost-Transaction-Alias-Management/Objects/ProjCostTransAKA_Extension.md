# AxClass: ProjCostTransAKA_Extension

[← Back to Project Cost Transaction Alias Management](../README.md)

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| getAKALedgerDefaultDimension |  | DimensionDisplayValue | none |

## Declaration Code

```xpp

[ExtensionOf(tableStr(ProjCostTrans))]
final public class ProjCostTransAKA_Extension
{
}

```

## Key Methods Source

### getAKALedgerDefaultDimension

```xpp

    display DimensionDisplayValue getAKALedgerDefaultDimension()
    {
        LedgerJournalTrans ledgerJournalTrans;
        LedgerJournalTrans_Project ledgerJournalTrans_project;
        DimensionAttributeValueCombination davc;

        select firstonly AKALedgerDefaultDimension 
            from ledgerJournalTrans  
            where   ledgerJournalTrans.Voucher == this.VoucherJournal
            join ledgerJournalTrans_project
                where ledgerJournalTrans_project.RefRecId == ledgerJournalTrans.Recid
                && ledgerJournalTrans_project.ProjId == this.ProjId
            join davc
            where davc.RecId == ledgerJournalTrans.AKALedgerDefaultDimension;

        return davc.DisplayValue;
    }


```

---

*Generated on 2025-10-17 15:42*
