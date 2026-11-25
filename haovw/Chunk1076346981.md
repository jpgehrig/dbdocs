## Configuring Level 3: Mask Unplanned and Planned Failovers from Applications

Building on Level 1 and Level 2, the features presented in Level 3 are recommended to achieve continuous availability for applications, regardless of database interruptions, outages, timeouts, or when application workload won't drain.

Application Continuity

Application Continuity (AC) hides unplanned outages, starting with Oracle Database 12.1 for thin Java-based applications, and Oracle Database 12.2.0.1 for OCI and ODP.NET based applications with support for open-source drivers, such as Node.js, and Python, beginning with Oracle Database 19c.

Application Continuity rebuilds the session by recovering the session from a known point which includes session states and transactional states. Application Continuity rebuilds all in-flight work. The application continues as it was, seeing a slightly delayed execution time when a failover occurs.

The standard mode for Application Continuity is for OLTP applications using an Oracle connection pool or a third party connection pool with request boundaries.

Transparent Application Continuity

Starting with Oracle Database19c, Transparent Application Continuity (TAC) transparently tracks and records session and transactional state so the database session can be recovered following recoverable outages. This is done with no reliance on application knowledge or application code changes, allowing Transparent Application Continuity to be enabled for applications by default.

Application transparency and failover are achieved by consuming the state-tracking information that captures and categorizes the session state usage as the application issues user calls.

Choose AC or TAC

If you have an OLTP application that uses an Oracle connection pool (or RedHat JBOSS EAP), you have a choice between Application Continuity and Transparent Application Continuity.

To decide which feature to use, you can run the application with each and choose the one with higher value for cumulative user calls protected by Application Continuity.

If you are not using an Oracle connection pool (as with SQL\*Plus 19c or SQLcl 23), or you do not have knowledge about the application, then use TAC.

Planned Failover with AC and TAC

Planned failover is failover that is invoked by the Oracle Database at points where the database decides that a session is replayable and is expected not to drain.

Planned failover is enabled by default when using AC or TAC. It improves situations where other draining methods are not active, for example, because FAN or connection tests are not configured.

Planned failover expedites maintenance by failing over early when replay is enabled.

For example, planned failover with TAC is the maintenance solution used with SQL\*Plus.

See also:

- [Ensuring Application Continuity](../racad/ensuring-application-continuity.md) in Oracle Real Application Clusters Administration and Deployment Guide

