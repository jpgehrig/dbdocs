This method adds an `OracleParameter` object to the collection using the supplied name, database type, size, parameter value, and direction.

### Declaration

    // C#
    public OracleParameter Add(string name, OracleDbType dbType, int size,
        object val, ParameterDirection dir;

### Parameters

- `name `

  The parameter name.

- `dbType`

  The data type of the `OracleParameter`.

- `size`

  The size of `OracleParameter`.

- `val`

  The `OracleParameter` value.

- `dir`

  The `ParameterDirection` value.

### Return Value

The newly created `OracleParameter` object which was added to the collection.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleParameterCollection Class](OracleParameterCollectionClass.md)

- [OracleParameterCollection Members](ParameterCollectionMembers.md)

- "[OracleDbType Enumeration](OracleDbTypeEnumerationType.md)"
