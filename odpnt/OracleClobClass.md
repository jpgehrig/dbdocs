An `OracleClob` is an object that has a reference to `CLOB` data. It provides methods for performing operations on `CLOB`s.

**Note:**

The `OracleClob` object uses the client side character set when retrieving or writing `CLOB` data using a .NET Framework byte array.

### Class Inheritance

`System.Object`

`  System.MarshalByRefObject`

`    System.IO.Stream`

`      Oracle.DataAccess.Types.OracleClob`

### Declaration

    // C#
    public sealed class OracleClob : Stream, ICloneable, INullable

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  | ODP.NET, Managed Driver           | ODP.NET Core                      |
|:---------------|:---------------------------|:----------------------------------|:----------------------------------|
| Assembly       | `Oracle.DataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` | `Oracle.ManagedDataAccess.Client` | `Oracle.ManagedDataAccess.Client` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7         | 4.5, 4.6, 4.7                     | 4.6.1 or higher                   |
| .NET Core      | \-                         | \-                                | 2.1 or higher                     |

### Thread Safety

All public static methods are thread-safe, although instance methods do not guarantee thread safety.

### Example

    // C#

    using System;
    using Oracle.DataAccess.Client;
    using Oracle.DataAccess.Types;

    class OracleClobSample
    {
      static void Main()
      {
        string constr = "User Id=scott;Password=tiger;Data Source=oracle";
        OracleConnection con = new OracleConnection(constr);
        con.Open();

        OracleClob clob = new OracleClob(con);

        // Write 4 chars from writeBuffer, starting at buffer offset 0
        char[] writeBuffer = new char[4] {'a', 'b', 'c', 'd'};
        clob.Write(writeBuffer, 0, 4);

        // Append first 2 chars from writeBuffer {'a', 'b'} to the oracleClob
        clob.Append(writeBuffer, 0, 2);

        // Prints "clob.Length  = 12"
        Console.WriteLine("clob.Length  = " + clob.Length);

        // Reset the Position for the Read
        clob.Position = 0;

        // Read 6 chars into readBuffer, starting at buffer offset 0
        char[] readBuffer = new char[6];
        int charsRead = clob.Read(readBuffer, 0, 6);

        // Prints "charsRead    = 6"
        Console.WriteLine("charsRead    = " + charsRead);

        // Prints "readBuffer   = abcdab"
        Console.Write("readBuffer   = ");
        for(int index = 0; index <  readBuffer.Length; index++)
        {
          Console.Write(readBuffer[index]);
        }
        Console.WriteLine();

        // Search for the 2nd occurrence of a char pattern 'ab'
        // starting from char offset 0 in the OracleClob
        char[] pattern = new char[2] {'a', 'b'};
        long posFound = clob.Search(pattern, 0, 2);

        // Prints "posFound     = 5"
        Console.WriteLine("posFound     = " + posFound);

        // Erase 4 chars of data starting at char offset 1
        // Sets chars to ''
        clob.Erase(1, 4);

        //Prints "clob.Value   = a    b"
        Console.WriteLine("clob.Value   = " + clob.Value);

        clob.Close();
        clob.Dispose();

        con.Close();
        con.Dispose();
      }
    }

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleClob Members](ClobMembers.md)

- [OracleClob Constructors](ClobCtors.md)

- [OracleClob Static Fields](ClobStaticFields.md)

- [OracleClob Static Methods](ClobStaticMethods.md)

- [OracleClob Instance Properties](ClobInstanceProperties.md)

- [OracleClob Instance Methods](ClobInstanceMethods.md)
