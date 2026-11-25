This method returns a new instance of the `OracleGlobalization` object that represents the globalization settings of the session.

### Declaration

    // C#
    public OracleGlobalization GetSessionInfo();

### Return Value

The newly created `OracleGlobalization` object.

### Example

    // C#

    using System;
    using Oracle.DataAccess.Client;

    class GetSessionInfoSample
    {
      static void Main()
      {
        string constr = "User Id=scott;Password=tiger;Data Source=oracle";
        OracleConnection con = new OracleConnection(constr);
        con.Open();

        // Get session info from connection object
        OracleGlobalization info = con.GetSessionInfo();

        // Update session info
        info.DateFormat = "YYYY-MM-DD";
        con.SetSessionInfo(info);

        // Execute SQL SELECT
        OracleCommand cmd = con.CreateCommand();
        cmd.CommandText = "select TO_CHAR(hiredate) from emp";
        Console.WriteLine("Hire Date ({0}): {1}",
          info.DateFormat, cmd.ExecuteScalar());

        // Clean up
        cmd.Dispose();
        con.Dispose();
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnection Class](OracleConnectionClass.md)

- [OracleConnection Members](ConnectionMembers.md)
