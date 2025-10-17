# AxTable: AKAMainAccountsMask

[← Back to Main Account and Financial Dimension Masking](../README.md)

## Fields

| Field Name | Type | Mandatory | Description |
|------------|------|-----------|-------------|
| MainAccountId | N/A |  |  |
| Name | N/A |  |  |

## Relations

| Relation Name | Related Table | Cardinality |
|---------------|---------------|-------------|
| MainAccount | MainAccount | ZeroOne |

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| createMainAccountToMask | ✓ | void | none |
| deleteMainAccountToMask | ✓ | void | none |
| find | ✓ | AKAMainAccountsMask | none |
| exist | ✓ | boolean | none |

## Declaration Code

```xpp

public class AKAMainAccountsMask extends common
{

}

```

## Key Methods Source

### createMainAccountToMask

```xpp

	/// <summary>
    ///		Create Main account to mask
    /// </summary>
    /// <param name = "_mainAccountId">
    ///		The _mainAccountId
	/// </param>
    /// Rchilukuri : 922 - Create Main account to mask
    public static void createMainAccountToMask(MainAccountNum _mainAccountId)
    {
        AKAMainAccountsMask		mainAccountsMask;
        MainAccount				mainAccount;

        mainAccount = MainAccount::findByMainAccountId(_mainAccountId);

        if (! AKAMainAccountsMask::exist(_mainAccountId) && mainAccount)
        {
            mainAccountsMask.MainAccountId	= mainAccount.MainAccountId;
            mainAccountsMask.Name			= mainAccount.Name;
            mainAccountsMask.insert();
        }
    }


```

### deleteMainAccountToMask

```xpp

    /// <summary>
    ///  Deletes Main account to mask record from database.
    /// </summary>
    /// <param name = "_mainAccountsMask">
    ///		The _mainAccountsMask record
    /// </param>
	/// Rchilukuri : 922 - Mask Financial dimension values for selected Main accounts
    public static void deleteMainAccountToMask(AKAMainAccountsMask _mainAccountsMask)
    {
        AKAMainAccountsMask		mainAccountsMask = _mainAccountsMask;

        mainAccountsMask.delete();
    }


```

### find

```xpp

    /// <summary>
    ///		Finds a specific AKAMainAccountsMask record with given parameters.
    /// </summary>
    /// <param name="_mainAccountId">
    ///		The main account Id.
    /// </param>
    /// <param name="_forupdate">
    ///		Determines whether the record is selected for update.
    /// </param>
    /// <returns>
    ///		The record that is searched for.
    /// </returns>
    /// Rchilukuri : 922 - Finds a specific AKAMainAccountsMask record with given parameters.
    public static AKAMainAccountsMask find(MainAccountNum _mainAccountId, boolean _forupdate = false)
    {
        AKAMainAccountsMask		mainAccountsMask;

        if (_mainAccountId)
        {
            mainAccountsMask.selectForUpdate(_forupdate);

            select firstonly mainAccountsMask
                where mainAccountsMask.MainAccountId == _mainAccountId;
        }

        return mainAccountsMask;
    }


```

---

*Generated on 2025-10-17 15:42*
