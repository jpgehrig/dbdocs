This property indicates whether the `OracleDataReader` has one or more rows.

### Declaration

    // C#
    public override bool HasRows {get;}

### Return Value

`bool`

### Remarks

`HasRows` indicates whether or not the `OracleDataReader` has any rows.

The value of `HasRows` does not change based on the row position. For example, even if the application has read all the rows from the result set and the next Read method invocation will return false, the `HasRows` property still returns true since the result set was not empty to begin with.

Rows are fetched to determine the emptiness of the `OracleDataReader` when `HasRows` property is accessed for the first time after the creation of the `OracleDataReader` object.

### Example

    // C#

    using System;
    using Oracle.DataAccess.Client;

    class HasRowsSample
    {
      static void Main()
      {
        string constr = "User Id=scott;Password=tiger;Data Source=oracle";
        OracleConnection con = new OracleConnection(constr);
        con.Open();

        OracleCommand cmd = new OracleCommand(
          "select * from emp where empno = 9999", con);

        OracleDataReader reader = cmd.ExecuteReader();

        if (!reader.HasRows)
          Console.WriteLine("The result set is empty.");
        else
          Console.WriteLine("The result set is not empty.");

        con.Dispose();
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataReader Class](OracleDataReaderClass.md)

- [OracleDataReader Members](DataReaderMembers.md)

- [`http://msdn.microsoft.com/library`](http://msdn.microsoft.com/library) for detailed information about this Microsoft .NET Framework feature
