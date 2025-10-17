# AxClass: PSATmpProjProposalTransAKA_Extension

[← Back to Project Proposal Transaction Processing](../README.md)

## Description

<summary> Augmented class for the table <c>PSATmpProjProposalTrans</c> </summary>

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| initFromProjCostTrans |  | void | none |

## Declaration Code

```xpp

/// <summary>
/// Augmented class for the table <c>PSATmpProjProposalTrans</c>
/// </summary>
/// AKA_2730_ProjectAdjustmentTrackingID , apendli, 1-dec-2020
[ExtensionOf(tableStr(PSATmpProjProposalTrans))]
final class PSATmpProjProposalTransAKA_Extension
{
}

```

## Key Methods Source

### initFromProjCostTrans

```xpp

    /// <summary>
    /// Assign tracking Id details to table buffer
    /// </summary>
    /// <param name = "tProjCostTrans">
    /// table buffer 
    /// </param>
    public void initFromProjCostTrans(PSAProjTrans tProjCostTrans)
    {
        ProjCostTrans   projCostTrans;

        next initFromProjCostTrans(tProjCostTrans);

        projCostTrans               = tProjCostTrans;

        this.AKATrackingID          = projCostTrans.AKATrackingID;
        this.AKATrackingIDCompany   = projCostTrans.AKATrackingIDCompany;
    }


```

---

*Generated on 2025-10-17 15:42*
