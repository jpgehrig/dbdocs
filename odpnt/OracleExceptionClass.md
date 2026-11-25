The `OracleException` class represents an exception that is thrown when the Oracle Data Provider for .NET encounters an error. Each `OracleException` object contains at least one `OracleError` object in the `Error` property that describes the error or warning.

### Class Inheritance

`System.Object`

`  System.Exception`

`    System.SystemException`

`      System.Runtime.InteropServices.ExternalException`

`        System.Data.Common.DbException`

    `     Oracle.DataAccess.Client.OracleException`

### Declaration

    // C#
    public sealed class OracleException : SystemException

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  | ODP.NET, Managed Driver           | ODP.NET Core                      |
|:---------------|:---------------------------|:----------------------------------|:----------------------------------|
| Assembly       | `Oracle.DataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` | `Oracle.ManagedDataAccess.Client` | `Oracle.ManagedDataAccess.Client` |
| .NET Framework | 4.5, 4.6, 4.7              | 4.5, 4.6, 4.7                     | 4.6.1 or higher                   |
| .NET Core      | \-                         | \-                                | 2.1 or higher                     |

### Thread Safety

All public static methods are thread-safe, although instance methods do not guarantee thread safety.

### Remarks

If there are multiple errors, ODP.NET only returns the first error message on the stack.

### Example

    // C#

    using System;
    using System.Data;
    using Oracle.DataAccess.Client;

    class OracleExceptionSample
    {
      static void Main()
      {
        string constr = "User Id=scott;Password=tiger;Data Source=oracle";
        OracleConnection con = new OracleConnection(constr);
        con.Open();

        // Create an OracleCommand object using the connection object
        OracleCommand cmd = con.CreateCommand();

        try
        {
          cmd.CommandText = "insert into notable values (99, 'MyText')";
          cmd.ExecuteNonQuery();
        }
        catch (OracleException ex)
        {
          Console.WriteLine("Record is not inserted into the database table.");
          Console.WriteLine("Exception Message: " + ex.Message);
          Console.WriteLine("Exception Source: " + ex.Source);
        }
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleException Members](ExceptionMembers.md)

- [OracleException Methods](ExceptionMembers.md)

- [OracleException Static Methods](ExceptionStaticMethods.md)

- [OracleException Static Methods](ExceptionStaticMethods.md)

- [OracleException Properties](ExceptionProperties.md)

- [OracleException Methods](ExceptionMethods.md)
