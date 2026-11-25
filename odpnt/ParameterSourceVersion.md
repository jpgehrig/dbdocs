This property specifies the `DataRowVersion` value to use when loading the `Value` property of the parameter.

### Declaration

    // C#
    public override DataRowVersion SourceVersion { get; set; }

### Property Value

`DataRowVersion`

### Implements

`IDataParameter`

### Exceptions

`ArgumentOutOfRangeException` - The `DataRowVersion` value specified is invalid.

### Remarks

Default = `DataRowVersion.Current`

`SourceVersion` is used by the `OracleDataAdapter.UpdateCommand()` during the `OracleDataAdapter.Update` to determine whether the original or current value is used for a parameter value. This allows primary keys to be updated. This property is ignored by the `OracleDataAdapter.InsertCommand()` and the `OracleDataAdapter.DeleteCommand()`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleParameter Class](OracleParameterClass.md)

- [OracleParameter Members](ParameterMembers.md)
