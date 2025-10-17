# AxClass: AKAAPInvoiceCopyNewDateController

[← Back to AP Invoice Copy with New Date](../README.md)

## Description

<summary> The <c>AKAAPInvoiceCopyNewDateController</c> class is a controller class used to update open ap invoices. </summary>

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| new |  | void | none |
| defaultCaption |  | ClassDescription | none |
| construct | ✓ | AKAAPInvoiceCopyNewDateController | none |
| main | ✓ | void | none |

## Declaration Code

```xpp

/// <summary>
///     The <c>AKAAPInvoiceCopyNewDateController</c> class is a controller class used to update open ap invoices.
/// </summary>
public class AKAAPInvoiceCopyNewDateController extends SysOperationServiceController
{
}

```

## Key Methods Source

### new

```xpp

    protected void new()
    {
        super(classStr(AKAAPInvoiceCopyNewDateService), methodStr(AKAAPInvoiceCopyNewDateService, process), SysOperationExecutionMode::Synchronous);
    }


```

### defaultCaption

```xpp

    public ClassDescription defaultCaption()
    {
        return "@AKA:UpdateAPInvoices";
    }


```

### construct

```xpp

    public static AKAAPInvoiceCopyNewDateController construct(SysOperationExecutionMode _executionMode = SysOperationExecutionMode::Synchronous)
    {
        AKAAPInvoiceCopyNewDateController controller;
        controller = new AKAAPInvoiceCopyNewDateController();
        controller.parmExecutionMode(_executionMode);
        return controller;
    }


```

---

*Generated on 2025-10-17 15:42*
