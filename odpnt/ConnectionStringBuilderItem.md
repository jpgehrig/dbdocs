This property specifies the value associated with the specified attribute.

### Declaration

    // C#
    public override object this[string keyword]{get; set;}


### Property Value

An object value corresponding to the attribute.

### Exceptions

`ArgumentNullException` - The specified attribute is null.

`OracleException` - The specified attribute is not supported or the specified value is invalid.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnectionStringBuilder Class](OracleConnectionStringBuilderClass.md)

- [OracleConnectionStringBuilder Members](OracleConnectionStringBuilderMembers.md)
