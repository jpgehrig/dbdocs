The `OracleArrayMappingAttribute` class is required to mark a custom class field or property with information that ODP.NET uses when a custom type represents an Oracle Collection type.

### Class Inheritance

`System.Object`

`  ``System.Attribute`

`    System.``OracleArrayMappingAttribute`

### Declaration

\[AttributeUsageAttribute(AttributeTargets.Field\|AttributeTargets.Property, AllowMultiple=false, Inherited=true)\]

    // C#
    public sealed class OracleArrayMappingAttribute : Attribute

### Requirements

| Provider       | ODP.NET, Unmanaged Driver |
|:---------------|:--------------------------|
| Assembly       | `Oracle.DataAccess.dll`   |
| Namespace      | `Oracle.DataAccess.Types` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7        |

### Remarks

An `OracleArrayMappingAttribute` object must be specified when a custom type represents an Oracle Collection. This attribute is applied only to the custom class member that stores the collection elements.

### Thread Safety

All public static methods are thread-safe, although instance methods do not guarantee thread safety.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleArrayMappingAttribute Members](OracleArrayMappingAttributeMembers.md)

- [OracleArrayMappingAttribute Constructors](OracleArrayMappingAttributeConstructors.md)

- [OracleArrayMappingAttribute Static Methods](ArrayMappingAttributeStaticMethods.md)

- [OracleArrayMappingAttribute Properties](ArrayMappingAttributeProperties.md)

- [OracleArrayMappingAttribute Methods](ArrayMappingAttributeMethods.md)
