This method determines whether or not an object has the same date and time as the current `OracleDate` instance.

### Declaration

    // C#
    public override bool Equals( object obj);

### Parameters

- `obj`

  An object.

### Return Value

Returns `true` if `obj` has the same type as the current instance and represents the same date and time; otherwise returns `false`.

### Remarks

The following rules apply to the behavior of this method.

- Any `OracleDate` that has a value compares greater than an `OracleDate` that has a null value.

- Two `OracleDate`s that contain a null value are equal.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDate Structure](OracleDateStructure.md)

- [OracleDate Members](DateMembers.md)
