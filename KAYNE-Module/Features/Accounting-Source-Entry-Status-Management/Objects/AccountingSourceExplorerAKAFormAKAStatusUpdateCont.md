# AxClass: AccountingSourceExplorerAKAFormAKAStatusUpdateControl_Extension

[← Back to Accounting Source Entry Status Management](../README.md)

## Description

<summary> Extension for the control of form <c>AccountingSourceExplorer</c> </summary>

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| clicked |  | void | none |

## Declaration Code

```xpp

/// <summary>
/// Extension for the control of form <c>AccountingSourceExplorer</c>
/// </summary>
/// AKA_2737_AbilityToReviewProjCostMarkReviewedAdj : apendli, 12-Nov-2020
[ExtensionOf(formControlStr(AccountingSourceExplorer, AKAStatusUpdate))]
final class AccountingSourceExplorerAKAFormAKAStatusUpdateControl_Extension
{
}

```

## Key Methods Source

### clicked

```xpp

    /// <summary>
    /// COC for the clicked method
    /// </summary>
    /// AKA_2737_AbilityToReviewProjCostMarkReviewedAdj : apendli, 12-Nov-2020
    public void clicked()
    {
        next clicked();

        element.akaLedgerReviewStatus();
        element.akaRefreshAccountingSourceExpolrerFormDS();
    }


```

---

*Generated on 2025-10-17 15:42*
