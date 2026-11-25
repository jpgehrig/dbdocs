This method adds the supplied number of milliseconds to the current instance.

### Declaration

    // C#
    public OracleTimeStampTZ AddMilliseconds(double milliseconds);

### Parameters

- `milliseconds`

  The supplied number of milliseconds. Range is (-8.64 \* 1016\< `milliseconds` \< 8.64 \* 1016).

### Return Value

An `OracleTimeStampTZ`.

### Exceptions

`OracleNullValueException` - The current instance has a null value.

`ArgumentOutofRangeException` - The argument value is out of the specified range.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStampTZ Structure](OracleTimeStampTZStructure.md)

- [OracleTimeStampTZ Members](TimeStampTZMembers.md)
