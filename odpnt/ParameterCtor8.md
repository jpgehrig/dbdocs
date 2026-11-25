This constructor instantiates a new instance of the `OracleParameter` class using the supplied parameter name, data type, size, direction, null indicator, precision, scale, source column, source version and parameter value.

### Declaration

    // C#
    public OracleParameter(string parameterName, OracleDbType oraType,
       int size, ParameterDirection direction, bool isNullable, byte
       precision, byte scale,  string srcColumn, DataRowVersion srcVersion,
       object obj);

### Parameters

- `parameterName`

  The parameter name.

- `oraType`

  The data type of the `OracleParameter`.

- `size `

  The size of the `OracleParameter` value.

- `direction`

  The `ParameterDirection` value.

- `isNullable`

  An indicator that specifies if the parameter value can be `null`.

- `precision`

  The precision of the parameter value.

- `scale`

  The scale of the parameter value.

- `srcColumn`

  The name of the source column.

- `srcVersion`

  The `DataRowVersion` value.

- `obj`

  The parameter value.

### Exceptions

`ArgumentException` - The supplied value does not belong to the type of `Value` property in any of the `OracleType`s.

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
