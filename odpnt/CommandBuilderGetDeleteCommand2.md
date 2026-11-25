This method gets the automatically generated `OracleCommand` object that has the SQL statement (`CommandText`) perform deletions on the database when an application calls `Update()` on the `OracleDataAdapter`.

### Declaration

    // C#
    public OracleCommand GetDeleteCommand(bool useColumnsForParameterNames);

### Parameters

- `useColumnsForParameterNames`

  If true, the method generates parameter names matching column names if possible. If false, the method binds parameters by position.

### Return Value

An `OracleCommand`.

### Exceptions

`ObjectDisposedException` - The `OracleCommandBuilder` object is already disposed.

`InvalidOperationException` - Either the `SelectCommand` or the `DataAdapter` property is null, or the primary key cannot be retrieved from the `SelectCommand` property of the `OracleDataAdapter`.

### Remarks

If the bool is `true`, the method generates parameter names matching column names if possible. If `false`, the method binds parameters by position.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleCommandBuilder Class](OracleCommandBuilderClass.md)

- [OracleCommandBuilder Members](CommandBuilderMembers.md)
