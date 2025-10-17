# AxClass: AccountingSourceExplorerProcessorAKA_Extension

[← Back to Accounting Source Explorer Enhancement](../README.md)

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| AccountingSourceExplorerProcessor_Pre_postDataUpdate | ✓ | void | none |
| KA_AccountingSourceExplorerProcessor_Post_postDataUpdate | ✓ | void | none |

## Declaration Code

```xpp

[ExtensionOf(classStr(AccountingSourceExplorerProcessor))]
final public class AccountingSourceExplorerProcessorAKA_Extension
{
}

```

## Key Methods Source

### AccountingSourceExplorerProcessor_Pre_postDataUpdate

```xpp

    [PreHandlerFor(classStr(AccountingSourceExplorerProcessor), methodStr(AccountingSourceExplorerProcessor, postDataUpdate))]
    public static void AccountingSourceExplorerProcessor_Pre_postDataUpdate(XppPrePostArgs args)
    {
        if(!LedgerParameters::allowedPeopleUserGroupAccess())
        {
            AccountingSourceExplorerProcessor processor = args.getThis();
            AccountingSourceExplorerTmp accountingSourceExplorerTmp = processor.parmAccountingSourceExplorerTmp();
            GeneralJournalAccountEntryEntity generalJournalAccountEntryEntity;
            ProjTransPosting projTransPosting;

            ttsbegin;
            update_recordSet accountingSourceExplorerTmp
                setting LedgerAccount = generalJournalAccountEntryEntity.AccountDisplayValueMask
            join GeneralJournalAccountEntryRecId, AccountDisplayValueMask from generalJournalAccountEntryEntity
                where generalJournalAccountEntryEntity.GeneralJournalAccountEntryRecId == accountingSourceExplorerTmp.GeneralJournalAccountEntry;
            ttscommit;

            //ttsbegin;
            //update_recordSet accountingSourceExplorerTmp
            //    setting ProjectId = projTransPosting.ProjId
            //join ProjId from projTransPosting
            //    where projTransPosting.Voucher == accountingSourceExplorerTmp.SubledgerVoucher
            //    && projTransPosting.TransId == accountingSourceExplorerTmp.DFSProjTransId;
            //ttscommit;
        }
    }


```

### KA_AccountingSourceExplorerProcessor_Post_postDataUpdate

```xpp

    [PreHandlerFor(classStr(AccountingSourceExplorerProcessor), methodStr(AccountingSourceExplorerProcessor, postDataUpdate))]
    public static void KA_AccountingSourceExplorerProcessor_Post_postDataUpdate(XppPrePostArgs args)
    {
        AccountingSourceExplorerProcessor processor = args.getThis();
        AccountingSourceExplorerTmp accountingSourceExplorerTmp = processor.parmAccountingSourceExplorerTmp();
        GeneralJournalAccountEntryEntity generalJournalAccountEntryEntity;
        ProjTransPosting projTransPosting;

        ttsbegin;
        update_recordSet accountingSourceExplorerTmp
            setting DFSProjTransId = generalJournalAccountEntryEntity.DFSProjTransId
        join GeneralJournalAccountEntryRecId, DFSProjTransId from generalJournalAccountEntryEntity
            where generalJournalAccountEntryEntity.GeneralJournalAccountEntryRecId == accountingSourceExplorerTmp.GeneralJournalAccountEntry;
        ttscommit;

        ttsbegin;
        update_recordSet accountingSourceExplorerTmp
            setting ProjectId = projTransPosting.ProjId
        join ProjId from projTransPosting
            where projTransPosting.Voucher == accountingSourceExplorerTmp.SubledgerVoucher
            && projTransPosting.TransId == accountingSourceExplorerTmp.DFSProjTransId;
        ttscommit;
    }

    /// <summary>
    /// Post eventhandler for the method of class <c>AccountingSourceExplorerProcessor</c>
    /// </summary>
    /// <param name="args">
    /// Args
    /// </param>
    /// AKA_2737_AbilityToReviewProjCostMarkReviewedAdj : apendli, 12-Nov-2020
    //[PostHandlerFor(classStr(AccountingSourceExplorerProcessor), methodStr(AccountingSourceExplorerProcessor, postDataUpdate))]
    //public static void AccountingSourceExplorerProcessor_Post_postDataUpdate(XppPrePostArgs args)
    //{
    //    #define.dimPeople('People')
    //    #define.dimDepartment('Department')
    //    #define.dimDeal('Deal')
    //    #define.dimValue('DimValue')
    //    DimensionFocusNameTmp                       dimensionFocusNameTmp;
    //    DimAttributeOMDepartment                    dimAttributeOMDepartment;
    //    DimensionFinancialTag                       dimAttributeFinancialTag;
    //    ProjTransPosting                            projTransPosting;
    //    ResourceView                                resourceView;
    //    AKALedgerTransSettlementPending             akaLedgerTransSettlementPending;
    //    LedgerTransSettlement                       ledgerTransSettlement;
    //    DimensionHierarchy                          dimHierarchy;
    //    DimensionAttribute                          dimAttr;
    //    int                                         levelCount;
    //    boolean                                     isPersonDimAvailable, isDepartmentAvailable, isDealAvailable;

// ... (truncated)
```

---

*Generated on 2025-10-17 15:42*
