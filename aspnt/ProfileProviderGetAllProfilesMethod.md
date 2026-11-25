This method retrieves all profile information from the data source.

### Declaration

    // C#
    public override ProfileInfoCollection GetAllProfiles(ProfileAuthenticationOption
       profileAuthenticationOption, int pageIndex, int pageSize,     out int totalRecords);

### Parameters

- `profileAuthenticationOption`

  `Anonymous`, `Authenticated`, or `All` profiles to be searched.

- `pageIndex`

  The 0-based index of the results page.

- `pageSize`

  The size of the page of the results page

- `totalRecords`

  The total number of profiles.

### Return Value

A `ProfileInfoCollection` object that contains all user profiles from the data source.

### Exceptions

`ArgumentException` - One of the following conditions exists:

- The `pageSize` parameter is less than 1.

- The `pageIndex` parameter is less than 0 or `pageIndex` multiplied by `pageSize` is larger than `Int32.MaxValue`.

### Remarks

This method retrieves all profiles from the data source for the application specified by the `applicationName` attribute in the configuration file. The `profileAuthenticationOption` parameter specifies whether to search only anonymous profiles, only authenticated profiles, or all profiles.

The returned results are constrained by the `pageIndex` and `pageSize` parameters. The `pageSize` parameter identifies the number of `ProfileInfo` objects to return in the `ProfileInfoCollection` object. The `pageIndex` parameter identifies which page of results to return. The `totalRecords` parameter is an out parameter for the total number of user profiles retrieved.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleProfileProvider Class](OracleProfileProviderClass.md)

- [OracleProfileProvider Members](OracleProfileProviderMembers.md)
