This method compares the current `OracleTimeStamp` instance to an object, and returns an integer that represents their relative values.

### Declaration

    // C#
    public int CompareTo(object obj);

### Parameters

- `obj`

  The object being compared to the current `OracleTimeStamp` instance.

### Return Value

The method returns a number that is:

Less than zero: if the current `OracleTimeStamp` instance value is less than that of `obj`.

Zero: if the current `OracleTimeStamp` instance and `obj` values are equal.

Greater than zero: if the current `OracleTimeStamp` instance value is greater than that of `obj`.

### Implements

`IComparable`

### Exceptions

`ArgumentException` - The `obj` parameter is not of type `OracleTimeStamp`.

### Remarks

The following rules apply to the behavior of this method.

- The comparison must be between `OracleTimeStamp`s. For example, comparing an `OracleTimeStamp` instance with an `OracleBinary` instance is not allowed. When an `OracleTimeStamp` is compared with a different type, an `ArgumentException` is thrown.

- Any `OracleTimeStamp` that has a value is greater than an `OracleTimeStamp` that has a null value.

- Two `OracleTimeStamp`s that contain a null value are equal.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStamp Structure](OracleTimeStampStructure.md)

- [OracleTimeStamp Members](TimeStampMembers.md)
