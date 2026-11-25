The `OracleBoolean` structure represents a logical value that is either `TRUE` or `FALSE`.

ODP.NET, Unmanaged Driver can access Oracle Database PL/SQL Booleans in Oracle Database Release 12.1 and later. ODP.NET, Managed Driver can access Oracle Database PL/SQL Booleans in Oracle Database Release 12.2 and later.

### Class Inheritance

`System.Object`

`  System.ValueType`

`    Oracle.DataAccess.Types.OracleBoolean`

### Declaration

    // C#
    public struct OracleBoolean : IComparable, INullable, IXmlSerializable

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

A `OracleBoolean` structure represents three possible values: `TRUE`, `FALSE`, and `NULL`. A non-zero value is interpreted as `TRUE`.

### Example

    // C#
    using System;
    using System.Data;
    using Oracle.DataAccess.Types; // for use with ODP.NET, Unmanaged Driver
    // using Oracle.ManagedDataAccess.Types; // for use with ODP.NET, Managed Driver

     class OracleBooleanSample
     {
        static void Main(string[] args)
        {
          OracleBoolean oracleBoolean1 = new OracleBoolean(true);
          OracleBoolean oracleBoolean2 = new OracleBoolean(0);

          Console.WriteLine("oracleBoolean1 : " + oracleBoolean1);
          Console.WriteLine("oracleBoolean2 : " + oracleBoolean2);
        }
     }

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleBoolean Members](BooleanMembers.md)

- [OracleBoolean Constructors](BooleanCtors.md)

- [OracleBoolean Static Fields](BooleanStaticFields.md)

- [OracleBoolean Static Methods](BooleanStaticMethods.md)

- [OracleBoolean Static Operators](BooleanStaticOperators.md)

- [OracleBoolean Static Type Conversions](BooleanStaticTypeConversions.md)

- [OracleBoolean Properties](BooleanProperties.md)

- [OracleBoolean Instance Methods](BooleanInstanceMethods.md)
