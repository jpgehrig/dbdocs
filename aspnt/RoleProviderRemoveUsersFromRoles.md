This method removes the specified array of users from the specified array of role names.

### Declaration

    // C#
    public override void RemoveUsersFromRoles(string[] userNames, string[] roleNames);

### Parameters

- `userNames`

  An array of user names to remove from the role names.

- `roleNames`

  An array of role names to remove the user names from.

### Exceptions

`ArgumentNullException` - One of the users in the `userNames` parameter or one of the roles in the `roleNames` parameter is null.

`OracleException` - An Oracle-related error has occurred.

`System.Configuration.Provider.ProviderException` - One or more of the role names or user names does not exist in the database, or one or more of the user names is not associated a role name.

`ArgumentException` - The `roleNames` or `userNames` parameter is an empty string, contains a comma, is longer than 256 characters, or contains a duplicate element.

### Remarks

This method removes the specified array of user names from the specified array of role names. The updates are made within a transaction. If an error occurs, the transaction is rolled back.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleRoleProvider Class](OracleRoleProviderClass.md)

- [OracleRoleProvider Members](OracleRoleProviderMembers.md)
