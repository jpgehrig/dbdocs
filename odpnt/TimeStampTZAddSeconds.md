This method adds the supplied number of seconds to the current instance.

### Declaration

    // C#
    public OracleTimeStampTZ AddSeconds(double seconds);

### Parameters

- `seconds`

  The supplied number of seconds. Range is (-8.64 \* 1013\< `seconds` \< 8.64 \* 1013).

### Return Value

An `OracleTimeStampTZ`.

### Exceptions

`OracleNullValueException` - The current instance has a null value.

`ArgumentOutofRangeException` - The argument value is out of the specified range.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStampTZ Structure](OracleTimeStampTZStructure.md)

- [OracleTimeStampTZ Members](TimeStampTZMembers.md)
