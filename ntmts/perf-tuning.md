These topics provide [Microsoft Transaction Server](glossary.md) performance tuning information.

- Improving Microsoft Transaction Server Application Performance

- Managing Microsoft Transaction Server Connections

- Increasing the Transaction Timeout Parameter

- Changing Initialization Parameter Settings

- Additional Parameters

- Starting MSDTC

### Improving Microsoft Transaction Server Application Performance

Optimizing the programming methods of your application improves its performance. For example, placing all code for a given transaction into one [component object model (COM)](glossary.md) component means you do not mark that component as transactional. This eliminates the overhead of going through Microsoft Transaction Server. You can subsequently use the Oracle commit or rollback functions to control that transaction in the component. If you are using the [Oracle Call Interface (OCI)](glossary.md), you can still use `ORAMTSSvcGet()`, but you can also use the `ORAMTS_CFLG_NOIMPLICIT` flag. If you are updating across two or more Oracle Database instances, use database links and connect to one database from the COM component.

**See Also:**

"[OCI Integration with Microsoft Transaction Server](program.md)" for more information on using `ORAMTSSvcGet()`

### Managing Microsoft Transaction Server Connections

When a .NET or COM component ends a session with the Oracle Database, the connection does not immediately terminate. Instead, it remains idle in a connection pool, where it is available for reuse by another component attempting a new connection to the Oracle Database.

#### Connection Pooling Registry Parameters

