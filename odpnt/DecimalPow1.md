This method returns a new `OracleDecimal` structure with its value set to the supplied `OracleDecimal` value raised to the supplied `Int32` power.

### Declaration

    // C#
    public static OracleDecimal Pow(OracleDecimal val, int power);

### Parameters

- `val`

  An `OracleDecimal` structure.

- `power`

  An `int` value that specifies the power.

### Return Value

An `OracleDecimal` structure.

### Remarks

If the supplied `OracleDecimal` structure has a null value, the returned `OracleDecimal` has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDecimal Members](DecimalMembers.md)

- [OracleDecimal Structure](OracleDecimalStructure.md)
