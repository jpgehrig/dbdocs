This method adds a new role to the database.

### Declaration

    // C#
    public override void CreateRole(string roleName);

### Parameters

- `roleName`

  The role name to be created in the database.

### Exceptions

`ArgumentNullException` - The `roleName` parameter is null.

`ArgumentException` - The `roleName` parameter is an empty string, contains a comma, or is longer than 256 characters.

`System.Configuration.Provider.ProviderException` - The role name already exists in the database.

`OracleException` - An Oracle-related error has occurred.

### Remarks

This method creates a new role in the database.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleRoleProvider Class](OracleRoleProviderClass.md)

- [OracleRoleProvider Members](OracleRoleProviderMembers.md)
