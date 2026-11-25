This property specifies the data type of the parameter using the `Data.DbType` enumeration type.

### Declaration

    // C#
    public override DbType DbType {get; set; }

### Property Value

A `DbType` enumerated value.

### Implements

`IDataParameter`

### Exceptions

`ArgumentException` - The `DbType` value specified is invalid.

### Remarks

Default = `DbType.String`

`DbType` is the data type of each element in the array if the `OracleParameter` object is used for Array Bind or PL/SQL Associative Array Bind execution.

Due to the link between `DbType` and `OracleDbType` properties, if the `DbType` property is set, the `OracleDbType` property is inferred from `DbType`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleParameter Class](OracleParameterClass.md)

- [OracleParameter Members](ParameterMembers.md)

- "[Inference of OracleDbType from DbType](featOraCommand.md)"

- "[CollectionType](ParameterCollectionType.md)"
