# AxView: AKADefaultDimensionNameValueView

[← Back to AKA Ledger Attribute Management](../README.md)

## Fields

| Field Name | Type | Mandatory | Description |
|------------|------|-----------|-------------|
| DimensionAttributeValueSetRecId | N/A |  |  |
| DepartmentName | N/A |  |  |
| PeopleName | N/A |  |  |
| DealName | N/A |  |  |

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| departmentValue | ✓ | str | none |
| departmentName | ✓ | str | none |
| peopleValue | ✓ | str | none |
| peopleName | ✓ | str | none |
| dealValue | ✓ | str | none |
| dealName | ✓ | str | none |

## Declaration Code

```xpp

public class AKADefaultDimensionNameValueView extends common
{
   

}

```

## Key Methods Source

### departmentValue

```xpp

    public static str departmentValue()
    {
        
        return 'T1.DepartmentValue';
    }


```

### departmentName

```xpp

    public static str departmentName()
    {
        return @"select Name from DimAttributeOMDepartment where                   
                            VALUE = T1.DepartmentValue";
    }


```

### peopleValue

```xpp

    public static str peopleValue()
    {
        
        return 'T1.PeopleValue';
    }


```

---

*Generated on 2025-10-17 15:42*
