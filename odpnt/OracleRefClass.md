An `OracleRef` instance represents an Oracle `REF`, which references a persistent, standalone, referenceable object that resides in the database. The `OracleRef` object provides methods to insert, update, and delete the Oracle `REF`.

### Class Inheritance

`System.Object`

`  System.MarshalByRefObject`

`    Oracle.DataAccess.Types.OracleRef`

### Declaration

    // C#
    public sealed class OracleRef : MarshalByRefObject,ICloneable, IDisposable,
      INullable

### Requirements

| Provider       | ODP.NET, Unmanaged Driver |
|:---------------|:--------------------------|
| Assembly       | `Oracle.DataAccess.dll`   |
| Namespace      | `Oracle.DataAccess.Types` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7        |

### Thread Safety

All public static methods are thread-safe, although instance methods do not guarantee thread safety.

### Remarks

If two or more `OracleRef` objects that refer to the same Oracle object in the database are retrieved through the same `OracleConnection`, then their operations on the referenced object must be synchronized.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleRef Members](OracleRefMembers.md)

- [OracleRef Constructors](RefConstructors.md)

- [OracleRef Static Methods](RefStaticMethods.md)

- [OracleRef Instance Properties](RefProperties.md)

- [Oracle Ref Instance Methods](RefInstanceMethods.md)
