This method subtracts an `OracleTimeStampTZ` value from the current instance and returns an `OracleIntervalYM` that represents the time interval.

### Declaration

    // C#
    public OracleIntervalYM GetYearsBetween(OracleTimeStampTZ val);

### Parameters

- `val`

  The `OracleTimeStampTZ` value being subtracted.

### Return Value

An `OracleIntervalYM` that represents the interval between two `OracleTimeStampTZ` values.

### Remarks

If either the current instance or the parameter has a null value, the returned `OracleIntervalYM` has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStampTZ Structure](OracleTimeStampTZStructure.md)

- [OracleTimeStampTZ Members](TimeStampTZMembers.md)
