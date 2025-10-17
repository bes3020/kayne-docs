# AxClass: LedgerJournalTransDailyFormDSAKA_Extension

[← Back to Ledger Journal Daily Form Customization](../README.md)

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| write |  | void | none |
| init |  | void | none |

## Declaration Code

```xpp

[ExtensionOf(formDataSourceStr(LedgerJournalTransDaily, LedgerJournalTrans))]
final public class LedgerJournalTransDailyFormDSAKA_Extension
{
}

```

## Key Methods Source

### write

```xpp

    public void write()
    {
        next write();

        LedgerJournalTrans ljt = this.cursor();
        if(ljt.AKALedgerDefaultDimension ||
            ljt.AKALedgerOffsetDefaultDimension)
        {
           // FormDataSource fds = ljt.dataSource();
           // fds.reread();
           // fds.refresh();
        }
    }


```

### init

```xpp

    public void init()
    {
        next init();
        
        Args args = this.formRun().args();
        if(args && args.parm() == "TrackingIDJumpRef")
        {
            LedgerJournalEngine lje = element.ledgerJournalEngine();
            lje.newJournalActive(element.args().record());     
            LedgerJournalFormTrans formTrans = element.journalForm();
            formTrans.parmFactureSource_RU(new  FactureSourceJourCust_RU(null)); // hack to workaround totals error when closing form
        }
    }


```

---

*Generated on 2025-10-17 15:42*
