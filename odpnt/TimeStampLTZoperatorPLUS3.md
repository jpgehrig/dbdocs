This static operator adds the supplied `TimeSpan` to the supplied `OracleTimeStampLTZ` and returns a new `OracleTimeStampLTZ` structure.

### Declaration

    // C#
    public static operator +(OracleTimeStampLTZ value1, TimeSpan value2);

### Parameters

- `value1`

  An `OracleTimeStampLTZ`.

- `value2`

  A `TimeSpan`.

### Return Value

An `OracleTimeStampLTZ.`

### Remarks

If the `OracleTimeStampLTZ` instance has a null value, the returned `OracleTimeStampLTZ` has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStampLTZ Structure](OracleTimeStampLTZStructure.md)

- [OracleTimeStampLTZ Members](TimeStampLTZMembers.md)
