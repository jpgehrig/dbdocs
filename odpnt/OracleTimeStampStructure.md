The `OracleTimeStamp` structure represents the Oracle `TIMESTAMP` data type to be stored in or retrieved from a database. Each `OracleTimeStamp` stores the following information: year, month, day, hour, minute, second, and nanosecond.

### Class Inheritance

`System.Object`

`  System.ValueType`

`    Oracle.DataAccess.Types.OracleTimeStamp`

### Declaration

     // C#public struct OracleTimeStamp : IComparable, INullable, IXmlSerializable

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

    class OracleTimeStampSample
    {
      static void Main()
      {
        OracleTimeStamp tsCurrent1 = OracleTimeStamp.GetSysDate();
        OracleTimeStamp tsCurrent2 = DateTime.Now;

        // Calculate the difference between tsCurrent1 and tsCurrent2
        OracleIntervalDS idsDiff = tsCurrent2.GetDaysBetween(tsCurrent1);

        // Calculate the difference using AddNanoseconds()
        int nanoDiff = 0;
        while (tsCurrent2 > tsCurrent1)
        {
          nanoDiff += 10;
          tsCurrent1 = tsCurrent1.AddNanoseconds(10);
        }
        Console.WriteLine("idsDiff.Nanoseconds = " + idsDiff.Nanoseconds);
        Console.WriteLine("nanoDiff = " + nanoDiff);
      }
    }

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStamp Members](TimeStampMembers.md)

- [OracleTimeStamp Constructors](TimeStampCtors.md)

- [OracleTimeStamp Static Fields](TimeStampStaticFields.md)

- [OracleTimeStamp Static Methods](TimeStampStaticMethods.md)

- [OracleTimeStamp Static Operators](TimeStampStaticOperators.md)

- [OracleTimeStamp Static Type Conversions](TimeStampStaticTypeConversions.md)

- [OracleTimeStamp Properties](TimeStampProperties.md)

- [OracleTimeStamp Methods](TimeStampMethods.md)
