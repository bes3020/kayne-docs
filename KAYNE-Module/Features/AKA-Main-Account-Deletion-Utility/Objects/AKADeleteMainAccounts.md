# AxClass: AKADeleteMainAccounts

[← Back to AKA Main Account Deletion Utility](../README.md)

## Description

<summary> Deleting Main Accounts and related dimensions </summary>

## Methods

| Method Name | Static | Return Type | Parameters |
|-------------|--------|-------------|------------|
| main | ✓ | void | none |
| run |  | void | none |
| deleteMainAccounts |  | void | none |

## Declaration Code

```xpp

/// <summary>
///		Deleting Main Accounts and related dimensions
/// </summary>
/// Rchilukuri : 1573 - Deleting Main Accounts
class AKADeleteMainAccounts
{
    Counter		counter;
		

}

```

## Key Methods Source

### main

```xpp

    /// <summary>
    ///		Deleting Main Accounts
    /// </summary>
    /// <param name = "_args">
	///		The specified arguments.
	/// </param>
    /// Rchilukuri : 1573 - Deleting Main Accounts
    public static void main(Args _args)
    {
        AKADeleteMainAccounts		deleteMainAccounts;

        deleteMainAccounts = new AKADeleteMainAccounts();
        deleteMainAccounts.run();
	}


```

### run

```xpp

	/// <summary>
    ///		Process file
    /// </summary>
    public void run()
    {
        AsciiStreamIo                       file;
        FileUploadTemporaryStorageResult    fileUpload;

        //Upload a file
        fileUpload  = File::GetFileFromUser() as FileUploadTemporaryStorageResult;
        file        = AsciiStreamIo::constructForRead(fileUpload.openResult());

        if (file)
        {
            if (file.status())
            {
                throw error("@SYS52680");
            }

            file.inFieldDelimiter(';'); //separator
            file.inRecordDelimiter('\r\n');
        }

        //Read a CSV File
        container record;

        while (!file.status())
        {
            record = file.read();

            if (conLen(record))
            {
                this.deleteMainAccounts(record);
            }
        }

        info(strFmt("@AKA:TotalDeleted", counter));
    }


```

### deleteMainAccounts

```xpp

	/// <summary>
    ///		Deleting Main Accounts and related dimensions
    /// </summary>
    /// <param name = "_record">
    ///		The _record
	/// </param>
    /// Rchilukuri : 1573 - Deleting Main Accounts
    public void deleteMainAccounts(container	_record)
    {
        MainAccount								mainAccount;
        DimensionAttributeValueCombination		dimAttributeValueCombo;
        DimensionAttributeValueGroupCombination dimAttributeValueGroupCombo;
        DimensionAttributeLevelValue			dimAttributeLevelValue;
        DimensionAttributeValue					dimAttributeValue;
        
        ttsBegin;

        //Delete MainAccount
        while select forUpdate mainAccount
            where mainAccount.MainAccountId == conPeek(_record, 1)
        {
            //Delete dimensions
            while select forUpdate dimAttributeLevelValue
               where dimAttributeLevelValue.DisplayValue == mainAccount.MainAccountId
            {
                delete_from dimAttributeValue
                   where dimAttributeValue.RecId == dimAttributeLevelValue.DimensionAttributeValue 
                    && dimAttributeValue.EntityInstance == mainAccount.RecId ;

                dimAttributeLevelValue.delete();

                while select forUpdate dimAttributeValueGroupCombo
					where dimAttributeValueGroupCombo.DimensionAttributeValueGroup == dimAttributeLevelValue.DimensionAttributeValueGroup
                {
                    delete_from dimAttributeValueCombo
                       where dimAttributeValueCombo.RecId == dimAttributeValueGroupCombo.DimensionAttributeValueCombination;

                    dimAttributeValueGroupCombo.delete();
                }                          
            }

            mainAccount.delete();

            counter++;

            info(strFmt("@AKA:MainAccountAndDimDeleted", mainAccount.MainAccountId));
        }

        ttscommit;        

// ... (truncated)
```

---

*Generated on 2025-10-17 15:42*
