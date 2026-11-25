This property indicates whether or the implicit database connection is available for use.

### Declaration

    // C#
    public static bool IsAvailable {get;}

### Property Value

Returns `true` if the implicit database connection is available for use.

### Remarks

The availability of the implicit database connection can be checked at runtime through this static property. When Oracle Data Provider for .NET is used within a .NET stored procedure, this property always returns `true`. Otherwise, `false` is returned.

To obtain an `OracleConnection` object in a .NET stored procedure that represents the implicit database connection, set the `ConnectionString` property of the `OracleConnection` object to `"context` `connection=true"` and invoke the `Open` method.

Note that not all features that are available for an explicit user connection are available for an implicit database connection. See "[Implicit Database Connection](extenRest.md)" for details.

### Example

    // C# (Library/DLL)
    using System;
    using Oracle.DataAccess.Client;

    public class IsAvailableSample
    {
      static void MyStoredProcedure()
      {
        OracleConnection con = new OracleConnection();
        if (OracleConnection.IsAvailable)
        {
          // This function is invoked as a stored procedure
          // Obtain the implicit database connection by setting
          //   "context connection=true" in the connection string
          con.ConnectionString = "context connection=true";
        }
        else
        {
          // This function is not invoked as a stored procedure
          // Set the connection string for a normal client connection
          con.ConnectionString = "user id=scott;password=tiger;data source=oracle";
        }

        con.Open();
        Console.WriteLine("connected!");
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnection Class](OracleConnectionClass.md)

- [OracleConnection Members](ConnectionMembers.md)
