This method returns a new `OracleDecimal` structure with its value set to that of the supplied `OracleDecimal` structure, and its decimal place shifted to the specified number of places to the right.

### Declaration

    // C#
    public static OracleDecimal Shift(OracleDecimal val, int decplaces);

### Parameters

- `val`

  An `OracleDecimal` structure.

- `decplaces`

  The specified number of places to be shifted.

### Return Value

An `OracleDecimal` structure.

### Remarks

If the supplied `OracleDecimal` structure has a null value, the returned `OracleDecimal` has a null value.

If `decplaces` is negative, the shift is to the left.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDecimal Members](DecimalMembers.md)

- [OracleDecimal Structure](OracleDecimalStructure.md)
