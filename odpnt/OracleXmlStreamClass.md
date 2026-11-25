An `OracleXmlStream` object represents a read-only stream of XML data stored in an `OracleXmlType` object.

### Class Inheritance

`System.Object`

`  System.MarshalByRefObject`

`    System.Stream`

`      System.OracleXmlStream`

### Declaration

    // C#
    public sealed class OracleXmlStream : IDisposable, ICloneable

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  | ODP.NET, Managed Driver           | ODP.NET Core                      |
|:---------------|:---------------------------|:----------------------------------|:----------------------------------|
| Assembly       | `Oracle.DataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` | `Oracle.ManagedDataAccess.Client` | `Oracle.ManagedDataAccess.Client` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7         | 4.5, 4.6, 4.7                     | 4.6.1 or higher                   |
| .NET Core      | \-                         | \-                                | 2.1 or higher                     |

### Thread Safety

All public static methods are thread-safe, although instance methods do not guarantee thread safety.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleXmlStream Members](XmlStreamMembers.md)

- [OracleXmlStream Constructor](XmlStreamCtors.md)

- [OracleXmlStream Static Methods](XmlStreamStaticMethods.md)

- [OracleXmlStream Instance Properties](XmlStreamProperties.md)

- [OracleXmlStream Instance Methods](XmlStreamPublicMethods.md)
