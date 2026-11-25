An `OracleParameter` object represents a parameter for an `OracleCommand` or a `DataSet` column.

### Class Inheritance

`System.Object`

`  System.MarshalByRefObject`

`    System.Data.Common.DbParameter`

`      Oracle.DataAccess.Client.OracleParameter`

### Declaration

    // C#
    public sealed class OracleParameter : DbParameter, IDisposable, ICloneable

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  | ODP.NET, Managed Driver           | ODP.NET Core                      |
|:---------------|:---------------------------|:----------------------------------|:----------------------------------|
| Assembly       | `Oracle.DataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` | `Oracle.ManagedDataAccess.Client` | `Oracle.ManagedDataAccess.Client` |
| .NET Framework | 4.5, 4.6, 4.7              | 4.5, 4.6, 4.7                     | 4.6.1 or higher                   |
| .NET Core      | \-                         | \-                                | 2.1 or higher                     |

### Thread Safety

All public static methods are thread-safe, although instance methods do not guarantee thread safety.

### Exceptions

`ArgumentException` - The type binding is invalid.

### Example

    // C#

    using System;
    using System.Data;
    using Oracle.DataAccess.Client;
    using Oracle.DataAccess.Types;

    class OracleParameterSample
    {
      static void Main()
      {
        string constr = "User Id=scott;Password=tiger;Data Source=oracle";
        OracleConnection con = new OracleConnection(constr);
        con.Open();

        OracleParameter[] prm = new OracleParameter[3];

        // Create OracleParameter objects through OracleParameterCollection
        OracleCommand cmd = con.CreateCommand();

        cmd.CommandText = "select max(empno) from emp";
        int maxno = int.Parse(cmd.ExecuteScalar().ToString());

        prm[0] = cmd.Parameters.Add("paramEmpno", OracleDbType.Decimal,
          maxno + 10, ParameterDirection.Input);
        prm[1] = cmd.Parameters.Add("paramEname", OracleDbType.Varchar2,
          "Client", ParameterDirection.Input);
        prm[2] = cmd.Parameters.Add("paramDeptNo", OracleDbType.Decimal,
          10, ParameterDirection.Input);
        cmd.CommandText =
          "insert into emp(empno, ename, deptno) values(:1, :2, :3)";
        cmd.ExecuteNonQuery();

        Console.WriteLine("Record for employee id {0} has been inserted.",
                          maxno + 10);
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleParameter Members](ParameterMembers.md)

- [OracleParameter Constructors](ParameterCtors.md)

- [OracleParameter Static Methods](ParameterStaticMethods.md)

- [OracleParameter Properties](ParameterProperties.md)

- [OracleParameter Public Methods](ParameterPublicMethods.md)
