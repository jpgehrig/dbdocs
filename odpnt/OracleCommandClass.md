An `OracleCommand` object represents a SQL command, a stored procedure, or a table name. The `OracleCommand` object is responsible for formulating the request and passing it to the database. If results are returned, `OracleCommand` is responsible for returning results as an `OracleDataReader`, a .NET `XmlReader`, a .NET `Stream`, a scalar value, or as output parameters.

### Class Inheritance

`System.Object`

`  System.MarshalByRefObject`

`    System.ComponentModel.Component`

`      System.Data.Common.DbCommand`

`        Oracle.DataAccess.Client.OracleCommand`

### Declaration

    // C#
    public sealed class OracleCommand : DbCommand, ICloneable

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  | ODP.NET, Managed Driver           | ODP.NET Core                      |
|:---------------|:---------------------------|:----------------------------------|:----------------------------------|
| Assembly       | `Oracle.DataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` | `Oracle.ManagedDataAccess.Client` | `Oracle.ManagedDataAccess.Client` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7         | 4.5, 4.6, 4.7                     | 4.6.1 or higher                   |
| .NET Core      | \-                         | \-                                | 2.1 or higher                     |

### Thread Safety

All public static methods are thread-safe, although instance methods do not guarantee thread safety.

### Remarks

The execution of any transaction-related statements from an `OracleCommand` is not recommended because it is not reflected in the state of the `OracleTransaction` object represents the current local transaction, if one exists.

`ExecuteXmlReader`, `ExecuteStream`, and `ExecuteToStream` methods are only supported for XML operations.

`ExecuteReader` and `ExecuteScalar` methods are not supported for XML operations.

To minimize the number of open server cursors, `OracleCommand` objects should be explicitly disposed.

### Example

    // C#

    using System;
    using System.Data;
    using Oracle.DataAccess.Client;

    class OracleCommandSample
    {
      static void Main()
      {
        string constr = "User Id=scott;Password=tiger;Data Source=oracle";
        OracleConnection con = new OracleConnection(constr);
        con.Open();

        string cmdQuery = "select ename, empno from emp";

        // Create the OracleCommand
        OracleCommand cmd = new OracleCommand(cmdQuery);

        cmd.Connection = con;
        cmd.CommandType = CommandType.Text;

        // Execute command, create OracleDataReader object
        OracleDataReader reader = cmd.ExecuteReader();

        while (reader.Read())
        {
          // output Employee Name and Number
          Console.WriteLine("Employee Name : " + reader.GetString(0) + " , " +
            "Employee Number : " + reader.GetDecimal(1));
        }

        // Clean up
        reader.Dispose();
        cmd.Dispose();
        con.Dispose();
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleCommand Members](OracleCommandMembers.md)

- [OracleCommand Constructors](OracleCommandCtors.md)

- [OracleCommand Static Methods](CommandStaticMethods.md)

- [OracleCommand Properties](CommandProperties.md)

- [OracleCommand Public Methods](CommandPublicMethods.md)
