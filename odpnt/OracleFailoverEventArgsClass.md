The `OracleFailoverEventArgs` class provides event data for the `OracleConnection.Failover` event. When database failover occurs, the `OracleConnection.Failover` event is triggered along with the `OracleFailoverEventArgs` object that stores the event data.

### Class Inheritance

`System.Object`

`  System.EventArgs`

`    Oracle.DataAccess.Client.OracleFailoverEventArgs`

### Declaration

    // C#
    public sealed class OracleFailoverEventArgs

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  |
|:---------------|:---------------------------|
| Assembly       | `Oracle.DataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7         |

Not supported in a .NET stored procedure

### Thread Safety

All public static methods are thread-safe, although instance methods do not guarantee thread safety.

### Example (Oracle.DataAccess.Client only)

    // Transparent Application Failover (TAF) Setup
    // Refer Oracle® Database Net Services Administrator's Guide

    // C#

    using System;
    using System.Threading;
    using Oracle.DataAccess.Client;
    using Oracle.DataAccess.Types;

    class FailoverSample
    {
      static void Main(string[] args)
      {
        string constr = "User Id=scott;Password=tiger;Data Source=oracle";
        OracleConnection con = new OracleConnection(constr);
        con.Open();

        // Register the event handler OnFailover
        con.Failover += new OracleFailoverEventHandler(OnFailover);

        Console.WriteLine("Wait for a failover for 5 seconds");
        Thread.Sleep(5000);

        con.Close();
        con.Dispose();
      }

      // TAF callback function
      static FailoverReturnCode OnFailover(object sender,
        OracleFailoverEventArgs eventArgs)
      {
        switch (eventArgs.FailoverEvent)
        {
          case FailoverEvent.Begin:
          {
            Console.WriteLine("FailoverEvent.Begin - Failover is starting");
            Console.WriteLine("FailoverType = " + eventArgs.FailoverType);
            break;
          }
          case FailoverEvent.End:
          {
            Console.WriteLine("FailoverEvent.End - Failover was successful");
            break;
          }
          case FailoverEvent.Reauth:
          {
            Console.WriteLine("FailoverEvent.Reauth - User reauthenticated");
            break;
          }
          case FailoverEvent.Error:
          {
            Console.WriteLine("FailoverEvent.Error - Failover was unsuccessful");

            // Sleep for 3 sec and Retry
            Thread.Sleep(3000);
            return FailoverReturnCode.Retry;
          }
          case FailoverEvent.Abort:
          {
            Console.WriteLine("FailoverEvent.Abort - Failover was unsuccessful");
            break;
          }
          default:
          {
            Console.WriteLine("Invalid FailoverEvent : " + eventArgs.FailoverEvent);
            break;
          }
        }
        return FailoverReturnCode.Success;
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleFailoverEventArgs Members](FailoverEventArgsMembers.md)

- [OracleFailoverEventArgs Static Methods](FailoverEventArgsStaticMethods.md)

- [OracleFailoverEventArgs Properties](FailoverEventArgsProperties.md)

- [OracleFailoverEventArgs Public Methods](FailoverEventArgsPublicMethods.md)

- "[OracleConnection Class](OracleConnectionClass.md)"

- [Oracle Database Net Services Administrator's Guide](../netag/identifying-and-accessing-database.md)
