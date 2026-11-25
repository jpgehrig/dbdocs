This method retrieves inactive profile information for the specified user name.

### Declaration

    // C#
    public override ProfileInfoCollection FindInactiveProfilesByUserName
       (ProfileAuthenticationOption profileAuthenticationOption, string userName,
       DateTime inactiveSinceDateTime,int pageIndex, int pageSize,
       out int totalRecords);

### Parameters

- `profileAuthenticationOption`

  `Anonymous`, `Authenticated`, or `All` profiles to be searched to find inactive profiles.

- `userName`

  The user name to match.

- `inactiveSinceDateTime`

  The cut-off date and time that indicate a profile is inactive.

- `pageIndex`

  The zero-based index of the results page.

- `pageSize`

  The size of the page of the results page.

- `totalRecords`

  The total number of profiles.

### Return Value

A `ProfileInfoCollection` object that contains inactive user profiles where the user name matches the supplied user name.

### Exceptions

`ArgumentException` - One of the following conditions exists:

- The `userName` parameter is an empty string or exceeds 256 characters.

- The `pageSize` parameter is less than 1.

- The `pageIndex` parameter is less than 0 or `pageIndex` multiplied by `pageSize` is larger than the `Int32.MaxValue`.

`ArgumentNullException` - The `userName` parameter is a null reference.

### Remarks

This method retrieves inactive profiles from the data source for the application specified by the `applicationName` attribute in the configuration file. The `profileAuthenticationOption` parameter specifies whether to search only anonymous profiles, only authenticated profiles, or all profiles. The `OracleProfileProvider` object searches for a match of the supplied `userName` parameter using the `LIKE` keyword and supports wildcard characters using the percent sign (%). This method retrieves profiles with a last activity date and time on or before the specified `inactiveSinceDateTime` parameter value.

The results returned by this method are constrained by the `pageIndex` and `pageSize` parameters. The `pageSize` parameter identifies the number of `ProfileInfo` objects to return in the `ProfileInfoCollection` object. The `pageIndex` parameter identifies which page of results to return. The `totalRecords` parameter is an out parameter for the total number of inactive user profiles that match the `userName` and `inactiveSinceDateTime` parameters.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleProfileProvider Class](OracleProfileProviderClass.md)

- [OracleProfileProvider Members](OracleProfileProviderMembers.md)
