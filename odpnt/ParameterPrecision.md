This property specifies the maximum number of digits used to represent the `Value` property.

### Declaration

    // C#
    Public byte Precision { get; set; }

### Property Value

`byte`

### Remarks

Default = `0`

The `Precision` property is used by parameters of type `OracleDbType.Decimal`.

Oracle supports `Precision` range from `0` to `38`.

For Array Bind and PL/SQL Associative Array Bind, `Precision` applies to each element in the `Value` property.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleParameter Class](OracleParameterClass.md)

- [OracleParameter Members](ParameterMembers.md)

- "[Value](ParameterValue.md)"
