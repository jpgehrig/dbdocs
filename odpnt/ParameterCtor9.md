This constructor instantiates a new instance of the `OracleParameter` class using the supplied parameter name, data type, size, value, and direction.

### Declaration

    // C#
    public OracleParameter(string parameterName, OracleDbType type, int size,
       object obj, ParameterDirection direction);

### Parameters

- `parameterName`

  The parameter name.

- `type`

  The data type of the `OracleParameter`.

- `size `

  The size of the `OracleParameter` value.

- `obj`

  The value of the `OracleParameter`.

- `direction`

  The `ParameterDirection` value.

### Remarks

Changing the `DbType` implicitly changes the `OracleDbType`.

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

- "[OracleParameterCollection Class](OracleParameterCollectionClass.md)"
