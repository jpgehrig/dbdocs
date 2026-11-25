This method retrieves profile information for the specified user name.

### Declaration

    // C#
    public override ProfileInfoCollection FindProfilesByUserName
      (ProfileAuthenticationOption profileAuthenticationOption, string userName,
       int pageIndex, int pageSize, out int totalRecords);

### Parameters

- `profileAuthenticationOption`

  `Anonymous`, `Authenticated`, or `All` profiles to be searched to find active profiles.

- `userName`

  The user name to match.

- `pageIndex`

  The zero-based index of the results page.

- `pageSize`

  The size of the page of results page.

- `totalRecords`

  The total number of profiles.

### Return Value

A `ProfileInfoCollection` object that contains user profiles where the user name matches the supplied user name.

### Exceptions

`ArgumentException` - One of the following conditions exists:

- The `userName` parameter is an empty string or exceeds 256 characters.

- The `pageSize` parameter value is less than 1.

- The `pageIndex` parameter value is less than 0 or `pageIndex` multiplied by `pageSize` is larger than `Int32.MaxValue`.

`ArgumentNullException` - The `userName` parameter is a null reference.

### Remarks

This method retrieves profiles from the data source for the application specified by the `applicationName` attribute in the configuration file. The `profileAuthenticationOption` parameter specifies whether to search only anonymous profiles, only authenticated profiles, or all profiles. The `OracleProfileProvider` object searches for a match of the `userName` parameter supplied using the `LIKE` keyword and supports wildcard characters using the percent sign`(%` ).

The results returned by this method are constrained by the `pageIndex` and `pageSize` parameters. The `pageSize` parameter identifies the number of `ProfileInfo` objects to return in the `ProfileInfoCollection` object. The `pageIndex` parameter identifies which results page to return. The `totalRecords` parameter is an out parameter for the total number of inactive user profiles that matched the `userName` parameter.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleProfileProvider Class](OracleProfileProviderClass.md)

- [OracleProfileProvider Members](OracleProfileProviderMembers.md)
