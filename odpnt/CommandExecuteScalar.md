This method executes the query using the connection, and returns the first column of the first row in the result set returned by the query.

### Declaration

    // C#
    public override object ExecuteScalar();

### Return Value

An object which represents the value of the first row, first column.

### Implements

`IDbCommand`

### Exceptions

`InvalidOperationException` - The command cannot be executed.

### Remarks

Extra columns or rows are ignored. `ExecuteScalar` retrieves a single value (for example, an aggregate value) from a database. This requires less code than using the `ExecuteReader()` method, and then performing the operations necessary to generate the single value using the data returned by an `OracleDataReader`.

If the query does not return any row, it returns `null`.

The `ExecuteScalar` method throws an `InvalidOperationException`, if the value of the `XmlCommandType` property is set to one of the following `OracleXmlCommandType` values: `Insert`, `Update`, `Delete`, `Query`.

### Example

    // C#

    using System;
    using System.Data;
    using Oracle.DataAccess.Client;

    class ExecuteScalarSample
    {
      static void Main()
      {
        string constr = "User Id=scott;Password=tiger;Data Source=oracle";
        OracleConnection con = new OracleConnection(constr);
        con.Open();

        OracleCommand cmd = new OracleCommand("select count(*) from emp", con);

        object count = cmd.ExecuteScalar();

        Console.WriteLine("There are {0} rows in table emp", count);

        // Clean up
        cmd.Dispose();
        con.Dispose();
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleCommand Class](OracleCommandClass.md)

- [OracleCommand Members](OracleCommandMembers.md)
