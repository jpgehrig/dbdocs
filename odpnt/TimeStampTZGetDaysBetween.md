This method subtracts an `OracleTimeStampTZ` value from the current instance and returns an `OracleIntervalDS` that represents the time interval.

### Declaration

    // C#
    public OracleIntervalDS GetDaysBetween(OracleTimeStampTZ value1);

### Parameters

- `value1`

  The `OracleTimeStampTZ` value being subtracted.

### Return Value

An `OracleIntervalDS` that represents the interval between two `OracleTimeStampTZ` values.

### Remarks

If either the current instance or the parameter has a null value, the returned `OracleIntervalDS` has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStampTZ Structure](OracleTimeStampTZStructure.md)

- [OracleTimeStampTZ Members](TimeStampTZMembers.md)
