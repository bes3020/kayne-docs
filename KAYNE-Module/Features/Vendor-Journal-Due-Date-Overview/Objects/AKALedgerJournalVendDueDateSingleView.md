# AxView: AKALedgerJournalVendDueDateSingleView

[← Back to Vendor Journal Due Date Overview](../README.md)

## Fields

| Field Name | Type | Mandatory | Description |
|------------|------|-----------|-------------|
| JournalNum | N/A |  |  |
| DueDate | N/A |  |  |

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| computedDueDate | ✓ | str | none |

## Declaration Code

```xpp

public class AKALedgerJournalVendDueDateSingleView extends common
{
}

```

## Key Methods Source

### computedDueDate

```xpp

    public static str computedDueDate()
    {
        TableName viewName = viewstr(AKALedgerJournalVendDueDateSingleView);

        return SysComputedColumn::if(
            SysComputedColumn::equalExpression(
                SysComputedColumn::returnField(viewName, identifierStr(AKALedgerJournalVendDueDateMinMaxView), identifierStr(DueDateMin)),
                SysComputedColumn::returnField(viewName, identifierStr(AKALedgerJournalVendDueDateMinMaxView), identifierStr(DueDateMax))	),
            SysComputedColumn::returnField(viewName, identifierStr(AKALedgerJournalVendDueDateMinMaxView), identifierStr(DueDateMin)),
            SysComputedColumn::returnLiteral(dateNull())
            );            
    }


```

---

*Generated on 2025-10-17 15:42*
