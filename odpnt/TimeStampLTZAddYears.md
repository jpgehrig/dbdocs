This method adds the supplied number of years to the current instance

### Declaration

    // C#
    public OracleTimeStampLTZ AddYears(int years);

### Parameters

- `years`

  The supplied number of years. Range is (-999,999,999 \<= `years` \< = 999,999,999)

### Return Value

An `OracleTimeStampLTZ`.

### Exceptions

`OracleNullValueException` - The current instance has a null value.

`ArgumentOutofRangeException` - The argument value is out of the specified range.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStampLTZ Structure](OracleTimeStampLTZStructure.md)

- [OracleTimeStampLTZ Members](TimeStampLTZMembers.md)
