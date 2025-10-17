# AxDataEntityView: AKAVendTransAttachmentEntity

[← Back to Vendor Transaction Attachment Data Management](../README.md)

## Fields

| Field Name | Type | Mandatory | Description |
|------------|------|-----------|-------------|
| VendAccount | N/A |  |  |
| Invoice | N/A |  |  |
| InvoiceDate | N/A |  |  |
| Voucher | N/A |  |  |
| Amount | N/A |  |  |
| FileName | N/A |  |  |
| FileContents | N/A |  |  |
| VendorName | N/A |  |  |
| PaymentDate | N/A |  |  |
| CheckNumber | N/A |  |  |
| PaymMethod | N/A |  |  |
| VendInvoiceRecId | N/A |  |  |
| VendPaymentRecId | N/A |  |  |
| DocumentId | N/A |  |  |
| WorkflowApprovalUserId | N/A |  |  |
| VendSettlementRecId | N/A |  |  |
| Company | N/A |  |  |
| FileType | N/A |  |  |
| Notes | N/A |  |  |
| WorkflowApprovalDateTime | N/A |  |  |

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| postLoad |  | void | none |
| getWorkflowApprovalUser | ✓ | str | none |
| getWorkflowApprovalDateTime | ✓ | str | none |

## Declaration Code

```xpp

public class AKAVendTransAttachmentEntity extends common
{
}

```

## Key Methods Source

### postLoad

```xpp

    public void postLoad()
    {
        super();

        // Virtual fields are not auto-populated from the base entity, so an extra select is necessary.
        if (this.RecId && this.DocumentId != emptyGuid())
        {
			try 
            {
				DocuRefEntity baseEntity;
				select firstonly baseEntity where baseEntity.DocumentId == this.DocumentId;
				this.FileContents = baseEntity.FileContents;
				this.fieldExternallySet(fieldNum(AKAVendTransAttachmentEntity, FileContents), false);
            }
            catch 
            {
                Filename fileName = this.FileName;
                if (fileName && this.FileType)
                {
                    fileName += '.' + this.FileType;
                }

                this.FileName = strFmt("@AKA:FileCantBeDownloaded", fileName);
                this.FileType = '';
            }
        }

        if (this.FileName && this.FileType)
        {
            this.FileName = this.FileName + '.' + this.FileType;
        }
    }


```

### getWorkflowApprovalUser

```xpp

    private static str getWorkflowApprovalUser()
    {
        str sql = 
        "SELECT REVERSE(STUFF(REVERSE((SELECT %1.%2 + ', '"+
            " FROM %3 " +
               " JOIN %5" +
                  " ON %5.%6 = %3.%4" +
                     " AND %5.%8 = %3.%24" +
				     " AND %5.%25 = %3.%26" +
               " JOIN %9" +
                 " ON %5.%7 = %9.%10" +
                " AND %9.%31 = %5.%25" +
               " JOIN %1" +
                  " ON %1.%16 =" +
                    " %9.%11" +
				" AND %1.%32 = %9.%31" +
               " JOIN %14" +
                 " ON %14.%15 = %1.%17" +
				 " AND %14.%33 = %1.%32" +
                    " WHERE  %9.%12 = %5.%8" +
               " AND %9.%13 = %22" +
			  " AND %3.%27 = %28" +
              " AND %3.%29 = %30" +
               " AND %1.%18 = %23" +
            " order by %1.%19 desc " +
             "for xml path(''))), 1, 2, ''))"
				  ;
			
        str invoiceField = SysComputedColumn::returnField(
                                tablestr(AKAVendTransAttachmentEntity),
                                dataEntityDataSourceStr(AKAVendTransAttachmentEntity, VendTrans),
                                fieldstr(VendTrans, Invoice));
        
		str recIdField = SysComputedColumn::returnField(
                                tablestr(AKAVendTransAttachmentEntity),
                                dataEntityDataSourceStr(AKAVendTransAttachmentEntity, VendTrans),
                                fieldstr(VendTrans, RecId));

        str partitionField = SysComputedColumn::returnField(
                                tablestr(AKAVendTransAttachmentEntity),
                                dataEntityDataSourceStr(AKAVendTransAttachmentEntity, VendTrans),
                                fieldstr(VendTrans, Partition));


        sql = strFmt(sql, 
            tablestr(WorkflowTrackingTable), //1
            "user_", //2
            tablestr(VendTrans), //3
            fieldStr(VendTrans, JournalNum), //4

// ... (truncated)
```

### getWorkflowApprovalDateTime

```xpp

    private static str getWorkflowApprovalDateTime()
    {
        
        str sql =
        "SELECT REVERSE(STUFF(REVERSE((SELECT FORMAT(%1.%2, 'M/d/yyyy hh:mm:s tt') + ', '"+
            " FROM %3 " +
               " JOIN %5" +
                  " ON %5.%6 = %3.%4" +
                     " AND %5.%8 = %3.%24" +
                     " AND %5.%25 = %3.%26" +
               " JOIN %9" +
                 " ON %5.%7 = %9.%10" +
                " AND %9.%31 = %5.%25" +
               " JOIN %1" +
                  " ON %1.%16 =" +
                    " %9.%11" +
                " AND %1.%32 = %9.%31" +
               " JOIN %14" +
                 " ON %14.%15 = %1.%17" +
                 " AND %14.%33 = %1.%32" +
                    " WHERE  %9.%12 = %5.%8" +
               " AND %9.%13 = %22" +
              " AND %3.%27 = %28" +
              " AND %3.%29 = %30" +
               " AND %1.%18 = %23" +
            " order by %1.%19 desc " +
             "for xml path(''))), 1, 2, ''))"
                  ;
   
        str invoiceField = SysComputedColumn::returnField(
                                tablestr(AKAVendTransAttachmentEntity),
                                dataEntityDataSourceStr(AKAVendTransAttachmentEntity, VendTrans),
                                fieldstr(VendTrans, Invoice));
        
        str recIdField = SysComputedColumn::returnField(
                                tablestr(AKAVendTransAttachmentEntity),
                                dataEntityDataSourceStr(AKAVendTransAttachmentEntity, VendTrans),
                                fieldstr(VendTrans, RecId));

        str partitionField = SysComputedColumn::returnField(
                                tablestr(AKAVendTransAttachmentEntity),
                                dataEntityDataSourceStr(AKAVendTransAttachmentEntity, VendTrans),
                                fieldstr(VendTrans, Partition));


        sql = strFmt(sql,
            tablestr(WorkflowTrackingTable), //1
            fieldStr(WorkflowTrackingTable, CreatedDateTime), //2
            tablestr(VendTrans), //3

// ... (truncated)
```

---

*Generated on 2025-10-17 15:42*
