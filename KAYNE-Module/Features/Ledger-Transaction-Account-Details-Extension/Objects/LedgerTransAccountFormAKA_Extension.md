# AxClass: LedgerTransAccountFormAKA_Extension

[← Back to Ledger Transaction Account Details Extension](../README.md)

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| init |  | void | none |
| akaTrackingIdJumpref |  | void | none |

## Declaration Code

```xpp

[ExtensionOf(formStr(LedgerTransAccount))]
final class LedgerTransAccountFormAKA_Extension
{
}

```

## Key Methods Source

### init

```xpp

    public void init()
    {
        next init();

        AKALedgerAttributeTrans_AKATrackingID.registerOverrideMethod(
                methodStr(FormStringControl, jumpRef),
                methodStr(LedgerTransAccountFormAKA_Extension, akaTrackingIdJumpref),
                this);
    }


```

### akaTrackingIdJumpref

```xpp

    private void akaTrackingIdJumpref(FormStringControl _formStringControl)
    {
        VendInvoiceJour::AKATrackingIDJumpRef(AKALedgerAttributeTrans.AKATrackingId, AKALedgerAttributeTrans.AKATrackingIdCompany);
        _formStringControl.jumpRef();
    }


```

---

*Generated on 2025-10-17 15:42*
