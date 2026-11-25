An `OracleRefCursor` object represents an Oracle `REF` `CURSOR`..

### Class Inheritance

`System.Object`

`  System.MarshalRefByObject`

`    Oracle.DataAccess.Types.OracleRefCursor`

### Declaration

    // C#
    public sealed class OracleRefCursor : MarshalByRefObject, IDisposable, INullable

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

To minimize the number of open server cursors, `OracleRefReader` objects should be explicitly disposed.

### Example

    // Database Setup
    /*
    connect scott/tiger@oracle
    CREATE OR REPLACE FUNCTION MyFunc(refcur_out OUT SYS_REFCURSOR)
      RETURN SYS_REFCURSOR IS refcur_ret SYS_REFCURSOR;
    BEGIN
      OPEN refcur_ret FOR SELECT * FROM EMP;
      OPEN refcur_out FOR SELECT * FROM DEPT;
      RETURN refcur_ret;
    END MyFunc;
    /
    */

    // C#

    using System;
    using System.Data;
    using Oracle.DataAccess.Client;
    using Oracle.DataAccess.Types;

    class OracleRefCursorSample
    {
      static void Main()
      {
        // Example demonstrates how to use REF CURSORs returned from
        // PL/SQL Stored Procedures or Functions
        // Create the PL/SQL Function MyFunc as defined previously

        string constr = "User Id=scott;Password=tiger;Data Source=oracle";
        OracleConnection con = new OracleConnection(constr);
        con.Open();

        // Create an OracleCommand
        OracleCommand cmd = new OracleCommand("MyFunc", con);
        cmd.CommandType = CommandType.StoredProcedure;

        // Bind the parameters
        // p1 is the RETURN REF CURSOR bound to SELECT * FROM EMP;
        OracleParameter p1 =
          cmd.Parameters.Add("refcur_ret", OracleDbType.RefCursor);
        p1.Direction = ParameterDirection.ReturnValue;

        // p2 is the OUT REF CURSOR bound to SELECT * FROM DEPT
        OracleParameter p2 =
          cmd.Parameters.Add("refcur_out", OracleDbType.RefCursor);
        p2.Direction = ParameterDirection.Output;

        // Execute the command
        cmd.ExecuteNonQuery();

        // Construct an OracleDataReader from the REF CURSOR
        OracleDataReader reader1 = ((OracleRefCursor)p1.Value).GetDataReader();

        // Prints "reader1.GetName(0) = EMPNO"
        Console.WriteLine("reader1.GetName(0) = " + reader1.GetName(0));

        // Construct an OracleDataReader from the REF CURSOR
        OracleDataReader reader2 = ((OracleRefCursor)p2.Value).GetDataReader();

        // Prints "reader2.GetName(0) = DEPTNO"
        Console.WriteLine("reader2.GetName(0) = " + reader2.GetName(0));

        reader1.Close();
        reader1.Dispose();

        reader2.Close();
        reader2.Dispose();

        p1.Dispose();
        p2.Dispose();

        cmd.Dispose();

        con.Close();
        con.Dispose();
      }
    }

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleRefCursor Members](RefCursorMembers.md)

- [OracleRefCursor Static Methods](RefcursorStaticMethods.md)

- [OracleRefCursor Static Fields](RefcursorStaticFields.md)

- [OracleRefCursor Properties](RefcursorProperties.md)

- [OracleRefCursor Instance Methods](RefcursorInstanceMethods.md)
