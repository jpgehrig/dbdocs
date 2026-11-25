This method determines whether or not supplied object is an instance of `OracleString` and has the same values as the current `OracleString` instance.

### Declaration

    // C#
    public override bool Equals(object obj);

### Parameters

- `obj`

  An object being compared.

### Return Value

Returns `true` if the supplied object is an instance of `OracleString` and has the same values as the current `OracleString` instance; otherwise, returns `false`.

### Remarks

The following rules apply to the behavior of this method.

- Any `OracleString` that has a value is greater than an `OracleString` that has a null value.

- Two `OracleString`s that contain a null value are equal.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleString Structure](OracleStringStructure.md)

- [OracleString Members](StringMembers.md)
