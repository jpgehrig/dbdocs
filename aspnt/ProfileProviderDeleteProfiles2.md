This method deletes profile properties and information from the data source for the supplied list of user names.

### Declaration

    // C#
    public override int DeleteProfiles(string[] userNames);

### Parameters

- `userNames`

  A string array of user names whose profiles are to be deleted.

### Return Value

An integer value indicating the number of profiles that were deleted from the data source.

### Exceptions

`ArgumentNullException` - The `userNames` parameter is a null reference or one of the items in `userNames` array has a null reference.

`ArgumentException` - One of the following conditions exists:

- The `length` of the `userNames` array is `0`.

- One of the items in the `userNames` array has an invalid user name, such as an empty string, exceeds 256 characters, or contains a comma.

- There are duplicated user names in the `userNames` array.

### Remarks

This method deletes all profile properties and information from the data source for the supplied list of user names for the application specified by the `applicationName` attribute in the configuration file.

The value returned may be different from the length of the supplied string array of user names because some of the profiles are no longer found in the data source.

The delete profiles operation is a transactional operation. If an error is encountered, then the transaction is rolled back and no changes are made.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleProfileProvider Class](OracleProfileProviderClass.md)

- [OracleProfileProvider Members](OracleProfileProviderMembers.md)
