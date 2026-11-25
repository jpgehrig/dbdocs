This static operator determines if two `OracleTimeStampTZ` values are equal.

### Declaration

    // C#
    public static bool operator == (OracleTimeStampTZ value1,
         OracleTimeStampTZ value2);

### Parameters

- `value1`

  The first `OracleTimeStampTZ`.

- `value2`

  The second `OracleTimeStampTZ.`

### Return Value

Returns `true` if they are equal; otherwise returns `false`.

### Remarks

The following rules apply to the behavior of this method.

- Any `OracleTimeStampTZ` that has a value is greater than an `OracleTimeStampTZ` that has a null value.

- Two `OracleTimeStampTZ`s that contain a null value are equal.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStampTZ Structure](OracleTimeStampTZStructure.md)

- [OracleTimeStampTZ Members](TimeStampTZMembers.md)
