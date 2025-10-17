# AxClass: ProjProposalCostAKA_Extension

[← Back to Project Proposal Cost Management](../README.md)

## Description

<summary> Augmented class for the table <c>ProjProposalCost</c> </summary>

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| insert |  | void | none |

## Declaration Code

```xpp

/// <summary>
/// Augmented class for the table <c>ProjProposalCost</c>
/// </summary>
/// AKA_2730_ProjectAdjustmentTrackingID , apendli, 1-dec-2020
[ExtensionOf(tableStr(ProjProposalCost))]
final class ProjProposalCostAKA_Extension
{
}

```

## Key Methods Source

### insert

```xpp

    /// <summary>
    /// Assign tracking Id details to table buffer before insert
    /// </summary>
    public void insert()
    {
        ProjCostTrans  projCostTrans  = ProjCostTrans::find(this.TransId);

        this.AKATrackingID          = projCostTrans.AKATrackingID;
        this.AKATrackingIDCompany   = projCostTrans.AKATrackingIDCompany;

        next insert();
    }


```

---

*Generated on 2025-10-17 15:42*
