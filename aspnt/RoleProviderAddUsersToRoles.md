This method adds the specified users to the specified roles.

### Declaration

    // C#
    public override void AddUsersToRoles(string[] userNames, string[] roleNames);

### Parameters

- `userNames`

  An array of user names to be added to roles.

- `roleNames`

  An array of role names to add the user names to.

### Exceptions

`ArgumentNullException` - One of the users in `userNames` or one of the roles in `roleNames` is null.

`ArgumentException` - Either the `roleNames` or `userNames` parameter is an empty string, contains a comma, is longer than 256 characters, or contains a duplicate element.

`System.Configuration.Provider.ProviderException` - One or more role names were not found, or one or more user names are already associated with one or more role names.

`OracleException` - An Oracle-related error has occurred.

### Remarks

This method adds one or more user names to one or more of the specified roles. The updates are performed in a transaction. If an error occurs, then the transaction is rolled back and no updates are made.

If one of the user names does not exist in the database, then the user name will be created and added to the database.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleRoleProvider Class](OracleRoleProviderClass.md)

- [OracleRoleProvider Members](OracleRoleProviderMembers.md)
