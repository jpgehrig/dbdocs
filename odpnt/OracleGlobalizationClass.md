The `OracleGlobalization` class is used to obtain and set the Oracle globalization settings of the session, thread, and local computer (read-only).

Class Inheritance

`System.Object`

`  Oracle.DataAccess.Client.OracleGlobalization`

### Declaration

    public sealed class OracleGlobalization : ICloneable, IDisposable

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

An exception is thrown for invalid property values. All newly set property values are validated, except the `TimeZone` property.

Changing the `OracleGlobalization` object properties does not change the globalization settings of the session or the thread. Either the `SetSessionInfo` method of the `OracleConnection` object or the `SetThreadInfo` method of the `OracleGlobalization` object must be called to alter the session's and thread's globalization settings, respectively.

### Example

    // C#

    using System;
    using Oracle.DataAccess.Client;

    class OracleGlobalizationSample
    {
      static void Main()
      {
        // Get thread's globalization info
        OracleGlobalization glob = OracleGlobalization.GetThreadInfo();

        // Prints "glob.Language = AMERICAN"
        Console.WriteLine("glob.Language = " + glob.Language);

        // Set language on thread's globalization info
        glob.Language = "FRENCH";
        OracleGlobalization.SetThreadInfo(glob);
        OracleGlobalization.GetThreadInfo(glob);

        // Prints "glob.Language = FRENCH"
        Console.WriteLine("glob.Language = " + glob.Language);

        glob.Dispose();
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleGlobalization Members](GlobalizationMembers.md)

- [OracleGlobalization Static Methods](GlobalizationStaticMethods.md)

- [OracleGlobalization Properties](GlobalizationProperties.md)

- [OracleGlobalization Public Methods](GlobalizationPublicMethods.md)

- [Oracle Database SQL Language Reference](../sqlrf/Format-Models.md)

- [Oracle Database Globalization Support Guide](../nlspg/datetime-data-types-and-time-zone-support.md)
