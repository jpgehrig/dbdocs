This method updates the password question and answer for a user.

### Declaration

    // C#
    public override bool ChangePasswordQuestionAndAnswer(string userName, string
       password, string newPasswordQuestion, string newPasswordAnswer);

### Parameters

- `userName`

  The user that the password question and answer change for.

- `password`

  The password for the specified user.

- `newPasswordQuestion`

  The new password question for the specified user.

- `newPasswordAnswer`

  The new password answer for the specified user.

### Return Value

Returns `true`, if the password question and answer were updated successfully; `false`, if otherwise.

### Exceptions

`ArgumentException` - One of the following conditions exists:

- The `userName` parameter is an empty string, contains a comma, or is longer than 256 characters.

- The `password` parameter is an empty string or is longer than 128 characters.

- The `newPasswordQuestion` parameter is an empty string or is longer than 256 characters.

- The `newPasswordAnswer` parameter is an empty string or is longer than 128 characters (including the encoded version).

### Remarks

If the user name and password supplied are valid and the password question and answer were updated successfully, then this method returns true. Otherwise, it returns `false`.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleMembershipProvider Class](OracleMembershipProviderClass.md)

- [OracleMembershipProvider Members](OracleMembershipProviderMembers.md)
