The `OracleCustomTypeMappingAttribute` class is used to mark a custom type factory class or struct with information that is used by ODP.NET when a custom type is used to represent an Oracle UDT.

### Class Inheritance

`System.Object`

` System.Attribute`

` System.OracleCustomTypeMappingAttribute`

### Declaration

    // C#
    [AttributeUsageAttribute(AttributeTargets.Class|AttributeTargets.Struct,
       AllowMultiple=false, Inherited=true)]
    public sealed class OracleCustomTypeMappingAttribute : Attribute

### Requirements

| Provider       | ODP.NET, Unmanaged Driver |
|:---------------|:--------------------------|
| Assembly       | `Oracle.DataAccess.dll`   |
| Namespace      | `Oracle.DataAccess.Types` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7        |

### Remarks

The `OracleCustomTypeMapping` attribute must be specified on the custom type factory class to indicate the Oracle UDT that the corresponding custom type represents. The Oracle UDT may be specified in the form `schema_name.type_name`.

For each Oracle UDT that the application uses, there must be a unique custom type factory, as follows:

- Oracle Object Types

  The custom type factory must return a custom type that cannot be used to represent any other Oracle Object Type.

- Oracle Collection Types

  The custom type factory may return a custom type that can be used by other Oracle Collection Types. This is common when an array type is used to represent an Oracle Collection, that is, when an `int[]` is used to represent a collection of `NUMBER`s.

If the `OracleCustomTypeMappingAttribute` is not specified, then custom type mappings must be specified through an XML configuration file, for example, `app.config` for Windows applications or the `web.config` for web applications, and the `machine.config`

### Thread Safety

All public static methods are thread-safe, although instance methods do not guarantee thread safety.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleCustomTypeMappingAttribute Members](OracleCustomTypeMappingAttributeMembers.md)

- [OracleCustomTypeMappingAttribute Constructors](CustomTypeMappingAttributeConstructors.md)

- [OracleCustomTypeMappingAttribute Static Methods](CustomTypeMappingAttributeStaticMethods.md)

- [OracleCustomTypeMappingAttribute Methods](CustomTypeMappingAttributeMethods.md)
