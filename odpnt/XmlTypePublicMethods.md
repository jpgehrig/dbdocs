The `OracleXmlType` instance methods are listed in Table 7-27.

Table 7-27 OracleXmlType Instance Methods

| Methods                                    | Description                                                                                                                        |
|:-------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------|
| [Clone](XmlTypeClone.md)                   | Creates a copy of the `OracleXmlType` instance                                                                                     |
| [Dispose](XmlTypeDispose.md)               | Releases the resources allocated by this `OracleXmlType` object                                                                    |
| `Equals`                                   | Inherited from `System.Object`                                                                                                     |
| [Extract](XmlTypeExtractOverloads.md)      | Extracts a subset from the XML data using the given XPath expression (Overloaded)                                                  |
| `GetHashCode`                              | Inherited from `System.Object`                                                                                                     |
| [GetStream](XmlTypeGetStream.md)           | Returns an instance of `OracleXmlStream` which provides a read-only stream of the XML data stored in this `OracleXmlType` instance |
| `GetType`                                  | Inherited from `System.Object`                                                                                                     |
| [GetXmlDocument](XmlTypeGetXmlDocument.md) | Returns a `XmlDocument` object containing the XML data stored in this `OracleXmlType` instance                                     |
| [GetXmlReader](XmlTypeGetXmlReader.md)     | Returns a `XmlTextReader` object that can be used to manipulate XML data directly using the .NET Framework classes and methods     |
| [IsExists](XmlTypeIsExistsOverloads.md)    | Checks for the existence of a particular set of nodes identified by the given XPath expression in the XMLdata (Overloaded)         |
| `ToString`                                 | Inherited from `System.Object`                                                                                                     |
| [Transform](XmlTypeTransformOverloads.md)  | Transforms the `OracleXmlType` into another `OracleXmlType` instance using the given XSL document (Overloaded)                     |
| [Update](XmlTypeUpdateOverloads.md)        | Updates the XML node or fragment identified by the given XPath expression in the current `OracleXmlType` instance (Overloaded)     |
| [Validate](XmlTypeValidate.md)             | Validates whether or not the XML data in the `OracleXmlType` object conforms to the given XML schema.                              |

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleXmlType Class](OracleXmlTypeClass.md)

- [OracleXmlType Members](XmlTypeMembers.md)
