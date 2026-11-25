This instance method creates a copy of an `OracleClob` object.

### Declaration

    // C#
    public object Clone();

### Return Value

An `OracleClob` object.

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

        OracleClob clob1 = new OracleClob(con);

        // Prints "clob1.Position = 0"
        Console.WriteLine("clob1.Position = " + clob1.Position);

        // Set the Position before calling Clone()
        clob1.Position = 1;

        // Clone the OracleClob
        OracleClob clob2 = (OracleClob)clob1.Clone();

        // Prints "clob2.Position = 1"
        Console.WriteLine("clob2.Position = " + clob2.Position);

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
