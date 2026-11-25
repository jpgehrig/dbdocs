This constructor creates a new instance of the `OracleString` structure and sets its value using a byte array and specifies the following: if the supplied byte array is Unicode encoded and if case is ignored in comparison.

### Declaration

    // C#
    public OracleString(byte[] data, bool fUnicode, bool isCaseIgnored);

### Parameters

- `data`

  Byte array data for the new `OracleString`.

- `fUnicode`

  Specifies if the supplied `data` is Unicode encoded. Specifies `true` if Unicode encoded; otherwise, `false`.

- `isCaseIgnored`

  Specifies if case is ignored in comparison. Specifies `true` if case is to be ignored; otherwise, specifies `false`.

### Exceptions

`ArgumentNullException` - The `data` parameter is null.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleString Structure](OracleStringStructure.md)

- [OracleString Members](StringMembers.md)
