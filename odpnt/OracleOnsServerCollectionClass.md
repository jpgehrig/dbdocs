The `OracleOnsServerCollection` class supports adding to and deleting from a collection of logical servers with their corresponding list of nodes where the Oracle Notification Service (ONS) daemons are talking to their remote clients.

In case of remote configuration, the application has to specify the \<host\>:\<port\> values for every potential database that it can connect to. The \<host\>:\<port\> value pairs represent the ports on the different nodes.

### Class Inheritance

`System.Object`

` Oracle.ManagedDataAccess.Client.OracleOnsServerCollection`

### Declaration

    // C#
    public static class OracleOnsServerCollection

### Requirements

| Provider       | ODP.NET Core                      |
|:---------------|:----------------------------------|
| Assembly       | `Oracle.ManagedDataAccess.dll`    |
| Namespace      | `Oracle.ManagedDataAccess.Client` |
| .NET Framework | 4.6.1 or higher                   |
| .NET Core      | 2.1 or higher                     |

### Thread Safety

All public static methods are thread-safe, although instance methods do not guarantee thread safety.

### Example

    using System;
    using Oracle.ManagedDataAccess.Client;

    namespace NetCoreApp
    {
      class OnsServersExample
      {
        static void Main(string[] args)
        {
          // Example to configure ONS Servers for the ODP.NET Core provider.

          // Add server through Add method on OracleOnsServerCollection
          OracleConfiguration.OracleOnsServers.Add("db1", "nodeList=host1:port1, host2:port2, host3:port3");

          // Add server through indexer method on OracleOnsServerCollection
          OracleConfiguration.OracleOnsServers["db2"] = "nodeList=m1:p1, m2:p2";

          // Get number of servers configured
          int numServers = OracleConfiguration.OracleOnsServers.Count;

          // Get OracleOnsServerCollection object
          OracleOnsServerCollection serverColl = OracleConfiguration.OracleOnsServers;

          // Add server through Add method on OracleOnsServerCollection
          serverColl.Add("db3", "nodeList=host1:port1, host2:port2, host3:port3");

          // Add server through indexer method on OracleOnsServerCollection
          serverColl["db4"] = "nodeList=m1:p1, m2:p2";

          // Remove a server
          OracleConfiguration.OracleOnsServers.Remove("db2");

          // Get number of servers configured
          numServers = OracleConfiguration.OracleOnsServers.Count;

          // Get value corresponding to a server.
          string serverVal = OracleConfiguration.OracleOnsServers["db1"];

          OracleConnection orclCon = null;

          try
          {
            // Open a test connection
            orclCon = new OracleConnection("user id=scott; password=tiger; data source=oracle");

            orclCon.Open();
            orclCon.Close();
          }
          catch (OracleException ex)
          {
            Console.WriteLine(ex);
          }
          finally
          {
            // Close the connection
            if (null != orclCon)
              orclCon.Close();
          }
        }
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleOnsServerCollection Members](OracleOnsServerCollectionMembers.md)

- [OracleOnsServerCollection Methods](OnsServerCollectionMethods.md)

- [OracleOnsServerCollection Properties](OnsServerCollectionProperties.md)
