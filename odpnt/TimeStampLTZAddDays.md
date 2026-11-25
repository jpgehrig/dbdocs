This method adds the supplied number of days to the current instance.

### Declaration

    // C#
    public OracleTimeStampLTZ AddDays(double days);

### Parameters

- `days`

  The supplied number of days. Range is (-1,000,000,000 \< `days` \< 1,000,000,000)

### Return Value

An `OracleTimeStampLTZ`.

### Exceptions

`OracleNullValueException` - The current instance has a null value.

`ArgumentOutofRangeException` - The argument value is out of the specified range.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStampLTZ Structure](OracleTimeStampLTZStructure.md)

- [OracleTimeStampLTZ Members](TimeStampLTZMembers.md)
