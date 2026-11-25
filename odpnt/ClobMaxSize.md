The `MaxSize` field holds the maximum number of bytes a `CLOB` can hold, which is 4,294,967,295 (2^32 - 1) bytes.

### Declaration

    // C#
    public static readonly Int64 MaxSize = 4294967295;

### Remarks

This field is useful in code that checks whether or not your operation exceeds the maximum length (in bytes) allowed.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleClob Class](OracleClobClass.md)

- [OracleClob Members](ClobMembers.md)
