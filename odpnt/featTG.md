Transaction Guard allows managed and unmanged ODP.NET applications to use at-most-once execution in case of planned and unplanned outages and repeated submissions. Without Transaction Guard, applications that attempt to retry operations following outages can cause logical corruption by committing duplicate transactions.

After an outage, one of the traditional problems for recovering applications had been the non-durable commit message sent back to the client. If there is a break between the client and the server, the client sees an error message indicating that the communication failed, also known as a recoverable error. This error does not inform the application if the submission executed any commit operations, or if a procedural call ran to completion while executing all expected commits. The error also does not indicate session state changes or intermittent failures. The client is left wondering if the transaction committed and if it fully completed.

These recoverable errors may require end users or applications to attempt replay by issuing duplicate transaction submissions or other forms of logical corruption. The transaction cannot be validly resubmitted if the non-transactional state is incorrect or if it is committed. Continuing to process a committed but not completed call can result in the application using a database session that is in the wrong state.

### ODP.NET and Transaction Guard

Transaction Guard allows ODP.NET, Managed Driver and ODP.NET, Unmanaged Driver to eliminate duplicate transactions automatically and transparently, and in a manner that scales.

When a failure occurs, such as a node, network, or database failure, ODP.NET applications can deterministically conclude whether the transaction committed by querying its status, if the database service is up. Oracle retains the transaction status automatically, even after one of these failures.

In ODAC 12c Release 4, using Transaction Guard application development has been streamlined, reducing the application logic needed to determine the transaction outcome. Moreover, these benefits are available to both managed and unmanaged ODP.NET.

When a recoverable error is raised by a Transaction Guard enabled database service upon a database commit or upon a SQL or PL/SQL execution, which could have called a commit, then an ODP.NET `OracleException` is created with an `OracleLogicalTransaction` instance. `OracleLogicalTransaction` is always non-null. The database maintains the outcome of the logical transaction for the retention period specified by the administrator. ODP.NET automatically queries the database on behalf of the application when a recoverable error occurs so that the `OracleLogicalTransaction` object instance on the `OracleException` object can indicate whether the transaction has committed or not and whether the user call has completed or not.

If the status is committed, then the transaction has completed successfully. No other action is likely needed by the administrator.

If not committed, then ODP.NET applications can learn the current transaction state, whether it is recoverable, and whether it can be retried using `OracleLogicalTransaction`. If the error is recoverable, then the transaction is safe to re-submit. If the error is not recoverable, the application will need to determine the transaction outcome using an alternative mechanism.

**Note:**

Transaction Guard supports only local transactions. It does not support distributed transactions.

The Transaction Guard feature is enabled or disabled through the Oracle service-level configuration through the `COMMIT_OUTCOME` setting. By default, it is not enabled. This setting can be changed without bringing down the database. Only new connections created against the service will use the new setting.

Here's an example of setting the `COMMIT_OUTCOME` using `SRVCTL`:

    srvctl modify service -d orcl -s GOLD -commit_outcome TRUE

**Note:**

Grant the `EXECUTE` privilege on the `DBMS_APP_CONT` package to the database users that retrieve the transaction status:

    GRANT EXECUTE ON DBMS_APP_CONT TO <user name> ;

The following is an example ODP.NET Transaction Guard application scenario:

An ODP.NET application receives a Fast Application Notification (FAN) down event or error. FAN automatically aborts the dead session and the application receives an `OracleException`. A Transaction Guard application built to handle errors transparently would do the following:

1.  `OracleException.OracleLogicalTransaction.LogicalTransactionId` property

    The value returned by this property will be non-null if

    - Transaction Guard is enabled,

    - Transparent Application Failover (TAF) is not enabled on the connection, and

    - ODP.NET was not able to determine the outcome of the transaction.

    For a given `OracleException` object, if `OracleLogicalTransaction.Committed` and `OracleLogicalTransaction.UserCallCompleted` return all nulls, then the error is either a non-recoverable error, Transaction Guard is not enabled, or TAF is enabled on the connection. In any of these cases, the application should rollback then re-submit the transaction.

    The `LogicalTransactionId` property will return null even if Transaction Guard is enabled and a recoverable error happens, if `OracleLogicalTransaction.Committed` is true or false.

2.  `OracleException.OracleLogicalTransaction.Committed` property

    This property returns true or false, depending on whether the transaction has been committed or not. If it returns null, then

    - ODP.NET could not determine the outcome of the transaction,

    - Error is not recoverable,

    - Transaction Guard was not enabled, or

    - TAF is enabled on the connection.

3.  `OracleException.OracleLogicalTransaction.UserCallCompleted` property

    This property returns true if the user call has completed, else it returns false. This property returns null if

    - Transaction Guard was not enabled,

    - Error is not recoverable,

    - TAF is enabled on the connection, or

    - ODP.NET is not able to determine if the user call has completed or not.

    See the following table for the implications of what `Committed` and `UserCallCompleted` values mean.

Table 3-6 Implication of Committed and UserCallCompleted Values

| Committed Value | UserCallCompleted Value | Outcome                                                                                                                                                             |
|:----------------|:------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `True`          | `True`                  | The transaction was successful. The result can be returned to the application.                                                                                      |
| `False`         | `False`                 | The transaction was not successful. The application can resubmit the transaction again.                                                                             |
| `True`          | `False`                 | The transaction committed, but there may be additional state, such as row counts or nested PL/SQL logic, that prevents the application from continuing as expected. |

Example 3-4 Using Transaction Guard: Sample Code

    using System;
    using Oracle.DataAccess.Client;
    //alternatively can use using Oracle.ManagedDataAccess.Client;

    class TransactionGuardSample
    {
        static void Main()
        {
            bool bReadyToCommit = false;

            string constr = "user id=hr;password=hr;data source=oracle";
            OracleConnection con = new OracleConnection(constr);
            OracleTransaction txn = null;
            OracleCommand cmd = null;

            try
            {
                string sql = " update employees set salary=10000 where employee_id=103";
                con.Open();
                txn = con.BeginTransaction();
                cmd = new OracleCommand(con, sql);
                cmd.ExecuteNonQuery();
                bReadyToCommit = true;
            }
            catch (Exception ex)
            {
                // rollback here as the SQL execution is unsuccessful
                txn.Rollback();
                Console.WriteLine(ex.ToString());
            }

            try
            {
                if (bReadyToCommit)
                    txn.Commit();
            }
            catch (Exception ex)
            {
                if (ex is OracleException)
                {
                    //  It's safe to re-submit the work if the error is recoverable and the transaction has not been committed
                    if (ex.IsRecoverable && ex.OracleLogicalTransaction.Committed == false)
                    {
                        // safe to re-submit work
                    }
                    else
                    {
                        // do not re-submit work
                    }
                }
            }
            finally
            {
                // dispose all objects
                txn.Dispose();
                cmd.Dispose();
                con.Dispose(); // place the connection back to the connection pool
            }
        }
    }

Transaction Guard is not supported when Transparent Application Failover (TAF) is enabled for the service. As such, when TAF is enabled, the `LogicalTransactionId` will always be null and the transaction outcome will not be determined.

**See Also:**

- "[OracleLogicalTransaction Class](OracleLogicalTransactionClass.md)"

- [Oracle Database Development Guide](../adfns/transaction-guard.md) for more information on Transaction Guard
