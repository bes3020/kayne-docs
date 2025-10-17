# AxClass: LedgerJournalTransVendInvoiceFormAKA_Extension

[← Back to Vendor Invoice Journal Form Extension](../README.md)

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| LedgerJournalTrans_AccountType_OnModified | ✓ | void | none |
| LedgerJournalTrans_OffsetAccountType_OnModified | ✓ | void | none |
| LedgerJournalTrans_OnActivated | ✓ | void | none |
| CategoryId_OnModified | ✓ | void | none |
| LedgerDimension_OnModified | ✓ | void | none |
| OffsetLedgerDimension_OnModified | ✓ | void | none |
| akaEnableDisableControls |  | void | none |

## Declaration Code

```xpp

[ExtensionOf(formStr(LedgerJournalTransVendInvoice))]
final public class LedgerJournalTransVendInvoiceFormAKA_Extension
{
   
}

```

## Key Methods Source

### LedgerJournalTrans_AccountType_OnModified

```xpp

    [FormControlEventHandler(formControlStr(LedgerJournalTransVendInvoice, LedgerJournalTrans_AccountType), FormControlEventType::Modified)]
    public static void LedgerJournalTrans_AccountType_OnModified(FormControl sender, FormControlEventArgs e)
    {
        FormRun     formRun = sender.formRun();
        LedgerJournalTrans  ledgerJournalTrans = formRun.dataSource(formDataSourceStr(LedgerJournalTransVendInvoice, LedgerJournalTrans)).cursor() as LedgerJournalTrans;
        FormSegmentedEntryControl ledgerJournalTrans_AKALedgerDefaultDimension = formRun.design().controlName(formControlStr(LedgerJournalTransVendInvoice, LedgerJournalTrans_AKALedgerDefaultDimension));
        ledgerJournalTrans_AKALedgerDefaultDimension.allowEdit(ledgerJournalTrans.AccountType == LedgerJournalACType::Project);
    }


```

### LedgerJournalTrans_OffsetAccountType_OnModified

```xpp

    [FormControlEventHandler(formControlStr(LedgerJournalTransVendInvoice, LedgerJournalTrans_OffsetAccountType), FormControlEventType::Modified)]
    public static void LedgerJournalTrans_OffsetAccountType_OnModified(FormControl sender, FormControlEventArgs e)
    {
        FormRun     formRun = sender.formRun();
        LedgerJournalTrans  ledgerJournalTrans = formRun.dataSource(formDataSourceStr(LedgerJournalTransVendInvoice, LedgerJournalTrans)).cursor() as LedgerJournalTrans;
        FormSegmentedEntryControl ledgerJournalTrans_AKALedgerOffsetDefaultDimension = formRun.design().controlName(formControlStr(LedgerJournalTransVendInvoice, ledgerJournalTrans_AKALedgerOffsetDefaultDimension));
        ledgerJournalTrans_AKALedgerOffsetDefaultDimension.allowEdit(ledgerJournalTrans.OffsetAccountType == LedgerJournalACType::Project);
    }


```

### LedgerJournalTrans_OnActivated

```xpp

    [FormDataSourceEventHandler(formDataSourceStr(LedgerJournalTransVendInvoice, LedgerJournalTrans), FormDataSourceEventType::Activated),
        SuppressBPWarning('BPParameterNotUsed', 'Standard paramter')]
    public static void LedgerJournalTrans_OnActivated(FormDataSource sender, FormDataSourceEventArgs e)
    {
        FormRun     formRun = sender.formRun();
        LedgerJournalTrans  ledgerJournalTrans = sender.cursor();

        FormSegmentedEntryControl ledgerJournalTrans_AKALedgerDefaultDimension = formRun.design().controlName(formControlStr(LedgerJournalTransVendInvoice, LedgerJournalTrans_AKALedgerDefaultDimension));
        FormSegmentedEntryControl ledgerJournalTrans_AKALedgerOffsetDefaultDimension = formRun.design().controlName(formControlStr(LedgerJournalTransVendInvoice, LedgerJournalTrans_AKALedgerOffsetDefaultDimension));

        ledgerJournalTrans_AKALedgerDefaultDimension.allowEdit(ledgerJournalTrans.AccountType == LedgerJournalACType::Project);
        ledgerJournalTrans_AKALedgerOffsetDefaultDimension.allowEdit(ledgerJournalTrans.OffsetAccountType == LedgerJournalACType::Project);
    }


```

---

*Generated on 2025-10-17 15:42*
