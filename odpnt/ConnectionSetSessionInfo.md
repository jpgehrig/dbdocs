This method alters the session's globalization settings with all the property values specified in the provided `OracleGlobalization` object.

### Declaration

    // C#
    public void SetSessionInfo(OracleGlobalization oraGlob);

### Parameters

- `oraGlob`

An `OracleGlobalization` object.

### Remarks

Calling this method is equivalent to calling an `ALTER` `SESSION` `SQL` on the session.

### Example

    // C#

    using System;
    using Oracle.DataAccess.Client;

    class SetSessionInfoSample
    {
      static void Main()
      {
        string constr = "User Id=scott;Password=tiger;Data Source=oracle";
        OracleConnection con = new OracleConnection(constr);
        con.Open();

        // Get session info from connection object
        OracleGlobalization info = con.GetSessionInfo();

        // Execute SQL SELECT
        OracleCommand cmd = con.CreateCommand();
        cmd.CommandText = "select TO_CHAR(hiredate) from emp";
        Console.WriteLine("Hire Date ({0}): {1}",
          info.DateFormat, cmd.ExecuteScalar());

        // Update session info
        info.DateFormat = "MM-DD-RR";
        con.SetSessionInfo(info);

        // Execute SQL SELECT again
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
