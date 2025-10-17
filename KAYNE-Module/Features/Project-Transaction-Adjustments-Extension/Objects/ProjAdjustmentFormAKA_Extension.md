# AxClass: ProjAdjustmentFormAKA_Extension

[← Back to Project Transaction Adjustments Extension](../README.md)

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| init |  | void | none |
| akaTrackingIdJumpref |  | void | none |

## Declaration Code

```xpp

[ExtensionOf(formStr(ProjAdjustment))]
final class ProjAdjustmentFormAKA_Extension
{
}

```

## Key Methods Source

### init

```xpp

    public void init()
    {
        next init();

        TmpProjAdjustment_AKATrackingID.registerOverrideMethod(
                methodStr(FormStringControl, jumpRef),
                methodStr(ProjAdjustmentFormAKA_Extension, akaTrackingIdJumpref),
                this);
    }


```

### akaTrackingIdJumpref

```xpp

    /// <summary>
    /// Jumpref method of TrackingID
    /// </summary>
    /// <param name = "_formStringControl">
    /// Form control
    /// </param>
    /// AKA_2730_ProjectAdjustmentTrackingID , apendli, 1-dec-2020
    private void akaTrackingIdJumpref(FormStringControl _formStringControl)
    {
        VendInvoiceJour::AKATrackingIDJumpRef(TmpProjAdjustment.AKATrackingId, TmpProjAdjustment.AKATrackingIdCompany);
        _formStringControl.jumpRef();
    }


```

---

*Generated on 2025-10-17 15:42*
