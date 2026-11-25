This method determines whether or not the specified `object` has the same time interval as the current instance.

### Declaration

    // C#
    public override bool Equals(object obj);

### Parameters

- `obj`

  The specified object.

### Return Value

Returns `true` if `obj` is of type `OracleIntervalDS` and has the same time interval as the current instance; otherwise, returns `false`.

### Remarks

The following rules apply to the behavior of this method.

- Any `OracleIntervalDS` that has a value compares greater than an `OracleIntervalDS` that has a null value.

- Two `OracleIntervalDS`s that contain a null value are equal.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleIntervalDS Structure](OracleIntervalDSStructure.md)

- [OracleIntervalDS Members](IntervalDSMembers.md)
