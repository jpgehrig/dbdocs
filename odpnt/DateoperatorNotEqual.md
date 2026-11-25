This method determines if the two `OracleDate` values are not equal.

### Declaration

    // C#
    public static bool operator != (OracleDate value1, OracleDate value2);

### Parameters

- `value1`

  The first `OracleDate`.

- `value2`

  The second `OracleDate`.

### Return Value

Returns `true` if the two `OracleDate` values are not equal; otherwise, returns `false`.

### Remarks

The following rules apply to the behavior of this method.

- Any `OracleDate` that has a value compares greater than an `OracleDate` that has a null value.

- Two `OracleDate`s that contain a null value are equal.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDate Structure](OracleDateStructure.md)

- [OracleDate Members](DateMembers.md)
