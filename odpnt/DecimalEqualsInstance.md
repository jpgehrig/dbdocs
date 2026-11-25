Overrides `Object`

This method determines whether or not an object is an instance of `OracleDecimal`, and whether or not the value of the object is equal to the current instance.

### Declaration

    // C#
    public override bool Equals(object obj);

### Parameters

- `obj`

  An `OracleDecimal` instance.

### Return Value

Returns `true` if `obj` is an instance of `OracleDecimal`, and the value of `obj` is equal to the current instance; otherwise, returns `false`.

### Remarks

The following rules apply to the behavior of this method.

- Any `OracleDecimal` that has a value compares greater than an `OracleDecimal` that has a null value.

- Two `OracleDecimal`s that contain a null value are equal.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDecimal Members](DecimalMembers.md)

- [OracleDecimal Structure](OracleDecimalStructure.md)
