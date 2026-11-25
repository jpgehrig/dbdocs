This method adds an `OracleParameter` object to the collection using the supplied name, database type, size, direction, null indicator, precision, scale, source column, source version, and parameter value.

### Declaration

    // C#
    public OracleParameter Add(string name, OracleDbType dbType, int size,
        ParameterDirection dir, bool isNullable, byte precision,
        byte scale, string srcColumn, DataRowVersion version, object val);

### Parameters

- `name `

  The parameter name.

- `dbType`

  The data type of the `OracleParameter`.

- `size`

  The size of `OracleParameter`.

- `dir`

  The `ParameterDirection` value.

- `isNullable`

  An indicator that specifies if the `parameter` value can be `null`.

- `precision`

  The precision of the `parameter` value.

- `scale`

  The scale of the `parameter` value.

- `srcColumn`

  The name of the source column.

- `version`

  The `DataRowVersion` value.

- `val`

  The `parameter` value.

### Return Value

The newly created `OracleParameter` object which was added to the collection.

### Exceptions

`ArgumentException` - The type of supplied `val` does not belong to the type of `Value` property in any of the ODP.NET Types.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleParameterCollection Class](OracleParameterCollectionClass.md)

- [OracleParameterCollection Members](ParameterCollectionMembers.md)
