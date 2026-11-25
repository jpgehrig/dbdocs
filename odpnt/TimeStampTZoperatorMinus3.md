This static operator subtracts the supplied `TimeSpan` value, from the supplied `OracleTimeStampTZ` value, and returns a new `OracleTimeStampTZ` structure.

### Declaration

    // C#
    public static operator - (OracleTimeStampTZ value1, TimeSpan value2);

### Parameters

- `value1`

  An `OracleTimeStampTZ`.

- `value2`

  A `TimeSpan`.

### Return Value

An `OracleTimeStampTZ` structure.

### Remarks

If the `OracleTimeStampTZ` instance has a null value, the returned `OracleTimeStampTZ` structure has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStampTZ Structure](OracleTimeStampTZStructure.md)

- [OracleTimeStampTZ Members](TimeStampTZMembers.md)
