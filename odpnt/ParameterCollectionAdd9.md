This method adds an `OracleParameter` object to the collection using the supplied name, database type, size, and source column.

### Declaration

    // C#
    public OracleParameter Add(string name, OracleDbType dbType, int size,
        string srcColumn);

### Parameters

- `name `

  The parameter name.

- `dbType`

  The data type of the `OracleParameter`.

- `size`

  The size of `OracleParameter`.

- `srcColumn`

  The name of the source column.

### Return Value

An `OracleParameter`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleParameterCollection Class](OracleParameterCollectionClass.md)

- [OracleParameterCollection Members](ParameterCollectionMembers.md)
