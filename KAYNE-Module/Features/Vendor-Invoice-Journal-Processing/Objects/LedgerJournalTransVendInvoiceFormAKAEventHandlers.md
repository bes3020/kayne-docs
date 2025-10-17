# AxClass: LedgerJournalTransVendInvoiceFormAKAEventHandlers

[← Back to Vendor Invoice Journal Processing](../README.md)

## Description

<summary> Eventhandler class for the form <c>LedgerJournalTransVendInvoice</c> </summary>

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| LedgerJournalTrans_OnActivated | ✓ | void | none |

## Declaration Code

```xpp

/// <summary>
/// Eventhandler class for the form <c>LedgerJournalTransVendInvoice</c>
/// </summary>
/// AKA_2730_ProjectAdjustmentTrackingID , apendli, 1-dec-2020
class LedgerJournalTransVendInvoiceFormAKAEventHandlers
{
}

```

## Key Methods Source

### LedgerJournalTrans_OnActivated

```xpp

    /// <summary>
    /// Enable disable controls when datasource record activated
    /// </summary>
    /// <param name="sender">
    /// Datasorce
    /// </param>
    /// <param name="e">
    /// Event args
    /// </param>
    [FormDataSourceEventHandler(formDataSourceStr(LedgerJournalTransVendInvoice, LedgerJournalTrans), FormDataSourceEventType::Activated),
        SuppressBPWarning('BPParameterNotUsed', "Parameter required")]
    public static void LedgerJournalTrans_OnActivated(FormDataSource sender, FormDataSourceEventArgs e)
    {
        FormRun formRun = sender.formRun();

        formRun.akaEnableDisableControls();
    }


```

---

*Generated on 2025-10-17 15:42*
