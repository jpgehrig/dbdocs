This constructor creates a new instance of the `OracleDate` structure and sets its value for date and time using the supplied `DateTime` value.

### Declaration

    // C#
    public OracleDate (DateTime dt);

### Parameters

- `dt`

  The provided `DateTime` value.

### Remarks

The `OracleDate` structure only supports up to a second precision. The time value in the provided `DateTime` structure that has a precision smaller than second is ignored.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDate Structure](OracleDateStructure.md)

- [OracleDate Members](DateMembers.md)
