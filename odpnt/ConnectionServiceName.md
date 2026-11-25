This property is used to set and get the database service name to which the session will be connected to when connecting to a pluggable database.

### Declaration

    // C#
    public string ServiceName{ get; set;}

### Property Value

`ServiceName` returns a string specifying the service name of the connection.

### Exceptions

`InvalidOperationException()` - the connection is already open.

`InvalidOperationException()` - if the `CPVersion` is set to `1.0` and the `ServiceName` property is set. Applicable only to ODP.NET, Unmanaged Driver.

### Remarks

Pluggable databases are available in Oracle Database 12c and higher. The `ServiceName` and `PDBName` properties can be used to connect to the specified Service that is running on a particular PDB.

`ServiceName` must be set before opening the connection so that the correct service is used for the connection.

`PDBName` property must be set when the `ServiceName` property is set. Otherwise, an exception is thrown when the connection is opened.

If the `ServiceName` property is specified before connection is opened, then the connection's service will be the same as the specified `ServiceName` when the connection is opened.

If the service name is not changed before the connection is next opened, then the connection will continue using the `ServiceName` value that had been previously set.

In unmanaged ODP.NET, if the `ServiceName` property is set and if the `CPVersion` attribute is not set, then the `CPVersion` attribute will be automatically set to `2.0`.

`ServiceName` property's value is case insensitive.

The `ServiceName` property can also be used to retrieve the session service name after opening the connection. If retrieved before opening the connection, then `ServiceName` returns the service name provided by the application, if any.

Only supported for .NET Framework 4 and higher.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnection Class](OracleConnectionClass.md)

- [OracleConnection Members](ConnectionMembers.md)
