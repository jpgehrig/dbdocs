This constructor creates a new instance of the `OracleTimeStampTZ` structure and sets its value to the provided byte array, that represents the internal Oracle `TIMESTAMP` `WITH` `TIME` `ZONE` format.

### Declaration

    // C#
    public OracleTimeStampLTZ (byte[] bytes);

### Parameters

- `bytes`

  The provided byte array that represents an Oracle `TIMESTAMP` `WITH` `TIME` `ZONE` in Oracle internal format.

### Exceptions

`ArgumentException` - `bytes` is not in internal Oracle `TIMESTAMP` `WITH` `TIME` `ZONE` format or `bytes` is not a valid Oracle `TIMESTAMP` `WITH` `TIME` `ZONE`.

`ArgumentNullException` - `bytes` is null.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStampTZ Structure](OracleTimeStampTZStructure.md)

- [OracleTimeStampTZ Members](TimeStampTZMembers.md)
