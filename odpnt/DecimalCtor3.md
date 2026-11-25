This constructor creates a new instance of the `OracleDecimal` structure and sets its value to the supplied `double` value.

### Declaration

    // C#
    public OracleDecimal(double doubleX)

### Parameters

- `doubleX`

  The provided double value.

### Exceptions

`OverFlowException` - The value of the supplied `double` is greater than the maximum value or less than the minimum value of `OracleDecimal`.

### Remarks

`OracleDecimal` contains the following values depending on the provided double value:

- `double.PositiveInfinity`: positive infinity value

- `double.NegativeInfinity`:` `negative infinity value.

- `double.NaN`: null value

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDecimal Members](DecimalMembers.md)

- [OracleDecimal Structure](OracleDecimalStructure.md)