The idle period during which a connection is reusable reduces the resource costs associated with opening a new connection. The amount of time that the connection remains idle and available in the connection pool is determined by several registry parameter settings. You can modify these parameters on the computers on which the client Microsoft Transaction Server components are installed, in the file `HKEY_``LOCAL_MACHINE``\SOFTWARE\ORACLE\``HOMEID`:

##### ORAMTS_CONN_POOL_TIMEOUT

The time, in seconds, that the connection remains idle and available for reuse in the client side connection pool, before timing out and being released. The default value of this parameter is `120` seconds.

##### ORAMTS_SESS_TXNTIMETOLIVE

The time, in seconds, that the connection established using `OraMTSSvcGet()` remains alive in the client side connection pool after being released by an `OraMTSSvcRel()` call. The sum of the `ORAMTS_CONN_POOL_TIMEOUT` and `ORAMTS_NET_CACHE_TIMEOUT` values determines the actual time before a connection terminates completely. The default value of this parameter is `120` seconds.

##### ORAMTS_NET_CACHE_TIMEOUT

The resource dispenser implemented inside Oracle Services for Microsoft Transaction Server establishes pooled connections to Oracle databases. When these connections are no longer in use, the user sessions are disconnected after the timeout specified by `ORAMTS_CONN_POOL_TIMEOUT`. However, the underlying Oracle Net connections are cached for the period specified by this parameter. After this time, expressed in milliseconds, a cached Oracle Net connection to the database will be terminated. The default value of this parameter is 120000 milliseconds. Oracle recommends setting this parameter to a higher value than the value for `ORAMTS_CONN_POOL_TIMEOUT`. The sum of the time periods specified for `ORAMTS_CONN_POOL_TIMEOUT` and `ORAMTS_NET_CACHE_TIMEOUT` determines the actual time before a connection terminates completely.

##### ORAMTS_NET_CACHE_MAXFREE

The maximum number of free server connections that should be maintained in the client-side connection pool at a given time. The default value of this parameter is `5`.

##### ORAMTS_OSCREDS_MATCH_LEVEL

The level of Windows security checking implemented when the `OS_ROLES` initialization parameter in the `init.ora` file is `true`.

When a user establishes a connection to the Oracle Database using the `CONNECT` command, the Windows username is associated with specific database roles and privileges. When the user disconnects, this connection becomes idle and available in the pool. When another user enters the `CONNECT` command, if the Windows username is identical to the one used by the first user, the second user can receive the same database roles and privileges as the first user. This is a considerable security concern, especially if the second user possesses only the `CREATE SESSION` and `RESOURCE` database roles but receives the `DBA` privileges of the first user.

By default, the `ORAMTS_OSCREDS_MATCH_LEVEL` parameter value is `OS_AUTH_LOGIN`, and Windows security checking is performed only if the username and password are `NULL`.

The most secure setting for this parameter is `ALWAYS`, which ensures that Windows security checking is performed in all cases, and takes care of possible security breaches due to identical non-null Window usernames.

Because Windows security checking is a resource-intensive operation, you may wish to set the value of this parameter to `NEVER`. However, if you know that `OS_ROLES` is `true`, or if you use operating system-authenticated connections, you should avoid this option.

### Increasing the Transaction Timeout Parameter

If transaction requests are timing out before completing, the transaction timeout parameter may be set too low. Increase the transaction timeout parameter to ensure that transactions have enough time to complete.

To increase the transaction timeout parameter:

1.  Go to the Windows computer on which Microsoft Transaction Server is installed.
2.  From the Start menu, select Programs, then Administrative Tools, then Component Services.
    The Component Services window appears.
3.  Double-click Console Root in the Component Services window so its tree structure expands.
4.  Double-click Component Services.
5.  Double-click Computers.
6.  Right-click My Computer.
    A menu appears with several options.
7.  Choose Properties.
    The My Computer Properties dialog box appears.
8.  Choose the Options tab.
9.  Enter a value in the Transaction Timeout field and click OK.
    The transaction timeout value is increased. For most environments, `60` seconds may be enough. However, if the transaction is competing with numerous concurrent transactions, this value may be too low.

### Changing Initialization Parameter Settings

You may need to modify several initialization parameters to use the Oracle Database with Microsoft Transaction Server. The values you should set these parameters to are based on the database workload environment.

To verify initialization parameter file values, follow these steps:

1.  Ensure that you have `SYSDBA` privileges.
2.  Go to the computer on which the Oracle Database is installed.
3.  Start SQL\*Plus:
        C:\> sqlplus /NOLOG
4.  Connect to the database as `SYSDBA`:
        SQL> CONNECT / AS SYSDBA
5.  Check the value for the `SESSIONS` parameter:
        SQL> SHOW PARAMETER SESSIONS
6.  Check the value for the `PROCESSES` parameter:
        SQL> SHOW PARAMETER PROCESSES

    The current settings for both `SESSIONS` and `PROCESS` parameters are typically appropriate for running the Microsoft application demo. For creating and deploying .NET or COM-based applications, the values for these parameters depend on the database environment's anticipated workload. For example, if you anticipate `100` concurrent connections to the Oracle Database, consider setting both values to `200` to accommodate a possible system overload. Ensure that you do not set these parameters too high, because they are resource-intensive.
7.  Set the following initialization parameters to at least these values:
    - `SESSIONS` = `200` (or larger if anticipating heavier loads)

    - `PROCESSES` = `200` (or larger if anticipating heavier loads)
8.  Shut down the Oracle Database:
        SQL> SHUTDOWN
9.  Restart the Oracle Database:
        SQL> STARTUP
10. Exit SQL\*Plus:
        SQL> EXIT

    **See Also:**

    [Oracle Database Reference](../refrn/initialization-parameters-2.md) for information about these parameters.

### Additional Parameters

Use the registry variable `ORAMTS_ABORT_MODE` to control whether a new connection always performs an abort or whether the originally enlisted connection can be used to perform the abort, that is, whether the abort is synchronous or asynchronous.

By default, the originally enlisted connection performs transaction aborts (whenever possible).

Registry variable: `ORAMTS_ABORT_MODE`

Values:

- `ORAMTS_ABORT_MODE_NEW_CONN_ONLY:` Results in asynchronous aborts. A new connection to the database is opened for performing transaction aborts.

- Any other value implies the default behavior.

### Starting MSDTC

The [Microsoft Distributed Transaction Coordinator (MS DTC)](glossary.md) must be running to enable communication with Oracle Services for Microsoft Transaction Server.

To start MS DTC, follow these steps:

1.  On the computer where Microsoft Transaction Server is installed, from the Start menu, choose Programs, then Administrative Tools, then Component Services.
    The Component Services window appears.
2.  In the Component Services Window, expand Component Services under the Console Root.
3.  Expand Computers under Component Services.
4.  Right-click My Computer.
    A menu with several options appears.
5.  Choose Start MSDTC.
    MS DTC starts.
