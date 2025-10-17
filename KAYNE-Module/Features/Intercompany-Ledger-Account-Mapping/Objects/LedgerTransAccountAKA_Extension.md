# AxClass: LedgerTransAccountAKA_Extension

[← Back to Intercompany Ledger Account Mapping](../README.md)

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| init |  | void | none |

## Declaration Code

```xpp

[ExtensionOf(formstr(LedgerTransAccount))]
public final class LedgerTransAccountAKA_Extension
{
}

```

## Key Methods Source

### init

```xpp

    void init()
    {
        next init();

        FormControl AccountNum = this.design().controlName(formcontrolstr(LedgerTransAccount, AccountNum));
        FormControl AKAGeneralJournalAccountEntryMaskView_DisplayValueMask = this.design().controlName(formcontrolstr(LedgerTransAccount, AKAGeneralJournalAccountEntryMaskView_DisplayValueMask));

        boolean allowedPeopleAccess = LedgerParameters::allowedPeopleUserGroupAccess();

        AccountNum.visible(allowedPeopleAccess);
        AKAGeneralJournalAccountEntryMaskView_DisplayValueMask.visible(!allowedPeopleAccess);
    }


```

---

*Generated on 2025-10-17 15:42*
