This instance method writes data from the provided character array buffer into the `OracleClob`.

### Declaration

    // C#
    public void Write(char[ ] buffer, int offset, int count);

### Parameters

- `buffer`

  The character array buffer that is written to the `OracleClob`.

- `offset`

  The offset (in characters) from which the `buffer` is read.

- `count`

  The amount (in characters) from the buffer that is to be written into the `OracleClob`.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

`ArgumentOutOfRangeException` - This exception is thrown if any of the following conditions exist:

- The `offset` or the `count` is less than `0`.

- The `offset` is greater than or equal to the `buffer`.`Length`.

- The `offset` and the `count` together are greater than `buffer`.`Length`.

- The `Position` is not even.

### Remarks

Handles all `CLOB` and `NCLOB` data as Unicode.

The LOB data is read starting from the position specified by the `Position` property.

If necessary, proper data conversion is carried out from the client character set to the database character set.

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

        OracleClob clob = new OracleClob(con);

        // Set the Position for the Write;
        clob.Position = 0;

        // Begin ChunkWrite to improve performance
        // Index updates occur only once after EndChunkWrite
        clob.BeginChunkWrite();

        // Write to the OracleClob in 5 chunks of 2 chars each
        char[] c = new char[2] {'a', 'b'};
        for (int index = 0; index < 5; index++)
        {
          clob.Write(c, 0, c.Length);
        }
        clob.EndChunkWrite();

        // Prints "clob.Value = ababababab"
        Console.WriteLine("clob.Value = " + clob.Value);

        clob.Close();
        clob.Dispose();

        con.Close();
        con.Dispose();
      }
    }

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleClob Class](OracleClobClass.md)

- [OracleClob Members](ClobMembers.md)
