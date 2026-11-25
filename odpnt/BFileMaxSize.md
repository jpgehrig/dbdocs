This static field holds the maximum number of bytes a `BFILE` can hold, which is 4,294,967,295 (2^32 - 1) bytes.

### Declaration

    // C#
    public static readonly Int64 MaxSize = 4294967295;

### Remarks

This field is useful in code that checks whether or not the operation exceeds the maximum length allowed.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleBFile Class](OracleBFileClass.md)

- [OracleBFile Members](BFileMembers.md)
