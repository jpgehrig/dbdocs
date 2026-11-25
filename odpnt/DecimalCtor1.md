This constructor creates a new instance of the `OracleDecimal` structure and sets its value to the supplied byte array, which is in an Oracle `NUMBER` format.

### Declaration

    // C#
    public OracleDecimal(byte [] bytes);

### Parameters

- `bytes`

  A byte array that represents an Oracle `NUMBER` in an internal Oracle format.

### Exceptions

`ArgumentException` - The `bytes` parameter is not in a internal Oracle `NUMBER` format or `bytes` has an invalid value.

`ArgumentNullException` - The `bytes` parameter is null.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDecimal Members](DecimalMembers.md)

- [OracleDecimal Structure](OracleDecimalStructure.md)
