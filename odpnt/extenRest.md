This section covers important concepts that apply when Oracle Data Provider for .NET is used within a .NET stored procedure.

**Note:**

ODP.NET, Managed Driver and ODP.NET Core do not support .NET stored procedures.

### Implicit Database Connection

Within a .NET stored procedure, an implicit database connection is available for use to access Oracle data. This implicit database connection should be used rather than establishing a user connection because the [implicit database connection](glossary.md) is already established by the caller of the .NET stored procedure, thereby minimizing resource usage.

To obtain an `OracleConnection` object in a .NET stored procedure that represents the implicit database connection, set the `ConnectionString` property of the `OracleConnection` object to `"context` `connection=true"` and invoke the `Open` method. No connection string attributes can be used with `"context` `connection=true"`, except the `Statement` `Cache` `Size` attribute.

The availability of the implicit database connection can be checked at run time through the static `OracleConnection.IsAvailable` property. This property always returns `true` when Oracle Data Provider for .NET is used within a .NET stored procedure. Otherwise, `false` is returned.

**Note:**

DBLinks are not supported in .NET stored procedures.

Only one implicit database connection is available within a .NET stored procedure invocation. To establish more connections in addition to the implicit database connection, an explicit connection must be created. When the `Close` method is invoked on the `OracleConnection` that represents the implicit database connection, the connection is not actually closed. Therefore, the `Open` method of the same or another `OracleConnection` object can be invoked to obtain the connection that represents the implicit database connection.

The implicit database connection can only be acquired by the `Open` method invocation by a native Oracle thread that initially invokes the .NET stored procedure. However, threads spawned from the native Oracle thread can use implicit database connections that are obtained by the native Oracle thread.

**See Also:**

"[IsAvailable](ConnectionIsAvailable.md)"

### Transaction Support

The .NET stored procedure execution automatically inherits the current transaction on the implicit database connection. No explicit transaction can be started, committed, or rolled back inside a .NET stored procedure on a Context connection. However, explicit transaction can be started, committed, or rolled back inside a .NET stored procedure on a Client connection.

For example, `OracleConnection.BeginTransaction` is not allowed inside a .NET stored procedure for a context connection, but is allowed for a client connection. .NET stored procedures do not support distributed transactions. If you have enlisted a client connection in a distributed transaction and call a .NET stored procedure or function, an error occurs.

If a .NET stored procedure or function performs operations on the database that are required to be part of a transaction, the transaction must be started prior to calling the .NET stored procedure. Any desired commit or rollback must be performed after returning from the .NET stored procedure or function.

The following example consists of a client application and a .NET stored procedure, `InsertRecordSP`, that inserts an employee record into an `EMP` table.

#### Example (.NET Stored Procedure)

    using System;
    using System.Data;
    using Oracle.DataAccess.Client;
    // This class represents an Oracle .NET stored procedure that inserts
    // an employee record into an EMP table of SCOTT schema.
    public class InsertRecordSP
    {
        // This procedure will insert a row into the emp database
        // For simplicity we are using only two parameters, the rest are hard coded
        public static void InsertRecord( int EmpNo, string EmpName )
        {
            if(OracleConnection.IsAvailable == true )
            {
                OracleConnection conn = new OracleConnection(
                    "context connection=true");
                conn.Open();
                // Create new command object from connection context
                OracleCommand Cmd = conn.CreateCommand();
                Cmd.CommandText = "INSERT INTO EMP( EMPNO, ENAME, JOB," +
                    "MGR, HIREDATE, SAL, COMM, DEPTNO ) " +
                    "VALUES ( :1, :2, 'ANALYST', 7566, " +
                    "'06-DEC-04', 5000, 0, 20 )";
                Cmd.Parameters.Add( ":1", OracleDbType.Int32,
                    EmpNo, ParameterDirection.Input );
                Cmd.Parameters.Add( ":2", OracleDbType.Varchar2,
                    EmpName, ParameterDirection.Input );
                Cmd.ExecuteNonQuery();
            }
        }
    }

#### Example (Client Application)

