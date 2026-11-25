This static operator adds the supplied `OracleIntervalDS` to the supplied `OracleTimeStampTZ` and returns a new `OracleTimeStampTZ` structure.

### Declaration

    // C#
    public static operator +(OracleTimeStampTZ value1,
      OracleIntervalDS value2);

### Parameters

- `value1`

  An `OracleTimeStampTZ`.

- `value2`

  An `OracleIntervalDS`.

### Return Value

An `OracleTimeStampTZ`.

### Remarks

If either parameter has a null value, the returned `OracleTimeStampTZ` has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStampTZ Structure](OracleTimeStampTZStructure.md)

- [OracleTimeStampTZ Members](TimeStampTZMembers.md)
