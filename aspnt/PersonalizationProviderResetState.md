This method deletes personalization state information from the underlying data source, based on the specified parameters.

### Declaration

    // C#
    public override int ResetState(PersonalizationScope scope, string[] paths,
       string[] usernames);

### Parameters

- `scope`

  A `PersonalizationScope` type indicating the personalization information to be queried. This value cannot be a null reference.

- `paths`

  The paths for personalization information in the shared `scope` parameter to be deleted.

- `usernames`

  The user names for personalization information in the user `scope` parameter to be deleted.

### Return Value

The number of rows deleted.

### Exceptions

`ArgumentOutOfRangeException` - The `scope` parameter specified is not a member of the `PersonalizationScope` enumeration value.

`OracleException` - An Oracle-related error has occurred.

`ArgumentException` - Either of the following conditions exists:

- The `paths` or `usernames` parameter is an empty array.

- Elements of the `paths` or `usernames` arrays do not meet the validation rules. Validation rules are discussed in the following Remarks section.

### Remarks

This method performs its operations as a single, atomic transaction.

Any `paths` and `usernames` elements contained within the respective arrays must meet the following validation rules. If a validation rule fails for any member of the parameter arrays, then an `ArgumentException` exception is thrown. The validation rules are:

- Null reference values are not allowed.

- An empty string ("") is not allowed. Parameters should be trimmed prior to performing an empty string check.

- The `usernames` array cannot contain a comma (,).

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OraclePersonalizationProvider Class](OraclePersonalizationProviderClass.md)

- [OraclePersonalizationProvider Members](OraclePersonalizationProviderMembers.md)
