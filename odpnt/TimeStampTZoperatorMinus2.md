This static operator subtracts the supplied `OracleIntervalYM` value, from the supplied `OracleTimeStampTZ` value, and returns a new `OracleTimeStampTZ` structure.

### Declaration

    // C#
    public static operator - (OracleTimeStampTZ value1,
      OracleIntervalYM value2);

### Parameters

- `value1`

  An `OracleTimeStampTZ`.

- `value2`

  An `OracleIntervalYM`.

### Return Value

An `OracleTimeStampTZ` structure.

### Remarks

If either parameter has a null value, the returned `OracleTimeStampTZ` has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStampTZ Structure](OracleTimeStampTZStructure.md)

- [OracleTimeStampTZ Members](TimeStampTZMembers.md)
