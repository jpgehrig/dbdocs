`OracleXmlType` members are listed in the following tables.

### OracleXmlType Constructors

The `OracleXmlType` constructors are listed in Table 7-19.

Table 7-19 OracleXmlType Constructors

| Constructor                                   | Description                                                   |
|:----------------------------------------------|:--------------------------------------------------------------|
| [OracleXmlType Constructors](XmlTypeCtors.md) | Creates an instance of the `OracleXmlType` class (Overloaded) |

### OracleXmlType Static Methods

The `OracleXmlType` static methods are listed in Table 7-20.

Table 7-20 OracleXmlType Static Methods

| Methods  | Description                                 |
|:---------|:--------------------------------------------|
| `Equals` | Inherited from `System.Object` (Overloaded) |

### OracleXmlType Static Fields

The `OracleXmlType` static field is listed in Table 7-21.

Table 7-21 OracleXmlType Static Field

| Static Field                      | Description                                                                 |
|:----------------------------------|:----------------------------------------------------------------------------|
| [Null](XmlTypeStaticFieldNull.md) | Represents a null value that can be assigned to an `OracleXmlType` instance |

### OracleXmlType Instance Properties

The `OracleXmlType` instance properties are listed in Table 7-22.

Table 7-22 OracleXmlType Instance Properties

| Properties                               | Description                                                                                                |
|:-----------------------------------------|:-----------------------------------------------------------------------------------------------------------|
| [Connection](XmlTypeConnection.md)       | Indicates the `OracleConnection` that is used to retrieve and store XML data in the `OracleXmlType`        |
| [IsEmpty](XmlTypeIsEmpty.md)             | Indicates whether or not the `OracleXmlType` is empty                                                      |
| [IsFragment](XmlTypeIsFragment.md)       | Indicates whether the XML data is a collection of XML elements or a well-formed XML document               |
| [IsNull](XmlTypeIsNull.md)               | Indicates whether or not the `OracleXmlType` is null                                                       |
| [IsSchemaBased](XmlTypeIsSchemaBased.md) | Indicates whether or not the XML data represented by the `OracleXmlType` is based on an XML schema         |
| [RootElement](XmlTypeRootElement.md)     | Represents the name of the top-level element of the schema-based XML data contained in the `OracleXmlType` |
| [Schema](XmlTypeSchema.md)               | Represents the XML schema of the XML data contained in the `OracleXmlType`                                 |
| [SchemaUrl](XmlTypeSchemaUrl.md)         | Represents in the database for the XML schema of the XML data contained in the `OracleXmlType`.            |
| [Value](XmlTypeValue.md)                 | Returns the XML data starting from the first character in the current instance as a string                 |

### OracleXmlType Instance Methods

The `OracleXmlType` instance methods are listed in Table 7-23.

Table 7-23 OracleXmlType Instance Methods

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
