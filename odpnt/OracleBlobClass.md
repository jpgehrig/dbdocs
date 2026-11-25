An `OracleBlob` object is an object that has a reference to `BLOB` data. It provides methods for performing operations on `BLOB`s.

### Class Inheritance

`System.Object`

`  System.MarshalByRefObject`

`    System.IO.Stream`

`      Oracle.DataAccess.Types.OracleBlob`

### Declaration

    // C#
    public sealed class OracleBlob : Stream, ICloneable, INullable

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

    class OracleBlobSample
    {
      static void Main()
      {
        string constr = "User Id=scott;Password=tiger;Data Source=oracle";
        OracleConnection con = new OracleConnection(constr);
        con.Open();

        OracleBlob blob = new OracleBlob(con);

        // Write 4 bytes from writeBuffer, starting at buffer offset 0
        byte[] writeBuffer = new byte[4] {1, 2, 3, 4};
        blob.Write(writeBuffer, 0, 4);

        // Append first 2 bytes from writeBuffer {1, 2} to the oracleBlob
        blob.Append(writeBuffer, 0, 2);

        // Prints "blob.Length  = 6"
        Console.WriteLine("blob.Length  = " + blob.Length);

        // Reset the Position for the Read
        blob.Position = 0;

        // Read 6 bytes into readBuffer, starting at buffer offset 0
        byte[] readBuffer = new byte[6];
        int bytesRead = blob.Read(readBuffer, 0, 6);

        // Prints "bytesRead    = 6"
        Console.WriteLine("bytesRead    = " + bytesRead);

        // Prints "readBuffer   = 123412"
        Console.Write("readBuffer   = ");
        for(int index = 0; index <  readBuffer.Length; index++)
        {
          Console.Write(readBuffer[index]);
        }
        Console.WriteLine();

        // Search for the 2nd occurrence of a byte pattern '12'
        // starting from byte offset 0 in the OracleBlob
        byte[] pattern = new byte[2] {1, 2};
        long posFound = blob.Search(pattern, 0, 2);

        // Prints "posFound     = 5"
        Console.WriteLine("posFound     = " + posFound);

        // Erase 4 bytes of data starting at byte offset 1
        // Sets bytes to zero
        blob.Erase(1, 4);

        byte[] erasedBuffer = blob.Value;

        //Prints "erasedBuffer = 100002"
        Console.Write("erasedBuffer = ");
        for(int index = 0; index < erasedBuffer.Length; index++)
        {
          Console.Write(erasedBuffer[index]);
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

- [OracleBlob Members](BlobMembers.md)

- [OracleBlob Constructors](BlobCtors.md)

- [OracleBlob Static Fields](BlobStaticFields.md)

- [OracleBlob Static Methods](BlobStaticMethods.md)

- [OracleBlob Instance Properties](BlobInstanceProperties.md)

- [OracleBlob Instance Methods](BlobInstanceMethods.md)
