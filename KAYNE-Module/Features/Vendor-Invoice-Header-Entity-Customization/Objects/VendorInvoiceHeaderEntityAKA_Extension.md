# AxClass: VendorInvoiceHeaderEntityAKA_Extension

[← Back to Vendor Invoice Header Entity Customization](../README.md)

## Description

<summary> Extension class for the data entity <c>VendorInvoiceHeaderEntity</c> </summary>

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| AKAValidateInvoice | ✓ | boolean | none |

## Declaration Code

```xpp

/// <summary>
/// Extension class for the data entity <c>VendorInvoiceHeaderEntity</c>
/// </summary>
/// AKA_2312_OCRNeedsToAssignAPInvoiceJourByUser: Apendli, 06-Nov-2020
[ExtensionOf(dataentityviewstr(VendorInvoiceHeaderEntity))]
final class VendorInvoiceHeaderEntityAKA_Extension
{
}

```

## Key Methods Source

### AKAValidateInvoice

```xpp

    /// <summary>
    /// Checks for the duplicate invioce number per vendor and returns false if exists 
    /// </summary>
    /// <param name = "_dataAreadId">
    /// Company name
    /// </param>
    /// <param name = "_vendor">
    /// Vendor account
    /// </param>
    /// <param name = "_invoiceId">
    /// Invoice number
    /// </param>
    /// <returns>
    /// True or false
    /// </returns>
    /// AKA_2312_OCRNeedsToAssignAPInvoiceJourByUser: Apendli, 06-Nov-2020
    [SysODataAction('AKAValidateInvoice', false)]
    public static boolean AKAValidateInvoice(DataAreaId _dataAreadId, VendAccount _vendor, InvoiceId _invoiceId)
    {
        return VendTable::AKAValidateInvoice(_dataAreadId, _vendor, _invoiceId);
    }


```

---

*Generated on 2025-10-17 15:42*
