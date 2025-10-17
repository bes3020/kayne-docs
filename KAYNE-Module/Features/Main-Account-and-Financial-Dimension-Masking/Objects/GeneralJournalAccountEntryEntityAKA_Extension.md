# AxClass: GeneralJournalAccountEntryEntityAKA_Extension

[← Back to Main Account and Financial Dimension Masking](../README.md)

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| getDisplayValueMask | ✓ | str | none |

## Declaration Code

```xpp

[ExtensionOf(dataentityviewstr(GeneralJournalAccountEntryEntity))]
public final class GeneralJournalAccountEntryEntityAKA_Extension
{
}

```

## Key Methods Source

### getDisplayValueMask

```xpp

    public static str getDisplayValueMask()
    {
        str sql = "CASE WHEN T3.%2 IN (Select MainAccountID from AKAMainAccountsMaskTable) " +
                  "THEN REPLACE(%3, T3.%4, 'XXXX') " +
                    "ELSE %3 END" ;

        sql = strFmt(sql,
            tablestr(DimensionCombinationEntity),
            fieldStr(DimensionCombinationEntity, MainAccount),
            fieldStr(DimensionCombinationEntity, DisplayValue),
            fieldStr(DimensionCombinationEntity, People)
            );
                               
        return sql;
    }


```

---

*Generated on 2025-10-17 15:42*
