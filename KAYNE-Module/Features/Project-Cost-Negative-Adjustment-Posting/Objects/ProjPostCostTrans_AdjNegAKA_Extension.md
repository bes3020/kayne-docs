# AxClass: ProjPostCostTrans_AdjNegAKA_Extension

[← Back to Project Cost Negative Adjustment Posting](../README.md)

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| initializeProjCostTrans |  | ProjCostTrans | none |

## Declaration Code

```xpp

[ExtensionOf(classStr(ProjPostCostTrans_AdjNeg))]
final class ProjPostCostTrans_AdjNegAKA_Extension
{
}

```

## Key Methods Source

### initializeProjCostTrans

```xpp

    protected ProjCostTrans initializeProjCostTrans()
    {
        ProjCostTrans local = next initializeProjCostTrans();

        local.AKATrackingID = projCostTrans.AKATrackingID;
        local.AKATrackingIDCompany = projCostTrans.AKATrackingIDCompany;

        local.TransDate = this.parmAdjustmentDate();

        return local;
    }


```

---

*Generated on 2025-10-17 15:42*
