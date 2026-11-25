This method adds the supplied number of months to the current instance.

### Declaration

    // C#
    public OracleTimeStampTZ AddMonths(long months);

### Parameters

- `months`

  The supplied number of months. Range is (-12,000,000,000 \< `months` \< 12,000,000,000).

### Return Value

An `OracleTimeStampTZ`.

### Exceptions

`OracleNullValueException` - The current instance has a null value.

`ArgumentOutofRangeException` - The argument value is out of the specified range.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStampTZ Structure](OracleTimeStampTZStructure.md)

- [OracleTimeStampTZ Members](TimeStampTZMembers.md)
