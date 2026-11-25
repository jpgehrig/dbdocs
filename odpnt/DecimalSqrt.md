This method returns a new `OracleDecimal` structure with its value set to the square root of the supplied `OracleDecimal` structure.

### Declaration

    // C#
    public static OracleDecimal Sqrt(OracleDecimal val);

### Parameters

- `val`

  An `OracleDecimal` structure.

### Return Value

An `OracleDecimal` structure.

### Exceptions

`ArgumentOutOfRangeException` - The provided `OracleDecimal` structure is less than zero.

### Remarks

If either argument has a null value, the returned `OracleDecimal` has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDecimal Members](DecimalMembers.md)

- [OracleDecimal Structure](OracleDecimalStructure.md)
