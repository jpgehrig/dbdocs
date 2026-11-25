This static operator adds the supplied `TimeSpan` to the supplied `OracleTimeStamp` and returns a new `OracleTimeStamp` structure.

### Declaration

    // C#
    public static operator + (OracleTimeStamp value1, TimeSpan value2);

### Parameters

- `value1`

  An `OracleTimeStamp`.

- `value2`

  A `TimeSpan.`

### Return Value

An `OracleTimeStamp.`

### Remarks

If the `OracleTimeStamp` instance has a null value, the returned `OracleTimeStamp` has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStamp Structure](OracleTimeStampStructure.md)

- [OracleTimeStamp Members](TimeStampMembers.md)
