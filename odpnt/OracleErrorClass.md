The `OracleError` class represents an error reported by Oracle.

### Class Inheritance

`System.Object`

`  Oracle.DataAccess.Client.OracleError`

### Declaration

    // C#
    public sealed class OracleError

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

The `OracleError` class represents a warning or an error reported by Oracle.

If there are multiple errors, ODP.NET only returns the first error message on the stack.

### Example

    // C#

    using System;
    using System.Data;
    using Oracle.DataAccess.Client;

    class OracleErrorsSample
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

          foreach (OracleError error in ex.Errors)
          {
            Console.WriteLine("Error Message: " + error.Message);
            Console.WriteLine("Error Source: " + error.Source);
          }
        }
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleError Members](ErrorMembers.md)

- [OracleError Static Methods](ErrorStaticMethods.md)

- [OracleError Properties](ErrorProperties.md)

- [OracleError Methods](ErrorMethods.md)
