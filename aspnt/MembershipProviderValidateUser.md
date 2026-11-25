This method validates the user.

### Declaration

    // C#
    public override bool ValidateUser(string userName, string password);

### Parameters

- `userName`

  The name of the user to be validated.

- `password`

  The password for the specified user.

### Return Value

Returns `true` if the specified user name and password are valid; returns `false` if they are not valid or the user does not exist in the database.

### Remarks

Leading and trailing spaces are trimmed from the `userName` and `password` parameter values.

When a user is successfully validated, the last activity date and last sign-in date values are updated to the current date and time in the database.

The `ValidateUser` method returns `false` on any user who was created with the `isApproved` parameter set to `false`.

If an incorrect password is supplied to the `ValidateUser` method, then the internal counter that tracks invalid password attempts is incremented by one. This can result in the user being locked out and unable to log on until the lock status is cleared by a call to the `UnlockUser` method. If the correct password is supplied and the user is not currently locked out, then the internal counters that track invalid password and password-answer attempts are reset to zero.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleMembershipProvider Class](OracleMembershipProviderClass.md)

- [OracleMembershipProvider Members](OracleMembershipProviderMembers.md)
