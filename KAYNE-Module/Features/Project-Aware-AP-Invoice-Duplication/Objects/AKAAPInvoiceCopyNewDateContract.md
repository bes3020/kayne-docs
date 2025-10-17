# AxClass: AKAAPInvoiceCopyNewDateContract

[← Back to Project-Aware AP Invoice Duplication](../README.md)

## Description

<summary> Data Contract class for AP open invoices </summary>

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| parmAsOfDate |  | TransDate | none |
| parmDateForUpdate |  | TransDate | none |
| parmProject |  | AKA_ProjectType | none |
| validate |  | boolean | none |

## Declaration Code

```xpp

/// <summary>
/// Data Contract class for AP open invoices
/// </summary>
[DataContract]
public class AKAAPInvoiceCopyNewDateContract implements SysOperationValidatable
{
    TransDate      asOfDate, dateForUdpate;
    AKA_ProjectType project;
 
}

```

## Key Methods Source

### parmAsOfDate

```xpp

    [DataMember,
    SysOperationLabel(literalstr("@AKA:InvoiceAsofDateText")),
    SysOperationHelpText(literalstr("@AKA:InvoiceAsofDateHT")),
    SysOperationDisplayOrder('1')]
    public TransDate parmAsOfDate(TransDate _asOfDate = asOfDate)
    {
        asOfDate = _asOfDate;
        return asOfDate;
    }


```

### parmDateForUpdate

```xpp

    [DataMember,
    SysOperationLabel(literalstr("@AKA:InvoiceDateForUpdate")),
    SysOperationHelpText(literalstr("@AKA:InvoiceDateForUpdateHT")),
    SysOperationDisplayOrder('2')]
    public TransDate parmDateForUpdate(TransDate _dateForUdpate = dateForUdpate)
    {
        dateForUdpate = _dateForUdpate;
        return dateForUdpate;
    }


```

### parmProject

```xpp

    [DataMember,
    SysOperationLabel(literalstr("Project")),
    SysOperationDisplayOrder('3')]
    public AKA_ProjectType parmProject(AKA_ProjectType _project = project)
    {
        project = _project;
        return project;
    }


```

---

*Generated on 2025-10-17 15:42*
