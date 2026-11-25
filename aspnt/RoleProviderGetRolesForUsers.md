This method returns an array of role names for the specified user.

### Declaration

    // C#
    public override string[] GetRolesForUser(string userName);

### Parameters

- `userName`

  The user name for which an array of role names is returned.

### Return Value

An array of role names for the specified user name.

### Exceptions

`ArgumentNullException` - The `userName` parameter is null.

`ArgumentException` - The `userName` parameter contains a comma or is longer than 256 characters.

`OracleException` - An Oracle-related error has occurred.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleRoleProvider Class](OracleRoleProviderClass.md)

- [OracleRoleProvider Members](OracleRoleProviderMembers.md)
