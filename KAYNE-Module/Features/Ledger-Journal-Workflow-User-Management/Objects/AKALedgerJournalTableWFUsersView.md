# AxView: AKALedgerJournalTableWFUsersView

[← Back to Ledger Journal Workflow User Management](../README.md)

## Fields

| Field Name | Type | Mandatory | Description |
|------------|------|-----------|-------------|
| JournalNum | N/A |  |  |
| WFUsers | N/A |  |  |

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| getWorkflowApprovalUser | ✓ | str | none |

## Declaration Code

```xpp

public class AKALedgerJournalTableWFUsersView extends common
{
}

```

## Key Methods Source

### getWorkflowApprovalUser

```xpp

    private static str getWorkflowApprovalUser()
    {
        str sql =
        "SELECT REVERSE(STUFF(REVERSE((SELECT %1.%2 + ', '"+
            " FROM %1 " +
               " JOIN %3" +
                  " ON %3.%4 = %1.%5" +
                     " AND %3.%6 = %1.%7" +
                     " AND %3.%8 = %9" +
					 " AND %3.%10 = %11" +
				     " AND %3.%12 = %13" +
					 " WHERE %1.%14 = %15" +
             " for xml path(''))), 1, 2, ''))"
                  ;
   
        str recIdField = SysComputedColumn::returnField(
                                tablestr(AKALedgerJournalTableWFUsersView),
                                dataEntityDataSourceStr(AKALedgerJournalTableWFUsersView, LedgerJournalTable),
                                fieldstr(LedgerJournalTable, RecId));

        str partitionField = SysComputedColumn::returnField(
                                tablestr(AKALedgerJournalTableWFUsersView),
                                dataEntityDataSourceStr(AKALedgerJournalTableWFUsersView, LedgerJournalTable),
                                fieldstr(LedgerJournalTable, Partition));

        sql = strFmt(sql,
            tablestr(WorkflowWorkItemTable), //1
            fieldStr(WorkflowWorkItemTable, UserId), //2
            tablestr(WorkflowTrackingStatusTable), //3
            fieldStr(WorkflowTrackingStatusTable, CorrelationId), //4
            fieldStr(WorkflowWorkItemTable, CorrelationId), //5
            fieldStr(WorkflowTrackingStatusTable, Partition), //6
            fieldStr(WorkflowWorkItemTable, Partition), //7
            fieldStr(WorkflowTrackingStatusTable, ContextRecId), //8
            recIdField, // 9
            fieldStr(WorkflowTrackingStatusTable, ContextTableId), //10
            tableNum(LedgerJournalTable), //11
            fieldStr(WorkflowTrackingStatusTable, Partition), //12
            partitionField, //13
			fieldStr(WorkflowWorkItemTable, Status), //14
			any2Int(WorkflowWorkItemStatus::Pending) //15
            );

        return sql;
                        
    }


```

---

*Generated on 2025-10-17 15:42*
