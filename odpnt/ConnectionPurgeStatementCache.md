This method flushes the statement cache by closing all open cursors on the database, when statement caching is enabled.

### Declaration

    // C#
    public void PurgeStatementCache();

### Remarks

Flushing the statement cache repetitively results in decreased performance and may negate the performance benefit gained by enabling the statement cache.

Statement caching remains enabled after the call to `PurgeStatementCache`.

Invocation of this method purges the cached cursors that are associated with the `OracleConnection`. It does not purge all the cached cursors in the database.

### Example

    // C#

    using System;
    using System.Data;
    using Oracle.DataAccess.Client;

    class PurgeStatementCacheSample
    {
      static void Main()
      {
        string constr = "User Id=scott;Password=tiger;Data Source=oracle;" +
          "Statement Cache Size=20";
        OracleConnection con = new OracleConnection(constr);
        con.Open();

        OracleCommand cmd = new OracleCommand("select * from emp", con);
        cmd.CommandType = CommandType.Text;
        OracleDataReader reader = cmd.ExecuteReader();

        // Purge Statement Cache
        con.PurgeStatementCache();

        // Close and Dispose OracleConnection object
        Console.WriteLine("Statement Cache Flushed");
        con.Close();
        con.Dispose();
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnection Class](OracleConnectionClass.md)

- [OracleConnection Members](ConnectionMembers.md)

- "[Statement Caching](featOraCommand.md)"

- [ConnectionString](ConnectionConnectionString.md)
