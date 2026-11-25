This method compares the current `OracleTimeStampTZ` instance to an object, and returns an integer that represents their relative values.

### Declaration

    // C#
    public int CompareTo(object obj);

### Parameters

- `obj`

  The object being compared to the current `OracleTimeStampTZ` instance.

### Return Value

The method returns a number that is:

Less than zero: if the current `OracleTimeStampTZ` instance value is less than that of `obj`.

Zero: if the current `OracleTimeStampTZ` instance and `obj` values are equal.

Greater than zero: if the current `OracleTimeStampTZ` instance value is greater than that of `obj`.

### Implements

`IComparable`

### Exceptions

`ArgumentException` - The `obj` is not of type `OracleTimeStampTZ`.

### Remarks

The following rules apply to the behavior of this method.

- The comparison must be between `OracleTimeStampTZ`s. For example, comparing an `OracleTimeStampTZ` instance with an `OracleBinary` instance is not allowed. When an `OracleTimeStampTZ` is compared with a different type, an `ArgumentException` is thrown.

- Any `OracleTimeStampTZ` that has a value is greater than an `OracleTimeStampTZ` that has a null value.

- Two `OracleTimeStampTZ`s that contain a null value are equal.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStampTZ Structure](OracleTimeStampTZStructure.md)

- [OracleTimeStampTZ Members](TimeStampTZMembers.md)
