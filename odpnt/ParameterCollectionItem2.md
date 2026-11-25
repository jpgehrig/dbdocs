This property gets and sets the `OracleParameter` object using the parameter name specified by the supplied `parameterName`.

### Declaration

    // C#
    public OracleParameter Item[string parameterName] {get; set;};

### Property Value

An `OracleParameter`.

### Implements

`IDataParameterCollection`

### Exceptions

`IndexOutOfRangeException` - The supplied parameter name does not exist.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleParameterCollection Class](OracleParameterCollectionClass.md)

- [OracleParameterCollection Members](ParameterCollectionMembers.md)
