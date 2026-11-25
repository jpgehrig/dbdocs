The `OracleDate` structure represents the Oracle `DATE` data type to be stored in or retrieved from a database. Each `OracleDate` stores the following information: year, month, day, hour, minute, and second.

### Class Inheritance

`System.Object`

`  System.ValueType`

`    Oracle.DataAccess.Types.OracleDate`

### Declaration

    // C#
    public struct OracleDate : IComparable, INullable, IXmlSerializable

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
    using Oracle.DataAccess.Client;

    class OracleDateSample
    {
      static void Main(string[] args)
      {
        // Initialize the dates to the lower and upper boundaries
        OracleDate date1 = OracleDate.MinValue;
        OracleDate date2 = OracleDate.MaxValue;
        OracleDate date3 = new OracleDate(DateTime.MinValue);
        OracleDate date4 = new OracleDate(DateTime.MaxValue);

        // Set the thread's DateFormat for output
        OracleGlobalization info = OracleGlobalization.GetClientInfo();
        info.DateFormat = "DD-MON-YYYY BC";
        OracleGlobalization.SetThreadInfo(info);

        // Print the lower and upper boundaries
        Console.WriteLine("OracleDate ranges from\n{0}\nto\n{1}\n",
          date1, date2);
        Console.WriteLine(".NET DateTime ranges from\n{0}\nto\n{1}\n",
          date3, date4);
      }
    }

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDate Members](DateMembers.md)

- [OracleDate Constructors](DateCtors.md)

- [OracleDate Static Fields](DateStaticFields.md)

- [OracleDate Static Methods](DateStaticMethods.md)

- [OracleDate Static Operators](DateStaticOperators.md)

- [OracleDate Static Type Conversions](DateStaticTypeConversions.md)

- [OracleDate Properties](DateProperties.md)

- [OracleDate Methods](DateMethods.md)
