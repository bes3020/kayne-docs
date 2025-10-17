# AxClass: LedgerTransModuleTmpAKA_Extension

[← Back to Extended Ledger Transaction Module Processing (AKA Customization)](../README.md)

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| defaultDimesionDisplayValueMask |  | str | none |

## Declaration Code

```xpp

[ExtensionOf(tableStr(LedgerTransModuleTmp))]
final class LedgerTransModuleTmpAKA_Extension
{
}

```

## Key Methods Source

### defaultDimesionDisplayValueMask

```xpp

   /// <summary>
   /// This method is added for to display the people dimension with mask XXXX
   /// </summary>
   /// <returns> Dimension value</returns>
    public display str defaultDimesionDisplayValueMask()
    {
        DimensionAttributeValueSet           dimensionAttributeValueSet;
        DimensionAttributeValueSetItem		 dimensionAttributeValueSetItem;
        DimensionAttributeValue              dimensionAttributeValue;
        DimensionAttribute                   dimensionAttribute;
        str									 defaultDimesionMask;


        while select  RecId from dimensionAttributeValueSet
            where  dimensionAttributeValueSet.RecId == this.DefaultDimension
                join RecId, DisplayValue from dimensionAttributeValueSetItem
            where dimensionAttributeValueSetItem.DimensionAttributeValueSet == dimensionAttributeValueSet.RecId
                join RecId from dimensionAttributeValue
            where dimensionAttributeValue.RecId == dimensionAttributeValueSetItem.DimensionAttributeValue
                join RecId, Name from dimensionAttribute order by Name asc
            where dimensionAttribute.RecId == dimensionAttributeValue.DimensionAttribute
        {
            if(dimensionattribute.name == 'people')
            {
                dimensionattributevaluesetitem.displayvalue = 'XXXX';
            }
            defaultDimesionMask  += DimensionAttributeValueSetItem.DisplayValue +'--' ;
        }

        return defaultDimesionMask;
    }


```

---

*Generated on 2025-10-17 15:42*
