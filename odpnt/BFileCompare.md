This instance method compares data referenced by the two `OracleBFile`s.

### Declaration

    // C#
    public int Compare(Int64 src_offset, OracleBFile obj, Int64 dst_offset,
        Int64 amount);

### Parameters

- `src_offset`

  The offset of the current instance.

- `obj`

  The provided `OracleBFile` object.

- `dst_offset`

  The offset of the `OracleBFile` object.

- `amount`

  The number of bytes to compare.

### Return Value

Returns a number that is:

- Less than zero: if the `BFILE` data of the current instance is less than that of the provided `BFILE` data.

- Zero: if both the `BFILE`s store the same data.

- Greater than zero: if the `BFILE` data of the current instance is greater than that of the provided `BFILE` data.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

`ArgumentOutOfRangeException` - The `src_offset`, the `dst_offset`, or the `amount` is less than `0`.

### Remarks

The provided object and the current instance must be using the same connection, that is, the same `OracleConnection` object.

The `BFILE` needs to be opened using `OpenFile` before the operation.

### Example

    // Database Setup, if you have not done so yet.
    /* Log on as DBA (SYS or SYSTEM) that has CREATE ANY DIRECTORY privilege.

    CREATE OR REPLACE DIRECTORY MYDIR AS 'C:\TEMP';

    */

    // C#

    using System;
    using Oracle.DataAccess.Client;
    using Oracle.DataAccess.Types;

    class CompareSample
    {
      static void Main()
      {
        // Create MYDIR directory object as indicated previously and create a file
        // MyFile.txt with the text ABCDABC under C:\TEMP directory.
        // Note that the byte representation of the ABCDABC is 65666768656667

        string constr = "User Id=scott;Password=tiger;Data Source=oracle";
        OracleConnection con = new OracleConnection(constr);
        con.Open();

        OracleBFile bFile1 = new OracleBFile(con, "MYDIR", "MyFile.txt");
        OracleBFile bFile2 = new OracleBFile(con, "MYDIR", "MyFile.txt");

        // Open the OracleBFiles
        bFile1.OpenFile();
        bFile2.OpenFile();

        // Compare 2 bytes from the 1st byte of bFile1 and
        // the 5th byte of bFile2 onwards
        int result = bFile1.Compare(1, bFile2, 5, 2);

        // Prints "result = 0" (Indicates the data is identical)
        Console.WriteLine("result = " + result);

        // Close the OracleBFiles
        bFile1.CloseFile();
        bFile2.CloseFile();

        bFile1.Close();
        bFile1.Dispose();

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
