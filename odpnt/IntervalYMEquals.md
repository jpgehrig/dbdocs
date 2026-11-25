Overrides `Object`

This method determines whether or not the specified object has the same time interval as the current instance.

### Declaration

    // C#
    public override bool Equals(object obj);

### Parameters

- `obj`

  The supplied object.

### Return Value

Returns `true` if the specified object instance is of type `OracleIntervalYM` and has the same time interval; otherwise, returns `false`.

### Remarks

The following rules apply to the behavior of this method.

- Any `OracleIntervalYM` that has a value compares greater than an `OracleIntervalYM` that has a null value.

- Two `OracleIntervalYM`s that contain a null value are equal.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleIntervalYM Structure](OracleIntervalYMStructure.md)

- [OracleIntervalYM Members](IntervalYMMembers.md)
