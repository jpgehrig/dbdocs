This constructor creates a new instance of the `OracleTimeStampTZ` structure and sets its value for date and time using the supplied `DateTime` value.

### Declaration

    // C#
    public OracleTimeStampTZ (DateTime dt);

### Parameters

- `dt`

  The supplied `DateTime` value.

### Remarks

The time zone is set to the `OracleGlobalization.TimeZone` of the thread.

### Exceptions

`ArgumentException` - The `dt` parameter cannot be used to construct a valid `OracleTimeStampTZ`.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStampTZ Structure](OracleTimeStampTZStructure.md)

- [OracleTimeStampTZ Members](TimeStampTZMembers.md)
