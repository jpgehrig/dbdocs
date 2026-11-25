This instance method reads a specified amount of characters from the current instance and populates the character array buffer.

### Declaration

    // C#
    public int Read(char[ ] buffer, int offset, int count);

### Parameters

- `buffer`

  The character array buffer that is populated.

- `offset`

  The offset (in characters) at which the buffer is populated.

- `count`

  The amount of characters to be read.

### Return Value

The return value indicates the number of characters read from the `CLOB`.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

`ArgumentOutOfRangeException` - This exception is thrown if any of the following conditions exist:

- The `offset` or the `count` is less than `0`.

- The `offset` is greater than or equal to the `buffer`.`Length`.

- The `offset` and the `count` together are greater than `buffer`.`Length`.

### Remarks

Handles all `CLOB` and `NCLOB` data as Unicode.

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

        OracleClob clob = new OracleClob(con);

        // Write 3 chars, starting at buffer offset 1
        char[] writeBuffer = new char[4] {'a', 'b', 'c', 'd'};
        clob.Write(writeBuffer, 1, 3);

        // Reset the Position (in bytes) for Read
        clob.Position = 2;

        // Read 2 chars into buffer starting at buffer offset 1
        char[] readBuffer = new char[4];
        int charsRead = clob.Read(readBuffer, 1, 2);

        // Prints "charsRead  = 2"
        Console.WriteLine("charsRead  = " + charsRead);

        // Prints "readBuffer =  cd "
        Console.Write("readBuffer = ");
        for(int index = 0; index <  readBuffer.Length; index++)
        {
          Console.Write(readBuffer[index]);
        }
        Console.WriteLine();

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
