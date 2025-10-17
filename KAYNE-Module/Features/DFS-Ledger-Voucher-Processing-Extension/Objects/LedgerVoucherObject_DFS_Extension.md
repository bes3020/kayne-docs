# AxClass: LedgerVoucherObject_DFS_Extension

[← Back to DFS Ledger Voucher Processing Extension](../README.md)

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| parmSkipInfoMessages |  | NoYes | none |
| showErrorTransactions |  | void | none |

## Declaration Code

```xpp

[ExtensionOf(classStr(LedgerVoucherObject))]
Final class LedgerVoucherObject_DFS_Extension
{
    public NoYes SkipInfoMessges;

}

```

## Key Methods Source

### parmSkipInfoMessages

```xpp

	public NoYes parmSkipInfoMessages(NoYes _skipInfoMessages = SkipInfoMessges)
    {
        SkipInfoMessges = _skipInfoMessages;

        return SkipInfoMessges;
    }


```

### showErrorTransactions

```xpp

    public void showErrorTransactions(Map _subledgerVoucherCollection)
    {
        Map oldMapDetails = _subledgerVoucherCollection;
        Map NewMaptoSkipInfo;

  //if (this.parmSkipInfoMessages())
  //      {
  //          NewMaptoSkipInfo.empty();
  //      }

        next showErrorTransactions(NewMaptoSkipInfo);
    }


```

---

*Generated on 2025-10-17 15:42*
