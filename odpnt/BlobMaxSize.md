The `MaxSize` field holds the maximum number of bytes a `BLOB` can hold, which is 4,294,967,295 (2^32 - 1) bytes.

### Declaration

    // C#
    public static readonly Int64 MaxSize = 4294967295;

### Remarks

This field can be useful in code that checks whether or not the operation exceeds the maximum length allowed.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleBlob Class](OracleBlobClass.md)

- [OracleBlob Members](BlobMembers.md)
