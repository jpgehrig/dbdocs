This constructor creates a new instance of the `OracleDecimal` structure and sets its value to the supplied `string` value.

### Declaration

    // C#
    public OracleDecimal(string numStr);

### Parameters

- `numStr`

  The provided `string` value.

### Exceptions

`ArgumentException` - The `numStr` parameter is an invalid string representation of an `OracleDecimal`.

`ArgumentNullException` - The `numStr` parameter is null.

`OverFlowException` - The value of `numStr` is greater than the maximum value or less than the minimum value of `OracleDecimal`.

`input string format is incorrect` - The locale's numeric separator is a comma(`,`).

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDecimal Members](DecimalMembers.md)

- [OracleDecimal Structure](OracleDecimalStructure.md)

- "[OracleGlobalization Class](OracleGlobalizationClass.md)"

- "[Globalization Support](featGlobal.md)"
