This property returns an array of `OracleRefCursors`, where each `OracleRefCursor` maps to an implicit resultset returned by the stored procedure.

### Declaration

    // C#
    public OracleRefCursor[] ImplicitRefCursors {get; set;}

### Property Value

An array of `OracleRefCursors`.

### Remarks

This property is populated only when the stored procedure is executed through `ExecuteNonQuery` and it does not get populated in any other scenarios.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleCommand Class](OracleCommandClass.md)

- [OracleCommand Members](OracleCommandMembers.md)
