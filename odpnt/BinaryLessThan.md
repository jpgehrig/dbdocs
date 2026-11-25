This method determines whether or not the first of two `OracleBinary` values is less than the second.

### Declaration

    // C#
    public static bool LessThan(OracleBinary value1, OracleBinary value2);

### Parameters

- `value1`

  The first `OracleBinary`.

- `value2`

  The second `OracleBinary`.

### Return Value

Returns `true` if the first of two `OracleBinary` values is less than the second; otherwise returns `false`.

### Remarks

The following rules apply to the behavior of this method.

- Any `OracleBinary` that has a value is greater than an `OracleBinary` that has a null value.

- Two `OracleBinary`s that contain a null value are equal.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleBinary Structure](OracleBinaryStructure.md)

- [OracleBinary Members](BinaryMembers.md)
