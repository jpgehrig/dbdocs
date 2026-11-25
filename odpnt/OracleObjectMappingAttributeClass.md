The `OracleObjectMappingAttribute` class marks custom class fields or properties with information that ODP.NET uses when a custom type represents an Oracle Object type.

### Class Inheritance

`System.Object`

  `System.Attribute`

    `System.OracleObjectMappingAttribute`

### Declaration

    // C#
    [AttributeUsageAttribute(AttributeTargets.Field|AttributeTargets.Property, AllowMultiple=false, Inherited=true)]

    public sealed class OracleObjectMappingAttribute : Attribute

### Requirements

| Provider       | ODP.NET, Unmanaged Driver |
|:---------------|:--------------------------|
| Assembly       | `Oracle.DataAccess.dll`   |
| Namespace      | `Oracle.DataAccess.Types` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7        |

### Remarks

The `OracleObjectMappingAttribute` is specified on members of a custom type that represent an Oracle object type. This attribute must specify the name or zero-based index of the attribute in the Oracle object that the custom class field or property maps to. This also allows the custom type to declare field or property names which differ from the Oracle Object type.

### Thread Safety

All public static methods are thread-safe, although instance methods do not guarantee thread safety.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleObjectMappingAttribute Members](OracleObjectMappingAttributeMembers.md)

- [OracleObjectMappingAttribute Constructors](ObjectMappingAttributeConstructors.md)

- [OracleObjectMappingAttribute Static Methods](ObjectMappingAttributeStaticMethods.md)

- [OracleObjectMappingAttribute Properties](ObjectMappingAttributeProperties.md)

- [OracleObjectMappingAttribute Methods](ObjectMappingAttributeAttributeMethods.md)
