This property specifies the value corresponding to the `Enlist` attribute in the `ConnectionString` property.

### Declaration

     // C#
    public string Enlist{get; set;};

### Property Value

A string that represents the value of the supplied attribute. Values are case-insensitive. Possible values are: dynamic, true, false, yes, and no.

### Exceptions

`ArgumentNullException` - The specified value is null.

`OracleException` - The supplied value is not one of following: `dynamic`, `true`, `false`, `yes`, or `no`.

### Remarks

When an `OracleConnectionStringBuilder` instance is created, this property is set to the default value of the corresponding connection string attribute.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnectionStringBuilder Class](OracleConnectionStringBuilderClass.md)

- [OracleConnectionStringBuilder Members](OracleConnectionStringBuilderMembers.md)
