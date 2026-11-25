This method determines if the first of two `OracleDecimal` values is greater than or equal to the second.

### Declaration

    // C#
    public static bool operator >= (OracleDecimal val1, OracleDecimal val2);

### Parameters

- `val1`

  The first `OracleDecimal`.

- `val2`

  The second `OracleDecimal`.

### Return Value

Returns `true` if the first of two `OracleDecimal` values is greater than or equal to the second; otherwise, returns `false`.

### Remarks

The following rules apply to the behavior of this method.

- Any `OracleDecimal` that has a value compares greater than an `OracleDecimal` that has a null value.

- Two `OracleDecimal`s that contain a null value are equal.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDecimal Members](DecimalMembers.md)

- [OracleDecimal Structure](OracleDecimalStructure.md)
