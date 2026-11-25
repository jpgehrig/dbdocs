This method returns a new `OracleDecimal` structure with its value set to the modulus of two `OracleDecimal` structures.

### Declaration

    // C#
    public static OracleDecimal operator % (OracleDecimal val,
        OracleDecimal divider);

### Parameters

- `val`

  An `OracleDecimal`.

- `divider`

  An `OracleDecimal`.

### Return Value

A new `OracleDecimal` structure.

### Remarks

If either operand has a null value, the returned `OracleDecimal` has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDecimal Members](DecimalMembers.md)

- [OracleDecimal Structure](OracleDecimalStructure.md)
