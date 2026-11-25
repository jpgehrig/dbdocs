This method deletes user profile data that has its last activity date on or before the specified date and time.

### Declaration

    // C#
    public override int DeleteInactiveProfiles(ProfileAuthenticationOption
       profileAuthenticationOption, DateTime inactiveSinceDateTime);

### Parameters

- `profileAuthenticationOption`

  The options are `Anonymous`, `Authenticated`, or `All`, to indicate which profiles to delete.

- `inactiveSinceDateTime`

  The cut-off date and time that indicate a profile is inactive.

### Return Value

An integer value that indicates the number of inactive profiles deleted from the data source.

### Remarks

This method deletes inactive profile data from the data source for the application specified by the `applicationName` attribute in the configuration file. The `profileAuthenticationOption` parameter specifies whether to search only anonymous profiles, only authenticated profiles, or all profiles. This method deletes any profile with a last activity date and time occurring on or before the specified `inactiveSinceDateTime` parameter value.

The delete profiles operation is a transactional operation. If an error is encountered, the transaction is rolled back and no changes are made.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleProfileProvider Class](OracleProfileProviderClass.md)

- [OracleProfileProvider Members](OracleProfileProviderMembers.md)
