`OracleCredential` class provides a secure way to provide password while opening connection with Oracle Database using the ODP.NET driver. Use this class to avoid providing passwords in clear text in the connection string while opening a connection with Oracle Database. One can pass user id, password and DBA Privilege specific attributes through `OracleCredential` constructors and thus these attributes do not need to be in the connection string.

Operating system authenticated and context connections are not supported through `OracleCredential` class. An `ArgumentException` will be thrown if "`/`" is passed for `userId` or `proxyUserId` arguments of `OracleCredential` constructor.

### Class Inheritance

`System.Object`

`      Oracle.DataAccess.Client.OracleCredential`

### Declaration

    // C#
    public sealed class OracleCredential

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
    using System.Security;
    using Oracle.DataAccess.Client;
    //using Oracle.ManagedDataAccess.Client;

    class OracleCredentialSample

    {
      static void Main()
      {
        // Connect
        string constr = "Data Source=oracle";

        SecureString secPwd = new SecureString();
        secPwd.AppendChar('h');
        secPwd.AppendChar('r');

        // Make the password read-only.
        secPwd.MakeReadOnly();

        // Create OracleCredential with userid and secure password.
        OracleCredential oc = new OracleCredential("hr", secPwd);

        OracleConnection con = new OracleConnection(constr, oc);
        con.Open();

        // Execute a SQL SELECT

        OracleCommand cmd = con.CreateCommand();
        cmd.CommandText = "select * from employees";

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

- [OracleCredential Members](CredentialMembers.md)

- [OracleCredential Constructors](CredentialCtors.md)

- [OracleCredential Properties](CredentialProperties.md)

- [Connection Pooling with OracleCredential](featConnecting.md)
