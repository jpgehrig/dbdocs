This property specifies the properties that are used when an XML document is used to save changes to the database.

### Declaration

    // C#
    public OracleXmlSaveProperties XmlSaveProperties {get; set;}

### Property Value

`OracleXmlSaveProperties`.

### Remarks

When a new instance of `OracleCommand` is created, an instance of `OracleXmlSaveProperties` is automatically available on the `OracleCommand` instance through the `OracleCommand.XmlSaveProperties` property.

A new instance of `OracleXmlSaveProperties` can be assigned to an `OracleCommand` instance. Assigning an instance of `OracleXmlSaveProperties` to the `XmlSaveProperties` of an `OracleCommand` instance creates a new instance of the given `OracleXmlSaveProperties` instance for the `OracleCommand`. This way each `OracleCommand` instance has its own `OracleXmlSaveProperties` instance.

Use the default constructor to get a new instance of `OracleXmlSaveProperties`.

Use the `OracleXmlSaveProperties.Clone()` method to get a copy of an `OracleXmlSaveProperties` instance.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleCommand Class](OracleCommandClass.md)

- [OracleCommand Members](OracleCommandMembers.md)
