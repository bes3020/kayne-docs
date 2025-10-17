# AxClass: LedgerJournalTrans_AKA_Extension

[← Back to AKA General Ledger Journal Enhancements](../README.md)

## Description

<summary> This class is extension for table <c>LedgerJournalTrans</c>. </summary>

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| write |  | void | none |
| AKABuildQueryForLinesForm | ✓ | Query | none |

## Declaration Code

```xpp

/// <summary>
/// This class is extension for table <c>LedgerJournalTrans</c>.
/// </summary>
[ExtensionOf(tableStr(LedgerJournalTrans))]
final class LedgerJournalTrans_AKA_Extension
{
}

```

## Key Methods Source

### write

```xpp

    /// <summary>
    /// Writes data to ledger journal trans.
    /// </summary>
    public void write()
    {
        if (this.AKALedgerDefaultDimension)
        {
            this.AKALedgerDefaultAccountType  = LedgerJournalACType::Ledger;
            this.DefaultDimension             = LedgerDimensionFacade::DGGetDefaultDimensionFromLedgerDimension(this.AKALedgerDefaultDimension);
        }

        if (this.AKALedgerOffsetDefaultDimension)
        {
            this.AKALedgerOffsetDefaultAccountType  = LedgerJournalACType::Ledger;
            this.OffsetDefaultDimension = LedgerDimensionFacade::DGGetDefaultDimensionFromLedgerDimension(this.AKALedgerOffsetDefaultDimension);
        }

        next write();
    }


```

### AKABuildQueryForLinesForm

```xpp

    static public Query AKABuildQueryForLinesForm(FormRun _formRun)
    {
        Args                        args;
        FormDataSource              fds;
        Query                       query = new Query(queryStr(LedgerJournal));
        QueryBuildRange             qbr ;
        str                         queryString;
        
        qbr = query.dataSourceTable(tableNum(LedgerJournalTable)).addRange(fieldNum(LedgerJournalTable, RecId));
                
        args = _formRun.args();

        if(args.caller() && (args.caller().name() == formStr(LedgerJournalTable)))
        {
            //fds         = FormDataUtil::getFormDataSource(args.record());
            //if(fds.table() == tableNum(LedgerJournalTable))
            //{
                LedgerJournalTable ledgerJournalTable = args.record();
                queryString = int642str(ledgerJournalTable.RecId);
            //}
        }
        //Max 3/3/2022 - open form from invoice lines
        else if(args.caller() && (args.caller().name() == formStr(LedgerJournalTransVendInvoice)))
        {
            LedgerJournalTrans ledgerJournalTransLocal = args.record();
            LedgerJournalTable ledgerJournalTable = LedgerJournalTable::find(ledgerJournalTransLocal.JournalNum);
            queryString = int642str(ledgerJournalTable.RecId);
        }
        // end - Max 3/3/2022 - open form from lines
        
        qbr.value(queryString);
        
        return query;
    }


```

---

*Generated on 2025-10-17 15:42*
