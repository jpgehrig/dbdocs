This method returns a new `OracleDecimal` structure with its value set to the natural logarithm (base e) of the supplied `OracleDecimal` structure.

### Declaration

    // C#
    public static OracleDecimal Log(OracleDecimal val);

### Parameters

- `val`

  An `OracleDecimal` structure whose logarithm is to be calculated.

### Return Value

Returns a new `OracleDecimal` structure with its value set to the natural logarithm (base e) of `val`.

### Exceptions

`ArgumentOutOfRangeException` - The supplied `OracleDecimal` value is less than zero.

### Remarks

If the supplied `OracleDecimal` structure has a null value, the returned `OracleDecimal` has a null value.

If the supplied `OracleDecimal` structure has zero value, the result is undefined, and the returned `OracleDecimal` structure has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDecimal Members](DecimalMembers.md)

- [OracleDecimal Structure](OracleDecimalStructure.md)
