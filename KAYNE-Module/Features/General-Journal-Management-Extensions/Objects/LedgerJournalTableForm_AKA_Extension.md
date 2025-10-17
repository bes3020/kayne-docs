# AxClass: LedgerJournalTableForm_AKA_Extension

[← Back to General Journal Management Extensions](../README.md)

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| init |  | void | none |

## Declaration Code

```xpp

[ExtensionOf(formStr(LedgerJournalTable))]
final class LedgerJournalTableForm_AKA_Extension
{
}

```

## Key Methods Source

### init

```xpp

    public void init()
    {
        next init(); 
        
        AKALedgerJournalVendDueDateSingleView_ds.queryBuildDataSource().addLink(fieldNum(LedgerJournalTable, JournalNum), fieldNum(AKALedgerJournalVendDueDateSingleView, JournalNum));
        AKALedgerJournalVendDueDateSingleView_ds.object(fieldNum(AKALedgerJournalVendDueDateSingleView, DueDate)).visible(journalFormTable.journalTypeId() == LedgerJournalType::VendInvoiceRegister);
        AKALedgerJournalVendDueDateSingleView_ds.queryBuildDataSource().enabled(journalFormTable.journalTypeId() == LedgerJournalType::VendInvoiceRegister);

        AKALedgerJournalTableWFUsersView_ds.queryBuildDataSource().addLink(fieldNum(LedgerJournalTable, JournalNum), fieldNum(AKALedgerJournalTableWFUsersView, JournalNum));
        AKALedgerJournalTableWFUsersView_ds.object(fieldNum(AKALedgerJournalTableWFUsersView, WFUsers)).visible(journalFormTable.journalTypeId() == LedgerJournalType::VendInvoiceRegister || journalFormTable.journalTypeId() == LedgerJournalType::Payment);
        //AKALedgerJournalTableWFUsersView_ds.object(fieldNum(AKALedgerJournalTableWFUsersView, WFUsers)).visible(journalFormTable.journalTypeId() == LedgerJournalType::Payment);
        AKALedgerJournalTableWFUsersView_ds.queryBuildDataSource().enabled(journalFormTable.journalTypeId() == LedgerJournalType::VendInvoiceRegister || journalFormTable.journalTypeId() == LedgerJournalType::Payment);
        //AKALedgerJournalTableWFUsersView_ds.queryBuildDataSource().enabled(journalFormTable.journalTypeId() == LedgerJournalType::Payment);
        
		AKAVendTrans.visible(journalFormTable.journalTypeId() == LedgerJournalType::VendInvoiceRegister);

    }


```

---

*Generated on 2025-10-17 15:42*
