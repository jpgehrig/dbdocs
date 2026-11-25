This property specifies the command type that indicates how the `CommandText` property is to be interpreted.

### Declaration

    // C#
    public override CommandType CommandType {get; set;}

### Property Value

A `CommandType`.

### Exceptions

`ArgumentException` - The value is not a valid `CommandType` such as: `CommandType.Text`, `CommandType.StoredProcedure`, `CommandType.TableDirect`.

### Remarks

Default = `CommandType.Text`

If the value of the `XmlCommandType` property is not `None`, then the `CommandType` property is ignored.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleCommand Class](OracleCommandClass.md)

- [OracleCommand Members](OracleCommandMembers.md)
