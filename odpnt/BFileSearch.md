This instance method searches for a binary pattern in the current instance of an `OracleBFile`.

### Declaration

    // C#
    public int Search(byte[] val, Int64 offset, Int64 nth);

### Parameters

- `val`

  The binary pattern being searched for.

- `offset`

  The `0`-based offset (in bytes) starting from which the `OracleBFile` is searched.

- `nth`

  The specific occurrence (`1`-based) of the match for which the offset is returned.

### Return Value

Returns the absolute `offset` of the start of the matched pattern (in bytes) for the `nth` occurrence of the match. Otherwise, `0` is returned.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

`ArgumentOutOfRangeException` - Either the `offset` is less than `0` or `nth` is less than or equal to `0` or `val`.`Length` is greater than `16383` or `nth` is greater than or equal to `OracleBFile.MaxSize` or `offset` is greater than or equal to `OracleBFile.MaxSize`.

### Remarks

The limit of the search pattern is 16383 bytes.

### Example

    // Database Setup, if you have not done so yet.
    /* Log on as DBA (SYS or SYSTEM) that has CREATE ANY DIRECTORY privilege.

    CREATE OR REPLACE DIRECTORY MYDIR AS 'C:\TEMP';

    */

    // C#

    using System;
    using Oracle.DataAccess.Client;
    using Oracle.DataAccess.Types;

    class SearchSample
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

        // Search for the 2nd occurrence of a byte pattern {66,67}
        // starting from byte offset 1 in the OracleBFile
        byte[] pattern = new byte[2] {66, 67};
        long posFound = bFile.Search(pattern, 1, 2);

        // Prints "posFound = 6"
        Console.WriteLine("posFound = " + posFound);

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
