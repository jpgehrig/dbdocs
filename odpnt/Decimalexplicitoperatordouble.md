This method returns the `double` representation of the `OracleDecimal` value.

### Declaration

    // C#
    public static explicit operator double(OracleDecimal val);

### Parameters

- `val`

  An `OracleDecimal` structure.

### Return Value

A `double`.

### Exceptions

`OracleNullValueException` - The `OracleDecimal` has a null value.

`OverFlowException` - The `double` cannot represent the supplied `OracleDecimal` structure.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDecimal Members](DecimalMembers.md)

- [OracleDecimal Structure](OracleDecimalStructure.md)
