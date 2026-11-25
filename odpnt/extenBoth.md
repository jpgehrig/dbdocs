Oracle Data Provider for .NET classes and APIs provide data access to the Oracle Database from a .NET client application and from .NET stored procedures and functions.

However, some limitations and restrictions exist when Oracle Data Provider for .NET is used within a .NET stored procedure. These are discussed in the next section.

The following is a simple .NET stored procedure example.

    using System;
    using Oracle.DataAccess.Client;
    using Oracle.DataAccess.Types;

    public class CLRLibrary1
    {
      // .NET Stored Function returning the DEPTNO of the employee whose
      // EMPNO is 'empno'
      public static uint GetDeptNo(uint empno)
      {
        uint deptno = 0;

        // Create and open a context connection
        OracleConnection conn = new OracleConnection();
        if( OracleConnection.IsAvailable == true )
        {
          conn.ConnectionString = "context connection=true";
        }
        else
        {
          //set connection string for a normal client connection
          conn.ConnectionString = "user id=scott;password=tiger;" +
            "data source=oracle";
        }
        conn.Open();

        // Create and execute a command
        OracleCommand cmd = conn.CreateCommand();
        cmd.CommandText = "SELECT DEPTNO FROM EMP WHERE EMPNO = :1";
        cmd.Parameters.Add(":1",OracleDbType.Int32,empno,
        System.Data.ParameterDirection.Input);
        OracleDataReader rdr = cmd.ExecuteReader();
        if (rdr.Read())
          deptno = (uint)rdr.GetInt32(0);
        rdr.Close();
        cmd.Dispose();
        conn.Close();
        return deptno;
      } // GetDeptNo
    } // CLRLibrary1

**See Also:**

- [Oracle Database Extensions for .NET Developer's Guide for Microsoft Windows](../clrnt/intro.md) for more information about how to create .NET Stored procedures

- [Table 5-1](extenPorting.md)
