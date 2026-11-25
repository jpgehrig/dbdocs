The `OracleBinary` structure represents a variable-length stream of binary data to be stored in or retrieved from a database.

### Class Inheritance

`System.Object`

`  System.ValueType`

`    Oracle.DataAccess.Types.OracleBinary`

### Declaration

    // C#
    public struct OracleBinary : IComparable, INullable, IXmlSerializable

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  | ODP.NET, Managed Driver           | ODP.NET Core                      |
|:---------------|:---------------------------|:----------------------------------|:----------------------------------|
| Assembly       | `Oracle.DataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` | `Oracle.ManagedDataAccess.Client` | `Oracle.ManagedDataAccess.Client` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7         | 4.5, 4.6, 4.7                     | 4.6.1 or higher                   |
| .NET Core      | \-                         | \-                                | 2.1 or higher                     |

### Thread Safety

All public static methods are thread-safe, although instance methods do not guarantee thread safety.

### Example

    // C#

    using System;
    using Oracle.DataAccess.Types;

    class OracleBinarySample
    {
      static void Main(string[] args)
      {
        // Initialize the OracleBinary structures
        OracleBinary binary1= new OracleBinary(new byte[] {1,2,3,4,5});
        OracleBinary binary2 = new OracleBinary(new byte[] {1,2,3});
        OracleBinary binary3 = new OracleBinary(new byte[] {4,5});
        OracleBinary binary4 = binary2 + binary3;

        // Compare binary1 and binary4; they're equal
        if (binary1 == binary4)
          Console.WriteLine("The two OracleBinary structs are equal");
        else
          Console.WriteLine("The two OracleBinary structs are different");
      }
    }

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleBinary Members](BinaryMembers.md)

- [OracleBinary Constructor](BinaryCtor.md)

- [OracleBinary Static Fields](BinaryStaticFields.md)

- [OracleBinary Static Methods](BinaryStaticMethods.md)

- [OracleBinary Static Operators](BinaryStaticOperators.md)

- [OracleBinary Static Type Conversion Operators](BinaryStaticTypeConversionOperators.md)

- [OracleBinary Properties](BinaryProperties.md)

- [OracleBinary Instance Methods](BinaryInstanceMethods.md)
