This method returns the index of the `OracleParameter` object in the collection.

### Declaration

    // C#
    public override int IndexOf(object obj);

### Parameters

- `obj`

  The specified object.

### Return Value

Returns the index of the `OracleParameter` object in the collection.

### Implements

`IList`

### Exceptions

`InvalidCastException` - The supplied `obj` cannot be cast to an `OracleParameter` object.

### Remarks

Returns the `index` of the supplied `OracleParameter` `obj` in the collection.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleParameterCollection Class](OracleParameterCollectionClass.md)

- [OracleParameterCollection Members](ParameterCollectionMembers.md)
