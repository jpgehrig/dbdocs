This type conversion operator converts the total number of months as time interval to an `OracleIntervalYM` structure.

### Declaration

    // C#
    public static implicit operator OracleIntervalYM (long months);

### Parameters

- `months`

  The number of months to be converted. Range is (-999,999,999 \* 12)-11 \<= `months` \<= (999,999,999 \* 12)+11.

### Return Value

An `OracleIntervalYM` structure.

### Exceptions

`ArgumentOutOfRangeException` - The `months` parameter is out of the specified range.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleIntervalYM Structure](OracleIntervalYMStructure.md)

- [OracleIntervalYM Members](IntervalYMMembers.md)
