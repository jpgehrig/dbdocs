This method updates the password for a user.

### Declaration

    // C#
    public override bool ChangePassword(string userName, string oldPassword,
      string newPassword);

### Parameters

- `userName`

  The user to update the password for.

- `oldPassword`

  The current password for the specified user.

- `newPassword`

  The new password for the specified user.

### Return Value

Returns `true` if the password was updated successfully; otherwise, returns `false`.

### Exceptions

`ArgumentNullException` - The `userName`, `oldPassword`, or `newPassword` parameter is null.

`System.Web.Security.MembershipPasswordException` - `userName` was not found in the membership database.

`System.Configuration.Provider.ProviderException` - An error occurred when setting the new password in the database.

`Exception` - An unhandled exception has occurred.

`ArgumentException` - One of the following conditions exists:

- The `userName` parameter is an empty string, contains a comma, or is longer than 256 characters.

- The `oldPassword` parameter is an empty string or is longer than 128 characters.

- The `newPassword` parameter is an empty string, is longer than 128 characters (including the encoded version), is less than the value of the `MinRequiredPasswordLength` property, has a number of nonalphanumeric characters less than the value of `MinRequiredNonAlphanumericCharacters` property, or does not match the regular expression defined in the `PasswordStrengthRegularExpression` property.

- The change-password operation was canceled by a subscriber to the `ValidatingPassword` event, and the `FailureInformation` property was a null reference.

### Remarks

The `ChangePassword` method returns `true` if the supplied user name and password are valid and the password was updated successfully; otherwise, it returns `false`.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleMembershipProvider Class](OracleMembershipProviderClass.md)

- [OracleMembershipProvider Members](OracleMembershipProviderMembers.md)
