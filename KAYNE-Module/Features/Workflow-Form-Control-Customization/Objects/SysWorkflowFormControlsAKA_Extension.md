# AxClass: SysWorkflowFormControlsAKA_Extension

[← Back to Workflow Form Control Customization](../README.md)

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| showSubmit |  | void | none |

## Declaration Code

```xpp

[ExtensionOf(classStr(SysWorkflowFormControls))]
final public class SysWorkflowFormControlsAKA_Extension
{
    
}

```

## Key Methods Source

### showSubmit

```xpp

    public void showSubmit(WorkflowVersionTable _versionTable)
    {
       
        next showSubmit(_versionTable);
        
        if(actionBarSubmitButton && actionBarButtonGroup && actionBarSubmitButton.menuItemName() == menuItemActionStr(VendInvRegisterWFApprSubmitToWF))
        {
            actionBarSubmitButton.multiselect(true);
            actionBarButtonGroup.multiselect(true);
        }
    }


```

---

*Generated on 2025-10-17 15:42*
