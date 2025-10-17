# AxClass: ProjPostAKA_Extension

[← Back to Project Transaction Posting Enhancement](../README.md)

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| initializeLedgerVoucherTransObject |  | void | none |
| initLedgerVoucherTransObjectForPostTurnover |  | LedgerVoucherTransObject | none |

## Declaration Code

```xpp

[ExtensionOf(classStr(ProjPost))]
final class ProjPostAKA_Extension
{
}

```

## Key Methods Source

### initializeLedgerVoucherTransObject

```xpp

    protected void initializeLedgerVoucherTransObject(
        LedgerVoucherTransObject    _ledgerVoucherTransObject,
        LedgerVoucherObject         _ledgerVoucherObject,
        RecId                       _fundingAllocation,
        Map                         _splitTransQty,
        ProjLedger                  _tmpProjLedger
        )
    {
        next initializeLedgerVoucherTransObject(_ledgerVoucherTransObject, _ledgerVoucherObject, _fundingAllocation, _splitTransQty, _tmpProjLedger);

        AKALedgerAttributeTrans AKALedgerAttributeTrans;
        AKALedgerAttributeTrans.AKATrackingID = _tmpProjLedger.parmDFSTrackinID();;
        AKALedgerAttributeTrans.AKATrackingIDCompany = _tmpProjLedger.parmDFSTrackinIDCompany();
        AKALedgerAttributeTrans.ProjId = _tmpProjLedger.parmProjId();
        AKALedgerAttributeTrans.CategoryId = _tmpProjLedger.parmProjCategoryId();
        AKALedgerAttributeTrans.Resource = _tmpProjLedger.parmResource();
        AKALedgerAttributeTrans.insert();

        _ledgerVoucherTransObject.parmAKALedgerAttributes(AKALedgerAttributeTrans.Recid);
    }


```

### initLedgerVoucherTransObjectForPostTurnover

```xpp

    protected LedgerVoucherTransObject initLedgerVoucherTransObjectForPostTurnover(
        LedgerVoucherObject     _ledgerVoucherObject,
        LedgerDimensionAccount  _mergedLedgerDimension,
        MapEnumerator           _fundingAllocationEnumerator,
        CurrencyExchangeHelper  _exchangeRateHelper,
        Map                     _splitTransQty,
        ProjLedger              _tmpProjLedger
        )
    {
        LedgerVoucherTransObject _ledgerVoucherTransObject = next initLedgerVoucherTransObjectForPostTurnover(_ledgerVoucherObject, _mergedLedgerDimension, _fundingAllocationEnumerator, _exchangeRateHelper, _splitTransQty, _tmpProjLedger);

        AKALedgerAttributeTrans AKALedgerAttributeTrans;
        AKALedgerAttributeTrans.AKATrackingID = _tmpProjLedger.parmDFSTrackinID();
        AKALedgerAttributeTrans.AKATrackingIDCompany = _tmpProjLedger.parmDFSTrackinIDCompany();
        AKALedgerAttributeTrans.ProjId = _tmpProjLedger.parmProjId();
        AKALedgerAttributeTrans.CategoryId = _tmpProjLedger.parmProjCategoryId();
        AKALedgerAttributeTrans.Resource = _tmpProjLedger.parmResource();
        AKALedgerAttributeTrans.insert();

        _ledgerVoucherTransObject.parmAKALedgerAttributes(AKALedgerAttributeTrans.Recid);

        return _ledgerVoucherTransObject;
    }


```

---

*Generated on 2025-10-17 15:42*
