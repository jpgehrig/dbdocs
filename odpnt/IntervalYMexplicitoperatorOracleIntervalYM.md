This type conversion operator converts the string `intervalStr` to an `OracleIntervalYM` structure.

### Declaration

    // C#
    public static explicit operator OracleIntervalYM (string intervalStr);

### Parameters

- `intervalStr`

  A string representation of an Oracle `INTERVAL` `YEAR` `TO` `MONTH`.

### Return Value

An `OracleIntervalYM` structure.

### Exceptions

`ArgumentException` - The supplied `intervalStr` parameter is not in the correct format or has an invalid value.

`ArgumentNullException` - The `intervalStr` parameter is null.

### Remarks

The returned `OracleIntervalDS` structure contains the same time interval represented by the supplied `intervalStr`. The value specified in the supplied `intervalStr` must be in Year-Month format.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleIntervalYM Structure](OracleIntervalYMStructure.md)

- [OracleIntervalYM Members](IntervalYMMembers.md)
