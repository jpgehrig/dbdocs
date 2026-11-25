This method clears all connections from all the connection pools.

### Declaration

    // C#
    public static void ClearAllPools();

### Remarks

This call is analogous to calling `ClearPool` for all the connection pools that are created for the application.

### Exceptions

`InvalidOperationException` – No connection pool could be found for the application.

### Example

    // C#
    // Sample demonstrating the use of ClearAllPools API in OracleConnection class

    using System;
    using Oracle.DataAccess.Client;

    class ClearAllPoolsSample
    {
      static void Main()
      {
        Console.WriteLine("Running ClearAllPools sample..." );
        // Set the connection string
        string strConn = "User Id=scott;Password=tiger;Data Source=oracle;" +
               "Min pool size=5;";
        OracleConnection conn = new OracleConnection(strConn);

        // Create another connection object with a different connection string
        string strConnNew = "User Id=scott;Password=tiger;Data Source=oracle;";
        OracleConnection connNew = new OracleConnection(strConnNew);

        // Open the connections. Separate pools are created for conn and connNew
        conn.Open();
        connNew.Open();

        // Clears the pools associated with conn and connNew
        OracleConnection.ClearAllPools ();

        // cleanup
        conn.Close();
        connNew.Close();
        Console.WriteLine("Done!");
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnection Class](OracleConnectionClass.md)

- [OracleConnection Members](ConnectionMembers.md)

- "[ClearPool](ConnectionClearPoolCtor1.md)"
