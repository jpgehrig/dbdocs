Database Resident Connection Pool (DRCP) is a connection pool in the server that is shared across many clients. You should use DRCP in connection pools where the number of active connections is fairly less than the number of open connections. As the number of instances of connection pools that can share the connections from DRCP pool increases, the benefits derived from using DRCP increases. DRCP increases Database server scalability and resolves the resource wastage issue that is associated with middle-tier connection pooling.

This chapter contains the following sections:

- Overview of Database Resident Connection Pooling

- Enabling Database Resident Connection Pooling

- About Sharing Pooled Servers Across Multiple Connection Pools

- DRCP Tagging

- PL/SQL Callback for Session State Fix Up

- APIs for Using DRCP

### 23.1 Overview of Database Resident Connection Pooling

In middle-tier connection pools, every connection cache maintains a minimum number of connections to the server. Each connection represents used up resources at the server. All these open connections are not utilized at any given time, which means that there are unused resources that unnecessarily take up server resources. In a multiple middle-tier scenario, these connections are not shared with any other middle tier and are retained in the cache even if some of these are idle. However, a large number of such middle-tier connection pools increase the number of inactive connections to the Database server significantly and waste a lot of Database resources because all the connections do not remain active simultaneously.

For example, in a middle-tier connection pool, if the minimum pool size is 200, then the connection pool has 200 connections to the server, and the Database server has 200 server processes associated with these connections. If there are 30 middle tiers with a connection pool of minimum size 200, then the server has 6000 (200 \* 30) corresponding server processes running. Typically, on an average only 5% of the connections, and in turn, server processes are in use at any given time. So, out of the 6,000 server processes, only 300 server processes are active at any given time. This leads to over 5,700 unused server processes on the server. These unused processes are the wasted resources on the server.

The Database Resident Connection Pool implementation creates a pool on the server side, which is shared across multiple client pools. This significantly lowers memory consumption on the server because of reduced number of server processes on the server and increases the scalability of the Database server.

**See Also:**

- [Oracle Database Concepts](../cncpt/application-and-networking-architecture.md)

- [Oracle Database Administrator’s Guide](../admin/managing-processes.md)

### 23.2 Enabling Database Resident Connection Pooling

This section describes how to enable DRCP in the server side and the client side:

- Enabling DRCP on the Server Side

- Enabling DRCP on the Client Side

#### 23.2.1 Enabling DRCP on the Server Side

You must be a database administrator (DBA) and must log on as `SYSDBA` to start and end a pool. This section discusses the following concepts:

- Starting the Default Connection Pool

- Configuring the Default Connection Pool

- Ending a Pool

- Setting the Statement Cache Size

**Note:**

The features of DRCP can be leveraged only with a connection pool on the client because JDBC does not have a default pool on its own. If you do not have a client connection pool and make any change to the Database with auto commit set to `false`, then the changes are not committed to the Database while closing the connection.

##### Starting the Default Connection Pool

Run the `dbms_connection_pool.start_pool` method with the default settings to start the Oracle Database default connection pool, `SYS_DEFAULT_CONNECTION_POOL`. For example:

    sqlplus /nolog
    connect / as sysdba
    execute dbms_connection_pool.start_pool();

##### Configuring the Default Connection Pool

The default connection pool is configured using default parameter values. You can use the procedures in the `DBMS_CONNECTION_POOL` package to configure the connection pool for Database Resident Connection Pooling.

Oracle Database 12c Release 2 (12.2.0.1) introduced the `MAX_TXN_THINK_TIME` parameter, which is a new parameter for specifying the think timeout for pooled servers with transactions in progress. The think timeout is the maximum time of inactivity, in seconds, for a client after it obtains a pooled server from the pool.

**See Also:**

[Oracle Database Administrator’s Guide](../admin/managing-processes.md) for more information about configuration parameters

##### Ending a Pool

Run the `dbms_connection_pool.stop_pool` method with the default settings to end the pool. For example:

    sqlplus /nolog
    connect / as sysdba
    execute dbms_connection_pool.stop_pool();

##### Setting the Statement Cache Size

If you use DRCP, caching is also done at the server side. So, you must specify the statement cache size on the server side in the following way, where 50 is the preferred size:

    execute DBMS_CONNECTION_POOL.CONFIGURE_POOL (session_cached_cursors=>50);

**Related Topics**

- [About Statement Caching](statement-and-resultset-caching.md)

#### 23.2.2 Enabling DRCP on the Client Side

Perform the following steps to enable DRCP on the client side:

**Note:**

The example in this section uses Universal Connection Pool as the client-side connection pool. For any other connection pools, you can enable DRCP by performing the following two steps and using `oracle.jdbc.pool.OracleConnectionPoolDataSource` as the connection factory.

- Pass a non-null and non-empty String value to the connection property `oracle.jdbc.DRCPConnectionClass`

- Append (`SERVER=POOLED`) to the `CONNECT_DATA` in the long connection string

You can also specify `(SERVER=POOLED)` in short URL from as follows:

    jdbc:oracle:thin:@//<host>:<port>/<service_name>[:POOLED]

For example:

    jdbc:oracle:thin:@//localhost:5221/orcl:POOLED

The following example shows how to enable DRCP on client side:

**Note:**

In UCP, if you do not provide a connection class, then the connection pool name is used as the connection class name by default.

