The `OracleInfoMessageEventArgs` class provides event data for the `OracleConnection.InfoMessage` event. When any warning occurs in the database, the `OracleConnection.InfoMessage` event is triggered along with the `OracleInfoMessageEventArgs` object that stores the event data.

### Class Inheritance

`System.Object`

`  System.EventArgs`

`    Oracle.DataAccess.Client.OracleInfoMessageEventArgs`

### Declaration

    // C#
    public sealed class OracleInfoMessageEventArgs

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  | ODP.NET, Managed Driver           | ODP.NET Core                      |
|:---------------|:---------------------------|:----------------------------------|:----------------------------------|
| Assembly       | `Oracle.DataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` | `Oracle.ManagedDataAccess.Client` | `Oracle.ManagedDataAccess.Client` |
| .NET Framework | 4.5, 4.6, 4.7              | 4.5, 4.6, 4.7                     | 4.6.1 or higher                   |
| .NET Core      | \-                         | \-                                | 2.1 or higher                     |

### Thread Safety

All public static methods are thread-safe, although instance methods do not guarantee thread safety.

### Example

    // C#

    using System;
    using System.Data;
    using Oracle.DataAccess.Client;
    using Oracle.DataAccess.Types;


    class InfoMessageSample
    {
      public static void WarningHandler(object src,
        OracleInfoMessageEventArgs args)
      {
          Console.WriteLine("Source object is: " + src.GetType().Name);
          Console.WriteLine("InfoMessageArgs.Message is " + args.Message);
          Console.WriteLine("InfoMessageArgs.Source is " + args.Source);
      }
      static void Main()
      {
        OracleConnection con = new OracleConnection("User Id=scott;" +
          "Password=tiger;Data Source=oracle;");

        con.Open();

        OracleCommand cmd = con.CreateCommand();

        //Register to the InfoMessageHandler
        cmd.Connection.InfoMessage +=
          new OracleInfoMessageEventHandler(WarningHandler);

        cmd.CommandText =
          "create or replace procedure SelectWithNoInto( " +
          "  empname in VARCHAR2) AS " +
          "BEGIN " +
          "  select * from emp where ename = empname; " +
          "END SelectWithNoInto;";

        // Execute the statement that produces a warning
        cmd.ExecuteNonQuery();

        // Clean up
        cmd.Dispose();
        con.Dispose();
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleInfoMessageEventArgs Members](OracleInfoMessageEventArgsmembers.md)

- [OracleInfoMessageEventArgs Static Methods](InfoMessageEventArgsStaticMethods.md)

- [OracleInfoMessageEventArgs Properties](InfoMessageEventArgsProperties.md)

- [OracleInfoMessageEventArgs Public Methods](InfoMessageEventArgsPublicMethods.md)

- "[OracleConnection Class](OracleConnectionClass.md)"
