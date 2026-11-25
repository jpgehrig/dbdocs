This method returns the `long` representation of the `OracleDecimal` value.

### Declaration

    // C#
    public static explicit operator long(OracleDecimal val);

### Parameters

- `val`

  An `OracleDecimal` structure.

### Return Value

A `long`.

### Exceptions

`OracleNullValueException` - The `OracleDecimal` has a null value.

`OverFlowException` - The `long` cannot represent the supplied `OracleDecimal` structure.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDecimal Members](DecimalMembers.md)

- [OracleDecimal Structure](OracleDecimalStructure.md)
