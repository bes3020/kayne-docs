# AxClass: ProjInvoiceProposalCreateLinesFormAKA_Extension

[← Back to Project Invoice Proposal Line Management](../README.md)

## Description

<summary> Augmented class for the form <c>ProjInvoiceProposalCreateLines</c> </summary>

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| init |  | void | none |
| akaTrackingIdJumpRef |  | void | none |

## Declaration Code

```xpp

/// <summary>
/// Augmented class for the form <c>ProjInvoiceProposalCreateLines</c>
/// </summary>
/// AKA_2730_ProjectAdjustmentTrackingID , apendli, 1-dec-2020
[ExtensionOf(formStr(ProjInvoiceProposalCreateLines))]
final class ProjInvoiceProposalCreateLinesFormAKA_Extension
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

        PSATmpProjProposalTrans_AKATrackingID.registerOverrideMethod(
                methodStr(FormStringControl, jumpRef),
                methodStr(ProjInvoiceProposalCreateLinesFormAKA_Extension, akaTrackingIdJumpRef),
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
        VendInvoiceJour::AKATrackingIDJumpRef(PSATmpProjProposalTrans.AKATrackingId, PSATmpProjProposalTrans.AKATrackingIdCompany);
        _formStringControl.jumpRef();
    }


```

---

*Generated on 2025-10-17 15:42*
