This constructor creates a new instance of the `OracleIntervalDS` structure and sets its value using a string that indicates a period of time.

### Declaration

    // C#
    public OracleIntervalDS(string intervalStr);

### Parameters

- `intervalStr`

  A string representing the Oracle `INTERVAL` `DAY` `TO` `SECOND`.

### Exceptions

`ArgumentException` - The `intervalStr` parameter is not in the valid format or has an invalid value.

`ArgumentNullException` - The `intervalStr` parameter is null.

### Remarks

The value specified in the supplied `intervalStr` must be in Day HH:MI:SSxFF format.

### Example

"1 2:3:4.99" means 1 day, 2 hours, 3 minutes, 4 seconds, and 990 milliseconds or 1 day, 2 hours, 3 minutes, 4 seconds, and 990000000 nanoseconds.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleIntervalDS Structure](OracleIntervalDSStructure.md)

- [OracleIntervalDS Members](IntervalDSMembers.md)
