This constructor instantiates a new instance of the `OracleParameter` class using the supplied parameter name, data type, size, and source column.

### Declaration

    // C#
    public OracleParameter(string parameterName, OracleDbType type, int size,
      string srcColumn);

### Parameters

- `parameterName`

  The parameter name.

- `type`

  The data type of the `OracleParameter`.

- `size `

  The size of the `OracleParameter` value.

- `srcColumn `

  The name of the source column.

### Remarks

Unless explicitly set in the constructor, all the properties have the default values.

Default Values:

- `DbType` - `String`

- `ParameterDirection` - `Input`

- `isNullable` - `true`

- `offset` - `0`

- `OracleDbType` - `Varchar2`

- `ParameterAlias` - Empty string

- `ParameterName` - Empty string

- `Precision` - `0`

- `Size` - `0`

- `SourceColumn` - Empty string

- `SourceVersion` - `Current`

- `ArrayBindStatus` - `Success`

- `Value` - `null`

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleParameter Class](OracleParameterClass.md)

- [OracleParameter Members](ParameterMembers.md)

- "[OracleParameterStatus Enumeration](OracleParameterStatusEnumeration.md)"
