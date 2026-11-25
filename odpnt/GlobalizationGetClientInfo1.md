This method returns an `OracleGlobalization` instance that represents the globalization settings of the local computer.

### Declaration

    // C#
    public static OracleGlobalization GetClientInfo();

### Return Value

An `OracleGlobalization` instance.

### Example

    // C#

    using System;
    using Oracle.DataAccess.Client;

    class GetClientInfoSample
    {
      static void Main()
      {
        // Get client's globalization info
        OracleGlobalization glob = OracleGlobalization.GetClientInfo();

        // Prints "glob.Language = AMERICAN"
        Console.WriteLine("glob.Language = " + glob.Language);

        glob.Dispose();
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleGlobalization Class](OracleGlobalizationClass.md)

- [OracleGlobalization Members](GlobalizationMembers.md)
