The `OracleIntervalDS` structure represents the Oracle `INTERVAL` `DAY` `TO` `SECOND` data type to be stored in or retrieved from a database. Each `OracleIntervalDS` stores a period of time in term of days, hours, minutes, seconds, and fractional seconds.

### Class Inheritance

`System.Object`

`  System.ValueType`

`    Oracle.DataAccess.Types.OracleIntervalDS`

### Declaration

    // C#
    public struct OracleIntervalDS : IComparable, INullable, IXmlSerializable

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

    class OracleIntervalDSSample
    {
      static void Main()
      {
        OracleIntervalDS iDSMax = OracleIntervalDS.MaxValue;
        double totalDays = iDSMax.TotalDays;

        totalDays -= 1;
        OracleIntervalDS iDSMax_1 = new OracleIntervalDS(totalDays);

        // Calculate the difference
        OracleIntervalDS iDSDiff = iDSMax - iDSMax_1;

        // Prints "iDSDiff.ToString() = +000000000 23:59:59.999999999"
        Console.WriteLine("iDSDiff.ToString() = " + iDSDiff.ToString());
      }
    }

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleIntervalDS Members](IntervalDSMembers.md)

- [OracleIntervalDS Constructors](IntervalDSCtors.md)

- [OracleIntervalDS Static Fields](IntervalDSStaticFields.md)

- [OracleIntervalDS Static Methods](IntervalDSStaticMethods.md)

- [OracleIntervalDS Static Operators](IntervalDSStaticOperators.md)

- [OracleIntervalDS Type Conversions](IntervalDSTypeConversions.md)

- [OracleIntervalDS Properties](IntervalDSProperties.md)

- [OracleIntervalDS Methods](IntervalDSMethods.md)
