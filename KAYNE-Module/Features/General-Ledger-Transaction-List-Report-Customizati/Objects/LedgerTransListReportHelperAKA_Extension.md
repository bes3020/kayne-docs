# AxClass: LedgerTransListReportHelperAKA_Extension

[← Back to General Ledger Transaction List Report Customization](../README.md)

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| createReportData |  | void | none |

## Declaration Code

```xpp

[ExtensionOf(classStr(LedgerTransListReportHelper))]
final class LedgerTransListReportHelperAKA_Extension
{
}

```

## Key Methods Source

### createReportData

```xpp

    public void createReportData(
        LedgerTransactionListTmp _reportTmpTable,
        Query _query,
        TransDate _fromDate,
        TransDate _toDate,
        Reversed _includeReversed,
        TaxSpecification _includeTaxTransactions,
        boolean _sortByAccount,
        boolean _includeIntercompanyTaxes,
        boolean _summaryOnly)
    {
        next createReportData(_reportTmpTable, _query, _fromDate, _toDate, _includeReversed, _includeTaxTransactions, _sortByAccount, _includeIntercompanyTaxes,_summaryOnly);

        if(!LedgerParameters::allowedPeopleUserGroupAccess())
        {
            GeneralJournalAccountEntryEntity generalJournalAccountEntryEntity;
            update_recordset _reportTmpTable
                setting Dimension = generalJournalAccountEntryEntity.AccountDisplayValueMask
            join GeneralJournalAccountEntryRecId, AccountDisplayValueMask from generalJournalAccountEntryEntity
                where generalJournalAccountEntryEntity.GeneralJournalAccountEntryRecId == _reportTmpTable.GeneralJournalAccountEntry;
        }
    }


```

---

*Generated on 2025-10-17 15:42*
