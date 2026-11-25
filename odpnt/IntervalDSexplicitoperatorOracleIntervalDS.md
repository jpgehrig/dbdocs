This type conversion operator converts a string to an `OracleIntervalDS` structure.

### Declaration

    // C#
    public static explicit operator OracleIntervalDS (string intervalStr);

### Parameters

- `intervalStr`

  A string representation of an Oracle `INTERVAL` `DAY` `TO` `SECOND`.

### Return Value

An `OracleIntervalDS` structure.

### Exceptions

`ArgumentException` - The supplied `intervalStr` parameter is not in the correct format or has an invalid value.

`ArgumentNullException` - The `intervalStr` parameter is null.

### Remarks

The returned `OracleIntervalDS` structure contains the same time interval represented by the supplied `intervalStr`. The value specified in the supplied `intervalStr` must be in Day HH:MI:SSxFF format.

### Example

`"1 2:3:4.99"` means 1 day, 2 hours, 3 minutes 4 seconds and 990 milliseconds or 1 day, 2 hours, 3 minutes 4 seconds and 990000000 nanoseconds.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleIntervalDS Structure](OracleIntervalDSStructure.md)

- [OracleIntervalDS Members](IntervalDSMembers.md)
