This instance method copies data from the current `OracleBlob` instance to the provided `OracleBlob` object with the specified source offset, destination offset, and character amounts.

### Declaration

    // C#
    public Int64 CopyTo(Int64 src_offset,OracleBlob obj,Int64 dst_offset,
       Int64 amount);

### Parameters

- `src_offset`

  The offset (in bytes) in the current instance, from which the data is read.

- `obj`

  The `OracleBlob` object to which the data is copied.

- `dst_offset`

  The offset (in bytes) at which the `OracleBlob` object is copied.

- `amount`

  The amount of data to be copied.

### Return Value

The return value is the amount copied.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The parameter has a different connection than the object, `OracleConnection` is not opened, or `OracleConnection` has been reopened.

`ArgumentOutOfRangeException` - The `src_offset`, the `dst_offset`, or the `amount` parameter is less than `0`.

### Remarks

If the `dst_offset` is beyond the end of the `OracleBlob` data, spaces are written into the `OracleBlob` until the `dst_offset` is met.

The offsets are `0`-based. No character conversion is performed by this operation.

The provided object and the current instance must be using the same connection; that is, the same `OracleConnection` object.

### Example

    // C#

    using System;
    using Oracle.DataAccess.Client;
    using Oracle.DataAccess.Types;

    class CopyToSample
    {
      static void Main()
      {
        string constr = "User Id=scott;Password=tiger;Data Source=oracle";
        OracleConnection con = new OracleConnection(constr);
        con.Open();

        OracleBlob blob1 = new OracleBlob(con);
        OracleBlob blob2 = new OracleBlob(con);

        // Write 4 bytes, starting at buffer offset 0
        byte[] buffer = new byte[4] {1, 2, 3, 4};
        blob1.Write(buffer, 0, 4);

        // Copy 2 bytes from byte 0 of blob1 to byte 1 of blob2
        blob1.CopyTo(0, blob2, 1, 2);

        byte[] copyBuffer = blob2.Value;

        //Prints "Value = 012"
        Console.Write("Value = ");
        for(int index = 0; index < copyBuffer.Length; index++)
        {
          Console.Write(copyBuffer[index]);
        }
        Console.WriteLine();

        blob1.Close();
        blob1.Dispose();

        blob2.Close();
        blob2.Dispose();

        con.Close();
        con.Dispose();
      }
    }

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleBlob Class](OracleBlobClass.md)

- [OracleBlob Members](BlobMembers.md)
