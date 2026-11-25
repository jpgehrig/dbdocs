This property specifies the value corresponding to the `Incr` `Pool` `Size` attribute in the `ConnectionString` property.

### Declaration

    // C#
    public int IncrPoolSize{get; set;}

### Property Value

An `int` that represents the value of the supplied attribute.

### Exceptions

`OracleException` - The specified value is less than `1`.

### Remarks

When an `OracleConnectionStringBuilder` instance is created, this property is set to the default value of the corresponding connection string attribute.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnectionStringBuilder Class](OracleConnectionStringBuilderClass.md)

- [OracleConnectionStringBuilder Members](OracleConnectionStringBuilderMembers.md)
