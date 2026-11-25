This static method returns an `OracleIntervalYM` structure and sets its value for time interval using a string.

### Declaration

    // C#
    public static OracleIntervalYM Parse (string intervalStr);

### Parameters

- `intervalStr`

  A string representing the Oracle `INTERVAL` `YEAR` `TO` `MONTH`.

### Return Value

Returns an `OracleIntervalYM` structure.

### Exceptions

`ArgumentException` - The `intervalStr` parameter is not in the valid format or `intervalStr` has an invalid value.

`ArgumentNullException` - The `intervalStr` parameter is null.

### Remarks

The value specified in the supplied `intervalStr` must be in the Year-Month format.

### Example

"1-2" means 1 year and 2 months.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleIntervalYM Structure](OracleIntervalYMStructure.md)

- [OracleIntervalYM Members](IntervalYMMembers.md)
