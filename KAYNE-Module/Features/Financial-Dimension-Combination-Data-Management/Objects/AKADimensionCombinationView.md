# AxView: AKADimensionCombinationView

[← Back to Financial Dimension Combination Data Management](../README.md)

## Fields

| Field Name | Type | Mandatory | Description |
|------------|------|-----------|-------------|
| AccountStructure | N/A |  |  |
| RecordId | N/A |  |  |
| DisplayValue | N/A |  |  |
| AccountValue | N/A |  |  |

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| displayValue | ✓ | str | none |
| getCombinationDisplayValue | ✓ | str | none |
| accountValue | ✓ | str | none |
| getValueColumnForDimensionAttributeSql | ✓ | str | none |

## Declaration Code

```xpp

public class AKADimensionCombinationView extends common
{




}

```

## Key Methods Source

### displayValue

```xpp

    private static server str displayValue()
    {
        str displayValueSql;
        str accountDelimiterSql;
        str accountDelimiterEscapedSql;

        SysDictEnum delimiterDictEnum = new SysDictEnum(enumnum(DimensionSegmentDelimiter));
        int enumValue = delimiterDictEnum.firstValue();

        for (int i = 1; i <= delimiterDictEnum.values(); i++)
        {
            str enumLabel = delimiterDictEnum.index2Label(enumValue);
            accountDelimiterSql += strfmt(
                "WHEN %1 THEN '%2'\n", delimiterDictEnum.index2Value(enumValue), enumLabel);

            accountDelimiterEscapedSql += strfmt(
                "WHEN %1 THEN '%2'\n", delimiterDictEnum.index2Value(enumValue), DimensionCombinationEntity::generateEscapedDelimiter(enumLabel));
            enumValue = delimiterDictEnum.nextValue(enumValue);
        }


        // Get the list of all dimension attributes that have metadata columns.
        str dimensionValueColumns = DimensionSchemaAndDataSynchronizationUtility::getSynchronizedDimensionValueColumnNames(
            tablestr(DimensionAttributeValueCombination));

        // Detect default accounts.
        str regularAccountCondition = strFmt('T1.LEDGERDIMENSIONTYPE != %1', enum2int(LedgerDimensionType::DefaultAccount));

        // Detect dynamic accounts.
        Set keyColumnSet =
            DimensionSchemaAndDataSynchronizationUtility::getSynchronizedSystemGeneratedDimensionAttributeKeyColumns(
                tableStr(DimensionAttributeValueCombination));
        SetEnumerator keyColumn = keyColumnSet.getEnumerator();

        while (keyColumn.moveNext())
        {
            regularAccountCondition += strFmt('\nAND %1 = 0', keyColumn.current());
        }

        if (strLen(dimensionValueColumns) == 0)
        {
            // No table extension columns.
            displayValueSql = @"''";
        }
        else
        {
            str errorMessage = strReplace("@Dimension:DimensionEntitiesDimensionStructureNotCreated", "'", "''");
            LanguageId systemLanguageId = SystemParameters::find().SystemLanguageId;


// ... (truncated)
```

### getCombinationDisplayValue

```xpp

    /// <summary>
    /// Gets the displayValue for a dimension entity.
    /// </summary>
    /// <param name = "_entityName">The name of the entity containing the dimension field for which a display value is needed.</param>
    /// <param name = "_propertyName">The name of the dimension field for which a display value is needed.</param>
    /// <param name = "_attributeNames">The names of the dimensions.</param>
    /// <param name = "_attributeValues">The values of the dimensions.</param>
    /// <param name = "_ledgerJournalACType">The type of the dynamic dimension.</param>
    /// <returns>A string of dimension values separated by the dimension segment delimiter.</returns>
    [SysODataActionAttribute("getCombinationDisplayValue", false),
    SysODataCollectionAttribute("_attributeNames", Types::String),
    SysODataCollectionAttribute("_attributeValues", Types::String),
    SysODataCollectionAttribute("return", Types::String)]
    public static str getCombinationDisplayValue(str _entityName, str _propertyName, array _attributeNames, array _attributeValues, LedgerJournalACType _ledgerJournalACType)
    {
        var entityMetadata = ExportToExcelMetadataCache::getEntityByPublicName(_entityName);

        if (entityMetadata != null)
        {
            _entityName = entityMetadata.Name;
        }

        SysDictField dimensionField = SysDictField::findFieldByName(_entityName, _propertyName);

        ExtendedDataTypeName extendedTypeName = dimensionField.typeName();

        return DimensionResolver::getEntityDisplayValue(_attributeNames, _attributeValues, extendedTypeName, _ledgerJournalACType);
    }


```

### accountValue

```xpp

    /// <summary>
    /// Generates the sql to populate the system generated view field.
    /// </summary>
    private static server str accountValue()
    {
        str displayValueSql;
        str systemGeneratedValueColumns;
        DimensionAttribute  dimensionAttribute;

        while select * from dimensionAttribute
            where dimensionAttribute.Type == DimensionAttributeType::DynamicAccount
        {
            if (dimensionAttribute
            && dimensionAttribute.getStatus() != DimensionAttributeStatus::Inactive
            && fieldName2id(tableNum(DimensionAttributeValueCombination), dimensionAttribute.DimensionKeyColumnName) != 0
            && fieldName2id(tableNum(DimensionAttributeValueCombination), dimensionAttribute.DimensionValueColumnName) != 0
            && fieldName2id(tableNum(DimensionAttributeValueSet), dimensionAttribute.DimensionKeyColumnName) != 0
            && fieldName2id(tableNum(DimensionAttributeValueSet), dimensionAttribute.DimensionValueColumnName) != 0)
            {
                systemGeneratedValueColumns += strFmt(@"
                   WHEN (T1.%1 != '') THEN T1.%1", dimensionAttribute.DimensionValueColumnName);
            }
        }

        // If no system generated columns exist, default to use the DisplayValue column.

        if (strLen(systemGeneratedValueColumns) == 0)
        {
            displayValueSql = strFmt('T1.%1', strUpr(fieldStr(DimensionAttributeValueCombination, DisplayValue)));
        }
        else
        {
            displayValueSql = strFmt(@" CASE %1 ELSE '' END ", systemGeneratedValueColumns);
        }

        return displayValueSql;
    }


```

---

*Generated on 2025-10-17 15:42*
