This constructor creates a new instance of the `OracleDate` structure and sets its value to the provided byte array, which is in the internal Oracle `DATE` format.

### Declaration

    // C#
    public OracleDate(byte [] bytes);

### Parameters

- `bytes`

  A byte array that represents Oracle `DATE` in the internal Oracle `DATE` format.

### Exceptions

`ArgumentException` - `bytes` is null or `bytes` is not in internal Oracle `DATE` format or `bytes` is not a valid Oracle `DATE`.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDate Structure](OracleDateStructure.md)

- [OracleDate Members](DateMembers.md)
