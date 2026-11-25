Session purity specifies whether an application can reuse a pooled session (`Pooled`) or must use a new session (`New`).

### Declaration

    // C#
    public string DRCPPurity {get; set;}

### Property Value

`OracleDRCPPurity` Enumeration values.

### Exceptions

- `InvalidOperationException() `-  if `CPVersion=1.0` and the `DRCPPurity` is set to a non-null / non-empty string. Applies to unmanaged ODP.NET only.

- `InvalidOperationException()` -  if the `DRCPPurity` is set to a non-null / non-empty string after opening a connection.

- `InvalidOperationException()` -  if DRCP is not enabled and the `DRCPPurity` is set to a non-null / non-empty string.

### Remarks

The default value is `Pooled`.

If set to `New`, then ODP.NET will dispense a new DRCP connection, rather than try to find an existing connection from the pool. In general, this property is used by applications that want a connection without any preexisting session state set.

If set to `Pooled`, then ODP.NET will first attempt to use a preexisting connection, that already exists in the DRCP pool.

Only supported for .NET Framework 4 and higher.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnection Class](OracleConnectionClass.md)

- [OracleConnection Members](ConnectionMembers.md)

- [OracleDRCPPurity Enumeration](OracleDRCPPurityEnumeration.md)
