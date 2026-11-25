This constructor creates and initializes an `OracleCustomTypeMappingAttribute` using the specified Oracle user-defined type name.

### Declaration

    // C#
    public OracleCustomTypeMappingAttribute(string udtTypeName)

### Parameters

- `udtTypeName`

  The Oracle user-defined type name that the custom class maps to.

### Remarks

The `udtTypeName` parameter is case-sensitive. The `udtTypeName` is specified in the form of `schema_name.type_name`.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleCustomTypeMappingAttribute Class](OracleCustomTypeMappingAttributeClass.md)

- [OracleCustomTypeMappingAttribute Members](OracleCustomTypeMappingAttributeMembers.md)
