This method deletes a role in the database.

### Declaration

    // C#
    public override bool DeleteRole(string roleName, bool throwOnPopulatedRole);

### Parameters

- `roleName`

  The role name to be deleted from the database.

- `throwOnPopulatedRole`

  A Boolean value that, if set to `true`, causes an exception if the role contains any user names. If the value is set to `false`, deletes the role from the database.

### Return Value

Returns `true` if the specified role was successfully deleted; otherwise, returns `false`.

### Exceptions

`ArgumentNullException` - The `roleName` parameter is null.

`System.Configuration.Provider.ProviderException` - The role name contains at least one user name and the `throwOnPopulatedRole` parameter is set to `true`.

`OracleException` - An Oracle-related error has occurred.

`ArgumentException` - The `roleName` parameter is an empty string, contains a comma, or is longer than 256 characters:

### Remarks

If the `throwOnPopulatedRole` parameter is set to `false`, then it deletes the specified role from the database regardless of whether it contains any users. If the `throwOnPopulatedRole` parameter is set to `true`, then an exception is thrown if the specified role in the database contains any users, but the role is not deleted.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleRoleProvider Class](OracleRoleProviderClass.md)

- [OracleRoleProvider Members](OracleRoleProviderMembers.md)
