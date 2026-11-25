This method returns a collection containing zero or more `PersonalizationStateInfo`-derived objects based on scope and specific query parameters.

### Declaration

    // C#
    public override PersonalizationStateInfoCollection FindState(PersonalizationScope
       scope, PersonalizationStateQuery query, int pageIndex, int pageSize,
       out int totalRecords);

### Parameters

- `scope`

  The scope of query (User or Shared) for personalization information. This cannot be a null reference.

- `query`

  The query to be used for filtering personalization information. This can be a null reference.

- `pageIndex`

  The location where the query starts.

- `pageSize`

  The number of records to return.

- `totalRecords`

  The total number of records available.

### Return Value

A `PersonalizationStateInfoCollection` object containing zero or more `PersonalizationStateInfo`-derived objects.

### Exceptions

`ArgumentOutOfRangeException` - The scope contains a value other than `PersonalizationScope.User` or `PersonalizationScope.Shared`.

`OracleException` - An Oracle-related error has occurred.

`ArgumentException` - One of the following conditions exists:

- The value of the `pageSize` parameter is 0 or 1.

- The `pageIndex` or `pageSize` parameter is less than 0.

- ((`pageIndex * pageSize + pageSize`) - 1) is greater than `Int32.MaxValue`. -1 accounts for zero-based indexing of records.

### Remarks

The `PersonalizationStateInfo`-derived objects should be returned in alphabetic order and sorted by a combination of their `Path` and `Username` property values, both in ascending order.

This method passes the query wildcard characters to the underlying Oracle database. The database performs a wildcard search on a partial path with the wildcard character appearing at the beginning, the end, or the middle of the search string text in the `PathToMatch` property of the `query` parameter. For example, setting the `PathToMatch` property to `~/appdir%` finds all paths that start with `~/appdir`.

Likewise, in a wildcard search on a partial user name, the wildcard character can appear at any point in the text string of the `UsernameToMatch` property of the `query` parameter. For example, to find all user names that start with `scott`, the `UsernameToMatch` parameter looks like `scott%`.

The following query rules must be followed:

- If only the `scope` parameter is provided, and the `query` parameter is null or all the properties on the `query` parameter return either a null reference or default values, then all records matching the indicated `scope` parameter are returned.

- If the `PathToMatch` property is not a null reference, then the returned records are also filtered based on paths that match the `PathToMatch` value.

- If the `UsernameToMatch` property is not a null reference, then the returned records are also filtered based on user names that match the `UsernameToMatch` property value.

- If the `UserInactiveSinceDate` property is not equal to the `MaxValue`, then the records returned are also filtered to return only those records associated with inactive users. The comparison includes records where the `Last` `ActivityDate` property is less than or equal to the `User` `Inactive` `Since` `Date` property.

This method does not validate combinations of query parameters. For example, the application code can request a set of personalization state records associated with a specific user name in the shared scope. Because user names are not associated with shared information, the returned collection is empty.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OraclePersonalizationProvider Class](OraclePersonalizationProviderClass.md)

- [OraclePersonalizationProvider Members](OraclePersonalizationProviderMembers.md)
