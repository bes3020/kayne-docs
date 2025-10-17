# AxView: AKADimensionCombinationMaskView

[← Back to Main Account and Financial Dimension Masking](../README.md)

## Fields

| Field Name | Type | Mandatory | Description |
|------------|------|-----------|-------------|
| RecordId | N/A |  |  |
| DisplayValue | N/A |  |  |
| People | N/A |  |  |
| MainAccount | N/A |  |  |
| DisplayValueMask | N/A |  |  |

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| getDisplayValueMask | ✓ | str | none |
| getPeopleValue | ✓ | str | none |

## Declaration Code

```xpp

public class AKADimensionCombinationMaskView extends common
{
}

```

## Key Methods Source

### getDisplayValueMask

```xpp

    /// <summary>
    ///		Mask financial dimension values for selected main accounts
    /// </summary>
    /// <returns>
    ///		Returns Mask financial dimension values for selected main accounts
	/// </returns>
    /// Rchilukuri : 922 - Mask Financial dimension values for selected Main accounts
    public static str getDisplayValueMask()
    {
        str sql = "CASE WHEN T1.%2 IN (Select MainAccountID from AKAMainAccountsMaskTable where Partition = 5637144576) " +
                  "THEN REPLACE(%3, (SELECT TOP 1 PEOPLEVALUE FROM DIMENSIONATTRIBUTEVALUECOMBINATION where PARTITION = 5637144576 AND T1.RECID = RECID), 'XXXX') " +
                    "ELSE %3 END" ;

        sql = strFmt(sql,
            tablestr(DimensionAttributeValueCombination),
            fieldStr(DimensionAttributeValueCombination, MainAccountValue),
            fieldStr(DimensionAttributeValueCombination, DisplayValue)
            );

        return sql;
    }


```

### getPeopleValue

```xpp

    /// <summary>
    ///
    /// </summary>
    public static str getPeopleValue()
    {
        return "SELECT TOP 1 PEOPLEVALUE FROM DIMENSIONATTRIBUTEVALUECOMBINATION where PARTITION = 5637144576 AND T1.RECID = RECID";
    }


```

---

*Generated on 2025-10-17 15:42*
