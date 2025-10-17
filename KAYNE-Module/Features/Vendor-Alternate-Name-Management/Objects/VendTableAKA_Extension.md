# AxClass: VendTableAKA_Extension

[← Back to Vendor Alternate Name Management](../README.md)

## Description

<summary> Extension class for the table <c>VendTable</c> </summary>

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| AKAValidateInvoice | ✓ | boolean | none |

## Declaration Code

```xpp

/// <summary>
/// Extension class for the table <c>VendTable</c>
/// </summary>
/// AKA_2312_OCCNeedsToAssignAPInvoiceJourByUser : apendli, 05-11-2020
[ExtensionOf(tablestr(VendTable))]
final class VendTableAKA_Extension
{
}

```

## Key Methods Source

### AKAValidateInvoice

```xpp

    /// <summary>
    /// Checks for the duplicate invoices per vendor and returns false if exists
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
    /// AKA_2312_OCCNeedsToAssignAPInvoiceJourByUser : apendli, 05-11-2020
    public static boolean AKAValidateInvoice(DataAreaId _dataAreadId, VendAccount _vendor, InvoiceId _invoiceId)
    {
        boolean                 ret = true;
        VendInvoiceInfoTable    vendInvoiceInfoTable;
        LedgerJournalTrans      ledgerJournalTrans;
        VendInvoiceJour         vendInvoiceJour;

        changecompany(_dataAreadId)
        {
            ret  = ((select firstonly RecId from vendInvoiceInfoTable 
                        where vendInvoiceInfoTable.InvoiceAccount == _vendor
                           && vendInvoiceInfoTable.Num == _invoiceId).RecId != 0);

            if (ret)
            {
                while select ledgerJournalTrans
                    where ledgerJournalTrans.AccountType == LedgerJournalACType::Vend
                {
                    if (_vendor == ledgerJournalTrans.accountDisplay())
                    {
                        ret = false;
                        break;
                    }
                }
            }

            if (ret)
            {
                ret  = ((select vendInvoiceJour
                        where vendInvoiceJour.OrderAccount == _vendor
                           && vendInvoiceJour.InvoiceId == _invoiceId).RecId != 0);
            }
        }

// ... (truncated)
```

---

*Generated on 2025-10-17 15:42*
