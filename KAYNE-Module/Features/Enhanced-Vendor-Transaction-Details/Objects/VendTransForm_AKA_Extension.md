# AxClass: VendTransForm_AKA_Extension

[← Back to Enhanced Vendor Transaction Details](../README.md)

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| init |  | void | none |

## Declaration Code

```xpp

[ExtensionOf(formStr(VendTrans))]
final class VendTransForm_AKA_Extension
{
}

```

## Key Methods Source

### init

```xpp

    public void init()
    {
        next init();

        if (common.TableId == tableNum(LedgerJournalTable))
        {
            LedgerJournalTable	ledgerJournalTable = common;
            QueryBuildRange		qbr;
            
            QueryBuildDataSource qbdS = vendTrans_ds.query().dataSourceTable(tableNum(VendTrans));
            qbdS.clearDynalinks();

            qbdS = qbdS.addDataSource(tableNum(DimensionAttributeValueCombination));
            qbdS.addLink(fieldNum(VendTrans, AccountNum), fieldNum(DimensionAttributeValueCombination, DisplayValue));

            qbdS = qbdS.addDataSource(tableNum(LedgerJournalTrans));
            qbdS.addLink(fieldNum(DimensionAttributeValueCombination, RecId), fieldNum(LedgerJournalTrans, LedgerDimension));
            qbr = qbdS.addRange(fieldNum(LedgerJournalTrans, AccountType));
            qbr.value(SysQuery::value(LedgerJournalACType::Vend));
            qbr.status(RangeStatus::Hidden);
            
            qbr = qbdS.addRange(fieldNum(LedgerJournalTrans, JournalNum));
			qbr.value(ledgerJournalTable.JournalNum);
            qbr.status(RangeStatus::Hidden);
        }

    }


```

---

*Generated on 2025-10-17 15:42*
