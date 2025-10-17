# AxClass: ProjInvoiceProposalGenAPAKA_Extension

[← Back to APAKA Project Invoice Proposal Customization](../README.md)

## Description

<summary> This class <c>ProjInvoiceProposalGenAPAKA_Extension</c> is an extension of ProjInvoiceProposalGenAP class </summary>

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| AKAgetFundingSourceDimension |  | DimensionDynamicAccount | none |

## Declaration Code

```xpp

/// <summary>
///     This class <c>ProjInvoiceProposalGenAPAKA_Extension</c> is an extension of ProjInvoiceProposalGenAP class
/// </summary>
/// Rchilukuri : 916 - AKA_ProjectInvoiceProposalsAndRecalc
[ExtensionOf(classStr(ProjInvoiceProposalGenAP))]
final class ProjInvoiceProposalGenAPAKA_Extension
{
    

}

```

## Key Methods Source

### AKAgetFundingSourceDimension

```xpp

    /// <summary>
    ///     Gets dimension from project funding source in the source legal entity
    /// </summary>
    /// <param name = "_projCostTrans">
    ///     The _projCostTrans record
    /// </param>
    /// <param name = "_projCostTransCost">
    ///     The _projCostTransCost record
    /// </param>
    /// <returns>
    ///     Returns dimension from project funding source
    /// </returns>
    /// Rchilukuri : 916 - AKA_ProjectInvoiceProposalsAndRecalc
    //protected DimensionDynamicAccount replaceCompanySpecificDimensions(ProjCostTrans _projCostTrans, ProjCostTransCost _projCostTransCost)
    //{
    //    DimensionAttributeValueSetStorage   dimAttrSetStorage;
    //    DimensionAttributeValueSetStorage   dimAttrSetStorageNew;
    //    DimensionAttribute                  dimensionAttribute;
    //    DimensionAttributeValue             dimAttrValue;
    //    DimensionDynamicAccount             AKAfundingSourceDimension;
    //    int                                 i;        
    //    next replaceCompanySpecificDimensions(_projCostTrans,_projCostTransCost);
    //    AKAfundingSourceDimension = this.AKAgetFundingSourceDimension(_projCostTransCost);

    //    if (AKAfundingSourceDimension)
    //    {
    //        dimAttrSetStorage = DimensionAttributeValueSetStorage::find(AKAfundingSourceDimension);
    //        dimAttrSetStorageNew = DimensionAttributeValueSetStorage::find(_projCostTrans.DefaultDimension);

    //        for (i = 1; i <= dimAttrSetStorage.elements(); i++)
    //        {
    //            dimensionAttribute  = DimensionAttribute::find(dimAttrSetStorage.getAttributeByIndex(i));

    //            dimAttrValue = DimensionAttributeValue::findByDimensionAttributeAndValue(dimensionAttribute, dimAttrSetStorage.getDisplayValueByIndex(i), false, true);

    //            dimAttrSetStorageNew.addItem(dimAttrValue);
    //            AKAfundingSourceDimension = dimAttrSetStorageNew.save();                             
    //        }
    //    }
    //    else
    //    {
    //        AKAfundingSourceDimension = _projCostTrans.DefaultDimension;
    //    }

    //    /*dimAttrSetStorage = DimensionAttributeValueSetStorage::find(_projCostTrans.DefaultDimension);
    //    for (i = 1; i <= dimAttrSetStorage.elements(); i++)
    //    {

    //        dimensionAttribute= DimensionAttribute::find(dimAttrSetStorage.getAttributeByIndex(i));

// ... (truncated)
```

---

*Generated on 2025-10-17 15:42*
