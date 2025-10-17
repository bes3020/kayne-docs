# AxClass: AKAMainAccountsMaskFix

[← Back to Main Account and Financial Dimension Masking](../README.md)

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| main | ✓ | void | none |

## Declaration Code

```xpp

class AKAMainAccountsMaskFix
{
}

```

## Key Methods Source

### main

```xpp

    public static void main(Args _args)
    {
        AKAMainAccountsMask			mainAccountsMask;
        AKAMainAccountsMaskTable	mainAccountMaskTable;

        delete_from mainAccountMaskTable;

        while select mainAccountsMask
            group by mainAccountsMask.MainAccountId
        {
            AKAMainAccountsMaskTable::createMainAccountToMask(mainAccountsMask.MainAccountId);
        }

        info("@SYS112206");

    }


```

---

*Generated on 2025-10-17 15:42*
