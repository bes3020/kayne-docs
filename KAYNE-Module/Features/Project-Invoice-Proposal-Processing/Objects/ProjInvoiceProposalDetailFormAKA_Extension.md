# AxClass: ProjInvoiceProposalDetailFormAKA_Extension

[← Back to Project Invoice Proposal Processing](../README.md)

## Description

<summary> Augmented class for the form <c>ProjInvoiceProposalDetail</c> </summary>

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| init |  | void | none |
| akaTrackingIdJumpRef |  | void | none |

## Declaration Code

```xpp

/// <summary>
/// Augmented class for the form <c>ProjInvoiceProposalDetail</c>
/// </summary>
/// AKA_2730_ProjectAdjustmentTrackingID , apendli, 1-dec-2020
[ExtensionOf(formStr(ProjInvoiceProposalDetail))]
final class ProjInvoiceProposalDetailFormAKA_Extension
{
}

```

## Key Methods Source

### init

```xpp

    /// <summary>
    /// Register jumpref for TracingId control
    /// </summary>
    public void init()
    {
        next init();

        ProjProposalCost_AKATrackingID.registerOverrideMethod(
                methodStr(FormStringControl, jumpRef),
                methodStr(ProjInvoiceProposalDetailFormAKA_Extension, akaTrackingIdJumpRef),
                this);
    }


```

### akaTrackingIdJumpRef

```xpp

    /// <summary>
    /// Jumpref method of TrackingID
    /// </summary>
    /// <param name = "_formStringControl">
    /// Form control
    /// </param>
    private void akaTrackingIdJumpRef(FormStringControl _formStringControl)
    {
        VendInvoiceJour::AKATrackingIDJumpRef(ProjProposalCost.AKATrackingId, ProjProposalCost.AKATrackingIdCompany);
        _formStringControl.jumpRef();
    }


```

---

*Generated on 2025-10-17 15:42*
