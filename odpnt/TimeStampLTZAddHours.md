This method adds the supplied number of hours to the current instance.

### Declaration

    // C#
    public OracleTimeStampLTZ AddHours(double hours);

### Parameters

- `hours`

  The supplied number of hours. Range is (-24,000,000,000 \< `hours` \< 24,000,000,000).

### Return Value

An `OracleTimeStampLTZ`.

### Exceptions

`OracleNullValueException` - The current instance has a null value.

`ArgumentOutofRangeException` - The argument value is out of the specified range.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStampLTZ Structure](OracleTimeStampLTZStructure.md)

- [OracleTimeStampLTZ Members](TimeStampLTZMembers.md)
