# AxClass: DocuViewExtensionAKA

[← Back to Document Attachment View Enhancements](../README.md)

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| DocuView_ShowDefaultAttachmentField | ✓ | void | none |
| Docu_OnCopy | ✓ | void | none |

## Declaration Code

```xpp

class DocuViewExtensionAKA
{
    

}

```

## Key Methods Source

### DocuView_ShowDefaultAttachmentField

```xpp

    [SubscribesTo(formStr(DocuView), delegatestr(DocuView, ShowDefaultAttachmentField))]
    public static void DocuView_ShowDefaultAttachmentField(Common _testCursor, EventHandlerResult _eventHandlerResult)
    {
        switch (_testCursor.TableId)
        {
            case tableNum(LedgerJournalTrans):
                LedgerJournalTrans ledgerJournalTrans = _testCursor;
                if(ledgerJournalTrans.AccountType == LedgerJournalACType::Vend || ledgerJournalTrans.OffsetAccountType == LedgerJournalACType::Vend)
                {
                    _eventHandlerResult.booleanResult(true);
                }
                break;
        }
    }


```

### Docu_OnCopy

```xpp

    [SubscribesTo(classStr(Docu), delegateStr(Docu, OnCopy))]
    public static void Docu_OnCopy(DocuRef _orig, DocuRef _new)
    {
        if(_orig.RefTableId == tableNum(LedgerJournalTrans) && _new.RefTableId == tableNum(VendInvoiceJour))
        {            
            if(_orig.DefaultAttachment)
            {
                _new.selectForUpdate();
                _new.DefaultAttachment = _orig.DefaultAttachment;
                _new.update();
            }
        }
    }


```

---

*Generated on 2025-10-17 15:42*
