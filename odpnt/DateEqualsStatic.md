Overloads `Object`

This method determines if two `OracleDate` values are equal.

### Declaration

    // C#
    public static bool Equals(OracleDate value1, OracleDate value2);

### Parameters

- `value1`

  The first `OracleDate`.

- `value2`

  The second `OracleDate`.

### Return Value

Returns `true` if two `OracleDate` values are equal; otherwise, returns `false`.

### Remarks

The following rules apply to the behavior of this method.

- Any `OracleDate` that has a value compares greater than an `OracleDate` that has a null value.

- Two `OracleDate`s that contain a null value are equal.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDate Structure](OracleDateStructure.md)

- [OracleDate Members](DateMembers.md)
