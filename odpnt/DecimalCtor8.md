This constructor creates a new instance of the `OracleDecimal` structure and sets its value to the supplied `Single` value.

### Declaration

    // C#
    public OracleDecimal(float floatX);

### Parameters

- `floatX`

  The provided `float` value.

### Remarks

`OracleDecimal` contains the following values depending on the provided `float` value:

`float.PositiveInfinity`: positive infinity value

`float.NegativeInfinity`: negative infinity value

`float.NaN`: null value

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDecimal Members](DecimalMembers.md)

- [OracleDecimal Structure](OracleDecimalStructure.md)
