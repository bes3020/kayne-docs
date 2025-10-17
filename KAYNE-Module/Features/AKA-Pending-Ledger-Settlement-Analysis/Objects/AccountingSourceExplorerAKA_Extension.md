# AxClass: AccountingSourceExplorerAKA_Extension

[← Back to AKA Pending Ledger Settlement Analysis](../README.md)

## Description

<summary> Extension class for the form <c>AccountingSourceExplorer</c> </summary>

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| akaLedgerReviewStatus |  | void | none |
| akaRefreshAccountingSourceExpolrerFormDS |  | void | none |
| init |  | void | none |
| akaTrackingIdJumpref |  | void | none |
| displayDimensionAttributeValueColumns |  | void | none |

## Declaration Code

```xpp

/// <summary>
/// Extension class for the form <c>AccountingSourceExplorer</c>
/// </summary>
/// AKA_2737_AbilityToReviewProjCostMarkReviewedAdj : apendli, 11-Nov-2020
[ExtensionOf(formStr(AccountingSourceExplorer))]
final class AccountingSourceExplorerAKA_Extension
{

}

```

## Key Methods Source

### akaLedgerReviewStatus

```xpp

    /// <summary>
    /// Create or delete the records for pending or reviewed status
    /// </summary>
    /// AKA_2737_AbilityToReviewProjCostMarkReviewedAdj : apendli, 11-Nov-2020
    public void akaLedgerReviewStatus()
    {
        AccountingSourceExplorerTmp     accountingSourceExplorerTmpLoc;
        AKALedgerTransSettlementPending akaLedgerTransSettlementPending;
        LedgerTransSettlement           ledgerTransSettlement;
        int                             selectionStatus;

        void createPending()
        {
            akaLedgerTransSettlementPending.clear();
            akaLedgerTransSettlementPending.initValue();
            akaLedgerTransSettlementPending.TransRecId    = accountingSourceExplorerTmpLoc.GeneralJournalAccountEntry;
            if (akaLedgerTransSettlementPending.validateWrite())
            {
                akaLedgerTransSettlementPending.insert();
            }
        };

        void createReviewed()
        {
            ledgerTransSettlement.clear();
            ledgerTransSettlement.initValue();
            ledgerTransSettlement.SettleId      = NumberSeq::newGetNum(CompanyInfo::numRefParmId()).num();
            ledgerTransSettlement.TransRecId    = accountingSourceExplorerTmpLoc.GeneralJournalAccountEntry;
            if (ledgerTransSettlement.validateWrite())
            {
                ledgerTransSettlement.insert();
            }
        };

        void deletePending()
        {
            delete_from akaLedgerTransSettlementPending
                    where akaLedgerTransSettlementPending.TransRecId == accountingSourceExplorerTmpLoc.GeneralJournalAccountEntry;
        };

        void deleteReviewed()
        {
            delete_from ledgerTransSettlement
                    where ledgerTransSettlement.TransRecId == accountingSourceExplorerTmpLoc.GeneralJournalAccountEntry;
        };

        selectionStatus = AKALedgerReviewStatusMarkAs.selection();//0 = unreview, 1 = Pending, 2 = Reviewed

        for (accountingSourceExplorerTmpLoc = getFirstSelection(AccountingSourceExplorerTmp_ds); accountingSourceExplorerTmpLoc; accountingSourceExplorerTmpLoc = AccountingSourceExplorerTmp_ds.getNext())

// ... (truncated)
```

### akaRefreshAccountingSourceExpolrerFormDS

```xpp

    /// <summary>
    /// Refresh all the records of datasource
    /// </summary>
    /// AKA_2737_AbilityToReviewProjCostMarkReviewedAdj : apendli, 16-Nov-2020
    public void akaRefreshAccountingSourceExpolrerFormDS()
    {
        AccountingSourceExplorerTmp_ds.Research();
    }


```

### init

```xpp

    /// <summary>
    /// Register jumpref for TracingId control
    /// </summary>
    /// AKA_2730_ProjectAdjustmentTrackingID , apendli, 1-dec-2020
    public void init()
    {
        next init();

        AccountingSourceExplorerTmp_AKATrackingID.registerOverrideMethod(
                methodStr(FormStringControl, jumpRef),
                methodStr(AccountingSourceExplorerAKA_Extension, akaTrackingIdJumpref),
                this);

        AccountingSourceExplorerTmp_AKAPeopleName.visible(LedgerParameters::allowedPeopleUserGroupAccess());
    }


```

---

*Generated on 2025-10-17 15:42*
