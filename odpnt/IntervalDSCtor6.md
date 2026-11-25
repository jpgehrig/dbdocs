This constructor creates a new instance of the `OracleIntervalDS` structure and sets its value to the provided byte array, which is in an internal Oracle `INTERVAL` `DAY` `TO` `SECOND` format.

### Declaration

    // C#
    public OracleIntervalDS (byte[ ] bytes);

### Parameters

- `bytes`

  A byte array that is in an internal Oracle `INTERVAL` `DAY` `TO` `SECOND` format.

### Exceptions

`ArgumentException` - `bytes` is not in internal Oracle `INTERVAL` `DAY` `TO` `SECOND` format, or `bytes` is not a valid Oracle `INTERVAL` `DAY` `TO` `SECOND`.

`ArgumentNullException` - `bytes` is null.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleIntervalDS Structure](OracleIntervalDSStructure.md)

- [OracleIntervalDS Members](IntervalDSMembers.md)
