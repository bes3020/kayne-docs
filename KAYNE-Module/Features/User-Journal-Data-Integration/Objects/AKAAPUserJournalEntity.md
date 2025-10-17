# AxDataEntityView: AKAAPUserJournalEntity

[← Back to User Journal Data Integration](../README.md)

## Fields

| Field Name | Type | Mandatory | Description |
|------------|------|-----------|-------------|
| Name | N/A |  |  |
| JournalName | N/A |  |  |
| User | N/A |  |  |
| Id | N/A |  |  |
| company | N/A |  |  |
| PersonnelNumber | N/A |  |  |

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| AKAValidateInvoice | ✓ | boolean | none |

## Declaration Code

```xpp

public class AKAAPUserJournalEntity extends common
{

}

```

## Key Methods Source

### AKAValidateInvoice

```xpp

    [SysODataAction('AKAValidateInvoice', false)]
    public static boolean AKAValidateInvoice(DataAreaId _dataAreadId, VendAccount _vendor, InvoiceId _invoiceId)
    {
        return VendTable::AKAValidateInvoice(_dataAreadId, _vendor, _invoiceId);
    }


```

---

*Generated on 2025-10-17 15:42*
