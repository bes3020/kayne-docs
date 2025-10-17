# AxClass: ProjFundingRuleEntityAKA_Extension

[← Back to Project Funding Rule Data Management Extension](../README.md)

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| insertEntityDataSource |  | boolean | none |
| mapEntityToDataSource |  | void | none |

## Declaration Code

```xpp

[ExtensionOf(dataentityviewstr(ProjFundingRuleEntity))]
final class ProjFundingRuleEntityAKA_Extension
{

}

```

## Key Methods Source

### insertEntityDataSource

```xpp

    public boolean insertEntityDataSource(DataEntityRuntimeContext _entityCtx, DataEntityDataSourceRuntimeContext _dataSourceCtx)
    {
        boolean ret;

        if (_dataSourceCtx.name() == dataentitydatasourcestr(ProjFundingRuleEntity, ProjFundingRule))
        {
            if (this.ResourceId)
            {
                ProjFundingRule buffer = _dataSourceCtx.getBuffer();
                ResourceView resource;

                select firstonly RecId from resource
                            where resource.ResourceCompanyId == curext() &&
                                  resource.ResourceId == this.ResourceId;

                buffer.Resource = resource.RecId;
            }
        }

        next insertEntityDataSource(_entityCtx, _dataSourceCtx);

        return ret;
    }


```

### mapEntityToDataSource

```xpp

    public void mapEntityToDataSource(DataEntityRuntimeContext _entityCtx, DataEntityDataSourceRuntimeContext _dataSourceCtx)
    {
        if (_dataSourceCtx.name() == dataEntityDataSourceStr(ProjFundingRuleEntity, ProjFundingRule))
        {           
            if (_entityCtx.getDatabaseOperation() == DataEntityDatabaseOperation::Insert)
            {
                ProjFundingRule rule;
                ResourceView resource;

                select firstonly RecId from resource
                            where resource.ResourceCompanyId == curext() &&
                                  resource.ResourceId == this.ResourceId;

                select firstonly rule
                    where   rule.ActivityNumber == this.ActivityNumber || !this.ActivityNumber
                    &&      rule.CategoryId == this.CategoryId || !this.CategoryId
                    &&      rule.CategoryGroupId == this.CategoryGroupId || !this.CategoryGroupId
                    &&      rule.ContractId == this.ProjectContractId
                    &&      rule.ProjId == this.ProjectId 
                    &&      rule.ItemId == this.ItemId || !this.ItemId
                    &&      rule.Priority == this.Priority || !this.Priority
                    &&      rule.StartDate == this.StartDate || !this.StartDate
                    &&      rule.EndDate == this.EndDate || !this.EndDate
                    &&      rule.Resource == resource.RecId || !this.ResourceId;
                

                if (rule)
                {
                    _dataSourceCtx.setBuffer(rule);
                    _dataSourceCtx.setDatabaseOperation(DataEntityDatabaseOperation::None);
                }
            }
        }

        next mapEntityToDataSource(_entityCtx, _dataSourceCtx);
    }


```

---

*Generated on 2025-10-17 15:42*
