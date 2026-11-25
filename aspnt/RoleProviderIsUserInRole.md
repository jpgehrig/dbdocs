This method indicates whether the specified user is in the specified role.

### Declaration

    // C#
    public override bool IsUserInRole(string userName, string roleName);

### Parameters

- `userName`

  The user name being searched for.

- `roleName`

  The role name being searched in.

### Return Value

Returns `true` if the specified user name is in the specified role name; otherwise, returns `false`.

### Exceptions

`ArgumentNullException` - The `userName` or `roleName` parameter is null.

`OracleException` - An Oracle-related error has occurred.

`ArgumentException` - One of the following conditions exists:

- The `roleName` parameter is an empty string, contains a comma, or is longer than 256 characters.

- The `userName` parameter contains a comma or is longer than 256 characters.

### Remarks

This method determines if the specified user name exists in the specified role name in the database.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleRoleProvider Class](OracleRoleProviderClass.md)

- [OracleRoleProvider Members](OracleRoleProviderMembers.md)
