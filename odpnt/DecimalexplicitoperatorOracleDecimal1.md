This method returns the `OracleDecimal` representation of a double.

### Declaration

    // C#
    public static explicit operator OracleDecimal(double val);

### Parameters

- `val`

  A `double`.

### Return Value

An `OracleDecimal`.

### Exceptions

`OverFlowException` - The value of the supplied `double` is greater than the maximum value of `OracleDecimal` or less than the minimum value of `OracleDecimal`.

### Remarks

`OracleDecimal` contains the following values depending on the provided double value:

- `double.PositiveInfinity`: positive infinity value

- `double.NegativeInfinity`:` `negative infinity value.

- `double.NaN`: null value` `

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDecimal Members](DecimalMembers.md)

- [OracleDecimal Structure](OracleDecimalStructure.md)
