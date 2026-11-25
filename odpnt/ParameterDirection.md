This property specifies whether the parameter is input-only, output-only, bi-directional, or a stored function return value parameter.

### Declaration

    // C#
    public override ParameterDirection Direction { get; set; }

### Property Value

A `ParameterDirection` enumerated value.

### Implements

`IDataParameter`

### Exceptions

`ArgumentOutOfRangeException` - The `ParameterDirection` value specified is invalid.

### Remarks

Default = `ParameterDirection.Input`

Possible values: `Input`, `InputOutput`, `Output`, and `ReturnValue`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleParameter Class](OracleParameterClass.md)

- [OracleParameter Members](ParameterMembers.md)
