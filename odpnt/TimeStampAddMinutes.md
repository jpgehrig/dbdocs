This method adds the supplied number of minutes to the current instance.

### Declaration

    // C#
    public OracleTimeStamp AddMinutes(double minutes);

### Parameters

- `minutes`

  The supplied number of minutes. Range is (-1,440,000,000,000 \< `minutes` \< 1,440,000,000,000).

### Return Value

An `OracleTimeStamp`.

### Exceptions

`ArgumentOutofRangeException` - The argument value is out of the specified range.

`OracleNullValueException` - The current instance has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStamp Structure](OracleTimeStampStructure.md)

- [OracleTimeStamp Members](TimeStampMembers.md)
