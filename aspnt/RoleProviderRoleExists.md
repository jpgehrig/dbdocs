This method indicates whether the specified role name exists in the database.

### Declaration

    // C#
    public override bool RoleExists(string roleName);

### Parameters

- `roleName`

  The role name being searched for in the database.

### Return Value

Returns `true` if the role name exists; otherwise, returns `false`.

### Exceptions

`ArgumentNullException` - The `roleName` parameter is null

`OracleException` - An Oracle-related error has occurred.

`ArgumentException` - The `roleName` parameter is an empty string, contains a comma, or is longer than 256 characters.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleRoleProvider Class](OracleRoleProviderClass.md)

- [OracleRoleProvider Members](OracleRoleProviderMembers.md)
