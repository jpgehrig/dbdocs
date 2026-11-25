Overrides `Object`

This method returns the `string` representation of the current instance.

### Declaration

    // C#
    public override string ToString();

### Return Value

Returns the number in a string returns and a period (`.`) as a numeric separator.

### Remarks

If the current instance has a null value, the returned string is "null".

The returned value is a string representation of an `OracleDecimal` in the numeric format specified by the `Format` property.

The decimal and group separator characters are specified by the thread's `OracleGlobalization`.`NumericCharacters`.

The currency symbols are specified by the following thread properties:

- `OracleGlobalization.Currency`

- `OracleGlobalization`.`ISOCurrency`

- `OracleGlobalization`.`DualCurrency`

If the numeric format is not specified, an Oracle default value is used.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDecimal Members](DecimalMembers.md)

- [OracleDecimal Structure](OracleDecimalStructure.md)

- "[OracleGlobalization Class](OracleGlobalizationClass.md)"

- "[Globalization Support](featGlobal.md)"
