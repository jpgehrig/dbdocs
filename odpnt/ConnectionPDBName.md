This property is used to set and get the name of the pluggable database to which the session is connected to.

### Declaration

    // C#
    public string PDBName{ get; set; }

### Property Value

`PDBName` returns a string specifying the pluggable database name for the connection.

### Exceptions

- `InvalidOperationException() `-  if the connection is already open.

- `InvalidOperationException()` -  if the `CPVersion` is set to `1.0` and the `PDBName` property is set. Applicable only to ODP.NET, Unmanaged Driver.

- `InvalidOperationException()` -  If `PDBName` value is retrieved when `CPVersion` is set to `1.0`. Applicable only to ODP.NET, Unmanaged Driver.

### Remarks

Pluggable databases are available in Oracle Database 12c and higher. The `ServiceName` and `PDBName` properties can be used to connect to the specified Service that is running on a particular PDB.

Property must be set before opening the connection so that a connection with requested pluggable database name is returned.

If the `PDBName` property is set before connection is opened, then the connection's pluggable database name will be the same as `PDBName` when `OracleConnection.Open()` is successfully executed.

If only the `PDBName` property is set, then the default service of the pluggable database is used as the `ServiceName` for this connection.

In unmanaged ODP.NET, if the `PDBName` property is set and if the .NET configuration setting, `CPVersion`, is not set, then the `CPVersion` attribute will be automatically set to `2.0`.

`PDBName` property's value is case insensitive.

The `PDBName` property can be used to retrieve the session's pluggable database name after the connection has been opened. If it is used to get the pluggable database name before the connection is opened, then it just returns the pluggable database name provided by the application, if any.

Only supported for .NET Framework 4 and higher.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnection Class](OracleConnectionClass.md)

- [OracleConnection Members](ConnectionMembers.md)
