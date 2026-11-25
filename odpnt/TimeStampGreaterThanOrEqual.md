This static method determines if the first of two `OracleTimeStamp` values is greater than or equal to the second.

### Declaration

    // C#
    public static bool GreaterThanOrEqual(OracleTimeStamp value1,
         OracleTimeStamp value2);

### Parameters

- `value1`

  The first `OracleTimeStamp`.

- `value2`

  The second `OracleTimeStamp`.

### Return Value

Returns `true` if the first of two `OracleTimeStamp` values is greater than or equal to the second; otherwise, returns `false`.

### Remarks

The following rules apply to the behavior of this method.

- Any `OracleTimeStamp` that has a value is greater than an `OracleTimeStamp` that has a null value.

- Two `OracleTimeStamp`s that contain a null value are equal.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStamp Structure](OracleTimeStampStructure.md)

- [OracleTimeStamp Members](TimeStampMembers.md)
