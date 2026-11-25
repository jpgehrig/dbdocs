This method inserts the supplied `OracleParameter` object to the collection at the specified `index`.

### Declaration

    // C#
    public override void Insert(int index, object obj);

### Parameters

- `index`

  The specified index.

- `obj`

  The `OracleParameter` object.

### Implements

`IList`

### Remarks

An `InvalidCastException` is thrown if the supplied `obj` cannot be cast to an `OracleParameter` object.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleParameterCollection Class](OracleParameterCollectionClass.md)

- [OracleParameterCollection Members](ParameterCollectionMembers.md)
