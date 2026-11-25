This method deletes user personalization data from the underlying Oracle data source, based on the specified parameters.

### Declaration

    // C#
    public override int ResetUserState(string path, DateTime userInactiveSinceDate);

### Parameters

- `path`

  The path of the personalization data to be deleted. This value can be a null reference but cannot be an empty string ("").

- `userInactiveSinceDate`

  The date that indicates the last activity.

### Return Value

The count of rows deleted from the underlying Oracle data source.

### Exceptions

`ArgumentException` - The `path` parameter is an empty string.

`OracleException` - An Oracle-related error has occurred.

### Remarks

The parameters of this method have the following restrictions:

- The `path` parameter cannot contain wildcard characters.

- If the `path` parameter is a non-null reference, then only per-user personalization records associated with the `path` parameter are deleted.

- Only per-user personalization records associated with users that are considered inactive since the date specified in the `userInactiveSinceDate` parameter are deleted. The exact comparison deletes records where the `Last Activity Date` property is less than or equal to the `userInactiveSinceDate` parameter.

- If both parameters are provided, then records that match both constraints are deleted.

- The `path` parameter can be a null reference.

- The `path` parameter cannot be an empty string after trimming.

- The `userInactiveSinceDate` parameter cannot be a null reference.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OraclePersonalizationProvider Class](OraclePersonalizationProviderClass.md)

- [OraclePersonalizationProvider Members](OraclePersonalizationProviderMembers.md)
