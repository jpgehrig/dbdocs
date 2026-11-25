This property specifies the binding method in the collection.

### Declaration

    // C#
    public bool BindByName {get; set;}

### Property Value

Returns `true` if the parameters are bound by name; returns `false` if the parameters are bound by position.

### Remarks

Default = `false`.

`BindByName` is ignored under the following conditions:

- The value of the `XmlCommandType` property is `Insert`, `Update`, or `Delete`.

- The value of the `XmlCommandType` property is `Query`, but there are no parameters set on the `OracleCommand`.

If the `XmlCommandType` property is `OracleXmlCommandType.Query` and any parameters are set on the `OracleCommand`, the `BindByName` property must be set to `true`. Otherwise, the following `OracleCommand` methods throw an `InvalidOperationException`.

- `ExecuteNonQuery`

- `ExecuteXmlReader`

- `ExecuteStream`

- `ExecuteToStream`

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleCommand Class](OracleCommandClass.md)

- [OracleCommand Members](OracleCommandMembers.md)

- "[Array Binding](featOraCommand.md)"

- "[Value](ParameterValue.md)"
