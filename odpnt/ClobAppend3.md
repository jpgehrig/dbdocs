This instance method appends data from the supplied character array buffer to the end of the current `OracleClob` instance, starting at the offset (in characters) of the supplied character buffer.

### Declaration

    // C#
    public void Append(char[] buffer, int offset, int count);

### Parameters

- `buffer`

  An array of characters.

- `offset`

  The zero-based offset (in characters) in the buffer from which data is read.

- `count`

  The number of characters to be appended.

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

        OracleClob clob = new OracleClob(con);

        // Append 2 chars {'d', 'e'} to the OracleClob
        char[] buffer = new char[3] {'d', 'e', 'f'};
        clob.Append(buffer, 0, 2);

        // Prints "clob.Value = de"
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
