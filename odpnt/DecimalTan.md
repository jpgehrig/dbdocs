This method returns the tangent of the supplied angle in radians.

### Declaration

    // C#
    public static OracleDecimal Tan(OracleDecimal val);

### Parameters

- `val`

  An `OracleDecimal` structure that represents an angle in radians.

### Return Value

An `OracleDecimal` instance.

### Exceptions

`ArgumentOutOfRangeException `- The `val` parameter is positive or negative infinity.

### Remarks

If either argument has a null value, the returned `OracleDecimal` has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDecimal Members](DecimalMembers.md)

- [OracleDecimal Structure](OracleDecimalStructure.md)
