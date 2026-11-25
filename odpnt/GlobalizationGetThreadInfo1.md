This method returns an `OracleGlobalization` instance of the current thread.

### Declaration

    // C#
    public static OracleGlobalization GetThreadInfo();

### Return Value

An `OracleGlobalization` instance.

### Remarks

Initially, `GetThreadInfo()` returns an `OracleGlobalization` object that has the same property values as that returned by `GetClientInfo()`, unless the application changes it by invoking `SetThreadInfo()`.

### Example

    // C#

    using System;
    using Oracle.DataAccess.Client;

    class GetThreadInfoSample
    {
      static void Main()
      {
        // Get thread's globalization info
        OracleGlobalization glob = OracleGlobalization.GetThreadInfo();

        // Prints "glob.Language = AMERICAN"
        Console.WriteLine("glob.Language = " + glob.Language);

        // Get thread's globalization info using overloaded
        OracleGlobalization.GetThreadInfo(glob);

        // Prints "glob.Language = AMERICAN"
        Console.WriteLine("glob.Language = " + glob.Language);

        glob.Dispose();
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleGlobalization Class](OracleGlobalizationClass.md)

- [OracleGlobalization Members](GlobalizationMembers.md)
