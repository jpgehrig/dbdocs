This method compares the current `OracleDate` instance to an object, and returns an integer that represents their relative values.

### Declaration

    // C#
    public int CompareTo(object obj);

### Parameters

- `obj`

  An object.

### Return Value

The method returns:

- Less than zero: if the current `OracleDate` instance value is less than that of `obj`.

- Zero: if the current `OracleDate` instance and `obj` values are equal.

- Greater than zero: if the current `OracleDate` instance value is greater than `obj`.

### Implements

`IComparable`

### Exceptions

`ArgumentException` - The `obj` parameter is not an instance of `OracleDate`.

### Remarks

The following rules apply to the behavior of this method.

- The comparison must be between `OracleDate`s. For example, comparing an `OracleDate` instance with an `OracleBinary` instance is not allowed. When an `OracleDate` is compared with a different type, an `ArgumentException` is thrown.

- Any `OracleDate` that has a value compares greater than an `OracleDate` that has a null value.

- Two `OracleDate`s that contain a null value are equal.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDate Structure](OracleDateStructure.md)

- [OracleDate Members](DateMembers.md)
