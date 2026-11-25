This method compares the current `OracleIntervalDS` instance to an object, and returns an integer that represents their relative values.

### Declaration

    // C#
    public int CompareTo(object obj);

### Parameters

- `obj`

  The object being compared to.

### Return Value

The method returns:

- Less than zero: if the current `OracleIntervalDS` represents a shorter time interval than `obj`.

- Zero: if the current `OracleIntervalDS` and `obj` represent the same time interval.

- Greater than zero: if the current `OracleIntervalDS` represents a longer time interval than `obj`.

### Implements

`IComparable`

### Exceptions

`ArgumentException` - The `obj` parameter is not of type `OracleIntervalDS`.

### Remarks

The following rules apply to the behavior of this method.

- The comparison must be between `OracleIntervalDS`s. For example, comparing an `OracleIntervalDS` instance with an `OracleBinary` instance is not allowed. When an `OracleIntervalDS` is compared with a different type, an `ArgumentException` is thrown.

- Any `OracleIntervalDS` that has a value compares greater than an `OracleIntervalDS` that has a null value.

- Two `OracleIntervalDS`s that contain a null value are equal.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleIntervalDS Structure](OracleIntervalDSStructure.md)

- [OracleIntervalDS Members](IntervalDSMembers.md)
