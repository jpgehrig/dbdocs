Overrides `Stream`

This instance method reads a specified amount of bytes from the ODP.NET LOB instance and populates the `buffer`.

### Declaration

    // C#
    public override int Read(byte[] buffer, int offset, int count);

### Parameters

- `buffer`

  The byte array buffer to be populated.

- `offset`

  The starting offset (in bytes) at which the buffer is populated.

- `count`

  The amount of bytes to read.

### Return Value

The return value indicates the number of bytes read from the LOB.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

`ArgumentOutOfRangeException` - This exception is thrown if any of the following conditions exist:

- The `offset` or the `count` parameter is less than `0`.

- The `offset` is greater than or equal to the `buffer`.`Length`.

- The `offset` and the `count` together are greater than the `buffer`.`Length`.

### Remarks

The LOB data is read starting from the position specified by the `Position` property.

### Example

    // C#

    using System;
    using Oracle.DataAccess.Client;
    using Oracle.DataAccess.Types;

    class ReadSample
    {
      static void Main()
      {
        string constr = "User Id=scott;Password=tiger;Data Source=oracle";
        OracleConnection con = new OracleConnection(constr);
        con.Open();

        OracleBlob blob = new OracleBlob(con);

        // Write 3 bytes, starting at buffer offset 1
        byte[] writeBuffer = new byte[4] {1, 2, 3, 4};
        blob.Write(writeBuffer, 1, 3);

        // Reset the Position for Read
        blob.Position = 1;

        // Read 2 bytes into buffer starting at buffer offset 1
        byte[] readBuffer = new byte[4];
        int bytesRead = blob.Read(readBuffer, 1, 2);

        // Prints "bytesRead  = 2"
        Console.WriteLine("bytesRead  = " + bytesRead);

        // Prints "readBuffer = 0340"
        Console.Write("readBuffer = ");
        for(int index = 0; index <  readBuffer.Length; index++)
        {
          Console.Write(readBuffer[index]);
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
