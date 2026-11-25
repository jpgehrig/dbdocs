This method compares the current `OracleTimeStampLTZ` instance to an object, and returns an integer that represents their relative values.

### Declaration

    // C#
    public int CompareTo(object obj);

### Parameters

- `obj`

  The object being compared to the current `OracleTimeStampLTZ` instance.

### Return Value

The method returns a number that is:

- Less than zero: if the current `OracleTimeStampLTZ` instance value is less than that of `obj`.

- Zero: if the current `OracleTimeStampLTZ` instance and `obj` values are equal.

- Greater than zero: if the current `OracleTimeStampLTZ` instance value is greater than that of `obj`.

### Implements

`IComparable`

### Exceptions

`ArgumentException` - The `obj` parameter is not of type `OracleTimeStampLTZ`.

### Remarks

The following rules apply to the behavior of this method.

- The comparison must be between `OracleTimeStampLTZ`s. For example, comparing an `OracleTimeStampLTZ` instance with an `OracleBinary` instance is not allowed. When an `OracleTimeStampLTZ` is compared with a different type, an `ArgumentException` is thrown.

- Any `OracleTimeStampLTZ` that has a value is greater than an `OracleTimeStampLTZ` that has a null value.

- Two `OracleTimeStampLTZ`s that contain a null value are equal.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStampLTZ Structure](OracleTimeStampLTZStructure.md)

- [OracleTimeStampLTZ Members](TimeStampLTZMembers.md)
