This property specifies the number of decimal places to which `Value` property is resolved.

### Declaration

    // C#
    public byte Scale { get; set; }

### Property Value

`byte`

### Remarks

Default = `0`.

`Scale` is used by parameters of type `OracleDbType.Decimal`.

Oracle supports `Scale` between `-84` and `127`.

For Array Bind and PL/SQL Associative Array Bind, `Scale` applies to each element in the `Value` property.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleParameter Class](OracleParameterClass.md)

- [OracleParameter Members](ParameterMembers.md)

- "[Value](ParameterValue.md)"
