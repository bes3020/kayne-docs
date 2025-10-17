# AxClass: LedgerJournalTransDailyForm_AKA_Extension

[← Back to Daily Ledger Journal Form Customization](../README.md)

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| LedgerJournalTrans_AccountType_OnModified | ✓ | void | none |
| LedgerJournalTrans_OffsetAccountType_OnModified | ✓ | void | none |
| LedgerJournalTrans_OnActivated | ✓ | void | none |

## Declaration Code

```xpp

[ExtensionOf(formStr(LedgerJournalTransDaily))]
final public class LedgerJournalTransDailyForm_AKA_Extension
{
    

}

```

## Key Methods Source

### LedgerJournalTrans_AccountType_OnModified

```xpp

    [FormControlEventHandler(formControlStr(LedgerJournalTransDaily, LedgerJournalTrans_AccountType), FormControlEventType::Modified)]
    public static void LedgerJournalTrans_AccountType_OnModified(FormControl sender, FormControlEventArgs e)
    {
        FormRun     formRun = sender.formRun();
        LedgerJournalTrans  ledgerJournalTrans = formRun.dataSource(formDataSourceStr(LedgerJournalTransDaily, LedgerJournalTrans)).cursor() as LedgerJournalTrans;
        FormSegmentedEntryControl ledgerJournalTrans_AKALedgerDefaultDimension = formRun.design().controlName(formControlStr(LedgerJournalTransDaily, LedgerJournalTrans_AKALedgerDefaultDimension));
        ledgerJournalTrans_AKALedgerDefaultDimension.allowEdit(ledgerJournalTrans.AccountType == LedgerJournalACType::Project);
    }


```

### LedgerJournalTrans_OffsetAccountType_OnModified

```xpp

    [FormControlEventHandler(formControlStr(LedgerJournalTransDaily, LedgerJournalTrans_OffsetType), FormControlEventType::Modified)]
    public static void LedgerJournalTrans_OffsetAccountType_OnModified(FormControl sender, FormControlEventArgs e)
    {
        FormRun     formRun = sender.formRun();
        LedgerJournalTrans  ledgerJournalTrans = formRun.dataSource(formDataSourceStr(LedgerJournalTransDaily, LedgerJournalTrans)).cursor() as LedgerJournalTrans;
        FormSegmentedEntryControl ledgerJournalTrans_AKALedgerOffsetDefaultDimension = formRun.design().controlName(formControlStr(LedgerJournalTransDaily, ledgerJournalTrans_AKALedgerOffsetDefaultDimension));
        ledgerJournalTrans_AKALedgerOffsetDefaultDimension.allowEdit(ledgerJournalTrans.OffsetAccountType == LedgerJournalACType::Project);
    }


```

### LedgerJournalTrans_OnActivated

```xpp

    [FormDataSourceEventHandler(formDataSourceStr(LedgerJournalTransDaily, LedgerJournalTrans), FormDataSourceEventType::Activated),
        SuppressBPWarning('BPParameterNotUsed', 'Standard paramter')]
    public static void LedgerJournalTrans_OnActivated(FormDataSource sender, FormDataSourceEventArgs e)
    {
        FormRun     formRun = sender.formRun();
        LedgerJournalTrans  ledgerJournalTrans = sender.cursor();

        FormSegmentedEntryControl ledgerJournalTrans_AKALedgerDefaultDimension = formRun.design().controlName(formControlStr(LedgerJournalTransDaily, LedgerJournalTrans_AKALedgerDefaultDimension));
        FormSegmentedEntryControl ledgerJournalTrans_AKALedgerOffsetDefaultDimension = formRun.design().controlName(formControlStr(LedgerJournalTransDaily, LedgerJournalTrans_AKALedgerOffsetDefaultDimension));

        //ledgerJournalTrans_AKALedgerDefaultDimension.allowEdit((ledgerJournalTrans.AccountType == LedgerJournalACType::Project) || (ledgerJournalTrans.AccountType == LedgerJournalACType::Cust));
        //ledgerJournalTrans_AKALedgerOffsetDefaultDimension.allowEdit((ledgerJournalTrans.OffsetAccountType == LedgerJournalACType::Project) || (ledgerJournalTrans.OffsetAccountType == LedgerJournalACType::Cust));

        ledgerJournalTrans_AKALedgerDefaultDimension.allowEdit((ledgerJournalTrans.AccountType == LedgerJournalACType::Project));
        ledgerJournalTrans_AKALedgerOffsetDefaultDimension.allowEdit((ledgerJournalTrans.OffsetAccountType == LedgerJournalACType::Project));
    }

    /*[FormDataFieldEventHandler(formDataFieldStr(LedgerJournalTransDaily, LedgerJournalTrans_Project, CategoryId), FormDataFieldEventType::Modified),
        SuppressBPWarning('BPParameterNotUsed', 'Standard paramter')]
    public static void CategoryId_OnModified(FormDataObject sender, FormDataFieldEventArgs e)
    {
        FormDataSource                  ledgerJournalTrans_ProjectDS =  sender.datasource() as FormDataSource;
        LedgerJournalTrans_project      ledgerJournalTrans_Project = ledgerJournalTrans_ProjectDS.cursor() as LedgerJournalTrans_project;        
        FormRun                         formRun = ledgerJournalTrans_ProjectDS.formRun() as FormRun;
        FormDataSource                  ledgerJournalTransDS = formRun.dataSource(formDataSourceStr(LedgerJournalTransDaily, LedgerJournalTrans)) as FormDataSource;
        LedgerJournalTrans              ledgerJournalTrans = FormRun.dataSource(formDataSourceStr(LedgerJournalTransDaily, LedgerJournalTrans)).cursor() as LedgerJournalTrans;
        LedgerDimensionDefaultAccount   ledgerDefaultAccount;
        
        ProjTable projTable = ProjTable::find(ledgerJournalTrans_Project.ProjId);

        if (projTable && ledgerJournalTrans_Project.CategoryId)
        {
            ledgerDefaultAccount = ProjectPosting::getProjectLedgerDimension(projTable,
                                                                            ProjCategory::find(ledgerJournalTrans_Project.CategoryId),
                                                                            ProjFundingSource::findCustAccount(projtable.ProjInvoiceProjId),
                                                                            ProjLineProperty::find(ledgerJournalTrans_Project.LinePropertyId),
                                                                            false);
        }

        if(ledgerJournalTrans.AccountType == LedgerJournalACType::Project)
        {
            ledgerJournalTrans.AKALedgerDefaultDimension = LedgerDimensionFacade::serviceCreateLedgerDimension(ledgerDefaultAccount);
            ledgerJournalTrans.AKALedgerDefaultAccountType      = LedgerJournalACType::Ledger;
        }
        else if(ledgerJournalTrans.OffsetAccountType == LedgerJournalACType::Project)
        {
            ledgerJournalTrans.AKALedgerOffsetDefaultDimension = LedgerDimensionFacade::serviceCreateLedgerDimension(ledgerDefaultAccount);
            ledgerJournalTrans.AKALedgerOffsetDefaultAccountType      = LedgerJournalACType::Ledger;
        }

// ... (truncated)
```

---

*Generated on 2025-10-17 15:42*
