This instance method creates a copy of an `OracleBFile` object.

### Declaration

    // C#
    public object Clone();

### Return Value

An `OracleBFile` object.

### Implements

`ICloneable`

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

### Remarks

The cloned object has the same property values as that of the object being cloned.

### Example

    // Database Setup, if you have not done so yet.
    /* Log on as DBA (SYS or SYSTEM) that has CREATE ANY DIRECTORY privilege.

    CREATE OR REPLACE DIRECTORY MYDIR AS 'C:\TEMP';

    */

    // C#

    using System;
    using Oracle.DataAccess.Client;
    using Oracle.DataAccess.Types;

    class CloneSample
    {
      static void Main()
      {
        // Create MYDIR directory object as indicated above and create a file
        // MyFile.txt with the text ABCDABC under C:\TEMP directory.
        // Note that the byte representation of the ABCDABC is 65666768656667

        string constr = "User Id=scott;Password=tiger;Data Source=oracle";
        OracleConnection con = new OracleConnection(constr);
        con.Open();

        OracleBFile bFile1 = new OracleBFile(con, "MYDIR", "MyFile.txt");

        // Open the OracleBFile
        bFile1.OpenFile();

        // Prints "bFile1.Position = 0"
        Console.WriteLine("bFile1.Position = " + bFile1.Position);

        // Set the Position before calling Clone()
        bFile1.Position = 1;

        // Clone the OracleBFile
        OracleBFile bFile2 = (OracleBFile) bFile1.Clone();

        // Open the OracleBFile
        bFile2.OpenFile();

        // Prints "bFile2.Position = 1"
        Console.WriteLine("bFile2.Position = " + bFile2.Position);

        // Close the OracleBFile
        bFile1.CloseFile();

        bFile1.Close();
        bFile1.Dispose();

        // Close the Cloned OracleBFile
        bFile2.CloseFile();

        bFile2.Close();
        bFile2.Dispose();

        con.Close();
        con.Dispose();
      }
    }

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleBFile Class](OracleBFileClass.md)

- [OracleBFile Members](BFileMembers.md)
