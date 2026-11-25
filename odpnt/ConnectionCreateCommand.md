This method creates and returns an `OracleCommand` object associated with the `OracleConnection` object.

### Declaration

    // C#
    public OracleCommand CreateCommand();

### Return Value

The `OracleCommand` object.

### Implements

`IDbConnection`

### Example

    // C#

    using System;
    using System.Data;
    using Oracle.DataAccess.Client;

    class CreateCommandSample
    {
      static void Main()
      {
        // Connect
        string constr = "User Id=scott;Password=tiger;Data Source=oracle";
        OracleConnection con = new OracleConnection(constr);
        con.Open();

        // Execute a SQL SELECT
        OracleCommand cmd = con.CreateCommand();
        cmd.CommandText = "select * from emp";
        OracleDataReader reader = cmd.ExecuteReader();

        // Print all employee numbers
        while (reader.Read())
          Console.WriteLine(reader.GetInt32(0));

        // Clean up
        reader.Dispose();
        cmd.Dispose();
        con.Dispose();
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnection Class](OracleConnectionClass.md)

- [OracleConnection Members](ConnectionMembers.md)
