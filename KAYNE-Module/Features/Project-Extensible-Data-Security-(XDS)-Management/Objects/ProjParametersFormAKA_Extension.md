# AxClass: ProjParametersFormAKA_Extension

[← Back to Project Extensible Data Security (XDS) Management](../README.md)

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| ProjParameters_AKAProjXDSEnabled_OnClicked | ✓ | void | none |

## Declaration Code

```xpp

[ExtensionOf(formStr(ProjParameters))]
final class ProjParametersFormAKA_Extension
{
    
}

```

## Key Methods Source

### ProjParameters_AKAProjXDSEnabled_OnClicked

```xpp

    /// <summary>
    ///
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    [FormControlEventHandler(formControlStr(ProjParameters, ProjParameters_AKAProjXDSEnabled), FormControlEventType::Clicked)]
    public static void ProjParameters_AKAProjXDSEnabled_OnClicked(FormControl sender, FormControlEventArgs e)
    {
        ProjParameters projParameters = sender.formRun().dataSource(formDataSourceStr(ProjParameters, ProjParameters)).cursor();
        if(projParameters.AKAProjXDSEnabled)
        {
            AKAXDSProjUtilities::enablePolicies();
        }
		else
        {
            AKAXDSProjUtilities::disablePolicies();
        }
    }


```

---

*Generated on 2025-10-17 15:42*
