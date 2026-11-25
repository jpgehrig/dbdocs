This method compares the current `OracleString` instance to the supplied object, and returns an integer that represents their relative values.

### Declaration

    // C#
    public int CompareTo(object obj);

### Parameters

- `obj`

  The object being compared to the current instance.

### Return Value

The method returns a number that is:

- Less than zero: if the current `OracleString` value is less than `obj`.

- Zero: if the current `OracleString` value is equal to `obj`.

- Greater than zero: if the current `OracleString` value is greater than `obj`.

### Implements

`IComparable`

### Exceptions

`ArgumentException` - The `obj` parameter is not of type `OracleString`.

### Remarks

The following rules apply to the behavior of this method.

- The comparison must be between `OracleString`s. For example, comparing an `OracleString` instance with an `OracleBinary` instance is not allowed. When an `OracleString` is compared with a different type, an `ArgumentException` is thrown.

- Any `OracleString` that has a value is greater than an `OracleString` that has a null value.

- Two `OracleString`s that contain a null value are equal.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleString Structure](OracleStringStructure.md)

- [OracleString Members](StringMembers.md)
