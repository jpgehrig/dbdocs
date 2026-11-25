This method returns a collection of users that match the specified user name.

### Declaration

    // C#
    public override MembershipUserCollection FindUsersByEmail(string userNameToMatch,
      int pageIndex, int pageSize, out int totalRecords);

### Parameters

- `userNameToMatch`

  The user name to search for.

- `pageIndex`

  The zero-based index of the returned results page.

- `pageSize`

  The size of the returned results page.

- `totalRecords`

  The total number of matched users.

### Return Value

Returns a `MembershipUserCollection` object that contains `MembershipUser` objects.

### Exceptions

`ArgumentException` - One of the following conditions exists:

- The `userNameToMatch` parameter is an empty string, contains a comma, or is longer than 256 characters.

- The `pageIndex` parameter is less than 0.

- The `pageSize` parameter is less than 1 or the page upper bound is larger than `Int32.MaxValue`.

**Note:**

The page lower bound is (`pageIndex` \* `pageSize`) and the page upper bound is (`pageIndex` \*`pageSize`) + (`pageSize` - 1).

`ArgumentNullException` - The `userNameToMatch`, `pageIndex`, `pageSize`, or `totalRecords` parameter is null.

### Remarks

Leading and trailing spaces are trimmed from the `userNameToMatch` parameter value.

The results returned by the `FindUsersByName` method are constrained by the `pageIndex` and `pageSize` parameters. The `pageSize` parameter identifies the maximum number of `MembershipUser` objects to return in the `MembershipUserCollection` object. The `pageIndex` parameter identifies which page of results to return. Zero identifies the first page, as the value is zero-based. The `totalRecords` parameter is an out parameter for the total number of users that matched the `userNameToMatch` value.

The `OracleMembershipProvider` class supports extensive search by accepting the percent character (%) as a wildcard.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleMembershipProvider Class](OracleMembershipProviderClass.md)

- [OracleMembershipProvider Members](OracleMembershipProviderMembers.md)
