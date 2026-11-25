This method refreshes the provided `OracleGlobalization` object with the globalization settings of the local computer.

### Declaration

    // C#
    public static void GetClientInfo(OracleGlobalization oraGlob);

### Parameters

- `oraGlob`

  The `OracleGlobalization` object being updated.

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

        // Get client's globalization info using overload
        OracleGlobalization.GetClientInfo(glob);

        // Prints "glob.Language = AMERICAN"
        Console.WriteLine("glob.Language = " + glob.Language);

        glob.Dispose();
    }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleGlobalization Class](OracleGlobalizationClass.md)

- [OracleGlobalization Members](GlobalizationMembers.md)
