# AxClass: LedgerJournalTransDailyFormAKA_Extension

[← Back to General Ledger Daily Journal Management](../README.md)

## Description

<summary> Augmented class for the form <c>LedgerJournalTransDaily</c> </summary>

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| akaEnableDisableControls |  | void | none |

## Declaration Code

```xpp

/// <summary>
/// Augmented class for the form <c>LedgerJournalTransDaily</c>
/// </summary>
/// AKA_2730_ProjectAdjustmentTrackingID , apendli, 1-dec-2020
[ExtensionOf(formStr(LedgerJournalTransDaily))]
final class LedgerJournalTransDailyFormAKA_Extension
{
}

```

## Key Methods Source

### akaEnableDisableControls

```xpp

    /// <summary>
    /// Enable or disable the controls
    /// </summary>
    /// AKA_2730_ProjectAdjustmentTrackingID , apendli, 1-dec-2020
    public void akaEnableDisableControls()
    {
        AKATrackingId.Visible(ledgerJournalTrans.LedgerJournalTable().Posted);
    }


```

---

*Generated on 2025-10-17 15:42*
