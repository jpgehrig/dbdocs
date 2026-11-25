This method sets Oracle globalization parameters to the current thread.

### Declaration

    // C#
    public static void SetThreadInfo(OracleGlobalization oraGlob);

### Parameters

- `oraGlob`

  An `OracleGlobalization` object.

### Remarks

Any .NET string conversions to and from ODP.NET Types, as well as ODP.NET Type constructors, use the globalization property values where applicable. For example, when constructing an `OracleDate` structure from a .NET string, that string is expected to be in the format specified by the `OracleGlobalization`.`DateFormat` property of the thread.

### Example

    // C#

    using System;
    using Oracle.DataAccess.Client;

    class SetThreadInfoSample
    {
      static void Main()
      {
        // Get thread's globalization info
        OracleGlobalization glob1 = OracleGlobalization.GetThreadInfo();

        // Prints "glob1.Language = AMERICAN"
        Console.WriteLine("glob1.Language = " + glob1.Language);

        // Set language on thread's globalization info
        glob1.Language = "FRENCH";
        OracleGlobalization.SetThreadInfo(glob1);
        OracleGlobalization glob2 = OracleGlobalization.GetThreadInfo();

        // Prints "glob2.Language = FRENCH"
        Console.WriteLine("glob2.Language = " + glob2.Language);

        glob1.Dispose();
        glob2.Dispose();
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleGlobalization Class](OracleGlobalizationClass.md)

- [OracleGlobalization Members](GlobalizationMembers.md)
