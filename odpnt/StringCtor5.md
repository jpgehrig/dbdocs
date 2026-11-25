This constructor creates a new instance of the `OracleString` structure and sets its value using a byte array, and specifies the following: the starting index in the byte array, the number of bytes to copy from the byte array, and if the supplied byte array is Unicode encoded.

### Declaration

    // C#
    public OracleString(byte[] data, int index, int count, bool fUnicode);

### Parameters

- `data`

  Byte array data for the new `OracleString`.

- `index`

  The starting index to copy from `data`.

- `count`

  The number of bytes to copy.

- `fUnicode`

  Specifies if the supplied `data` is Unicode encoded. Specifies `true` if Unicode encoded; otherwise, `false`.

### Exceptions

`ArgumentNullException` - The `data` parameter is null.

`ArgumentOutOfRangeException` - The `count` parameter is less than zero.

`IndexOutOfRangeException` - The `index` parameter is greater than or equal to the length of `data` or less than zero.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleString Structure](OracleStringStructure.md)

- [OracleString Members](StringMembers.md)
