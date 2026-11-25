This method returns an array of user names that match the specified user name, for the specified role name.

### Declaration

    // C#
    public override string[ ] FindUsersInRole(string roleName, string
       userNameToMatch);

### Parameters

- `roleName`

  The role name being searched for in the database.

- `userNameToMatch`

  The user name being searched for.

### Return Value

A string array that contains user names in the specified role that match the specified `userNameToMatch` parameter.

### Exceptions

`ArgumentNullException` - The `roleName` or `userNameToMatch` parameter is null.

`OracleException` - An Oracle-related error has occurred.

`System.Configuration.Provider.ProviderException` - The role name does not exist in the database.

`ArgumentException` - One of the following conditions exists:

- The `roleName` parameter is an empty string, contains a comma, or is longer than 256 characters.

- The `userNameToMatch` parameter is an empty string or is longer than 256 characters.

### Remarks

This method returns an array of user names that match the specified user name, for the specified role name. This method supports Oracle wildcard characters. If the `userNameToMatch` parameter is set to `"oraUser%"`, then an array is returned for users such as `"oraUser1"`, `"oraUser2"`, and so on. However, if the `userNameToMatch` parameter is set to `"oraUser"`, then the array is returned with just the username `"oraUser"`, if there is an `"oraUser"`.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleRoleProvider Class](OracleRoleProviderClass.md)

- [OracleRoleProvider Members](OracleRoleProviderMembers.md)
