This method retrieves all profile information for profiles with the last activity date on or before the specified date and time.

### Declaration

    // C#
    public override ProfileInfoCollection GetAllInactiveProfiles
       (ProfileAuthenticationOption profileAuthenticationOption, DateTime
       inactiveSinceDateTime, int pageIndex, int pageSize, out int totalRecords);

### Parameters

- `profileAuthenticationOption`

  `Anonymous`, `Authenticated`, or `All` profiles to be searched.

- `inactiveSinceDateTime`

  The cut-off date and time that indicate a profile in inactive.

- `pageIndex`

  The zero-based index of the results page.

- `pageSize`

  The size of the page of the results page.

- `totalRecords`

  The total number of profiles.

### Return Value

A `ProfileInfoCollection` object that contains inactive user profiles that matches the supplied inactive date and time.

### Exceptions

`ArgumentException` - One of the following conditions exists:

- The `pageSize` parameter value is less than 1.

- The `pageIndex` parameter value is less than 0 or `pageIndex` multiplied by `pageSize` is larger than `Int32.MaxValue`.

### Remarks

This method retrieves inactive profiles from the data source for the application specified by the `applicationName` attribute in the configuration file. The `profileAuthenticationOption` parameter specifies whether to search only anonymous profiles, only authenticated profiles, or all profiles. This method retrieves profiles with a last activity date and time on or before the specified `inactiveSinceDateTime` parameter value.

The returned results are constrained by the `pageIndex` and `pageSize` parameters. The `pageSize` parameter identifies the number of `ProfileInfo` objects to return in the `ProfileInfoCollection` object. The `pageIndex` parameter identifies which page of results to return. Zero identifies the first page, as the value is zero-based. The `totalRecords` parameter is an out parameter for the total number of inactive user profiles that match the `inactiveSinceDateTime` parameter.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleProfileProvider Class](OracleProfileProviderClass.md)

- [OracleProfileProvider Members](OracleProfileProviderMembers.md)