The example enters new employee, Bernstein, employee number 7950, into the `EMP` table.

    // C#
    // This sample demonstrates how to start the transaction with ODP.NET client
    // application and execute an Oracle .NET stored procedure that performs
    // a DML operation. Since .NET stored procedure inherits the current
    // transaction from the implicit database connection,  DML operation
    // in .NET stored procedure will not be in auto-committed mode.
    // Therefore, it is up to the client application to do a COMMIT or ROLLBACK
    // after returning from .NET stored procedure
    using System;
    using System.Data;
    using Oracle.DataAccess.Client;
    // In this class we are starting a transaction on the client side and
    // executing a .NET stored procedure, which inserts a record into EMP
    // table and then verifies record count before and after COMMIT statement
    class TransactionSample
    {
        static void Main(string[] args)
        {
            OracleConnection Conn = null;
            OracleTransaction Txn = null;
            OracleCommand Cmd = null;
            try
            {
                Console.WriteLine( "Sample: Open DB connection in non auto-committed "
                   + "mode," +
                    "DML operation performed by .NET stored " +
                    "procedure doesn't have an effect before COMMIT " +
                    "is called." );
                // Create and Open oracle connection
                Conn = new OracleConnection();
                Conn.ConnectionString = "User Id=scott;Password=tiger;" +
                    "Data Source=oracle;";
                Conn.Open();
                // Start transaction
                Txn = Conn.BeginTransaction( IsolationLevel.ReadCommitted );
                // Create command object
                Cmd = new OracleCommand();
                Cmd.Connection = Conn;
                Cmd.CommandType = CommandType.StoredProcedure;
                Cmd.CommandText = "InsertRecord"; // .NET Stored procedure
                // Parameter settings
                OracleParameter EmpNoPrm = Cmd.Parameters.Add(
                    "empno", OracleDbType.Int32 );
                EmpNoPrm.Direction = ParameterDirection.Input;
                EmpNoPrm.Value = 7950;
                OracleParameter EmpNamePrm = Cmd.Parameters.Add(
                    "ename", OracleDbType.Varchar2, 10 );
                EmpNamePrm.Direction = ParameterDirection.Input;
                EmpNamePrm.Value = "Bernstein";
                // Execute .NET stored procedure
                Cmd.ExecuteNonQuery();
                Console.WriteLine( "Number of record(s) before COMMIT {0}",
                    RecordCount() );
                Txn.Commit();
                Console.WriteLine( "Number of record(s) after COMMIT {0}",
                    RecordCount() );
            }
            catch( OracleException OE )
            {
                Console.WriteLine( OE.Message );
            }
            finally
            {
                // Cleanup objects
                if( null != Txn )
                    Txn.Dispose();
                if( null != Cmd )
                    Cmd.Dispose();
                if( null != Conn && Conn.State == ConnectionState.Open )
                    Conn.Close();
            }
        }
        static int RecordCount()
        {
            int EmpCount = 0;
            OracleConnection Conn = null;
            OracleCommand Cmd = null;
            try
            {
                Conn = new OracleConnection( "User Id=scott;Password=tiger;" +
                    "Data Source=oracle;" );
                Conn.Open();
                Cmd = new OracleCommand( "SELECT COUNT(*) FROM EMP", Conn );
                Object o = Cmd.ExecuteScalar();
                EmpCount = Convert.ToInt32(o.ToString());
            }
            catch( OracleException OE )
            {
                Console.WriteLine( OE.Message );
            }
            finally
            {
                if( null != Cmd )
                    Cmd.Dispose();
            }
            return EmpCount;
           }
          }

### Unsupported SQL Commands

Transaction controls commands such as `COMMIT`, `ROLLBACK`, and `SAVEPOINT` are not supported in a .NET stored procedure.

Data definition commands such as `CREATE` and `ALTER` are not supported with an implicit database connection, but they are supported with an explicit user connection in a .NET stored procedure.

### Oracle User-Defined Type (UDT) Support

UDTs are not supported within a context connection but they are supported with a client connection. UDTs are not supported as parameters to .NET stored procedures.
