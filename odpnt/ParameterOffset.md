This property specifies the offset to the `Value` property.

### Declaration

    // C#
    public int Offset { get; set; }

### Property Value

An `int` that specifies the offset.

### Exceptions

`ArgumentOutOfRangeException` - The `Offset` value specified is invalid.

### Remarks

Default = `0`

For Array Bind and PL/SQL Associative Array Bind, `Offset` applies to every element in the `Value` property.

The `Offset` property is used for binary and string data types. The `Offset` property represents the number of bytes for binary types and the number of characters for strings. The count for strings does not include the terminating character if a `null` is referenced. The `Offset` property is used by parameters of the following types:

- `OracleDbType.BFile`

- `OracleDbType.Blob`

- `OracleDbType.LongRaw`

- `OracleDbType.Raw`

- `OracleDbType.Char`

- `OracleDbType.Clob`

- `OracleDbType.NClob`

- `OracleDbType.NChar`

- `OracleDbType.NVarchar2`

- `OracleDbType.Varchar2`

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleParameter Class](OracleParameterClass.md)

- [OracleParameter Members](ParameterMembers.md)
