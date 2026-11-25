This method unlocks a user so that the user can be validated.

### Declaration

    // C#
    public override bool UnLockUser(string userName);

### Parameters

- `userName`

  The name of the user to be unlocked.

### Return Value

Returns `true`, if the user was successfully unlocked; `false`, if otherwise.

### Exceptions

`ArgumentException` - The `userName` parameter is an empty string, contains a comma, or is longer than 256 characters.

`ArgumentNullException` - The `userName` parameter is null.

### Remarks

Leading and trailing spaces are trimmed from the `userName` parameter value.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleMembershipProvider Class](OracleMembershipProviderClass.md)

- [OracleMembershipProvider Members](OracleMembershipProviderMembers.md)