- [Blog: database-heartbeat Application Continuity](https://database-heartbeat.com/category/application-continuity/)

- [Restrictions and Other Considerations for Application Continuity](../racad/ensuring-application-continuity.md)

### Configure Services for AC and TAC

#### Set COMMIT_OUTCOME = TRUE

Determines whether transaction `COMMIT` outcome is accessible after the `COMMIT` has executed. While the database guarantees that `COMMIT` is durable, this setting ensures that the outcome of the `COMMIT` is durable. Applications use this feature to probe the status of the commit last executed after an outage, and is available to applications to determine an outcome

#### Set FAILOVER_TYPE

Set `FAILOVER_TYPE` to `AUTO` when using TAC.

Alternatively, set the database service attribute `FAILOVER_TYPE` to `TRANSACTION` to use Application Continuity.

#### Set FAILOVER_RESTORE

An application can be written to change the database session state (using `ALTER SESSION` commands typically), and these states need to be in place if you want the work to be replayed after failover.

To restore your session state at failover, set the attribute `FAILOVER_RESTORE` on your database service. Use `LEVEL1` for AC or use `AUTO` for TAC.

The use of wallets is highly recommended. AC and TAC leverage wallets to ensure all modifiable database parameters are restored automatically with `FAILOVER_RESTORE`. Wallets are enabled for Autonomous Database and are the same as those used for database links.

See also:

[Configuring a Keystore for FAILOVER_RESTORE](../racad/ensuring-application-continuity.md) in Oracle Real Application Clusters Administration and Deployment Guide to learn how to set up wallets for databases.

#### Examples

Example service configuration for TAC:

    $ srvctl add service -db mydb -service my_service -pdb mypdb
     –preferred inst1 -available inst2 -commit_outcome TRUE -failovertype AUTO
     -failover_restore AUTO -notification TRUE -drain_timeout 300 -stopoption IMMEDIATE
     -role PRIMARY

Example service configuration for AC:

    $ srvctl add service -db mydb -service my_service -pdb mypdb –preferred inst1
     -available inst2 -commit_outcome TRUE -failovertype TRANSACTION
     -failover_restore LEVEL1 -notification TRUE -drain_timeout 300 -stopoption IMMEDIATE
     -role PRIMARY

### Return Connections to the Connection Pool

Request boundaries are required for Application Continuity (AC) and are recommended for Transparent Application Continuity (TAC).

Request boundaries are automatically embedded in the session for you when you use an Oracle connection pool, such as Universal Connection Pool (UCP) or OCI Session Pool. The application should return the connection to the Oracle connection pool when the unit of work, the database request, is completed, to insert the end of request boundary. This also applies to using ODP.Net Unmanaged Provider, WebLogic Active GridLink, and RedHat.

### Side Effect

When a database request includes an external call from the database, such as sending mail or transferring a file, this is called a **side effect**.

When replay occurs, there is a choice as to whether side effects should be replayed. Many applications want to repeat side effects such as creating journal entries, sending mail, and performing file writes. For Application Continuity, side effects are replayed, but can be programmatically avoided. Conversely, Transparent Application Continuity does not replay side effects.

Starting with Oracle 23ai, there are PL/SQL procedures to set rules for how replay handles side effects. See the `REPLAY` related procedures in the `DBMS_APP_CONT` in [Summary of DBMS_APP_CONT Subprograms](../arpls/DBMS_APP_CONT.md).

### Restore Original Function Values During Replay

Oracle Database 19c keeps the values of `SYSDATE`, `SYSTIMESTAMP`, `SYS_GUID`, and sequence.`NEXTVAL, CURRENT_TIMESTAMP`, and `LOCALTIMESTAMP` for SQL during replay.

If you are using PL/SQL, then `GRANT KEEP` for application users, and use the `KEEP` clause for a sequence owner. When the `KEEP` privilege is granted, replay applies the original function result at replay.

    SQL> GRANT KEEP DATE TIME to scott;
    SQL> GRANT KEEP SYSGUID to scott;
    SQL> GRANT KEEP SEQUENCE mySequence on mysequence.myobject to scott;

### JDBC Configuration

Ensure your JDBC configuration uses:

- The recommended JDBC data source for standalone JDBC, or configure it as connection factory class for a Java connection pool (such as UCP) or a WebLogic AGL Server connection pool or RedHat JBOSS EAP.

  See [Configuring the Data Source for Application Continuity](../jjucp/application-continuity-using-ucp.md) in the Oracle Universal Connection Pool Developer's Guide for information about enabling AC and TAC on UCP. You configure the JDBC driver data source class `oracle.jdbc.replay.OracleDataSourceImpl` as the connection factory class on the UCP data source `PoolDataSourceImpl`.

  For 19c.x.x.x and older drivers, use `oracle.jdbc.replay.OracleDataSourceImpl`

  For 21ai.x.x.x and newer drivers, use `oracle.jdbc.datasource.impl.OracleDataSource`

  Note that the exact data source and connection pool configuration are always specific to a particular vendor's product, such as a 3rd-party connection pool, framework, application server, or container.

- The JDBC driver statement cache in place of an application server statement cache.

  This allows the driver to know that statements are closed and memory is to be freed at the end of requests. To use the JDBC statement cache, use the connection property `oracle.jdbc.implicitStatementCacheSize (OracleConnection.CONNECTION_PROPERTY_IMPLICIT_STATEMENT_CACHE_SIZE)`. The value for the cache size matches your number of `open_cursors`. For example:

  `oracle.jdbc.implicitStatementCacheSize=nnn` where `nnn` is typically between 10 and 100, and is equal to the number of open cursors your application maintains.

### Monitoring

Application Continuity collects statistics to monitor your protection levels.

These statistics are saved in the Automatic Workload Repository (AWR) and are available in Automatic Workload Repository reports. Review the statistics to determine the extent of protected calls or If the protected call count or protected time decreases. Use the `ACCHK` utility for details as to the cause.

See [Protection Level Statistics](../racad/ensuring-application-continuity.md) for details about using database statistics for analyzing AC protection.
