Oracle Application Continuity enables database requests to automatically replay transactional or non-transactional operations in a non-disruptive and rapid manner in the event of a severed database session, which results in a recoverable error. Application Continuity improves end-user experience by masking planned and unplanned related errors. Applications can be developed without complex logic to handle exceptions, while automatically replaying database operations upon a recoverable error.

Without Application Continuity, it is almost impossible to mask outages in a safe and reliable manner. Common issues encountered include:

- The client state remains at present time, with entered data, returned data, and variables cached, while the database state changes are lost.

- If a transaction commit has occurred, the commit message is not durable. Moreover, checking a lost request does not guarantee that it will not commit after being checked.

- Non-transactional database session state is lost.

- If the request can continue, the database and the client session must be synchronized.

Application Continuity is available with Oracle Database Enterprise Edition with a Real Application Clusters or Active Data Guard option license.

### ODP.NET and Application Continuity

ODP.NET, Unmanaged Driver first supported Application Continuity with version 12.2. While Application Continuity was first introduced in Oracle Database 12c Release 1 (12.1), ODP.NET requires a minimum of Oracle Database 12c Release 2 (12.2) server.

**Note:**

ODP.NET, Managed Driver and ODP.NET Core do not support Application Continuity.

With Application Continuity enabled, ODP.NET ensures all the application's executed statements are logged appropriately so that they can be replayed upon a recoverable error. This applies for all application SQL and PL/SQL, as well as any internal ODP.NET operations.

On the client side, Application Continuity is enabled by setting the ODP.NET connection string attribute, `Application Continuity=true`.

If `Application Continuity` is set to `true`, but the database server does not enable `Application Continuity`, ODP.NET will still create new connections. However, these connections will not be `Application Continuity` enabled.

**See Also:**

- [Oracle Call Interface Programmer's Guide](../lnoci/session-and-connection-pooling.md)

- [Oracle Real Application Clusters Administration and Deployment Guide](../racad/ensuring-application-continuity.md)
