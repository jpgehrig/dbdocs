This method adds the supplied number of years to the current instance.

### Declaration

    // C#
    public OracleTimeStamp AddYears(int years);

### Parameters

- `years`

  The supplied number of years. Range is (-999,999,999 \<= `years` \< = 999,999,999)

### Return Value

An `OracleTimeStamp`.

### Exceptions

`ArgumentOutofRangeException` - The argument value is out of the specified range.

`OracleNullValueException` - The current instance has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStamp Structure](OracleTimeStampStructure.md)

- [OracleTimeStamp Members](TimeStampMembers.md)
