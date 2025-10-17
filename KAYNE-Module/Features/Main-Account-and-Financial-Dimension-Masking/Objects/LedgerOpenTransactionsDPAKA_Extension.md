# AxClass: LedgerOpenTransactionsDPAKA_Extension

[← Back to Main Account and Financial Dimension Masking](../README.md)

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| processReport |  | void | none |

## Declaration Code

```xpp

[ExtensionOf(classstr(LedgerOpenTransactionsDP))]
final public class LedgerOpenTransactionsDPAKA_Extension
{
}

```

## Key Methods Source

### processReport

```xpp

    public void processReport()
    {
        next processReport();

        ledgerOpenTransactionsTmp ledgerOpenTransactionsTmp = this.ledgerOpenTransactionsTmp;
        if(!LedgerParameters::allowedPeopleUserGroupAccess())
        {
            AKADimensionCombinationMaskView akaDimensionCombinationView;

            update_recordSet ledgerOpenTransactionsTmp setting
                LedgerAccount = akaDimensionCombinationView.DisplayValueMask
            where ledgerOpenTransactionsTmp.AccountType == LedgerJournalACType::Ledger
            join akaDimensionCombinationView
                where akaDimensionCombinationView.RecId == ledgerOpenTransactionsTmp.LedgerDimension;
                

            /*ttsbegin;

            while select forupdate ledgerOpenTransactionsTmp 
                where ledgerOpenTransactionsTmp.AccountType == LedgerJournalACType::Ledger
                join akaDimensionCombinationView
                    where akaDimensionCombinationView.RecId == ledgerOpenTransactionsTmp.LedgerDimension
            {
                ledgerOpenTransactionsTmp.LedgerAccount = akaDimensionCombinationView.DisplayValueMask;
                ledgerOpenTransactionsTmp.update();
            }*/
            update_recordSet ledgerOpenTransactionsTmp setting
                OffsetLedgerAccount = akaDimensionCombinationView.DisplayValueMask
            where ledgerOpenTransactionsTmp.OffsetAccountType == LedgerJournalACType::Ledger
            join akaDimensionCombinationView
                where akaDimensionCombinationView.RecId == ledgerOpenTransactionsTmp.OffsetLedgerDimension;

        }
    }


```

---

*Generated on 2025-10-17 15:42*