Example 23-1 Enabling DRCP on Client Side Using Universal Connection Pool

    String url = "jdbc:oracle:thin:@//localhost:5521/orcl:POOLED";
    PoolDataSource pds = PoolDataSourceFactory.getPoolDataSource();
    pds.setConnectionFactoryClassName("oracle.jdbc.pool.OracleDataSource");
    // Set DataSource Property
    pds.setUser("HR");
    pds.setPassword("hr");
    System.out.println ("Connecting to " + url);
    pds.setURL(url);
    pds.setConnectionPoolName("HR-Pool1");
    pds.setMinPoolSize(2);
    pds.setMaxPoolSize(3);
    pds.setInitialPoolSize(2);
    Properties prop = new Properties();
    prop.put("oracle.jdbc.DRCPConnectionClass", "HR-Pool1");
    pds.setConnectionProperties(prop);

### 23.3 About Sharing Pooled Servers Across Multiple Connection Pools

To share pooled server processes on the server across multiple Connection pools, set the same DRCP Connection class name for all the pooled server processes on the server. You can set the DRCP Connection class name using the connection property `oracle.jdbc.DRCPConnectionClass`.

### 23.4 DRCP Tagging

DRCP enables you to request the server connection pool to associate a server process with a particular tag name. You can apply a tag to a given connection and retrieve that tagged connection later. Connection tagging enhances session pooling because you can retrieve specific sessions easily.

Starting from Oracle Database 12c Release 2 (12.2.0.1), DRCP provides support for multiple tagging. By default, this feature is disabled because of compatibility factor with existing DRCP applications. Set the `oracle.jdbc.UseDRCPMultipletag` connection property to `TRUE` for enabling this feature in your DRCP application.

Once you enable the multiple tagging feature, then the same APIs that you used for setting DRCP tags, can be used for setting multiple DRCP tags, only difference being the separator. Key and value of a DRCP tag are separated by an equal (`=`) character and multiple tags are separated by a semi-colon (`;`) character.

Remember the following points while working with DRCP tags:

- Key and value of a tag cannot be NULL or Empty.

- When you specify multiple tags, then the leftmost tag has the highest priority and the rightmost tag has the lowest priority.

- While retrieving a tagged connection, if a complete match is not found (all tags are not matched), then it searches for a partial match.

**Note:**

Starting from Oracle Database 12c Release 2 (12.2.0.1), DRCP sessions belonging to the same database user, but different proxy users, can be shared among the proxy users.

**See Also:**

[Oracle Call Interface Programmer's Guide](../lnoci/session-and-connection-pooling.md) for more information about session pooling and connection tagging

### 23.5 PL/SQL Callback for Session State Fix Up

Starting from Oracle Database 12c Release 2 (12.2.0.1), a PL/SQL based fix-up callback for the session state can be provided on the server. This application-provided callback transforms a session checked out from the pool to the desired state requested by the application. This callback works with or without Database Resident Connection Pooling (DRCP).

**Note:**

The PL/SQL based fix-up callback is only applicable for multiple tagging.

Using this callback can improve the performance of your application because the fix-up logic is run for the session state on the server. So, this feature eliminates application round-trips to the database for the fix-up logic. An appropriate installation user, who must be granted execute permissions on the related package, should register the fix-up callback during application installation.

Example 23-2 Example of PL/SQL Fix-Up Callback

Following is an example implementation of the PL/SQL fix up callback to fix up the session properties `SCHEMA` and `CURRENCY`:

    CREATE OR REPLACE PACKAGE mycb_pack AS
    PROCEDURE mycallback (
    desired_props IN VARCHAR2,
    actual_props IN VARCHAR2
    );
    END;
    /

    CREATE OR REPLACE PACKAGE BODY mycb_pack AS
    PROCEDURE mycallback (
    desired_props IN VARCHAR2,
    actual_props IN VARCHAR2
    ) IS
    property VARCHAR2(64);
    key VARCHAR2(64);
    value VARCHAR2(64);
    pos number;
    pos2 number;
    pos3 number;
    idx1 number;

    BEGIN
    idx1:=1;

    pos:=1;
    pos2:=1;
    pos3:=1;
    property := 'tmp';
    -- To check if desired properties are part of actual properties
    while (pos > 0 and length(desired_props)>pos)
    loop
    pos := instr (desired_props, ';', 1, idx1);
    if (pos=0)
    then
    property := substr (desired_props, pos2);
    else
    property := substr (desired_props, pos2, pos-pos2);
    end if ;
    pos2 := pos+1;
    pos3 := instr (property, '=', 1, 1);
    key := substr (property, 1, pos3-1);
    value := substr (property, pos3+1);
    if (key = 'CURRENCY') then
    EXECUTE IMMEDIATE 'ALTER SESSION SET NLS_CURRENCY=''' || value || '''';
    elsif (key = 'SCHEMA') then
    EXECUTE IMMEDIATE 'ALTER SESSION SET CURRENT_SCHEMA=' || value;
    end if;
    idx1 := idx1+1;
    end loop;

    END; -- mycallback
    END mycb_pack;
    /

**See Also:**

[Oracle Database JDBC Java API Reference](../jajdb/index.md)

### 23.6 APIs for Using DRCP

If you want to take advantage of DRCP with higher granular control for your custom connection pool implementations, then you must use the following APIs declared in the `oracle.jdbc.OracleConnection` interfaces:

- `attachServerConnection`

- `detachServerConnection`

- `isDRCPEnabled`

- `isDRCPMultitagEnabled`

- `getDRCPReturnTag`

- `needToPurgeStatementCache`

- `getDRCPState`

**See Also:**

[Oracle Database JDBC Java API Reference](../jajdb/index.md)
