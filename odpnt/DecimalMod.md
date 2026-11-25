This method returns a new `OracleDecimal` structure with its value set to the modulus of two `OracleDecimal` structures.

### Declaration

    // C#
    public static OracleDecimal Mod(OracleDecimal val1, OracleDecimal divider);

### Parameters

- `val1`

  An `OracleDecimal` structure.

- `divider`

  An `OracleDecimal` structure.

### Return Value

An `OracleDecimal`.

### Remarks

If either argument has a null value, the returned `OracleDecimal` has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDecimal Members](DecimalMembers.md)

- [OracleDecimal Structure](OracleDecimalStructure.md)
