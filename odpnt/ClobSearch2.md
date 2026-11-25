This instance method searches for a character pattern in the current instance of `OracleClob`.

### Declaration

    // C#
    public Int64 Search(char [ ] val, Int64 offset, Int64 nth);

### Parameters

- `val`

  The Unicode string being searched for.

- `offset`

  The `0`-based offset (in characters) starting from which the `OracleClob` is searched.

- `nth`

  The specific occurrence (`1`-based) of the match for which the absolute offset (in characters) is returned.

### Return Value

Returns the absolute `offset` of the start of the matched pattern (in characters) for the `nth` occurrence of the match. Otherwise, `0` is returned.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

`ArgumentOutOfRangeException` - This exception is thrown if any of the following conditions exist:

- The `offset` is less than `0`.

- The `nth` is less than or equal to `0`.

- The `val`.`Length` doubled is greater than `16383`.

- The `nth` is greater than or equal to `OracleClob.MaxSize`.

- The `offset` is greater than or equal to `OracleClob.MaxSize`.

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

        OracleClob clob = new OracleClob(con);

        // Write 7 chars, starting at buffer offset 0
        char[] buffer = new char[7] {'a', 'b', 'c', 'd', 'a', 'b', 'c'};
        clob.Write(buffer, 0, 7);

        // Search for the 2nd occurrence of a char pattern 'bc'
        // starting at offset 1 in the OracleBlob
        char[] pattern = new char[2] {'b', 'c'};
        long posFound = clob.Search(pattern, 1, 2);

        // Prints "posFound = 6"
        Console.WriteLine("posFound = " + posFound);

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
