This static method determines if two `OracleTimeStampLTZ` values are equal.

### Declaration

    // C#
    public static bool Equals(OracleTimeStampLTZ value1,
      OracleTimeStampLTZ value2);

### Parameters

- `value1`

  The first `OracleTimeStampLTZ`.

- `value2`

  The second `OracleTimeStampLTZ`.

### Return Value

Returns `true` if two `OracleTimeStampLTZ` values are equal. Returns `false` otherwise.

### Remarks

The following rules apply to the behavior of this method.

- Any `OracleTimeStampLTZ` that has a value is greater than an `OracleTimeStampLTZ` that has a null value.

- Two `OracleTimeStampLTZ`s that contain a null value are equal.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStampLTZ Structure](OracleTimeStampLTZStructure.md)

- [OracleTimeStampLTZ Members](TimeStampLTZMembers.md)
