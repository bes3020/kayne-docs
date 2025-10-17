# AxClass: DimensionFocusNameTmpAKA_Extension

[← Back to Main Account and Financial Dimension Masking](../README.md)

## Description

<summary> This class <c> DimensionFocusNameTmpAKA_Extension </c> is an extension of DimensionFocusNameTmp table </summary>

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| generateFocusDescriptions | ✓ | void | none |

## Declaration Code

```xpp

/// <summary>
///		This class <c> DimensionFocusNameTmpAKA_Extension </c> is an extension of DimensionFocusNameTmp table
/// </summary>
/// Rchilukuri : 922 - Mask Financial dimension values for selected Main accounts
[ExtensionOf(tablestr(DimensionFocusNameTmp))]
final public class DimensionFocusNameTmpAKA_Extension
{
}

```

## Key Methods Source

### generateFocusDescriptions

```xpp

    /// <summary>
    ///		This method is COC to Mask person dimension value for selected main accounts
    /// </summary>
    /// <param name="_tmp">
    ///		The <c>DimensionFocusNameTmp</c> table buffer.
    /// </param>
    /// <param name="_dimensionFocusName">
    ///		The dimension focus name.
    /// </param>
    /// <param name="_connection">
    ///		The database connection.
    /// </param>
    /// Rchilukuri : 922 - Mask Financial dimension values for selected Main accounts
    public static void generateFocusDescriptions(DimensionFocusNameTmp _tmp, Name _dimensionFocusName, Connection _connection)
    {
        DimensionHierarchy			dimHierarchy;
        DimensionAttribute			dimAttr;
        AKAMainAccountsMaskTable	mainAccountsMask;
        int							levelCount;
        boolean						isPersonDimAvailable;

        next generateFocusDescriptions(_tmp, _dimensionFocusName, _connection);

        if(!LedgerParameters::allowedPeopleUserGroupAccess())
        {
            //Check Person dimension available in financial dimension set
            dimHierarchy			= DimensionHierarchy::findByTypeAndName(DimensionHierarchyType::Focus, _dimensionFocusName);
            levelCount				= DimensionHierarchy::getLevelCount(dimHierarchy.RecId);
            isPersonDimAvailable	= false;
            int mainAccountLevel, peopleLevel;

            for (int i = 1; i <= levelCount; i++)
            {
                dimAttr = DimensionAttribute::find(DimensionHierarchyLevel::findByDimensionHierarchyAndLevel(dimHierarchy.RecId, i).DimensionAttribute);
                
                if (dimAttr.DimensionKeyColumnName == "People")
                {
                    isPersonDimAvailable = true;
                    peopleLevel = i;                   
                }

                if (dimAttr.DimensionKeyColumnName == "MainAccount")
                {
                    mainAccountLevel = i;
                }
            }
        
            //If available, mask person dimension value for selected main accounts
            if (isPersonDimAvailable)

// ... (truncated)
```

---

*Generated on 2025-10-17 15:42*
