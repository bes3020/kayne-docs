# AxTable: AKAXDSMyProjValues

[← Back to Project-Specific Data Security (XDS)](../README.md)

## Fields

| Field Name | Type | Mandatory | Description |
|------------|------|-----------|-------------|
| ProjId | N/A |  |  |

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| xds |  | RefreshFrequency | none |

## Declaration Code

```xpp

public class AKAXDSMyProjValues extends common
{
}

```

## Key Methods Source

### xds

```xpp

    public RefreshFrequency xds()
    {
        ProjTable					projTable;
        ProjGroup					projGroup;
        UserGroupList				userGroupList;
        UserGroupInfo				userGroupInfo;
        AKAXDSMyProjValues			myProjValues;

        unchecked(Uncheck::XDS)
        {
            insert_recordset myProjValues(ProjId)
                select ProjId from projTable
                    join projGroup
                        where projGroup.ProjGroupId == projTable.projGroupId
                    join userGroupInfo
                        where userGroupInfo.id == projGroup.AKAProjUserGroupAccessId
                    join userGroupList
                        where userGroupList.groupId == userGroupInfo.id
						&& userGroupList.userId == curUserId();
        }

        return RefreshFrequency::PerSession;
    }


```

---

*Generated on 2025-10-17 15:42*
