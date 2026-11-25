Overrides `Stream`

This instance method reads a specified amount of bytes from the `OracleBFile` instance and populates the `buffer`.

### Declaration

    // C#
    public override int Read(byte[] buffer, int offset, int count);

### Parameters

- `buffer`

  The byte array buffer to be populated.

- `offset`

  The offset of the byte array buffer to be populated.

- `count`

  The amount of bytes to read.

### Return Value

The return value indicates the number of bytes read from the `BFILE`, that is, the external LOB.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

`ArgumentOutOfRangeException` - Either the `offset` or the `count` parameter is less than `0` or the `offset` is greater than or equal to the `buffer`.`Length` or the `offset` and the `count` together are greater than `buffer`.`Length`.

### Remarks

The LOB data is read starting from the position specified by the `Position` property.

### Example

    // Database Setup, if you have not done so yet.
    /* Log on as DBA (SYS or SYSTEM) that has CREATE ANY DIRECTORY privilege.

    CREATE OR REPLACE DIRECTORY MYDIR AS 'C:\TEMP';

    */

    // C#

    using System;
    using Oracle.DataAccess.Client;
    using Oracle.DataAccess.Types;

    class ReadSample
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
