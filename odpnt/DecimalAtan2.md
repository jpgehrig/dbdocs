This method returns an angle in radians whose tangent is the quotient of the two supplied `OracleDecimal` structures.

### Declaration

    // C#
    public static OracleDecimal Atan2(OracleDecimal val1, OracleDecimal val2);

### Parameters

- `val1`

  An `OracleDecimal` structure that represents the y-coordinate.

- `val2`

  An `OracleDecimal` structure that represents the x-coordinate.

### Return Value

An `OracleDecimal` structure that represents an angle in radians.

### Remarks

If either argument has a null value, the returned `OracleDecimal` has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDecimal Members](DecimalMembers.md)

- [OracleDecimal Structure](OracleDecimalStructure.md)
