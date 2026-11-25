This constructor instantiates a new instance of `OracleParameter` class using the supplied parameter name and Oracle data type.

### Declaration

    // C#
    public OracleParameter(string parameterName, OracleDbType oraType);

### Parameters

- `parameterName`

  The parameter name.

- `oraType`

  The data type of the `OracleParameter`.

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
