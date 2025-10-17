# AxClass: AKAUpdateVendorDimension

[← Back to Vendor Financial Dimension Management](../README.md)

## Description

<summary> Bulk update financial dimension on vendor records </summary>

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| main | ✓ | void | none |

## Declaration Code

```xpp

/// <summary>
///		Bulk update financial dimension on vendor records
/// </summary>
/// Rchilukuri : 1962 - Bulk update financial dimension on vendor records
class AKAUpdateVendorDimension
{
}

```

## Key Methods Source

### main

```xpp

    /// <summary>
    ///		Bulk update financial dimension on vendor records
    /// </summary>
    /// <param name = "_args">
	///		The specified arguments.
	/// </param>
    /// Rchilukuri : 1962 - Bulk update financial dimension on vendor records
    public static void main(Args _args)
    {
        DimensionAttributeValueSetStorage	dimAttrValueSetStorage;
        DimensionAttribute					dimAttrVendor;
        DimensionAttributeValue				dimAttrVendValue;
        CompanyInfo							companyInfo;
        VendTable							vendTable;
        container							con;
        int									updatedRecords;

        dimAttrVendor = DimensionAttribute::findByName('Vendor');

        //Iterate all legal entities to update financial dimension on vendors
        while select companyInfo 
        {
            changeCompany(companyInfo.DataArea)
            {
                con = [companyInfo.DataArea];

                ttsbegin;

                while select forupdate crosscompany:con vendTable
                {
                    //Get original default Dimension
                    dimAttrValueSetStorage	= DimensionAttributeValueSetStorage::find(vendTable.DefaultDimension);
     
                    dimAttrVendValue		= DimensionAttributeValue::findByDimensionAttributeAndValue(dimAttrVendor, vendTable.AccountNum, false, true);

                    if (dimAttrVendValue)
                    {
                        // Add the dimensionAttibuteValue to the default dimension
                        dimAttrValueSetStorage.addItem(dimAttrVendValue);

                        vendTable.DefaultDimension = dimAttrValueSetStorage.save();
                        vendTable.update();

                        info(strFmt("@AKA:VendorDefaultDimUpdated", vendTable.AccountNum, vendTable.DataAreaId));

                        updatedRecords++;
                    }
                }


// ... (truncated)
```

---

*Generated on 2025-10-17 15:42*
