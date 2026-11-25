The `OracleString` structure represents a variable-length stream of characters to be stored in or retrieved from a database.

### Class Inheritance

`System.Object`

`  System.ValueType`

`    Oracle.DataAccess.Types.OracleString`

### Declaration

    // C#
    public struct OracleString : IComparable, INullable, IXmlSerializable

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

    class OracleStringSample
    {
      static void Main()
      {
        // Initialize OracleString structs
        OracleString string1 = new OracleString("AAA");

        // Display the string "AAA"
        Console.WriteLine("{0} has length of {1}", string1, string1.Length);

        // Contatenate characters to string1 until the length is 5
        while (string1.Length < 5)
          string1 = OracleString.Concat(string1,"a");

        // Display the string of "AAAaa"
        Console.WriteLine("{0} has length of {1}", string1, string1.Length);
      }
    }

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleString Members](StringMembers.md)

- [OracleString Constructors](StringCtors.md)

- [OracleString Static Fields](StringStaticFields.md)

- [OracleString Static Methods](StringStaticMethods.md)

- [OracleString Static Operators](StringStaticOperators.md)

- [OracleString Type Conversions](StringTypeConversions.md)

- [OracleString Properties](StringProperties.md)

- [OracleString Methods](StringMethods.md)
