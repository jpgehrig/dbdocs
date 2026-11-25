An `OracleParameterCollection` class represents a collection of all parameters relevant to an `OracleCommand` object and their mappings to `DataSet` columns.

### Class Inheritance

`System.Object`

`  System.MarshalByRefObject`

`    System.Data.Common.DbParameterCollection`

`      Oracle.DataAccess.Client.OracleParameterCollection`

### Declaration

    // C#
    public sealed class OracleParameterCollection : DbParameterCollection,
        IDataParameterCollection, IList, ICollection, IEnumerable

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

The position of an `OracleParameter` added into the `OracleParameterCollection` is the binding position in the SQL statement. Position is `0`-based and is used only for positional binding. If named binding is used, the position of an `OracleParameter` in the `OracleParameterCollection` is ignored.

### Example

    // C#

    using System;
    using System.Data;
    using Oracle.DataAccess.Client;

    class OracleParameterCollectionSample
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

        // Remove all parameters from OracleParameterCollection
        cmd.Parameters.Clear();

        prm[0].Dispose();
        prm[1].Dispose();
        prm[2].Dispose();
        cmd.Dispose();

        con.Close();
        con.Dispose();
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleParameterCollection Members](ParameterCollectionMembers.md)

- [OracleParameterCollection Static Methods](ParameterCollectionStaticMethods.md)

- [OracleParameterCollection Properties](ParameterCollectionProperties.md)

- [OracleParameterCollection Public Methods](ParameterCollectionPublicMethods.md)
