This constructor creates a new instance of the `OracleTimeStamp` structure and sets its value to the provided byte array, which is in the internal Oracle `TIMESTAMP` format.

### Declaration

    // C#
    public OracleTimeStamp (byte[] bytes);

### Parameters

- `bytes`

  A byte array that represents an Oracle `TIMESTAMP` in Oracle internal format.

### Exceptions

`ArgumentException` - `bytes` is not in an internal Oracle `TIMESTAMP` format or `bytes` is not a valid Oracle `TIMESTAMP`.

`ArgumentNullException` - `bytes` is null.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStamp Structure](OracleTimeStampStructure.md)

- [OracleTimeStamp Members](TimeStampMembers.md)
