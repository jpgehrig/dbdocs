This method returns the count of profiles where the last activity date is on or before the specified date and time.

### Declaration

    // C#
    public override int GetNumberOfInactiveProfiles
      (ProfileAuthenticationOption profileAuthenticationOption,
       DateTime inactiveSinceDateTime);

### Parameters

- `profileAuthenticationOption`

  `Anonymous`, `Authenticated`, or `All` profiles to be searched.

- `inactiveSinceDateTime`

  The cut-off date and time that indicate a profile is inactive.

### Return Value

An integer value indicating the number of user profiles that match the inactive date and time supplied.

### Remarks

This method returns a count of inactive profiles from the data source for the application specified by the `applicationName` attribute in the configuration file. The `profileAuthenticationOption` parameter specifies whether to search only anonymous profiles, only authenticated profiles, or all profiles. Of the searched user profiles, any profiles with a last activity date and time on or before the specified `inactiveSinceDateTime` parameter value are counted.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleProfileProvider Class](OracleProfileProviderClass.md)

- [OracleProfileProvider Members](OracleProfileProviderMembers.md)
