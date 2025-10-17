# AxClass: LedgerParametersAKA_Extension

[← Back to Alternate Ledger Account Configuration](../README.md)

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| allowedPeopleUserGroupAccess | ✓ | boolean | none |

## Declaration Code

```xpp

[ExtensionOf(tablestr(LedgerParameters))]
public final class LedgerParametersAKA_Extension
{
}

```

## Key Methods Source

### allowedPeopleUserGroupAccess

```xpp

	public static boolean allowedPeopleUserGroupAccess()
    {
        UserGroupList				userGroupList;
        UserGroupInfo				userGroupInfo;

        select userGroupInfo
            where userGroupInfo.id == LedgerParameters::find().AKAMaskUserGroupAccessId
        join userGroupList
            where userGroupList.groupId == userGroupInfo.id
            && userGroupList.userId == curUserId();

        return userGroupInfo.RecId != 0;
    }


```

---

*Generated on 2025-10-17 15:42*
