This method executes a command specified in the `CommandText` and returns an `OracleDataReader` object.

### Declaration

    // C#
    public OracleDataReader ExecuteReader();

### Return Value

An `OracleDataReader`.

### Implements

`IDbCommand`

### Exceptions

`InvalidOperationException` - The command cannot be executed.

### Remarks

When the `CommandType` property is set to `CommandType.StoredProcedure`, the `CommandText` property should be set to the name of the stored procedure.

The specified command executes this stored procedure when `ExecuteReader` is called. If parameters for the stored procedure consist of `REF` `CURSOR` objects, behavior differs depending on whether `ExecuteReader()` or `ExecuteNonQuery()` is called. If `ExecuteReader()` is invoked, `REF` `CURSOR` objects can be accessed through the `OracleDataReader` that is returned.If more than one `REF` `CURSOR` is returned from a single execution, subsequent `REF` `CURSOR` objects can be accessed sequentially by the `NextResult` method on the `OracleDataReader`. If the `ExecuteNonQuery` method is invoked, the output parameter value can be cast to a `OracleRefCursor` type and the `OracleRefCursor` object then can be used to either populate a `DataSet` or create an `OracleDataReader` object from it. This approach provides random access to all the `REF` `CURSOR` objects returned as output parameters.

The value of `100` is used for the `FetchSize`. If `0` is specified, no rows are fetched. For further information, see "[Obtaining LONG and LONG RAW Data](featData.md)".

If the value of the `XmlCommandType` property is set to `OracleXmlCommandType.Insert`, `OracleXmlCommandType.Update`, `OracleXmlCommandType.Delete`, or `OracleXmlCommandType.Query` then the `ExecuteReader` method throws an `InvalidOperationException`.

### Example

    // C#

    using System;
    using System.Data;
    using Oracle.DataAccess.Client;

    class ExecuteReaderSample
    {
      static void Main()
      {
        string constr = "User Id=scott;Password=tiger;Data Source=oracle";
        OracleConnection con = new OracleConnection(constr);
        con.Open();

        OracleCommand cmd = new OracleCommand("select ename from emp", con);

        OracleDataReader reader = cmd.ExecuteReader();

        while (reader.Read())
        {
          Console.WriteLine("Employee Name : " + reader.GetString(0));
        }

        // Clean up
        reader.Dispose();
        cmd.Dispose();
        con.Dispose();
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleCommand Class](OracleCommandClass.md)

- [OracleCommand Members](OracleCommandMembers.md)

- "[OracleRefCursor Class](OracleRefCursorClass.md)"
