# AxClass: LedgerVoucherTransObjectAKA_Extension

[← Back to Extended General Ledger Transaction Processing](../README.md)

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| parmAKALedgerAttributes |  | RefRecId | none |
| getLedgerPostingTransaction |  | LedgerPostingTransactionTmp | none |
| initFromLedgerPostingTransaction |  | void | none |
| newTransLedgerJournal | ✓ | LedgerVoucherTransObject | none |

## Declaration Code

```xpp

[ExtensionOf(classStr(LedgerVoucherTransObject))]
final class LedgerVoucherTransObjectAKA_Extension
{
}

```

## Key Methods Source

### parmAKALedgerAttributes

```xpp

    RefRecId parmAKALedgerAttributes(RefRecId _AKALedgerAttributes = generalJournalAccountEntry.AKALedgerAttributes)
    {
        GeneralJournalAccountEntry  generalJournalAccountEntryLocal = this.generalJournalAccountEntry;
        generalJournalAccountEntryLocal.AKALedgerAttributes = _AKALedgerAttributes;

        return generalJournalAccountEntryLocal.AKALedgerAttributes;
    }


```

### getLedgerPostingTransaction

```xpp

    public LedgerPostingTransactionTmp getLedgerPostingTransaction()
    {
        LedgerPostingTransactionTmp LedgerPostingTransactionTmpCOC;

        ledgerPostingTransactionTmpCOC = next getLedgerPostingTransaction();
       
        ledgerPostingTransactionTmpCOC.AKALedgerAttributes   = this.generalJournalAccountEntry.AKALedgerAttributes;
        return LedgerPostingTransactionTmpCOC;
    }


```

### initFromLedgerPostingTransaction

```xpp

    public void initFromLedgerPostingTransaction(
        LedgerPostingTransactionTmp _ledgerPostingTransaction,
        LedgerPostingTransactionProjectTmp _projectPostingTransaction)
    {
        GeneralJournalAccountEntry  generalJournalAccountEntryLocal = this.parmGeneralJournalAccountEntry();
        
        next initFromLedgerPostingTransaction(_ledgerPostingTransaction, _projectPostingTransaction);
        
        generalJournalAccountEntryLocal.AKALedgerAttributes    = _ledgerPostingTransaction.AKALedgerAttributes;
    }


```

---

*Generated on 2025-10-17 15:42*
