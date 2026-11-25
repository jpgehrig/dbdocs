This instance method searches for a binary pattern in the current instance of an `OracleBlob`.

### Declaration

    // C#
    public Int64 Search(byte[] val, int64 offset, int64 nth);

### Parameters

- `val`

  The binary pattern being searched for.

- `offset`

  The `0`-based offset (in bytes) starting from which the `OracleBlob` is searched.

- `nth`

  The specific occurrence (1-based) of the match for which the absolute offset (in bytes) is returned.

### Return Value

Returns the absolute `offset` of the start of the matched pattern (in bytes) for the `nth` occurrence of the match. Otherwise, `0` is returned.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

`ArgumentOutOfRangeException` - This exception is thrown if any of the following conditions exist:

- The `offset` is less than `0`.

- The `nth` is less than or equal to `0`.

- The `val`.`Length` is greater than `16383`.

- The `nth` is greater than or equal to `OracleBlob.MaxSize`.

- The `offset` is greater than or equal to `OracleBlob.MaxSize`.

### Remarks

The limit of the search pattern is 16383 bytes.

### Example

    // C#

    using System;
    using Oracle.DataAccess.Client;
    using Oracle.DataAccess.Types;

    class SearchSample
    {
      static void Main()
      {
        string constr = "User Id=scott;Password=tiger;Data Source=oracle";
        OracleConnection con = new OracleConnection(constr);
        con.Open();

        OracleBlob blob = new OracleBlob(con);

        // Write 7 bytes, starting at buffer offset 0
        byte[] buffer = new byte[7] {1, 2, 3, 4, 1, 2, 3};
        blob.Write(buffer, 0, 7);

        // Search for the 2nd occurrence of a byte pattern '23'
        // starting at offset 1 in the OracleBlob
        byte[] pattern = new byte[2] {2 ,3};
        long posFound = blob.Search(pattern, 1, 2);

        // Prints "posFound = 6"
        Console.WriteLine("posFound = " + posFound);

        blob.Close();
        blob.Dispose();

        con.Close();
        con.Dispose();
      }
    }

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleBlob Class](OracleBlobClass.md)

- [OracleBlob Members](BlobMembers.md)
