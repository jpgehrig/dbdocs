Overrides `Object`

This method determines whether or not an object is an instance of `OracleBoolean`, and whether or not the value of the object is equal to the current instance.

### Declaration

    // C#
    public override bool Equals(object obj);

### Parameter

- obj

  An `OracleBoolean` instance.

### Return Value

Returns `true` if obj is an instance of `OracleBoolean`, and the value of obj is equal to the current instance; otherwise, returns `false`.

### Remarks

The following rules apply to the behavior of this method.

- Any `OracleBoolean` that has a value compares greater than an `OracleBoolean` that has a null value.

- Two `OracleBooleans` that contain a null value are equal.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleBoolean Structure](OracleBooleanStructure.md)

- [OracleBoolean Members](BooleanMembers.md)
