# AxClass: AKALedgerJournalWFApprSubmitToWF

[← Back to General Ledger Journal Workflow Approval](../README.md)

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| checkJournal |  | boolean | none |
| run |  | void | none |
| main | ✓ | void | none |

## Declaration Code

```xpp

class AKALedgerJournalWFApprSubmitToWF extends LedgerJournalWFApprSubmitToWF
{
}

```

## Key Methods Source

### checkJournal

```xpp

     protected boolean checkJournal(LedgerJournalTable   _ledgerJournalTable)
    {
        boolean ret = true;
        if(_ledgerJournalTable.WorkflowApprovalStatus != LedgerJournalWFApprovalStatus::NotSubmitted)
        {
            return checkFailed(strFmt("@SYS111653", _ledgerJournalTable.JournalName, _ledgerJournalTable.JournalNum));
        }

        LedgerJournalTrans		ledgerJournalTrans;
        LedgerJournalTrans_Asset ledgerJournalTrans_Asset;
            
        while select RecId from ledgerJournalTrans
            where ledgerJournalTrans.JournalNum == _ledgerJournalTable.JournalNum
                && _ledgerJournalTable.JournalType == LedgerJournalType::Assets
                && ledgerJournalTrans.ReasonRefRecID == 0
                join TransType from ledgerJournalTrans_Asset
                    where ledgerJournalTrans_Asset.RefRecId == ledgerJournalTrans.RecId
        {
            if (ledgerJournalTrans && AssetParameters::transTypeRequiresValidation(ledgerJournalTrans_Asset.TransType))
            {
                // The Reason code required.
                return checkFailed (strFmt("@SYS111653", _ledgerJournalTable.JournalName, _ledgerJournalTable.JournalNum)+ '. ' + strFmt("@SYS110217", "@SYS111246"));
            }
        }
        return ret;
    }


```

### run

```xpp

    protected void run()
    {
        TableId                         tableId             = args.dataset();
        LedgerJournalTable              ledgerJournalTable;
        LedgerJournalName               ledgerJournalName ;
        WorkflowCorrelationId           workflowCorrelationId;
        WorkflowComment                 comment;
        WorkflowSubmitDialog            workflowSubmitDialog;
        MultiSelectionHelper			helper;

        FormDataSource					dataSource;

        Debug::assert(tableId == tableNum(LedgerJournalTable));
        Debug::assert(args.record().RecId != 0);
        dataSource = FormDataUtil::getFormDataSource(args.record());

        helper = MultiSelectionHelper::construct();
        helper.parmDatasource(dataSource);
        ledgerJournalTable = helper.getFirst() as LedgerJournalTable;
        
        // The method has not been called correctly.
        if (tableId != tableNum(LedgerJournalTable) ||
           !ledgerJournalTable)
        {
            throw error(strFmt("@SYS19306", funcName()));
        }
        // The journal does support workflow approvals.
        // Capture any comments/notes attached to the submission.
        workflowSubmitDialog = WorkflowSubmitDialog::construct(args.caller().getActiveWorkflowConfiguration());
        workflowSubmitDialog.preDialogRun += eventhandler(this.preWorkflowDialogRun);
        workflowSubmitDialog.run();
                
        if (workflowSubmitDialog.parmIsClosedOK())
        {
            comment = workflowSubmitDialog.parmWorkflowComment();
        }
        else
        {
            return;
        }
       
		while (ledgerJournalTable)
        {
            ledgerJournalName = ledgerJournalTable.ledgerJournalName();

            if (ledgerJournalName.RecId != 0 &&
                ledgerJournalName.checkWorkflowApprovalEnabled())
            {
                if(this.checkJournal(ledgerJournalTable))

// ... (truncated)
```

### main

```xpp

    public static void main(Args _args)
    {
        AKALedgerJournalWFApprSubmitToWF journalWFApprSubmit = new AKALedgerJournalWFApprSubmitToWF();
		
        journalWFApprSubmit.parmArgs(_args);
        journalWFApprSubmit.run();
    }


```

---

*Generated on 2025-10-17 15:42*
