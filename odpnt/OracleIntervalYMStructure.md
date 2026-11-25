The `OracleIntervalYM` structure represents the Oracle `INTERVAL` `YEAR` `TO` `MONTH` data type to be stored in or retrieved from a database. Each `OracleIntervalYM` stores a period of time in years and months.

### Class Inheritance

`System.Object`

`  System.ValueType`

`    Oracle.DataAccess.Types.OracleIntervalYM`

### Declaration

    // C#
    public struct OracleIntervalYM : IComparable

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

    class OracleIntervalYMSample
    {
      static void Main()
      {
        OracleIntervalYM iYMMax = OracleIntervalYM.MaxValue;
        double totalYears = iYMMax.TotalYears;

        totalYears -= 1;
        OracleIntervalYM iYMMax_1 = new OracleIntervalYM(totalYears);

        // Calculate the difference
        OracleIntervalYM iYMDiff = iYMMax - iYMMax_1;

        // Prints "iYMDiff.ToString() = +000000001-00"
        Console.WriteLine("iYMDiff.ToString() = " + iYMDiff.ToString());
      }
    }

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleIntervalYM Members](IntervalYMMembers.md)

- [OracleIntervalYM Constructors](IntervalYMCtors.md)

- [OracleIntervalYM Static Fields](IntervalYMStaticFields.md)

- [OracleIntervalYM Static Methods](IntervalYMStaticMethods.md)

- [OracleIntervalYM Static Operators](IntervalYMStaticOperators.md)

- [OracleIntervalYM Type Conversions](IntervalYMTypeConversions.md)

- [OracleIntervalYM Properties](IntervalYMProperties.md)

- [OracleIntervalYM Methods](IntervalYMMethods.md)
