# AxClass: AKAXDSProjMetadataProvider

[← Back to Project Extensible Data Security (XDS) Management](../README.md)

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| getProjTablesAndViews | ✓ | List | none |
| getTables | ✓ | System.Collections.IList | none |
| getViewNames | ✓ | System.Collections.IList | none |
| getExtendedDatatypeNames | ✓ | System.Collections.IList | none |
| init |  | void | none |
| getProjTablesAndFields |  | void | none |
| getProjViewsAndFields |  | void | none |
| getProjEdts |  | Map | none |

## Declaration Code

```xpp

using Microsoft.Dynamics365.LocalizationFramework;
using Microsoft.Dynamics365.LocalizationFramework.Metadata;
using System.Linq;
using System.Collections;
using Microsoft.Dynamics.AX.Metadata.Kernel;

class AKAXDSProjMetadataProvider
{
    Map projEdts;
    public List projTablesAndViews;

}

```

## Key Methods Source

### getProjTablesAndViews

```xpp

    public static List getProjTablesAndViews()
    {
        AKAXDSProjMetadataProvider provider = new AKAXDSProjMetadataProvider();

        provider.init();
        provider.getProjTablesAndFields();
        provider.getProjViewsAndFields();

        return provider.projTablesAndViews;
    }


```

### getTables

```xpp

    internal static System.Collections.IList getTables()
    {
        return Microsoft.Dynamics.Ax.Xpp.MetadataSupport::GetAllTables() as System.Collections.IList;
    }


```

### getViewNames

```xpp

    internal static System.Collections.IList getViewNames()
    {
        return Accessor::GetViewNames() as System.Collections.IList;
    }


```

---

*Generated on 2025-10-17 15:42*
