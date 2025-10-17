# AxClass: DFSAccountingSourceExplorerProcessorAKA_Extension

[← Back to Accounting Source Explorer Enhancement](../README.md)

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| DFSAccountingSourceExplorerProcessor_Pre_postDataUpdate | ✓ | void | none |

## Declaration Code

```xpp

[ExtensionOf(classStr(DFSAccountingSourceExplorerProcessor))]
final public class DFSAccountingSourceExplorerProcessorAKA_Extension
{

    public AccountingSourceExplorerBalanceParameters   accountingSourceExplorerBalanceParametersLoc;

}

```

## Key Methods Source

### DFSAccountingSourceExplorerProcessor_Pre_postDataUpdate

```xpp

    [PreHandlerFor(classStr(DFSAccountingSourceExplorerProcessor), methodStr(DFSAccountingSourceExplorerProcessor, postDataUpdate))]
    public static void DFSAccountingSourceExplorerProcessor_Pre_postDataUpdate(XppPrePostArgs args)
    {
        if (!LedgerParameters::allowedPeopleUserGroupAccess())
        {
            DFSAccountingSourceExplorerProcessor processor = args.getThis();

            DFSAccountingSourceExplorerTmp accountingSourceExplorerTmp = processor.parmAccountingSourceExplorerTmp();

            DFSAccountingSourceExplorerTmp accountingSourceExplorerTmpGroup;
            accountingSourceExplorerTmpGroup.linkPhysicalTableInstance(accountingSourceExplorerTmp);

            while select accountingSourceExplorerTmpGroup
                group by accountingSourceExplorerTmpGroup.DFSLegalEntity
            {
                if (accountingSourceExplorerTmpGroup.DFSLegalEntity)
                {
                    changecompany(accountingSourceExplorerTmpGroup.DFSLegalEntity)
                    {
                        GeneralJournalAccountEntryEntity generalJournalAccountEntryEntity;

                        ttsbegin;

                        update_recordSet accountingSourceExplorerTmp
                            setting LedgerAccount = generalJournalAccountEntryEntity.AccountDisplayValueMask
                        join GeneralJournalAccountEntryRecId, AccountDisplayValueMask 
                            from generalJournalAccountEntryEntity
                            where generalJournalAccountEntryEntity.GeneralJournalAccountEntryRecId == accountingSourceExplorerTmp.GeneralJournalAccountEntry;
                        ttscommit;
                    }
                }
            }

            
        }
    }


```

---

*Generated on 2025-10-17 15:42*
