This method returns a collection of all the users in the database.

### Declaration

    // C#
    public override MembershipUserCollection GetAllUsers(int pageIndex, int pageSize,
       out int totalRecords);

### Parameters

- `pageIndex`

  The zero-based index of the page of results to return.

- `pageSize`

  The size of the page of results to return.

- `totalRecords`

  The total number of users.

### Return Value

A `MembershipUserCollection` object that contains `MembershipUser` objects.

### Exceptions

`ArgumentException` - The `pageIndex` parameter is less than 0, or the `pageSize` parameter is less than 1 or the page upper bound is larger than `Int32.MaxValue`.

**Note:**

The page lower bound is (`pageIndex` \* `pageSize`) and the page upper bound is (`pageIndex` \*`pageSize`) + (`pageSize` - 1).

`ArgumentNullException` - The `pageIndex`, `pageSize`, or `totalRecords` parameter is null.

### Remarks

The results returned by the `GetAllUsers` method are constrained by the `pageIndex` and `pageSize` parameters. The `pageSize` parameter identifies the maximum number of `MembershipUser` objects to return in the `MembershipUserCollection` object. The `pageIndex` parameter identifies which page of results to return. Zero identifies the first page, as the value is zero-based. The `totalRecords` parameter is an out parameter for the total number of users for the configured `applicationName`.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleMembershipProvider Class](OracleMembershipProviderClass.md)

- [OracleMembershipProvider Members](OracleMembershipProviderMembers.md)
