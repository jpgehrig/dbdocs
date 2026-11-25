This method adds the supplied number of years to the current instance

### Declaration

    // C#
    public OracleTimeStampTZ AddYears(int years);

### Parameters

- `years`

  The supplied number of years. Range is (-999,999,999 \<= `years` \< = 999,999,999).

### Return Value

An `OracleTimeStampTZ`.

### Exceptions

`OracleNullValueException` - The current instance has a null value.

`ArgumentOutofRangeException` - The argument value is out of the specified range.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStampTZ Structure](OracleTimeStampTZStructure.md)

- [OracleTimeStampTZ Members](TimeStampTZMembers.md)
