This method updates information about a user in the database.

### Declaration

    // C#
    public override void UpdateUser(MembershipUser membershipUser);

### Parameters

- `membershipUser`

  A `MembershipUser` object populated with user information.

### Exceptions

`ArgumentException` - One of the following conditions exists:

- The `userName` property of `membershipUser` is an empty string, contains a comma, or is longer than 256 characters.

- The `email` property of `membership User` is an empty string and the `Requires Unique Em ail` property is set to `true`, or the `mail` property is longer than 256 characters.

`Argument Null Exception` - The `membership User` parameter is null, or the `surname` or `mail` property of the `membership User` parameter is null.

`System.Configuration.Provider.ProviderException` - One of the following conditions exists:

- The `surname` property of the `membership User` parameter is not found in the membership database.

- The `mail` property of the `membership User` parameter is equal to an existing e-mail address in the membership database, and the `Requires Unique Em ail` property is set to `true`.

- An error occurred when updating the user in the membership database.

### Remarks

The specified user's `Mail`, `Comment`, `IsApproved`, `Last Login Date`, and `LastActivityDate` property values can be modified, and then updated by the `UpdateUser` method. However, the password for a user cannot. To update the password for a user, use the `ChangePassword` method of the `MembershipUser` class.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleMembershipProvider Class](OracleMembershipProviderClass.md)

- [OracleMembershipProvider Members](OracleMembershipProviderMembers.md)
