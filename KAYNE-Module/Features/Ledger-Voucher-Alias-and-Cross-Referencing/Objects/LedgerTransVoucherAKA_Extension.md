# AxClass: LedgerTransVoucherAKA_Extension

[← Back to Ledger Voucher Alias and Cross-Referencing](../README.md)

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| init |  | void | none |

## Declaration Code

```xpp

[ExtensionOf(formstr(LedgerTransVoucher))]
public final class LedgerTransVoucherAKA_Extension
{
}

```

## Key Methods Source

### init

```xpp

	void init()
    {
        next init();

        FormControl LedgerTrans_AccountNum = this.design().controlName(formcontrolstr(LedgerTransVoucher, LedgerTrans_AccountNum));
        FormControl AKAGeneralJournalAccountEntryMaskView_DisplayValueMask = this.design().controlName(formcontrolstr(LedgerTransVoucher, AKAGeneralJournalAccountEntryMaskView_DisplayValueMask));

        boolean allowedPeopleAccess = LedgerParameters::allowedPeopleUserGroupAccess();

        LedgerTrans_AccountNum.visible(allowedPeopleAccess);
        AKAGeneralJournalAccountEntryMaskView_DisplayValueMask.visible(!allowedPeopleAccess);
    }


```

---

*Generated on 2025-10-17 15:42*
