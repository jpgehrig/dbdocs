This method subtracts an `OracleTimeStampLTZ` value from the current instance and returns an `OracleIntervalDS` that represents the difference.

### Declaration

    // C#
    public OracleIntervalDS GetDaysBetween(OracleTimeStampLTZ value1);

### Parameters

- `value1`

  The `OracleTimeStampLTZ` value being subtracted.

### Return Value

An `OracleIntervalDS` that represents the interval between two `OracleTimeStampLTZ` values.

### Remarks

If either the current instance or the parameter has a null value, the returned `OracleIntervalDS` has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStampLTZ Structure](OracleTimeStampLTZStructure.md)

- [OracleTimeStampLTZ Members](TimeStampLTZMembers.md)
