This method adds the supplied number of seconds to the current instance.

### Declaration

    // C#
    public OracleTimeStampLTZ AddSeconds(double seconds);

### Parameters

- `seconds`

  The supplied number of seconds. Range is (-8.64 \* 1013\< `seconds` \< 8.64 \* 1013).

### Return Value

An `OracleTimeStampLTZ`.

### Exceptions

`OracleNullValueException` - The current instance has a null value.

`ArgumentOutofRangeException` - The argument value is out of the specified range.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStampLTZ Structure](OracleTimeStampLTZStructure.md)

- [OracleTimeStampLTZ Members](TimeStampLTZMembers.md)
