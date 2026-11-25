This instance method creates a copy of an `OracleBlob` object.

### Declaration

    // C#
    public object Clone();

### Return Value

An `OracleBlob` object.

### Implements

`ICloneable`

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

### Remarks

The cloned object has the same property values as that of the object being cloned.

### Example

    // C#

    using System;
    using Oracle.DataAccess.Client;
    using Oracle.DataAccess.Types;

    class CloneSample
    {
      static void Main()
      {
        string constr = "User Id=scott;Password=tiger;Data Source=oracle";
        OracleConnection con = new OracleConnection(constr);
        con.Open();

        OracleBlob blob1 = new OracleBlob(con);

        // Prints "blob1.Position = 0"
        Console.WriteLine("blob1.Position = " + blob1.Position);

        // Set the Position before calling Clone()
        blob1.Position = 1;

        // Clone the OracleBlob
        OracleBlob blob2 = (OracleBlob)blob1.Clone();

        // Prints "blob2.Position = 1"
        Console.WriteLine("blob2.Position = " + blob2.Position);

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
