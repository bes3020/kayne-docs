# AxClass: LedgerJournalEngineAKA_Extension

[← Back to Extended General Ledger Journal Processing](../README.md)

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| accountModified |  | DebCredProposal | none |
| offsetAccountModified |  | void | none |
| projCategoryModified |  | void | none |

## Declaration Code

```xpp

[ExtensionOf(classstr(LedgerJournalEngine))]
final public class LedgerJournalEngineAKA_Extension
{
}

```

## Key Methods Source

### accountModified

```xpp

    public DebCredProposal accountModified(
        LedgerJournalTrans          _ledgerJournalTrans,
        LedgerJournalTrans_Project  _ledgerJournalTrans_Project,
        LedgerJournalTrans_Asset    _ledgerJournalTrans_Asset,
        Tax1099BoxDetail            _tax1099Detail
        ,LedgerJournalTrans_RAsset    _ledgerJournalTrans_RAsset,
        LedgerJournalTrans_RDeferrals _ledgerJournalTrans_RDeferrals
        )
    {
        DebCredProposal debCredProposal = next accountModified(_ledgerJournalTrans, _ledgerJournalTrans_Project, _ledgerJournalTrans_Asset, _tax1099Detail, _ledgerJournalTrans_RAsset, _ledgerJournalTrans_RDeferrals);

        if (_ledgerJournalTrans.AccountType == LedgerJournalACType::Project)
        {
            LedgerDimensionDefaultAccount   ledgerDefaultAccount;
            _ledgerJournalTrans.AKALedgerDefaultAccountType      = LedgerJournalACType::Ledger;

            DimensionAttributeValueCombination davc;

            select firstonly DisplayValue from davc
                where davc.RecId == _ledgerJournalTrans.LedgerDimension;

            ProjTable projTable = ProjTable::find(davc.DisplayValue);

            if (projTable && _ledgerJournalTrans_Project.CategoryId)
            {
                ledgerDefaultAccount = ProjectPosting::getProjectLedgerDimension(projTable,
                                                                                ProjCategory::find(_ledgerJournalTrans_Project.CategoryId),
                                                                                ProjFundingSource::findCustAccount(projtable.ProjInvoiceProjId),
                                                                                ProjLineProperty::find(_ledgerJournalTrans_Project.LinePropertyId),
                                                                                false);  
                _ledgerJournalTrans.AKALedgerDefaultDimension = LedgerDimensionFacade::serviceCreateLedgerDimension(ledgerDefaultAccount);
                _ledgerJournalTrans.AKALedgerDefaultDimension = LedgerDimensionFacade::serviceCreateLedgerDimForDefaultDim(projTable.DefaultDimension, _ledgerJournalTrans.AKALedgerDefaultDimension);
            }                        
        }

        return debCredProposal;
    }


```

### offsetAccountModified

```xpp

    public void offsetAccountModified(LedgerJournalTrans _ledgerJournalTrans,
                                      LedgerJournalTrans_Project _ledgerJournalTrans_Project,
                                      LedgerJournalTrans_Asset _ledgerJournalTrans_Asset,
                                      LedgerJournalTrans_RAsset _ledgerJournalTrans_RAsset,
                                      LedgerJournalTrans_RDeferrals _ledgerJournalTrans_RDeferrals
                                      )
    {
        next offsetAccountModified(_ledgerJournalTrans, _ledgerJournalTrans_Project, _ledgerJournalTrans_Asset, _ledgerJournalTrans_RAsset, _ledgerJournalTrans_RDeferrals);

        if (_ledgerJournalTrans.OffsetAccountType == LedgerJournalACType::Project)
        {
            LedgerDimensionDefaultAccount   ledgerDefaultAccount;
            _ledgerJournalTrans.AKALedgerOffsetDefaultAccountType      = LedgerJournalACType::Ledger;

            DimensionAttributeValueCombination davc;

            select firstonly DisplayValue from davc
                where davc.RecId == _ledgerJournalTrans.OffsetLedgerDimension;

            ProjTable projTable = ProjTable::find(davc.DisplayValue);

            if (projTable && _ledgerJournalTrans_Project.CategoryId)
            {
                ledgerDefaultAccount = ProjectPosting::getProjectLedgerDimension(projTable,
                                                                                ProjCategory::find(_ledgerJournalTrans_Project.CategoryId),
                                                                                ProjFundingSource::findCustAccount(projtable.ProjInvoiceProjId),
                                                                                ProjLineProperty::find(_ledgerJournalTrans_Project.LinePropertyId),
                                                                                false);
                _ledgerJournalTrans.AKALedgerOffsetDefaultDimension = LedgerDimensionFacade::serviceCreateLedgerDimension(ledgerDefaultAccount);
                _ledgerJournalTrans.AKALedgerOffsetDefaultDimension = LedgerDimensionFacade::serviceCreateLedgerDimForDefaultDim(projTable.DefaultDimension, _ledgerJournalTrans.AKALedgerOffsetDefaultDimension);
            }

            
        }
    }


```

### projCategoryModified

```xpp

    public void projCategoryModified(
        LedgerJournalTrans          _ledgerJournalTrans,
        LedgerJournalTrans_Project  _ledgerJournalTrans_Project)
    {
        next projCategoryModified(_ledgerJournalTrans, _ledgerJournalTrans_Project);

        ProjTable projTable = ProjTable::find(_ledgerJournalTrans_Project.ProjId);
        LedgerDimensionDefaultAccount   ledgerDefaultAccount;

        if (projTable && _ledgerJournalTrans_Project.CategoryId)
        {
            ledgerDefaultAccount = ProjectPosting::getProjectLedgerDimension(projTable,
                                                                            ProjCategory::find(_ledgerJournalTrans_Project.CategoryId),
                                                                            ProjFundingSource::findCustAccount(projtable.ProjInvoiceProjId),
                                                                            ProjLineProperty::find(_ledgerJournalTrans_Project.LinePropertyId),
                                                                            false);
        }

        if(_ledgerJournalTrans.AccountType == LedgerJournalACType::Project)
        {
            _ledgerJournalTrans.AKALedgerDefaultDimension = LedgerDimensionFacade::serviceCreateLedgerDimension(ledgerDefaultAccount);
            _ledgerJournalTrans.AKALedgerDefaultAccountType      = LedgerJournalACType::Ledger;

            if(projTable)
            {
                _ledgerJournalTrans.AKALedgerDefaultDimension = LedgerDimensionFacade::serviceCreateLedgerDimForDefaultDim(projTable.DefaultDimension, _ledgerJournalTrans.AKALedgerDefaultDimension);
            }
        }
        else if(_ledgerJournalTrans.OffsetAccountType == LedgerJournalACType::Project)
        {
            _ledgerJournalTrans.AKALedgerOffsetDefaultDimension = LedgerDimensionFacade::serviceCreateLedgerDimension(ledgerDefaultAccount);
            _ledgerJournalTrans.AKALedgerOffsetDefaultAccountType      = LedgerJournalACType::Ledger;

            if(projTable)
            {
                _ledgerJournalTrans.AKALedgerOffsetDefaultDimension = LedgerDimensionFacade::serviceCreateLedgerDimForDefaultDim(projTable.DefaultDimension, _ledgerJournalTrans.AKALedgerOffsetDefaultDimension);
            }
        }
    }


```

---

*Generated on 2025-10-17 15:42*
