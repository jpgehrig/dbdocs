Overrides `Stream`

This instance method writes the supplied buffer into the `OracleBlob`.

### Declaration

    // C#
    public override void Write(byte[ ] buffer, int offset, int count);

### Parameters

- `buffer`

  The byte array `buffer` that provides the data.

- `offset`

  The `0`-based offset (in bytes) from which the `buffer` is read.

- `count`

  The amount of data (in bytes) that is to be written into the `OracleBlob`.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

`ArgumentOutOfRangeException` - This exception is thrown if any of the following conditions exist:

- The `offset` or the `count` is less than `0`.

- The `offset` is greater than or equal to the `buffer`.`Length`.

- The `offset` and the `count` together are greater than `buffer`.`Length`.

### Remarks

Destination `offset` in the `OracleBlob` can be specified by the `Position` property.

### Example

    // C#

    using System;
    using Oracle.DataAccess.Client;
    using Oracle.DataAccess.Types;

    class WriteSample
    {
      static void Main()
      {
        string constr = "User Id=scott;Password=tiger;Data Source=oracle";
        OracleConnection con = new OracleConnection(constr);
        con.Open();

        OracleBlob blob = new OracleBlob(con);

        // Set the Position for the Write
        blob.Position = 0;

        // Begin ChunkWrite to improve performance
        // Index updates occur only once after EndChunkWrite
        blob.BeginChunkWrite();

        // Write to the OracleBlob in 5 chunks of 2 bytes each
        byte[] b = new byte[2] {1, 2};
        for(int index = 0; index < 5; index++)
        {
          blob.Write(b, 0, b.Length);
        }
        blob.EndChunkWrite();

        byte[] chunkBuffer = blob.Value;

        // Prints "chunkBuffer = 1212121212"
        Console.Write("chunkBuffer = ");
        for(int index = 0; index < chunkBuffer.Length; index++)
        {
          Console.Write(chunkBuffer[index]);
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
