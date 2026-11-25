This method removes a user from the database.

### Declaration

    // C#
    public override bool DeleteUser(string userName, bool deleteAllRelatedData);

### Parameters

- `userName`

  The name of the user to delete.

- `deleteAllRelatedData`

  A Boolean value that indicates whether all the data related to the user is to be removed from the database.

### Return Value

Returns `true`, if the user was successfully deleted; `false`, if otherwise or if the user does not exist in the database.

### Exceptions

`ArgumentException` - The `userName` parameter is an empty string, contains a comma, or is longer than 256 characters.

`ArgumentNullException` - The `userName` parameter is a null reference.

### Remarks

Leading and trailing spaces are trimmed from the `userName` parameter value. If `deleteAllRelatedData` is `true`, then all data related to the user in the database such as, data for roles, profiles, and personalization, are also deleted, even if the user does not exist in the Oracle membership database.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleMembershipProvider Class](OracleMembershipProviderClass.md)

- [OracleMembershipProvider Members](OracleMembershipProviderMembers.md)
