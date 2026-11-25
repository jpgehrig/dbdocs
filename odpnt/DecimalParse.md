This method converts a `string` to an `OracleDecimal`.

### Declaration

    // C#
    public static OracleDecimal Parse (string str);

### Parameters

- `str`

  The string being converted.

### Return Value

A new `OracleDecimal` structure.

### Exceptions

`ArgumentException` - The `numStr` parameter is an invalid string representation of an `OracleDecimal`.

`ArgumentNullException` - The `numStr` parameter is null.

`OverFlowException` - The value of `numStr` is greater than the maximum value or less than the minimum value of `OracleDecimal`.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDecimal Members](DecimalMembers.md)

- [OracleDecimal Structure](OracleDecimalStructure.md)

- "[OracleGlobalization Class](OracleGlobalizationClass.md)"

- "[Globalization Support](featGlobal.md)"
