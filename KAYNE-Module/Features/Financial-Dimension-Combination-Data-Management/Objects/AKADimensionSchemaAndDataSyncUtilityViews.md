# AxClass: AKADimensionSchemaAndDataSyncUtilityViews

[← Back to Financial Dimension Combination Data Management](../README.md)

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| getViewDimensionAttributeValueColumnSql | ✓ | str | none |

## Declaration Code

```xpp

class AKADimensionSchemaAndDataSyncUtilityViews
{

}

```

## Key Methods Source

### getViewDimensionAttributeValueColumnSql

```xpp

    public static str getViewDimensionAttributeValueColumnSql(TableName _dataEntityName, TableId _tableId, MethodName _methodName)
    {
        str sql = SysComputedColumn::returnLiteral('');

        // Get the metadata for the data entity extension.
        var metadataProvider = new Microsoft.Dynamics.AX.Framework.Analytics.Runtime.AggregateQueryController().get_MetadataProvider();
        var extension = metadataProvider.get_ViewExtensions().Read(
            _dataEntityName + '.' + DimensionMetadataConstants::DimensionDataEntityExtensionName);

        if (extension != null)
        {
            // Get the field names for all the computed fields that point to the specified computed column method.
            Array fieldNames = new Array(Types::String);
            var fields = extension.get_Fields().GetEnumerator();

            while (fields.MoveNext())
            {
                // Get the field if it is of the relevant type.
                var field = fields.get_Current() as Microsoft.Dynamics.AX.Metadata.MetaModel.AxViewFieldComputedString;

                if (field != null && field.get_ViewMethod() == _methodName)
                {
                    // Add to the end of the list.
                    fieldNames.value(fieldNames.lastIndex() + 1, field.get_Name());
                }
            }

            // Get the session local cache instance.
            SysGlobalCache cache = classFactory.globalCache();

            if (fieldNames.lastIndex() > 0)
            {
                // Get the current field, falling back to the first field.
                int currentFieldOrdinal = cache.get(_dataEntityName, _methodName, 1);

                // Get the field name from the list.
                FieldName targetField = fieldNames.value(currentFieldOrdinal);

                if (currentFieldOrdinal >= fieldNames.lastIndex())
                {
                    // It should not be possible to iterate past the last field,
                    // as the current field index should have been set back to 1.
                    Debug::assert(currentFieldOrdinal == fieldNames.lastIndex());

                    // Loop back around to the first element for the next time the entity is synchronized.
                    cache.set(_dataEntityName, _methodName, 1);
                }
                else
                {

// ... (truncated)
```

---

*Generated on 2025-10-17 15:42*
