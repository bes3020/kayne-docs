# AxClass: ProjTransPostingAKA_Extension

[← Back to Project Transaction Posting Enhancements](../README.md)

## Description

<summary> Augmented class for table <c>ProjTransPosting</c> </summary>

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| initFromProjLedger |  | void | none |

## Declaration Code

```xpp

/// <summary>
/// Augmented class for table <c>ProjTransPosting</c>
/// </summary>
/// AKA_2730_ProjectAdjustmentTrackingID , apendli, 1-dec-2020
[ExtensionOf(tableStr(ProjTransPosting))]
final class ProjTransPostingAKA_Extension
{
}

```

## Key Methods Source

### initFromProjLedger

```xpp

    public void initFromProjLedger(ProjLedger projLedger)
    {
        next initFromProjLedger(projLedger);

        this.AKATrackingID          = projLedger.parmDFSTrackinID();
        this.AKATrackingIDCompany   = projLedger.parmDFSTrackinIDCompany();
    }


```

---

*Generated on 2025-10-17 15:42*
