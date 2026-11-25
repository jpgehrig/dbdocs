This instance method appends data from the supplied byte array buffer to the end of the current `OracleBlob` instance.

### Declaration

    // C#
    public void Append(byte[] buffer, int offset, int count);

### Parameters

- `buffer`

  An array of bytes.

- `offset`

  The zero-based byte offset in the buffer from which data is read.

- `count`

  The number of bytes to be appended.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

### Example

    // C#

    using System;
    using Oracle.DataAccess.Client;
    using Oracle.DataAccess.Types;

    class AppendSample
    {
      static void Main()
      {
        string constr = "User Id=scott;Password=tiger;Data Source=oracle";
        OracleConnection con = new OracleConnection(constr);
        con.Open();

        OracleBlob blob = new OracleBlob(con);

        // Append 2 bytes {4, 5} to the OracleBlob
        byte[] buffer = new byte[3] {4, 5, 6};
        blob.Append(buffer, 0, 2);

        byte[] appendBuffer = blob.Value;

        // Prints "appendBuffer = 45"
        Console.Write("appendBuffer = ");
        for(int index = 0; index < appendBuffer.Length; index++)
        {
          Console.Write(appendBuffer[index]);
        }
        Console.WriteLine();

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
