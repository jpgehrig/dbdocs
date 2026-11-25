This method determines whether or not an object is an instance of `OracleBinary`, and has the same binary data as the current instance.

### Declaration

    // C#
    public override bool Equals(object obj);

### Parameters

- `obj`

  The object being compared.

### Return Value

Returns `true` if `obj` is an instance of `OracleBinary`, and has the same binary data as the current instance; otherwise, returns `false`.

### Remarks

The following rules apply to the behavior of this method.

- Any `OracleBinary` that has a value is greater than an `OracleBinary` that has a null value.

- Two `OracleBinary`s that contain a null value are equal.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleBinary Structure](OracleBinaryStructure.md)

- [OracleBinary Members](BinaryMembers.md)
