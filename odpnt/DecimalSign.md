This method determines the sign of an `OracleDecimal` structure.

### Declaration

    // C#
    public static int Sign(OracleDecimal val);

### Parameters

- `val`

  An `OracleDecimal` structure.

### Return Value

- `-1`: if the supplied `OracleDecimal` `<` 0

- `0`: if the supplied `OracleDecimal` `==` 0

- `1`: if the supplied `OracleDecimal` `>` 0

### Exceptions

`OracleNullValueException` - The argument has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDecimal Members](DecimalMembers.md)

- [OracleDecimal Structure](OracleDecimalStructure.md)
