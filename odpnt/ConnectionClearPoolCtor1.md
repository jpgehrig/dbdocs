This method clears the connection pool that is associated with the provided `OracleConnection` object.

### Declaration

    // C#
    public static void ClearPool(OracleConnection connection);

### Remarks

When this method is invoked, all idle connections are closed and freed from the pool. Currently used connections are not discarded until they are returned to the pool.

Beginning with ODP.NET 12c Release 1 (12.1), `ClearPool` does not automatically repopulate the pool with new connections. This prevents the pool from being repopulated with invalid connections if client remains unable to connect with the database server. Developers programmatically control when the pool is repopulated by calling `OracleConnection.Open()`, which will repopulate the pool with at least the Min Pool Size number of connections.

Connections created after this method invocation are not cleared unless another invocation is made.

This method can be invoked with an `OracleConnection` object before opening the connection as well as after, provided the `ConnectionString` is properly set.

### Exceptions

`InvalidOperationException` – Either the connection pool cannot be found or the provided connection string is invalid.

### Example

    // C#
    // Sample demonstrating the use of ClearPool API in OracleConnection class

    using System;
    using Oracle.DataAccess.Client;

    class ClearPoolSample
    {
      static void Main()
      {
        Console.WriteLine("Running ClearPool sample..." );
        // Set the connection string
        string strConn = "User Id=scott;Password=tiger;Data Source=oracle;" +
                         "Min pool size=5;";
        OracleConnection conn = new OracleConnection(strConn);

        // Open the connection
        conn.Open();

        // Clears the connection pool associated with connection 'conn'
        OracleConnection.ClearPool (conn);

        // This connection will be placed back into the pool
        conn.Close ();

        // Open the connection again to create additional connections in the pool
        conn.Open();

        // Create a new connection object
        OracleConnection connNew = new OracleConnection(strConn);

        // Clears the pool associated with Connection 'connNew'
        // Since the same connection string is set for both the connections,
        // connNew and conn, they will be part of the same connection pool.
        // We need not do an Open() on the connection object before calling
        // ClearPool
        OracleConnection.ClearPool (connNew);

        // cleanup
        conn.Close();
        Console.WriteLine("Done!");
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnection Class](OracleConnectionClass.md)

- [OracleConnection Members](ConnectionMembers.md)
