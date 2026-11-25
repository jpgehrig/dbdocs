This method returns a new `OracleDecimal` structure with its value set to that of the supplied `OracleDecimal` structure and rounded off to the specified place.

### Declaration

    // C#
    public static OracleDecimal Round(OracleDecimal val, int decplace);

### Parameters

- `val`

  An `OracleDecimal` structure.

- `decplace`

  The specified decimal place. If the value is positive, the function rounds the `OracleDecimal` structure to the right of the decimal point. If the value is negative, the function rounds to the left of the decimal point.

### Return Value

An `OracleDecimal` structure.

### Remarks

If the supplied `OracleDecimal` structure has a null value, the returned `OracleDecimal` has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDecimal Members](DecimalMembers.md)

- [OracleDecimal Structure](OracleDecimalStructure.md)
