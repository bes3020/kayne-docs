# AxView: AKAVendTransInvoicePaymentView

[← Back to AKA Ledger Attribute Management](../README.md)

## Fields

| Field Name | Type | Mandatory | Description |
|------------|------|-----------|-------------|
| AccountNum | N/A |  |  |
| LastSettleDate | N/A |  |  |
| Voucher | N/A |  |  |
| DefaultDimension | N/A |  |  |
| TransType | N/A |  |  |
| PaymReference | N/A |  |  |
| PaymentStatus | N/A |  |  |
| VendTransId | N/A |  |  |
| AccountType | N/A |  |  |
| Name | N/A |  |  |
| Invoice | N/A |  |  |
| JournalNum | N/A |  |  |
| Txt | N/A |  |  |

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| departmentName | ✓ | str | none |
| peopleName | ✓ | str | none |
| dealName | ✓ | str | none |
| ledgerJournalNameId |  | LedgerJournalNameId | none |

## Declaration Code

```xpp

public class AKAVendTransInvoicePaymentView extends common
{
}

```

## Key Methods Source

### departmentName

```xpp

    /// <summary>
    /// This method is use to get department name
    /// </summary>
    /// <returns>Department name</returns>
    public static str departmentName()
    {
        str departmentName;

        departmentName = @"select a.Name from DimAttributeOMDepartment as a
                        join DIMENSIONATTRIBUTEVALUESETITEMVIEW as b 
                            on b.DIMENSIONATTRIBUTEVALUESET = T1.DefaultDimension and
                            b.DISPLAYVALUE = a.VALUE
                        join DimensionAttribute as c
                            on c.RECID = b.DIMENSIONATTRIBUTE and c.NAME = 'Department'";
        return departmentName;
    }


```

### peopleName

```xpp

    /// <summary>
    /// This method is use to get peopleName
    /// </summary>
    /// <returns>str</returns>
    public static str peopleName()
    {
        str peopleName;

        peopleName = @"select a.Name from dimAttributeFinancialTag as a
                    join DIMENSIONATTRIBUTEVALUESETITEMVIEW as b 
                        on b.DIMENSIONATTRIBUTEVALUESET = T1.DefaultDimension and
                        b.DISPLAYVALUE = a.VALUE
                    join DimensionAttribute as c
                        on c.RECID = b.DIMENSIONATTRIBUTE and c.NAME = 'People'";
        return peopleName;
    }


```

### dealName

```xpp

    /// <summary>
    /// This method is use to get dealName
    /// </summary>
    /// <returns>str</returns>
    public static str dealName()
    {
        str dealName;

        dealName = @"select a.Name from dimAttributeFinancialTag as a
                    join DIMENSIONATTRIBUTEVALUESETITEMVIEW as b
                        on b.DIMENSIONATTRIBUTEVALUESET = T1.DefaultDimension and
                        b.DISPLAYVALUE = a.VALUE
                    join DimensionAttribute as c
                        on c.RECID = b.DIMENSIONATTRIBUTE and c.NAME = 'Deal'";
        return dealName;
    }


```

---

*Generated on 2025-10-17 15:42*
