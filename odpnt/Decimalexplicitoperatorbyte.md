This method returns the `byte` representation of the `OracleDecimal` value.

### Declaration

    // C#
    public static explicit operator byte(OracleDecimal val);

### Parameters

- `val`

  An `OracleDecimal` structure.

### Return Value

A `byte`.

### Exceptions

`OracleNullValueException` - `OracleDecimal` has a null value.

`OverFlowException`- The `byte` cannot represent the supplied `OracleDecimal` structure.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDecimal Members](DecimalMembers.md)

- [OracleDecimal Structure](OracleDecimalStructure.md)
