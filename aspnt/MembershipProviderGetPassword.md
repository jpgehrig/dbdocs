This method returns the password for the specified user name from the database.

### Declaration

    // C#
    public override string GetPassword(string userName, string passwordAnswer);

### Parameters

- `userName`

  The user to retrieve the password for.

- `passwordAnswer`

  The password answer for the user.

### Return Value

A password string for the specified user name.

### Exceptions

`ArgumentNullException` - The `userName` parameter is null or the `passwordAnswer` parameter is null when the `RequiresQuestionAndAnswer` property is `true`.

`System.Web.Security.MembershipPasswordException` - The `passwordAnswer` parameter is invalid or the user identified by `userName` is being locked.

`System.Configuration.Provider.ProviderException` - The `userName` parameter is not found in the membership database, or an error occurred when retrieving the password from the membership database.

`NotSupportedException` - `EnablePasswordRetrieval` property is set to false.

`ArgumentException` - One of the following conditions exists:

- The `userName` parameter is an empty string, contains a comma, or is longer than 256 characters.

- The `passwordAnswer` parameter is an empty string and the `RequiresQuestionAndAnswer` property is `true`, or the `passwordAnswer` parameter is longer than 128 characters (including the encoded version).

### Remarks

Leading and trailing spaces are trimmed from the `userName` and `passwordAnswer` parameter values.

The `GetPassword` method requires that the `EnablePasswordRetrieval` property be set to `true`. However, if the `PasswordFormat` property is set to `Hashed`, then a `ProviderException` is thrown when the provider is initialized. In other words, the `GetPassword` method cannot retrieve `Hashed` passwords. By default, the `EnablePasswordRetrieval` property is set to `false`.

If the `RequiresQuestionAndAnswer` property is set to `true` and an incorrect password answer is supplied to the `GetPassword` method, then the internal counter that tracks invalid password-answer attempts is incremented by one. This can result in the user being locked out and unable to log on until the lock status is cleared by a call to the `UnlockUser` method. If the correct password answer is supplied and the user is not currently locked out, then the internal counter that tracks invalid password-answer attempts is reset to zero.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleMembershipProvider Class](OracleMembershipProviderClass.md)

- [OracleMembershipProvider Members](OracleMembershipProviderMembers.md)
