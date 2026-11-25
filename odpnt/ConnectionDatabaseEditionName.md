`DatabaseEditionName` property sets or gets the edition name for the `OracleConnection` object.

### Declaration

    // C#
    public string DatabaseEditionName{get;set;}

### Property Value

A string to be used as the edition name for the `OracleConnection` object.

### Exceptions

- `InvalidOperationException()` - if the connection is already open.

- `InvalidOperationException()` - If `CPVersion` is set to `1.0` when the connection is opened. `DatabaseEditionName` property is supported only with `CPVersion` of `2.0` or higher.

### Remarks

Property must be set before opening a connection or after closing a connection.

The edition name for the connection to use can be set in one of three places: `DatabaseEditionName` in the application code, `Edition` in the .NET configuration file, or `Edition` in the Windows Registry. The .NET configuration value overrides the Registry value and the DatabaseEditionName property value overrides the .NET configuration value.

`DatabaseEditionName` property value is case sensitive.

Only supported for .NET Framework 4 and higher.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnection Class](OracleConnectionClass.md)

- [OracleConnection Members](ConnectionMembers.md)
