This method adds the supplied number of days to the current instance.

### Declaration

    // C#
    public OracleTimeStamp AddDays(double days);

### Parameters

- `days`

  The supplied number of days. Range is (-1,000,000,000 \< `days` \< 1,000,000,000)

### Return Value

An `OracleTimeStamp`.

### Exceptions

`ArgumentOutofRangeException` - The argument value is out of the specified range.

`OracleNullValueException` - The current instance has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStamp Structure](OracleTimeStampStructure.md)

- [OracleTimeStamp Members](TimeStampMembers.md)
