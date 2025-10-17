# AxClass: LedgerJournalTransAKA_Extension

[← Back to General Ledger Journal Line Customization (AKA)](../README.md)

## Description

<summary> Augmented class for the table <c>LedgerJournalTrans</c> </summary>

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| akaTackingID |  | AKATrackingID | none |

## Declaration Code

```xpp

/// <summary>
/// Augmented class for the table <c>LedgerJournalTrans</c>
/// </summary>
/// AKA_2730_ProjectAdjustmentTrackingID , apendli, 1-dec-2020
[ExtensionOf(tableStr(LedgerJournalTrans))]
final class LedgerJournalTransAKA_Extension
{
}

```

## Key Methods Source

### akaTackingID

```xpp

    /// <summary>
    /// display method for AKATrackingId
    /// </summary>
    /// <returns>
    /// AKATrackingId
    /// </returns>
    display AKATrackingID akaTackingID()
    {
        return this.voucher;
    }


```

---

*Generated on 2025-10-17 15:42*
