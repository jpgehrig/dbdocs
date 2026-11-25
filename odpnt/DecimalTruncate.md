This method truncates the `OracleDecimal` at a specified position.

### Declaration

    // C#
    public static OracleDecimal Truncate(OracleDecimal val, int pos);

### Parameters

- `val`

  An `OracleDecimal` structure.

- `pos`

  The specified position. If the value is positive, the function truncates the `OracleDecimal` structure to the right of the decimal point. If the value is negative, it truncates the `OracleDecimal` structure to the left of the decimal point.

### Return Value

An `OracleDecimal` structure.

### Remarks

If the supplied `OracleDecimal` structure has a null value, the returned `OracleDecimal` has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDecimal Members](DecimalMembers.md)

- [OracleDecimal Structure](OracleDecimalStructure.md)
