Overrides `Exception`

This method returns the fully qualified name of this exception, the `error` message in the `Message` property, the `InnerException.ToString()` message, and the stack trace.

### Declaration

    // C#
    public override string ToString();

### Return Value

The string representation of the exception.

### Example

    // C#

    using System;
    using Oracle.DataAccess.Client;

    class ToStringSample
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
          cmd.ExecuteNonQuery();  // This will throw an exception
        }
        catch (OracleException ex)
        {
          Console.WriteLine("Record is not inserted into the database table.");
          Console.WriteLine("ex.ToString() : " + ex.ToString());
        }
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleException Class](OracleExceptionClass.md)

- [OracleException Members](ExceptionMembers.md)
