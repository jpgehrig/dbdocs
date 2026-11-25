This method returns an array of bytes, containing the contents of the `OracleString`, in the client character set format.

### Declaration

    // C#
    public byte[] GetNonUnicodeBytes();

### Return Value

A byte array that contains the contents of the `OracleString` in the client character set format.

### Remarks

If the current instance has a null value, an `OracleNullValueException` is thrown.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleString Structure](OracleStringStructure.md)

- [OracleString Members](StringMembers.md)
