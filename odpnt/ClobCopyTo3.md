This instance method copies data from the current `OracleClob` instance to the provided `OracleClob` object with the specified source offset, destination offset, and character amounts.

### Declaration

    // C#
    public Int64 CopyTo(Int64 src_offset,OracleClob obj,Int64 dst_offset,
        Int64 amount);

### Parameters

- `src_offset`

  The offset (in characters) in the current instance, from which the data is read.

- `obj`

  The `OracleClob` object to which the data is copied.

- `dst_offset`

  The offset (in characters) at which the `OracleClob` object is copied.

- `amount`

  The amount of data to be copied.

### Return Value

The return value is the amount copied.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The parameter has a different connection than the object, `OracleConnection` is not opened, or `OracleConnection` has been reopened.

`ArgumentOutOfRangeException` - The `src_offset`, the `dst_offset`, or the `amount` parameter is less than `0`.

### Remarks

If the `dst_offset` is beyond the end of the `OracleClob` data, spaces are written into the `OracleClob` until the `dst_offset` is met.

The offsets are `0`-based. No character conversion is performed by this operation.

The provided object and the current instance must be using the same connection, that is, the same `OracleConnection` object.

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

        OracleClob clob1 = new OracleClob(con);
        OracleClob clob2 = new OracleClob(con);

        // Write 4 chars, starting at buffer offset 0
        char[] buffer = new char[4] {'a', 'b', 'c', 'd'};
        clob1.Write(buffer, 0, 4);

        // Copy 2 chars from char 0 of clob1 to char 1 of clob2
        clob1.CopyTo(0, clob2, 1, 2);

        //Prints "clob2.Value =  ab"
        Console.WriteLine("clob2.Value = " + clob2.Value);

        clob1.Close();
        clob1.Dispose();

        clob2.Close();
        clob2.Dispose();

        con.Close();
        con.Dispose();
      }
    }

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleClob Class](OracleClobClass.md)

- [OracleClob Members](ClobMembers.md)
