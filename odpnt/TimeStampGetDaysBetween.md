This method subtracts an `OracleTimeStamp` value from the current instance and returns an `OracleIntervalDS` that represents the time difference between the supplied `OracleTimeStamp` structure and the current instance.

### Declaration

    // C#
    public OracleIntervalDS GetDaysBetween(OracleTimeStamp value1);

### Parameters

- `value1`

  The `OracleTimeStamp` value being subtracted.

### Return Value

An `OracleIntervalDS` that represents the interval between two `OracleTimeStamp` values.

### Remarks

If either the current instance or the parameter has a null value, the returned `OracleIntervalDS` has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStamp Structure](OracleTimeStampStructure.md)

- [OracleTimeStamp Members](TimeStampMembers.md)
