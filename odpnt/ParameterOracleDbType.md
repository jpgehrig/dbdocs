This property specifies the Oracle data type.

### Declaration

    // C#
    public OracleDbType OracleDbType { get; set; }

### Property Value

An `OracleDbType` enumerated value.

### Remarks

Default = `OracleDbType.Varchar2`

If the `OracleParameter` object is used for Array Bind or PL/SQL Associative Array Bind execution, `OracleDbType` is the data type of each element in the array.

The `OracleDbType` property and `DbType` property are linked. Therefore, setting the `OracleDbType` property changes the `DbType` property to a supporting `DbType`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleParameter Class](OracleParameterClass.md)

- [OracleParameter Members](ParameterMembers.md)

- "[OracleDbType Enumeration](OracleDbTypeEnumerationType.md)"

- "[Inference of DbType from OracleDbType](featOraCommand.md)"

- "[CollectionType](ParameterCollectionType.md)"
