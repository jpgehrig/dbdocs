The `OracleTimeStampTZ` structure represents the Oracle `TIMESTAMP` `WITH` `TIME` `ZONE` data type to be stored in or retrieved from a database. Each `OracleTimeStampTZ` stores the following information: year, month, day, hour, minute, second, nanosecond, and time zone.

### Class Inheritance

`System.Object`

`  System.ValueType`

`    Oracle.DataAccess.Types.OracleTimeStampTZ`

### Declaration

    // C#
    public struct OracleTimeStampTZ : IComparable, INullable, IXmlSerializable

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
    using Oracle.DataAccess.Client;
    using Oracle.DataAccess.Types;

    class OracleTimeStampTZSample
    {
      static void Main()
      {
        // Set the nls parameters for the current thread
        OracleGlobalization info = OracleGlobalization.GetClientInfo();
        info.TimeZone = "US/Eastern";
        info.TimeStampFormat = "DD-MON-YYYY HH:MI:SS.FF AM";
        info.TimeStampTZFormat = "DD-MON-YYYY HH:MI:SS.FF AM TZR";
        OracleGlobalization.SetThreadInfo(info);

        // Create an OracleTimeStampTZ in US/Pacific time zone
        OracleTimeStampTZ tstz1=new OracleTimeStampTZ("11-NOV-1999 "+
          "11:02:33.444 AM US/Pacific");

        // Note that ToOracleTimeStampTZ uses the thread's time zone region,
        // "US/Eastern"
        OracleTimeStamp ts = new OracleTimeStamp("11-NOV-1999 11:02:33.444 AM");
        OracleTimeStampTZ tstz2 = ts.ToOracleTimeStampTZ();

        // Calculate the difference between tstz1 and tstz2
        OracleIntervalDS idsDiff = tstz1.GetDaysBetween(tstz2);

        // Display information
        Console.WriteLine("tstz1.TimeZone = " + tstz1.TimeZone);

        // Prints "US/Pacific"
        Console.WriteLine("tstz2.TimeZone = " + tstz2.TimeZone);

        // Prints "US/Eastern"
        Console.WriteLine("idsDiff.Hours = " + idsDiff.Hours); // Prints 3
        Console.WriteLine("idsDiff.Minutes = " + idsDiff.Minutes); // Prints 0
      }
    }

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStampTZ Members](TimeStampTZMembers.md)

- [OracleTimeStampTZ Constructors](TimeStampTZCtors.md)

- [OracleTimeStampTZ Static Fields](TimeStampTZStaticFields.md)

- [OracleTimeStampTZ Static Methods](TimeStampTZStaticMethods.md)

- [OracleTimeStampTZ Static Operators](TimeStampTZStaticOperators.md)

- [OracleTimeStampTZ Static Type Conversions](TimeStampTZStaticTypeConversions.md)

- [OracleTimeStampTZ Properties](TimeStampTZProperties.md)

- [OracleTimeStampTZ Methods](TimeStampTZMethods.md)
