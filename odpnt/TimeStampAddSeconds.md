This method adds the supplied number of seconds to the current instance.

### Declaration

    // C#
    public OracleTimeStamp AddSeconds(double seconds);

### Parameters

- `seconds`

  The supplied number of seconds. Range is (-8.64 \* 1013\< `seconds` \< 8.64 \* 1013).

### Return Value

An `OracleTimeStamp`.

### Exceptions

`ArgumentOutofRangeException` - The argument value is out of the specified range.

`OracleNullValueException` - The current instance has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStamp Structure](OracleTimeStampStructure.md)

- [OracleTimeStamp Members](TimeStampMembers.md)
