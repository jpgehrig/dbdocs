This method returns the number of rows in the underlying Oracle database that are within the specified scope.

### Declaration

    // C#
    public override int GetCountOfState(PersonalizationScope scope,
       PersonalizationStateQuery query);

### Parameters

- `scope`

  The scope of query (User or Shared) for personalization information. This cannot be a null reference.

- `query`

  The query to be used for filtering personalization information. This can be a null reference.

### Return Value

The number of rows in the underlying data source that are within the specified scope parameter.

### Exceptions

`ArgumentException` -The `PathToMatch` or the `UsernameToMatch` property of `query` is a non-null reference and is an empty string ("") after trimming.

`ArgumentOutOfRangeException` - The scope specified is not a valid value from the `PersonalizationScope` enumeration.

`OracleException` - An Oracle-related error has occurred.

### Remarks

This method passes the query wildcard characters to the underlying Oracle database. The database performs a wildcard search on a partial path with the wildcard character appearing at the beginning, the end, or the middle of the search string text in the `PathToMatch` property of the `query` parameter. For example, setting the `PathToMatch` property to `~/appdir%` finds all paths that start with `~/appdir`.

Likewise, in a wildcard search on a partial user name, the wildcard character can appear at any point in the text string of the `UsernameToMatch` property of the `query` parameter. For example, to find all user names that start with `scott`, the `UsernameToMatch` parameter looks like `scott%`

The following query constraints must be followed:

- If only the `scope` parameter is provided, and the `query` parameter is a null reference or all the properties on the `query` parameter return either a null reference or default values, then all records matching the indicated `scope` parameter are returned.

- If the `PathToMatch` property is not a null reference, then the records returned are also filtered based on paths that match the `PathToMatch` value.

- If the `UsernameToMatch` property is not a null reference, then the returned records are also filtered based on user names that match the `UsernameToMatch` property value.

- If the `UserInactiveSinceDate` property is not equal to the `MaxValue`, then the returned records are also filtered to return only those records associated with inactive users. The comparison includes records where the `LastActivityDate` property is less than or equal to the `UserInactiveSinceDate` property.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OraclePersonalizationProvider Class](OraclePersonalizationProviderClass.md)

- [OraclePersonalizationProvider Members](OraclePersonalizationProviderMembers.md)
