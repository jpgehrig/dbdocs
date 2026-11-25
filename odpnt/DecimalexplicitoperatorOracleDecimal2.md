This method returns the `OracleDecimal` representation of a string.

### Declaration

    // C#
    public static explicit operator OracleDecimal(string numStr);

### Parameters

- `numStr`

  A `string` that represents a numeric value.

### Return Value

An `OracleDecimal`.

### Exceptions

`ArgumentException` - The `numStr` parameter is an invalid string representation of an `OracleDecimal`.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDecimal Members](DecimalMembers.md)

- [OracleDecimal Structure](OracleDecimalStructure.md)

- "[OracleGlobalization Class](OracleGlobalizationClass.md)"

- "[Globalization Support](featGlobal.md)"
