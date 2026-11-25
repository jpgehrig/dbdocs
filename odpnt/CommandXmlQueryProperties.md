This property specifies the properties that are used when an XML document is created from the result set of a SQL query statement.

### Declaration

    // C#
    public OracleXmlQueryProperties XmlQueryProperties {get; set;}

### Property Value

`OracleXmlQueryProperties`.

### Remarks

When a new instance of `OracleCommand` is created, an instance of `OracleXmlQueryProperties` is automatically available on the `OracleCommand` instance through the `OracleCommand.XmlQueryProperties` property.

A new instance of `OracleXmlQueryProperties` can be assigned to an `OracleCommand` instance. Assigning an instance of `OracleXmlQueryProperties` to the `XmlQueryProperties` of an `OracleCommand` instance creates a new instance of the given `OracleXmlQueryProperties` instance for the `OracleCommand`. This way each `OracleCommand` instance has its own `OracleXmlQueryProperties` instance.

Use the default constructor to get a new instance of `OracleXmlQueryProperties`.

Use the `OracleXmlQueryProperties.Clone()` method to get a copy of an `OracleXmlQueryProperties` instance.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleCommand Class](OracleCommandClass.md)

- [OracleCommand Members](OracleCommandMembers.md)
