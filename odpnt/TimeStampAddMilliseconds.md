This method adds the supplied number of milliseconds to the current instance.

### Declaration

    // C#
    public OracleTimeStamp AddMilliseconds(double milliseconds);

### Parameters

- `milliseconds`

  The supplied number of milliseconds. Range is (-8.64 \* 1016\< `milliseconds` \< 8.64 \* 1016).

### Return Value

An `OracleTimeStamp`.

### Exceptions

`ArgumentOutofRangeException` - The argument value is out of the specified range.

`OracleNullValueException` - The current instance has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStamp Structure](OracleTimeStampStructure.md)

- [OracleTimeStamp Members](TimeStampMembers.md)
