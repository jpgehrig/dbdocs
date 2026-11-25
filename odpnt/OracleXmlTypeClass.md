An `OracleXmlType` object represents an Oracle `XMLType` instance.

### Class Inheritance

`System.Object`

`  System.OracleXmlType`

### Declaration

    // C#
    public sealed class OracleXmlType : IDisposable, INullable

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  | ODP.NET, Managed Driver           | ODP.NET Core                      |
|:---------------|:---------------------------|:----------------------------------|:----------------------------------|
| Assembly       | `Oracle.DataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` | `Oracle.ManagedDataAccess.Client` | `Oracle.ManagedDataAccess.Client` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7         | 4.5, 4.6, 4.7                     | 4.6.1 or higher                   |
| .NET Core      | \-                         | \-                                | 2.1 or higher                     |

### Thread Safety

All public static methods are thread-safe, although instance methods do not guarantee thread safety.

### Remarks

`OracleXmlType` objects can be used for well-formed XML documents with or without XML schemas or XML fragments.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleXmlType Members](XmlTypeMembers.md)

- [OracleXmlType Constructors](XmlTypeCtors.md)

- [OracleXmlType Static Methods](XmlTypeStaticMethods.md)

- [OracleXmlType Static Fields](XmlTypeStaticFields.md)

- [OracleXmlType Instance Properties](XmlTypeProperties.md)

- [OracleXmlType Instance Methods](XmlTypePublicMethods.md)
