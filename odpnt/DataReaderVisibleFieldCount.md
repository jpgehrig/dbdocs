This property gets the number of fields in the `OracleDataReader` that are not hidden.

### Declaration

    // C#
    public override int VisibleFieldcount { get; }

### Property Value

The number of fields that are not hidden.

### Exceptions

`InvalidOperationException` - The reader is closed.

### Remarks

If an application sets the `AddRowid` property on an `OracleCommand` object to `true`, then the application can access the `RowId` but it is not a visible field. If `RowId` is added in the select statement list, then it is a visible field. `OracleDataReader.VisibleFieldCount` and `OracleDataReader.FieldCount` always have the same value.

### Example

    // C#

    using System;
    using System.Data;
    using System.Data.Common;
    using Oracle.DataAccess.Client;

    class VisibleFieldCountSample
    {
      static void Main(string[] args)
      {
        string constr = "User Id=scott; Password=tiger; Data Source=oracle;";
        DbProviderFactory factory =
                DbProviderFactories.GetFactory("Oracle.DataAccess.Client");

        using (DbConnection conn = factory.CreateConnection())
        {
          conn.ConnectionString = constr;
          try
          {
            conn.Open();
            OracleCommand cmd = (OracleCommand)factory.CreateCommand();
            cmd.Connection = (OracleConnection)conn;

            //to gain access to ROWIDs of the table
            cmd.AddRowid = true;
            cmd.CommandText = "select empno, ename from emp;";

            OracleDataReader reader = cmd.ExecuteReader();

            int visFC = reader.VisibleFieldCount; //Results in 2
            int hidFC = reader.HiddenFieldCount;  // Results in 1

            Console.Write("Visible field count: " + visFC);
            Console.Write("Hidden field count: " + hidFC);

            reader.Dispose();
            cmd.Dispose();
          }
          catch (Exception ex)
          {
            Console.WriteLine(ex.Message);
            Console.WriteLine(ex.StackTrace);
          }
        }
      }
    }



**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataReader Class](OracleDataReaderClass.md)

- [OracleDataReader Members](DataReaderMembers.md)

- "VisibleFieldCount"

- "[FieldCount](DataReaderFieldCount.md)"
