Overrides `Object`

This method determines whether or not an object has the same date and time as the current `OracleTimeStampTZ` instance.

### Declaration

    // C#
    public override bool Equals(object obj);

### Parameters

- `obj`

  The object being compared to the current `OracleTimeStampTZ` instance.

### Return Value

Returns `true` if the `obj` is of type `OracleTimeStampTZ` and represents the same date and time; otherwise, returns `false`.

### Remarks

The following rules apply to the behavior of this method.

- Any `OracleTimeStampTZ` that has a value is greater than an `OracleTimeStampTZ` that has a null value.

- Two `OracleTimeStampTZ`s that contain a null value are equal.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStampTZ Structure](OracleTimeStampTZStructure.md)

- [OracleTimeStampTZ Members](TimeStampTZMembers.md)
