This property specifies the value corresponding to the `Data` `Source` attribute in the `ConnectionString` property.

### Declaration

    // C#
    public string DataSource{get; set;}

### Property Value

A string that represents the value of the supplied attribute.

### Exceptions

`ArgumentNullException` - The specified value is null.

### Remarks

When an `OracleConnectionStringBuilder` instance is created, this property is set to the default value of the corresponding connection string attribute.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnectionStringBuilder Class](OracleConnectionStringBuilderClass.md)

- [OracleConnectionStringBuilder Members](OracleConnectionStringBuilderMembers.md)
