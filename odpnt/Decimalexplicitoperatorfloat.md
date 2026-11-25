This method returns the `float` representation of the `OracleDecimal` value.

### Declaration

    // C#
    public static explicit operator float(OracleDecimal val);

### Parameters

- `val`

  An `OracleDecimal` structure.

### Return Value

A `float`.

### Exceptions

`OracleNullValueException` - The `OracleDecimal` has a null value.

`OverFlowException` - The `float` cannot represent the supplied `OracleDecimal` structure.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDecimal Members](DecimalMembers.md)

- [OracleDecimal Structure](OracleDecimalStructure.md)
