# AxClass: LedgerJournalMultiEntityAKA_Extension

[← Back to Multi-Entity Ledger Journal Processing Extension](../README.md)

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| LedgerJournalMultiEntity_onInsertingEntityDataSource | ✓ | void | none |

## Declaration Code

```xpp

[ExtensionOf(dataentityviewstr(LedgerJournalMultiEntity))]
final public class LedgerJournalMultiEntityAKA_Extension
{

    

}

```

## Key Methods Source

### LedgerJournalMultiEntity_onInsertingEntityDataSource

```xpp

    /// <summary>
    ///
    /// </summary>
    /// <param name="_sender"></param>
    /// <param name="_eventArgs"></param>
    [DataEventHandler(tableStr(LedgerJournalMultiEntity), DataEventType::InsertingEntityDataSource)]
    public static void LedgerJournalMultiEntity_onInsertingEntityDataSource(Common _sender, DataEventArgs _eventArgs)
    {
        DataEntityContextEventArgs contextEventArgs = _eventArgs as DataEntityContextEventArgs;
        DataEntityRuntimeContext entityCtx = contextEventArgs.parmEntityContext();
        DataEntityDataSourceRuntimeContext dataSourceCtx = contextEventArgs.parmEntityDataSourceContext();
        LedgerJournalMultiEntity ledgerJournalMultiEntity = _sender as LedgerJournalMultiEntity;

        if (dataSourceCtx.name() == tableStr(LedgerJournalTrans))
        {
            LedgerJournalTrans ledgerJournalTrans =  dataSourceCtx.getBuffer();

            if(ledgerJournalMultiEntity.isFieldSet(fieldNum(LedgerJournalMultiEntity, AKAApprovedByRecId)))
            {
                ledgerJournalTrans.Approver = HcmWorker::findByPersonnelNumber(ledgerJournalMultiEntity.AKAApprovedByRecId).RecId;
            }
            
            if(ledgerJournalMultiEntity.isFieldSet(fieldNum(LedgerJournalMultiEntity, AKAApproved)))
            {
                ledgerJournalTrans.Approved = ledgerJournalMultiEntity.AKAApproved;
            }

            ProjTable projTable;
            DimensionAttributeValueCombination davc;
            LedgerDimensionDefaultAccount   ledgerDefaultAccount;
            Recid davcRecid = ledgerJournalTrans.AccountType == LedgerJournalACType::Project ? ledgerJournalTrans.LedgerDimension : 
                ledgerJournalTrans.OffsetAccountType == LedgerJournalACType::Project ? ledgerJournalTrans.OffsetLedgerDimension : 0;

            if(davcRecid)
            {
                select firstonly DisplayValue from davc where davc.RecId == davcRecid;
                projTable = ProjTable::find(davc.DisplayValue);

                if (projTable && ledgerJournalMultiEntity.ProjectCategory)
                {
                    ledgerDefaultAccount = ProjectPosting::getProjectLedgerDimension(projTable,
                                                            ProjCategory::find(ledgerJournalMultiEntity.ProjectCategory),
                                                            ProjFundingSource::findCustAccount(projtable.ProjInvoiceProjId),
                                                            ProjLineProperty::find(ledgerJournalMultiEntity.ProjectLineProperty),
                                                            false);
                }
            }

            if(ledgerJournalTrans.AccountType == LedgerJournalACType::Project)

// ... (truncated)
```

---

*Generated on 2025-10-17 15:42*
