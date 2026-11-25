This property specifies the Oracle data type to bind the parameter as, but returns a .NET type as output.

### Declaration

    // C#
    public OracleDbType OracleDbTypeEx { get; set; }

### Property Value

An `OracleDbType` enumerated value.

### Remarks

This property is used by applications that need to bind a parameter value as an Oracle type, but need a .NET type back for output. This property should be used with an output or input/output parameter. For an input parameter, using `OracleDbTypeEx` has the same affect as using `OracleDbType`. The .NET type that is returned for the output is the .NET type that the Oracle type closely maps to.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleParameter Class](OracleParameterClass.md)

- [OracleParameter Members](ParameterMembers.md)

- "[OracleDbType Enumeration](OracleDbTypeEnumerationType.md)"

- "[OracleDbType](ParameterOracleDbType.md)"

- "[Inference of DbType from OracleDbType](featOraCommand.md)"

- "[CollectionType](ParameterCollectionType.md)"
