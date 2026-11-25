This method adds the supplied object to the collection.

### Declaration

    // C#
    public override int Add(object obj);

### Parameters

- `obj`

  The supplied object.

### Return Value

The index at which the new `OracleParameter` is added.

### Implements

`IList`

### Remarks

`InvalidCastException` - The supplied `obj` cannot be cast to an `OracleParameter` object.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleParameterCollection Class](OracleParameterCollectionClass.md)

- [OracleParameterCollection Members](ParameterCollectionMembers.md)
