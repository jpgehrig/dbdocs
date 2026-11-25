This method returns the `decimal` representation of the `OracleDecimal` value.

### Declaration

    // C#
    public static explicit operator decimal(OracleDecimal val);

### Parameters

- `val`

  An `OracleDecimal` structure.

### Return Value

A `decimal`.

### Exceptions

`OracleNullValueException` - The `OracleDecimal` has a null value.

`OverFlowException` - The `decimal` cannot represent the supplied `OracleDecimal` structure.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDecimal Members](DecimalMembers.md)

- [OracleDecimal Structure](OracleDecimalStructure.md)
