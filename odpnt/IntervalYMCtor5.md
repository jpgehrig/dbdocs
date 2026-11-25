This method creates a new instance of the `OracleIntervalYM` structure and sets its value to the provided byte array, which is in an internal Oracle `INTERVAL` `DAY` `TO` `SECOND` format.

### Declaration

    // C#
    public OracleIntervalYM (byte[] bytes);

### Parameters

- `bytes`

  A byte array that is in an internal Oracle `INTERVAL` `YEAR` `TO` `MONTH` format.

### Exceptions

`ArgumentException` - The supplied byte array is not in an internal Oracle `INTERVAL` `YEAR` `TO` `MONTH` format or the supplied byte array has an invalid value.

`ArgumentNullException` - `bytes` is null.

### Remarks

The supplied byte array must be in an internal Oracle `INTERVAL` `YEAR` `TO` `MONTH` format.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleIntervalYM Structure](OracleIntervalYMStructure.md)

- [OracleIntervalYM Members](IntervalYMMembers.md)
