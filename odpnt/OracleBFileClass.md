An `OracleBFile` is an object that has a reference to `BFILE` data. It provides methods for performing operations on `BFILE`s.

**Note:**

`OracleBFile` is supported for applications running against Oracle8.x and later.

### Class Inheritance

`System.Object`

`  System.MarshalByRefObject`

`    System.IO.Stream`

             `Oracle.DataAccess.Types.OracleBFile`

### Declaration

    // C#
    public sealed class OracleBFile : Stream, ICloneable, INullable

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

`OracleBFile` is supported for applications running against Oracle8.x and later.

### Example

    // Database Setup, if you have not done so yet.
    /* Log on as DBA (SYS or SYSTEM) that has CREATE ANY DIRECTORY privilege.

    CREATE OR REPLACE DIRECTORY MYDIR AS 'C:\TEMP';

    */

    // C#

    using System;
    using Oracle.DataAccess.Client;
    using Oracle.DataAccess.Types;

    class OracleBFileSample
    {
    static void Main()
    {
        // Create MYDIR directory object as indicated previously and create a file
        // MyFile.txt with the text ABCDABC under C:\TEMP directory.
        // Note that the byte representation of the ABCDABC is 65666768656667

        string constr = "User Id=scott;Password=tiger;Data Source=oracle";
        OracleConnection con = new OracleConnection(constr);
        con.Open();

        OracleBFile bFile = new OracleBFile(con, "MYDIR", "MyFile.txt");

        // Open the OracleBFile
        bFile.OpenFile();

        // Read 7 bytes into readBuffer, starting at buffer offset 0
        byte[] readBuffer = new byte[7];
        int bytesRead = bFile.Read(readBuffer, 0, 7);

        // Prints "bytesRead  = 7"
        Console.WriteLine("bytesRead  = " + bytesRead);

        // Prints "readBuffer = 65666768656667"
        Console.Write("readBuffer = ");
        for(int index = 0; index <  readBuffer.Length; index++)
        {
          Console.Write(readBuffer[index]);
        }
        Console.WriteLine();

        // Search for the 2nd occurrence of a byte pattern {66,67}
        // starting from byte offset 1 in the OracleBFile
        byte[] pattern = new byte[2] {66, 67};
        long posFound = bFile.Search(pattern, 1, 2);

        // Prints "posFound   = 6"
        Console.WriteLine("posFound   = " + posFound);

        // Close the OracleBFile
        bFile.CloseFile();

        bFile.Close();
        bFile.Dispose();

        con.Close();
        con.Dispose();
    }
    }

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleBFile Members](BFileMembers.md)

- [OracleBFile Constructors](BFileCtors.md)

- [OracleBFile Static Fields](BFileStaticFields.md)

- [OracleBFile Static Methods](BFileStaticMethods.md)

- [OracleBFile Instance Properties](BFileProperties.md)

- [OracleBFile Instance Methods](BFileInstanceMethods.md)
