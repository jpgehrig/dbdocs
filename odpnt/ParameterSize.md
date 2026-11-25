This property specifies the maximum size, in bytes or characters, of the data transmitted to or from the database.

### Declaration

    // C#
    public override int Size { get; set;}

### Property Value

`int`

### Exceptions

`ArgumentOutOfRangeException` - The `Size` value specified is invalid.

`InvalidOperationException` - The `Size` = 0 when the `OracleParameter` object is used to bind a PL/SQL Associative Array.

### Remarks

If `Size` is not explicitly set, it is inferred from the actual size of the specified parameter value when binding only for input parameters. Output parameters must have their size defined explicitly.

The default value is `0`.

Before execution, this property specifies the maximum size to be bound in the `Value` property. After execution, it contains the size of the type in the `Value` property.

`Size` is used for parameters of the following types:

- `OracleDbType.Blob`

- `OracleDbType.Char`

- `OracleDbType.Clob`

- `OracleDbType.LongRaw`

- `OracleDbType.NChar `

- `OracleDbType.NClob `

- `OracleDbType.NVarchar2 `

- `OracleDbType.Raw`

- `OracleDbType.Varchar2 `

For the preceding types, the `Size` property describes the maximum amount of data transmitted to or from the database. For character data, `Size` is in number of characters and for binary data, it is in number of bytes.

For fixed length data types, the value of `Size` is ignored.

If the `Size` is not explicitly set, it is inferred from the actual size of the specified parameter value when binding.

**Note:**

`Size` does not include the null terminating character for the string data.

If the `OracleParameter` object is used to bind a PL/SQL Associative Array, `Size` specifies the maximum number of elements in the PL/SQL Associative Array. Before the execution, this property specifies the maximum number of elements in the PL/SQL Associative Array. After the execution, it specifies the current number of elements returned in the PL/SQL Associative Array. For `Output` and `InputOutput` parameters and return values, `Size` specifies the maximum number of elements in the PL/SQL Associative Array.

ODP.NET does not support binding an empty PL/SQL Associative Array. Therefore, `Size` cannot be set to `0` when the `OracleParameter` object is used to bind a PL/SQL Associative Array.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleParameter Class](OracleParameterClass.md)

- [OracleParameter Members](ParameterMembers.md)

- "[OracleDbType Enumeration](OracleDbTypeEnumerationType.md)"

- "[CollectionType](ParameterCollectionType.md)"

- "[ArrayBindSize](ParameterArrayBindSize.md)"

- "[ArrayBindStatus](ParameterArrayBindStatus.md)"

- "[Value](ParameterValue.md)"
