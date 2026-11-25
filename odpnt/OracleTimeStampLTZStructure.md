The `OracleTimeStampLTZ` structure represents the Oracle `TIMESTAMP` `WITH` `LOCAL` `TIME` `ZONE` data type to be stored in or retrieved from a database. Each `OracleTimeStampLTZ` stores the following information: year, month, day, hour, minute, second, and nanosecond.

### Class Inheritance

`System.Object`

`  System.ValueType`

`    Oracle.DataAccess.Types.OracleTimeStampLTZ`

### Declaration

    // C#
    public struct OracleTimeStampLTZ : IComparable, INullable, IXmlSerializable

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

    class OracleTimeStampLTZSample
    {
      static void Main()
      {
        // Illustrates usage of OracleTimeStampLTZ
        // Display Local Time Zone Name
        Console.WriteLine("Local Time Zone Name = " +
          OracleTimeStampLTZ.GetLocalTimeZoneName());
        OracleTimeStampLTZ tsLocal1 = OracleTimeStampLTZ.GetSysDate();
        OracleTimeStampLTZ tsLocal2 = DateTime.Now;

        // Calculate the difference between tsLocal1 and tsLocal2
        OracleIntervalDS idsDiff = tsLocal2.GetDaysBetween(tsLocal1);

        // Calculate the difference using AddNanoseconds()
        int nanoDiff = 0;
        while (tsLocal2 > tsLocal1)
        {
          nanoDiff += 10;
          tsLocal1 = tsLocal1.AddNanoseconds(10);
        }
        Console.WriteLine("idsDiff.Nanoseconds = " + idsDiff.Nanoseconds);
        Console.WriteLine("nanoDiff = " + nanoDiff);
      }
    }

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStampLTZ Members](TimeStampLTZMembers.md)

- [OracleTimeStampLTZ Constructors](TimeStampLTZCtors.md)

- [OracleTimeStampLTZ Static Fields](TimeStampLTZStaticFields.md)

- [OracleTimeStampLTZ Static Methods](TimeStampLTZStaticMethods.md)

- [OracleTimeStampLTZ Static Operators](TimeStampLTZStaticTypeOperators.md)

- [OracleTimeStampLTZ Static Type Conversions](TimeStampLTZStatictypeConversions.md)

- [OracleTimeStampLTZ Properties](TimeStampLTZProperties.md)

- [OracleTimeStampLTZ Methods](TimeStampLTZMethods.md)
