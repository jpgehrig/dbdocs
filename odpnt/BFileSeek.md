Overrides `Stream`

This instance method sets the position on the current LOB stream.

### Declaration

    // C#
    public override Int64 Seek(Int64 offset, SeekOrigin origin);

### Parameters

- `offset`

  A byte offset relative to origin.

- `origin`

  A value of type `System.IO.SeekOrigin` indicating the reference point used to obtain the new position.

### Return Value

Returns an `Int64` that indicates the position.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

### Remarks

If `offset` is negative, the new position precedes the position specified by `origin` by the number of bytes specified by `offset`.

If `offset` is zero, the new position is the position specified by `origin`.

If `offset` is positive, the new position follows the position specified by `origin` by the number of bytes specified by `offset`.

`SeekOrigin.Begin` specifies the beginning of a stream.

`SeekOrigin.Current` specifies the current position within a stream.

`SeekOrigin.End` specifies the end of a stream.

### Example

    // Database Setup, if you have not done so yet.
    /* Log on as DBA (SYS or SYSTEM) that has CREATE ANY DIRECTORY privilege.

    CREATE OR REPLACE DIRECTORY MYDIR AS 'C:\TEMP';

    */

    // C#

    using System;
    using System.IO;
    using Oracle.DataAccess.Client;
    using Oracle.DataAccess.Types;

    class SeekSample
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

        // Set the Position to 2 with respect to SeekOrigin.Begin
        long newPosition = bFile.Seek(2, SeekOrigin.Begin);

        // Prints "newPosition     = 2"
        Console.WriteLine("newPosition     = " + newPosition);

        // Prints "bFile.Position  = 2"
        Console.WriteLine("bFile.Position  = " + bFile.Position);

        // Read 2 bytes into readBuffer, starting at buffer offset 1
        byte[] readBuffer = new byte[4];
        int bytesRead = bFile.Read(readBuffer, 1, 2);

        // Prints "bytesRead       = 2"
        Console.WriteLine("bytesRead       = " + bytesRead);

        // Prints "readBuffer      = 067680"
        Console.Write("readBuffer      = ");
        for(int index = 0; index <  readBuffer.Length; index++)
        {
          Console.Write(readBuffer[index]);
        }
        Console.WriteLine();

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

- [OracleBFile Class](OracleBFileClass.md)

- [OracleBFile Members](BFileMembers.md)
