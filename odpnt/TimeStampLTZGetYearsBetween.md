This method subtracts an `OracleTimeStampLTZ` value from the current instance and returns an `OracleIntervalYM` that represents the time interval.

### Declaration

    // C#
    public OracleIntervalYM GetYearsBetween(OracleTimeStampLTZ value1);

### Parameters

- `value1`

  The `OracleTimeStampLTZ` value being subtracted.

### Return Value

An `OracleIntervalYM` that represents the interval between two `OracleTimeStampLTZ` values.

### Remarks

If either the current instance or the parameter has a null value, the returned `OracleIntervalYM` has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStampLTZ Structure](OracleTimeStampLTZStructure.md)

- [OracleTimeStampLTZ Members](TimeStampLTZMembers.md)
