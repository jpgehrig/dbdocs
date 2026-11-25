This event is triggered upon the `OracleConnection.Open()` method.

### Declaration

    // C#
    public event OracleConnectionOpenEventHandler ConnectionOpen;

### Event Data

The event handler receives a `OracleConnectionOpenEventArgs` object which exposes the following property containing information about the `ConnectionOpen` event.

- `Connection`

  `OracleConnection` object on which `Open()` is called.

### Exceptions

- `InvalidOperationException()` - if `CPVersion=1.0` and the `ConnectionOpen` event is used. Applies to unmanaged ODP.NET only.

- `InvalidOperationException()` - if the `ConnectionOpen` event is set after opening a connection.

### Remarks

This feature requires `CPVersion=2.0` to be used.

In order to configure the connection before it is dispensed, the application should register the callback to the `ConnectionOpen` event before `Open()` is called.

Only supported for .NET Framework 4 and higher.

### Example

    // C#
    // NOTE: The sample below requires CPVersion=2.0 to be configured in the .NET configuration
    using System;
    using Oracle.ManagedDataAccess.Client;

    class ConOpenEventSample
    {
      public static void ConOpenCallback(OracleConnectionOpenEventArgs eventArgs)
      {
        OracleCommand cmd = new OracleCommand("ALTER SESSION SET NLS_LANGUAGE='GERMAN'", eventArgs.Connection);
        cmd.ExecuteNonQuery();
        cmd.Dispose();
      }

      static void Main(string[] args)
      {
        // Establish a connection
        string constr = "user id=hr;password=hr;data source=oracle";
        OracleConnection con = new OracleConnection(constr);
        con.ConnectionOpen += ConOpenCallback;
        con.Open();
        con.Dispose();
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnection Class](OracleConnectionClass.md)

- [OracleConnection Members](ConnectionMembers.md)

- [OracleConnectionOpenEventArgs Properties](ConnectionOpenEventArgsProperties.md)

- [OracleConnectionOpenEventHandler Delegate](OracleConnectionOpenEventHandlerDelegate.md)
