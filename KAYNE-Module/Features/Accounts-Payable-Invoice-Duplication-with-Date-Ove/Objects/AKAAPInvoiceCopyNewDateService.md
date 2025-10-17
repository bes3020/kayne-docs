# AxClass: AKAAPInvoiceCopyNewDateService

[← Back to Accounts Payable Invoice Duplication with Date Override](../README.md)

## Description

<summary> This class is use to update the open AP invoices </summary>

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| process |  | void | none |

## Declaration Code

```xpp

/// <summary>
/// This class is use to update the open AP invoices
/// </summary>
public class AKAAPInvoiceCopyNewDateService extends SysOperationServiceBase
{

}

```

## Key Methods Source

### process

```xpp

    /// <summary>
    /// This method is use to process the logic
    /// </summary>
    /// <param name = "_contract">AKAAPInvoiceCopyNewDateContract</param>
    public void process(AKAAPInvoiceCopyNewDateContract _contract)
    { 
        LedgerJournalTrans_Project ledgerJournalTrans_Project, ledgerJournalTrans_Project_Local;
        LedgerJournalTrans  ledgerJournalTrans, ledgerJournalTransLocal;
        LedgerJournalTable  ledgerjournalTable;
        LedgerJournalName   ledgerJournalName;
        int                 counter = 0;
        List JournalNum = new List(Types::String);
        try
        {
            ttsbegin;
            while select ledgerjournalTable
                where ledgerjournalTable.Posted == NoYes::No
                && ledgerjournalTable.UserBlockId == ''
            exists join ledgerJournalName
                where ledgerJournalName.JournalName == ledgerjournalTable.JournalName
                 && ledgerJournalName.JournalType == LedgerJournalType::VendInvoiceRegister
            {
                switch (_contract.parmProject())
                {
                    case AKA_ProjectType::All:

                        while select forupdate ledgerJournalTrans
                            where ledgerJournalTrans.TransDate <= _contract.parmAsOfDate()
                            && ledgerjournalTable.JournalNum == ledgerJournalTrans.JournalNum
                        {
                            ledgerJournalTrans.TransDate  = _contract.parmDateForUpdate();
                            ledgerJournalTrans.doUpdate();

                            select firstonly forupdate ledgerJournalTrans_Project
                                where ledgerJournalTrans_Project.RefRecId == ledgerJournalTrans.RecId;

                            if (ledgerJournalTrans_Project.RecId)
                            {
                                ledgerJournalTrans_Project.ProjTransDate = _contract.parmDateForUpdate();
                                ledgerJournalTrans_Project.doUpdate();
                            }
                            counter++;
                            JournalNum.addEnd(ledgerjournalTable.JournalNum);
                        }

                        break;

                    case AKA_ProjectType::Firm:


// ... (truncated)
```

---

*Generated on 2025-10-17 15:42*
