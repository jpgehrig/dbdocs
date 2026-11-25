This method creates a copy of an `OracleConnection` object.

### Declaration

    // C#
    public object Clone();

### Return Value

An `OracleConnection` object.

### Implements

`ICloneable`

### Remarks

The cloned object has the same property values as that of the object being cloned.

### Remarks (.NET Stored Procedure)

This method is not supported for an implicit database connection.

### Example

    // C#

    using System;
    using Oracle.DataAccess.Client;

    class CloneSample
    {
      static void Main()
      {
        string constr = "User Id=scott;Password=tiger;Data Source=oracle";
        OracleConnection con = new OracleConnection(constr);
        con.Open();

        // Need a proper casting for the return value when cloned
        OracleConnection clonedCon = (OracleConnection)con.Clone();

        // Cloned connection is always closed, regardless of its source,
        //   But the connection string should be identical
        clonedCon.Open();
        if (clonedCon.ConnectionString.Equals(con.ConnectionString))
          Console.WriteLine("The connection strings are the same.");
        else
          Console.WriteLine("The connection strings are different.");

        // Close and Dispose OracleConnection object
        clonedCon.Dispose();
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnection Class](OracleConnectionClass.md)

- [OracleConnection Members](ConnectionMembers.md)
