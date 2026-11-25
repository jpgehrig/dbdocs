This method compares the current instance to the supplied object and returns an `integer` that represents their relative values.

### Declaration

    // C#
    public int CompareTo(object obj);

### Parameter

- `obj`

  The supplied instance.

### Return Value

The method returns a number:

- Less than zero: if the value of the current instance is less than obj.

- Zero: if the value of the current instance is equal to obj.

- Greater than zero: if the value of the current instance is greater than obj.

### Implements

`IComparable`

### Exceptions

`ArgumentException` - The parameter is not of type `OracleBoolean`.

### Remarks

The following rules apply to the behavior of this method.

- The comparison must be between `OracleBoolean`. For example, comparing an `OracleBoolean` instance with an `OracleBinary` instance is not allowed. When an `OracleBoolean` is compared with a different type, an `ArgumentException` is thrown.

- Any `OracleBoolean` that has a value compares greater than an `OracleBoolean` that has a null value.

- Two `OracleBoolean` that contain a null value are equal.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleBoolean Structure](OracleBooleanStructure.md)

- [OracleBoolean Members](BooleanMembers.md)
