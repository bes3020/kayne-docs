# AxClass: ProjInvoiceCostAKA_Extension

[← Back to Project Invoice Cost Management Extension](../README.md)

## Description

<summary> Augmented class for the table <c>ProjInvoiceCost</c> </summary>

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| initInvoiceFromProposal | ✓ | ProjInvoiceCost | none |

## Declaration Code

```xpp

/// <summary>
/// Augmented class for the table <c>ProjInvoiceCost</c>
/// </summary>
/// AKA_2730_ProjectAdjustmentTrackingID , apendli, 1-dec-2020
[ExtensionOf(tableStr(ProjInvoiceCost))]
final class ProjInvoiceCostAKA_Extension
{
}

```

## Key Methods Source

### initInvoiceFromProposal

```xpp

    /// <summary>
    /// Assign trackingId details to table buffer <c>projInvoiceCost</c>
    /// </summary>
    /// <param name = "_projProposalCost">
    /// table buffer
    /// </param>
    /// <returns>
    /// table buffer
    /// </returns>
    public static ProjInvoiceCost initInvoiceFromProposal(ProjProposalCost _projProposalCost)
    {
        ProjInvoiceCost projInvoiceCost;

        projInvoiceCost  = next initInvoiceFromProposal(_projProposalCost);

        projInvoiceCost.AKATrackingID           = _projProposalCost.AKATrackingID;
        projInvoiceCost.AKATrackingIDCompany    = _projProposalCost.AKATrackingIDCompany;

        return projInvoiceCost;
    }


```

---

*Generated on 2025-10-17 15:42*
