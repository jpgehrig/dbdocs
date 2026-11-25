This method determines whether or not the first of two `OracleBoolean` values is greater than the second.

### Declaration

    // C#
    public static operator  > (OracleBoolean value1, OracleBoolean value2);

### Parameters

- `value1`

  An `OracleBoolean` instance

- `value2`

  An `OracleBoolean` instance

### Return Value

An `OracleBoolean` that is `true` if the first of two `OracleBoolean` values is greater than the second; otherwise, returns false.

### Remarks

If either of the specified `OracleBoolean` instances is `null`, an `OracleBoolean` with a null value will be returned.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleBoolean Structure](OracleBooleanStructure.md)

- [OracleBoolean Members](BooleanMembers.md)
