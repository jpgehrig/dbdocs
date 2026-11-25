This property applies to pluggable database connections. Upon an `OracleConnection.Open()`, if the connection returned from the pool had to change its service name (`ServiceName`) or pluggable database (`PDBName`) in order to connect to the desired pluggable database, then the connection is considered switched. Thus, `SwitchedConnection` will then return `TRUE`. In all other cases, it will return `FALSE`.

### Declaration

    // C#
    public bool SwitchedConnection { get; }

### Remarks

Applications should use this property carefully when using `DRCPConnectionClass` values that are common across PDBs/Services. If the same `DRCPConnectionClass` values are used across PDBs/Services, but their semantics are different, then this property value can help determine if the requested connection is returned or not.

For example, in a scenario where the same `DRCPConnectionClass` that is used across PDBs/Services has a different semantic, the application should first check to see if the session has been switched or not. If it has switched between PDBs/Services, then the application should consider that the connection with a matching `DRCPConnectionClass` was not dispensed.

Only supported for .NET Framework 4 and higher.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnection Class](OracleConnectionClass.md)

- [OracleConnection Members](ConnectionMembers.md)
