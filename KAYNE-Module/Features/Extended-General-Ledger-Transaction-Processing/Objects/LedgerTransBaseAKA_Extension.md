# AxClass: LedgerTransBaseAKA_Extension

[← Back to Extended General Ledger Transaction Processing](../README.md)

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| init |  | void | none |

## Declaration Code

```xpp

[ExtensionOf(formStr(LedgerTransBase))]
final class LedgerTransBaseAKA_Extension
{

}

```

## Key Methods Source

### init

```xpp

    void init()
    {
        next init();

        FormControl dimensionContol = this.design().controlName(formcontrolstr(LedgerTransBase, TabFinancialDimensions));
        FormControl AKAFinancialDimensionDisplayMask = this.design().controlName(formcontrolstr(LedgerTransBase, AKAFinancialDimensionDisplayMask));

        boolean allowedPeopleAccess = LedgerParameters::allowedPeopleUserGroupAccess();

        dimensionContol.visible(allowedPeopleAccess);
        AKAFinancialDimensionDisplayMask.visible(!allowedPeopleAccess);
    }


```

---

*Generated on 2025-10-17 15:42*
