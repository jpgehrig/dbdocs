This constructor creates a new instance of the `OracleTimeStampLTZ` structure and sets its value to the provided byte array, which is in the internal Oracle `TIMESTAMP` `WITH` `LOCAL` `TIME` `ZONE` format.

### Declaration

    // C#
    public OracleTimeStampLTZ (byte[] bytes);

### Parameters

- `bytes`

  A byte array that represents an Oracle `TIMESTAMP` `WITH` `LOCAL` `TIME` `ZONE` in Oracle internal format.

### Exceptions

`ArgumentException` - `bytes` is not in an internal Oracle `TIMESTAMP` `WITH` `LOCAL` `TIME` `ZONE` format or `bytes` is not a valid Oracle `TIMESTAMP` `WITH` `LOCAL` `TIME` `ZONE`.

`ArgumentNullException` - `bytes` is null.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStampLTZ Structure](OracleTimeStampLTZStructure.md)

- [OracleTimeStampLTZ Members](TimeStampLTZMembers.md)
