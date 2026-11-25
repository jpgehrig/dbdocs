This property specifies whether or not the `OracleParameter` represents a collection, and if so, specifies the collection type.

### Declaration

    // C#
    public OracleCollectionType CollectionType { get; set; }

### Property Value

An `OracleCollectionType` enumerated value.

### Exceptions

`ArgumentException` - The `OracleCollectionType` value specified is invalid.

### Remarks

Default = `OracleCollectionType.None`. If `OracleParameter` is used to bind a PL/SQL Associative Array, then `CollectionType` must be set to `OracleCollectionType.PLSQLAssociativeArray`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleParameter Class](OracleParameterClass.md)

- [OracleParameter Members](ParameterMembers.md)
