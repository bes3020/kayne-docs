# AxClass: AKAXDSProjUtilities

[← Back to Project Extensible Data Security (XDS) Management](../README.md)

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| numberOfPoliciesActivated | ✓ | int | none |
| numberOfPolicies | ✓ | int | none |
| disablePolicies | ✓ | void | none |
| createTrackingTable | ✓ | void | none |
| createQueryDimRecord | ✓ | Query | none |
| enablePolicies | ✓ | void | none |
| getPoliciesFromFile | ✓ | List | none |
| createProjRecordQuery | ✓ | Query | none |
| createProjFilterQuery | ✓ | Query | none |
| refreshPolicies | ✓ | void | none |
| Application_Post_securityPolicyFullSync | ✓ | void | none |

## Declaration Code

```xpp

using Microsoft.Dynamics.AX.Metadata.MetaModel;
using MetaModelCore = Microsoft.Dynamics.AX.Metadata.Core.MetaModel;
using Microsoft.Dynamics.AX.Metadata.Core;
using Microsoft.Dynamics.AX.Framework.Analytics.Runtime;
using System.Collections.Generic;

class AKAXDSProjUtilities
{
    public const str policySuffix = 'Policy';
    private const str xdsMyTableName = "AKAXDSMyProjValues";
    private const str projFieldName = "ProjId";

    /*public static DGXDSStatus status()
    {
        if((select count(RecId) from AKAXDSProjModelSecPolRuntimeTracking
            where AKAXDSProjModelSecPolRuntimeTracking.ModelSecPolRecId != 0).recid != 0)
        {
            return DGXDSStatus::Active;
        }
		else
        {
            return DGXDSStatus::Inactive;
        }
    }*/

}

```

## Key Methods Source

### numberOfPoliciesActivated

```xpp

	public static int numberOfPoliciesActivated()
    {
        ModelSecPolRuntimeEx modelSecPolRuntimeEx;
        AKAXDSProjModelSecPolRuntimeTracking tracking;

        select count(RecId) from modelSecPolRuntimeEx
            join tracking
            where modelSecPolRuntimeEx.RecID == tracking.ModelSecPolRecId;

        return modelSecPolRuntimeEx.RecID;
    }


```

### numberOfPolicies

```xpp

    public static int numberOfPolicies()
    {
        return (select count(RecId) from AKAXDSProjModelSecPolRuntimeTracking).recid;
    }


```

### disablePolicies

```xpp

    public static void disablePolicies()
    {
        ttsbegin;

        ModelSecPolRuntimeEx modelSecPolRuntimeEx;
        AKAXDSProjModelSecPolRuntimeTracking tracking;

        delete_from modelSecPolRuntimeEx
            exists join tracking 
            where modelSecPolRuntimeEx.RecID == tracking.ModelSecPolRecId;

		update_recordset tracking setting ModelSecPolRecId = 0;

        ttscommit;
    }


```

---

*Generated on 2025-10-17 15:42*
