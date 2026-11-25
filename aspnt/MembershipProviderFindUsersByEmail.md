This method returns a collection of users whose e-mail addresses match the specified e-mail address.

### Declaration

    // C#
    public override MembershipUserCollection FindUsersByEmail(string emailToMatch,
       int pageIndex, int pageSize, out int totalRecords);

### Parameters

- `emailToMatch`

  The email address to search for.

- `pageIndex`

  The index of the page of results to return. The `PageIndex` is zero-based.

- `pageSize`

  The size of the page of results to return.

- `totalRecords`

  The total number of matched users.

### Return Value

Returns a `MembershipUserCollection` object that contains `MembershipUser` objects.

### Exceptions

`ArgumentException` - One of the following conditions exists:

- The `emailToMatch` parameter is an empty string or is longer than 256 characters.

- The `pageIndex` parameter is less than 0.

- The `pageSize` parameter is less than 1 or the page upper bound is larger than `Int32.MaxValue`.

`ArgumentNullException` - The `emailToMatch`, `pageIndex`, `pageSize`, or `totalRecords` parameter is null.

### Remarks

Leading and trailing spaces are trimmed from the `emailToMatch` parameter value. The results returned by the `FindUsersByEmail` method are constrained by the `pageIndex` and `pageSize` parameters. The `pageSize` parameter identifies the maximum number of `MembershipUser` objects to return in the `MembershipUserCollection` object. The `pageIndex` parameter identifies which page of results to return. Zero identifies the first page, as the value is zero-based. The `totalRecords` parameter is an out parameter for the total number of users that matched the `emailToMatch` value.

The `OracleMembershipProvider` class supports extensive searching by accepting the percent character (%) as a wildcard.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleMembershipProvider Class](OracleMembershipProviderClass.md)

- [OracleMembershipProvider Members](OracleMembershipProviderMembers.md)
