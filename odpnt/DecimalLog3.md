This method returns the supplied `OracleDecimal` structure with its value set to the logarithm of the supplied `OracleDecimal` structure in the supplied base.

### Declaration

    // C#
    public static OracleDecimal Log(OracleDecimal val, OracleDecimal logBase);

### Parameters

- `val`

  An `OracleDecimal` structure whose logarithm is to be calculated.

- `logBase`

  An `OracleDecimal` structure that specifies the base of the logarithm.

### Return Value

Returns the logarithm of `val` in the supplied base.

### Exceptions

`ArgumentOutOfRangeException` - Either the `val` or `logBase` parameter is less than zero.

### Remarks

If either argument has a null value, the returned `OracleDecimal` has a null value.

If both arguments have zero value, the result is undefined, and the returned `OracleDecimal` structure has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDecimal Members](DecimalMembers.md)

- [OracleDecimal Structure](OracleDecimalStructure.md)
