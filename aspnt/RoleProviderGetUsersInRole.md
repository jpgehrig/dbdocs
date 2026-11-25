This method returns an array of users in the specified role name.

### Declaration

    // C#
    public override string[ ] GetUsersInRole(string roleName);

### Parameters

- `roleName`

  The role name for which an array of users is returned.

### Return Value

An array of user names in the specified role name.

### Exceptions

`ArgumentNullException` - The `roleName` parameter is null.

`OracleException` - An Oracle-related error has occurred.

`System.Configuration.Provider.ProviderException` - The role name does not exist in the database.

`ArgumentException` - The `roleName` parameter is an empty string, contains a comma, or is longer than 256 characters:

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleRoleProvider Class](OracleRoleProviderClass.md)

- [OracleRoleProvider Members](OracleRoleProviderMembers.md)
