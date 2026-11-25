This method returns user information from the database based on the supplied user name.

### Declaration

    // C#
    public override MembershipUser GetUser(string userName, bool userIsOnline);

### Parameters

- `userName`

  The name of the user to get information for.

- `userIsOnline`

  A Boolean value that indicates whether the method updates the last-activity date/time stamp for the user. If the value is set to `true`, it is updated; otherwise, the method returns user information without updating the last-activity date/time stamp.

### Return Value

A `MembershipUser` object populated with the specified user's information from the database.

### Exceptions

`ArgumentException` - The `userName` parameter is an empty string, contains a comma, or is longer than 256 characters.

`ArgumentNullException` - The `userName` parameter is null.

### Remarks

The `GetUser` method provides an option to update the last-activity date/time stamp for the user.

The `GetUser` method returns a `MembershipUser` object populated with information about the specified user. If the user name is not found in the database, then the `GetUser` method returns a null reference.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleMembershipProvider Class](OracleMembershipProviderClass.md)

- [OracleMembershipProvider Members](OracleMembershipProviderMembers.md)
