This method adds the supplied number of minutes to the current instance.

### Declaration

    // C#
    public OracleTimeStampTZ AddMinutes(double minutes);

### Parameters

- `minutes`

  The supplied number of minutes. Range is (-1,440,000,000,000 \< `minutes` \< 1,440,000,000,000).

### Return Value

An `OracleTimeStampTZ`.

### Exceptions

`OracleNullValueException` - The current instance has a null value.

`ArgumentOutofRangeException` - The argument value is out of the specified range.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStampTZ Structure](OracleTimeStampTZStructure.md)

- [OracleTimeStampTZ Members](TimeStampTZMembers.md)
