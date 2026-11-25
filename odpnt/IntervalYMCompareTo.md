This method compares the current `OracleIntervalYM` instance to the supplied object, and returns an integer that represents their relative values.

### Declaration

    // C#
    public int CompareTo(object obj);

### Parameters

- `obj`

  The supplied object.

### Return Value

The method returns a number:

Less than zero: if the current `OracleIntervalYM` represents a shorter time interval than `obj.`

Zero: if the current `OracleIntervalYM` and `obj` represent the same time interval.

Greater than zero: if the current `OracleIntervalYM` represents a longer time interval than `obj.`

### Implements

`IComparable`

### Exceptions

`ArgumentException` - The `obj` parameter is not of type `OracleIntervalYM`.

### Remarks

The following rules apply to the behavior of this method.

- The comparison must be between `OracleIntervalYM`s. For example, comparing an `OracleIntervalYM` instance with an `OracleBinary` instance is not allowed. When an `OracleIntervalYM` is compared with a different type, an `ArgumentException` is thrown.

- Any `OracleIntervalYM` that has a value compares greater than an `OracleIntervalYM` that has a null value.

- Two `OracleIntervalYM`s that contain a null value are equal.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleIntervalYM Structure](OracleIntervalYMStructure.md)

- [OracleIntervalYM Members](IntervalYMMembers.md)
