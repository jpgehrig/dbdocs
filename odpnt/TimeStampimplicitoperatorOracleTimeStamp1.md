This static type conversion operator converts an `OracleDate` value to an `OracleTimeStamp` structure.

### Declaration

    // C#
    public static implicit operator OracleTimeStamp (OracleDate value1);

### Parameters

- `value1`

  An `OracleDate` instance.

### Return Value

An `OracleTimeStamp` structure that contains the date and time of the `OracleDate` structure, `value1`.

### Remarks

If the `OracleDate` structure has a null value, the returned `OracleTimeStamp` structure also has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStamp Structure](OracleTimeStampStructure.md)

- [OracleTimeStamp Members](TimeStampMembers.md)
