This chapter describes the basics of developing C++ applications using Oracle C++ Call Interface (OCCI) to work with data stored in relational databases.

This chapter contains these topics:

- About Connecting to a Database

- About Pooling Connections

- About Executing SQL DDL and DML Statements

- About Types of SQL Statements in the OCCI Environment

- About Executing SQL Queries

- About Executing Statements Dynamically

- About Using Larger Row Count and Error Code Range Data Types

- About Committing a Transaction

- Caching Statements

- About Handling Exceptions

### 3.1 About Connecting to a Database

You have several different options for how your application connects to the database.

This section includes the following topics:

- Creating and Terminating an Environment

- Opening and Closing a Connection

- About Support for Pluggable Databases

#### 3.1.1 Creating and Terminating an Environment

All OCCI processing takes place inside the `Environment` class. An OCCI environment provides application modes and user-specified memory management functions. Example 3-1 illustrates how to create an OCCI environment.

All OCCI objects created with the `create``xxx``()` methods (connections, connection pools, statements) must be explicitly terminated. When appropriate, you must also explicitly terminate the environment. Example 3-2 shows how you terminate an OCCI environment.

In addition, an OCCI environment should have a scope that is larger than the scope of the following object types created inside that environment: `Agent`, `Bytes`, `Date`, `Message`, `IntervalDS`, `IntervalYM`, `Subscription`, and `Timestamp`. This rule does not apply to `BFile`, `Blob`, and `Clob` objects, as demonstrated in Example 3-3.

If the application requires access to objects in the global scope, such as static or global variables, these objects must be set to `NULL` before the environment is terminated. In the preceding example, if `b` was a global variable, a `b.setNull()` call has to be made before the `terminateEnvironment()` call.

You can use the mode parameter of the `createEnvironment()` method to specify that your application:

- Runs in a threaded environment (`THREADED_MUTEXED` or `THREADED_UNMUTEXED`)

- Uses objects (`OBJECT`)

The mode can be set independently in each environment.

Example 3-1 How to Create an OCCI Environment

    Environment *env = Environment::createEnvironment();

Example 3-2 How to Terminate an OCCI Environment

    Environment::terminateEnvironment(env);

Example 3-3 How to Use Environment Scope with Blob Objects

    const string userName = "HR";
    const string password = "password";
    const string connectString = "";

    Environment *env = Environment::createEnvironment();
    {
       Connection *conn = env->createConnection(
          userName, password, connectString);
       Statement *stmt = conn->createStatement(
          "SELECT blobcol FROM mytable");
       ResultSet *rs = stmt->executeQuery();
       rs->next();
       Blob b = rs->getBlob(1);
       cout << "Length of BLOB : " << b.length();
       ...
       stmt->closeResultSet(rs);
       conn->terminateStatement(stmt);
       env->terminateConnection(conn);
    }
    Environment::terminateEnvironment(env);

#### 3.1.2 Opening and Closing a Connection

The `Environment` class is the factory class for creating `Connection` objects. You first create an `Environment` instance, and then use it to enable users to connect to the database through the `createConnection()` method.

Example 3-4 creates an environment instance and then uses it to create a database connection for a database user `HR` with the appropriate password.

You must use the `terminateConnection()` method shown in the following code example to explicitly close the connection at the end of the working session. In addition, the OCCI environment should be explicitly terminated.

You should remember that all objects (`Ref`s, `Bfile`s, `Producer`s, `Consumer`s, and so on) created or named within a `Connection` instance must be within the inner scope of that instance; the scope of these objects must be explicitly terminated before the `Connection` is terminated. Example 3-5 demonstrates how to terminate the connection and the environment.

Example 3-4 How to Create an Environment and then a Connection to the Database

    Environment *env = Environment::createEnvironment();
    Connection *conn = env->createConnection("HR", "password");

Example 3-5 How to Terminate a Connection to the Database and the Environment

    env->terminateConnection(conn);
    Environment::terminateEnvironment(env);

#### 3.1.3 About Support for Pluggable Databases

The multitenant architecture enables an Oracle database to contain a portable collection of schemas, schema objects, and nonschema objects that appear to an Oracle client as a separate database. A multitenant container database (CDB) is an Oracle database that includes one or more pluggable databases (PDBs).

OCCI clients can connect to a PDB using a service whose pluggable database property has been set to the relevant PDB.

**See:**

[Oracle Database Administrator’s Guide](../multi/administering-pdbs-with-sql-plus.md) for more information about PDBs and for more details about configuring the services to connect to various PDBs

**See:**

[Oracle Call Interface Programmer's Guide](../lnoci/index.md) for information about restrictions while working with PDBs

### 3.2 About Pooling Connections

This section discusses how to use the connection pooling feature of OCCI. The information covered includes the following topics:

- About Using Connection Pools

- Using Stateless Connection Pooling

The primary difference between the two is that `StatelessConnectionPool`s are used for applications that do not depend on state considerations; these applications can benefit from performance improvements available through use of pre-authenticated connections.

#### 3.2.1 About Using Connection Pools

For many middle-tier applications, connections to the database should be enabled for a large number of threads. Because each thread exists for a relatively short time, opening a connection to the database for every thread would be inefficient use of connections, and would result in poor performance.

By employing the connection pooling feature, your application can create a small set of connections available to a large number of threads, enabling you to use database resources very efficiently.

This section includes the following topics:

- Creating a Connection Pool

- Creating Proxy Connections

##### 3.2.1.1 Creating a Connection Pool

To create a connection pool, you use the [createConnectionPool()](environment-class.md) method, as demonstrated in Example 3-6.

The following parameters are used in Example 3-6:

- `poolUserName`: The owner of the connection pool

- `poolPassword`: The password to gain access to the connection pool

- `connectString`: The database name that specifies the database server to which the connection pool is related

- `minConn`: The minimum number of connections to be opened when the connection pool is created

- `maxConn`: The maximum number of connections that can be maintained by the connection pool. When the maximum number of connections are open in the connection pool, and all the connections are busy, an OCCI method call that needs a connection waits until it gets one, unless `setErrorOnBusy()` was called on the connection pool

- `incrConn`: The additional number of connections to be opened when all the connections are busy and a call needs a connection. This increment is implemented only when the total number of open connections is less than the maximum number of connections that can be opened in that connection pool.

Example 3-7 demonstrates how you can create a connection pool.

You can also configure all these attributes dynamically. This lets you design an application that has the flexibility of reading the current load (number of open connections and number of busy connections) and tune these attributes appropriately. In addition, you can use the `setTimeOut()` method to time out the connections that are idle for more than the specified time. The OCCI terminates idle connections periodically to maintain an optimum number of open connections.

There is no restriction that one environment must have only one connection pool. There can be multiple connection pools in a single OCCI environment, and these can connect to the same or different databases. This is useful for applications requiring load balancing.

Example 3-6 The createConnectionPool() Method

    virtual ConnectionPool* createConnectionPool(
       const string &poolUserName,
       const string &poolPassword,
       const string &connectString ="",
       unsigned int minConn =0,
       unsigned int maxConn =1,
       unsigned int incrConn =1) = 0;

Example 3-7 How to Create a Connection Pool

    const string connectString = "";
    unsigned int maxConn = 5;
    unsigned int minConn = 3;
    unsigned int incrConn = 2;

    ConnectionPool *connPool = env->createConnectionPool(
       poolUserName,
       poolPassword,
       connectString,
       minConn,
       maxConn,
       incrConn);

##### 3.2.1.2 Creating Proxy Connections

If you authorize the connection pool user to act as a proxy for other connections, then no password is required to log in database users who use connections in the connection pool.

A proxy connection can be created by using either of the following two versions of the [createProxyConnection()](connectionpool-class.md) method, demonstrated in Example 3-8.

or

    ConnectionPool->createProxyConnection(
       const string &username,
       string roles[],
       int numRoles,
       Connection::ProxyType proxyType = Connection::PROXY_DEFAULT);

The following parameters are used in the previous method example:

- `roles[]`: The roles array specifies a list of roles to be activated after the proxy connection is activated for the client

- `Connection::ProxyType proxyType = Connection::PROXY_DEFAULT`: The enumeration `Connection::ProxyType` lists constants representing the various ways of achieving proxy authentication. `PROXY_DEFAULT` is used to indicate that `name` represents a database username and is the only proxy authentication mode currently supported.

Example 3-8 The createProxyConnection() Method

    ConnectionPool->createProxyConnection(
       const string &username,
       Connection::ProxyType proxyType = Connection::PROXY_DEFAULT);

#### 3.2.2 Using Stateless Connection Pooling

Stateless Connection Pooling is specifically designed for use in applications that require short connection times and do not deal with state considerations. The primary benefit of Stateless Connection Pooling is increased performance, since the time consuming connection and authentication protocols are eliminated.

Stateless Connection Pools create and maintain a group of stateless, authenticated connection to the database that can be used by multiple threads. Once a thread finishes using its connection, it should release the connection back to the pool. If no connections are available, new ones are generated. Thus, the number of connections in the pool can increase dynamically.

Some connections in the pool may be tagged with specific properties. The user may request a default connection, set certain attributes, such as Globalization Support settings, then tag it and return it to the pool. When a connection with same attributes is needed, a request for a connection with the same tag can be made, and one of several connections in the pool with the same tag can be reused. The tag on a connection can be changed or reset.

Proxy connections may also be created and maintained through the Stateless Connection Pooling interface.

Stateless connection pooling improves the scalability of the mid-tier applications by multiplexing the connections. However, connections from a `StatelessConnectionPool` should not be used for long transactions, as holding connections for long periods leads to reduced concurrency.

**Note:**

- OCCI does not check for the correctness of the connection-tag pair. You are responsible for ensuring that connections with different client-side properties do not have the same tag.

- Your application should commit or rollback any open transactions before releasing the connection back to the pool. If this is not done, Oracle automatically commits any open transactions when the connection is released.

There are two types of stateless connection pools:

- A homogeneous pool is one in which all the connections are authenticated with the username and password provided at the time of creation of the pool. Therefore, all connections have the same authentication context. Proxy connections are not allowed in such pools.

- Different connections can be authenticated by different usernames in heterogeneous pools. Proxy connections can also exist in heterogeneous pools, provided the necessary privileges for creating them are granted on the server. Additionally, heterogeneous pools support external authentication.

Example 3-9 illustrates a basic usage scenario for connection pools. Example 3-10 presents the usage scenario for creating and using a homogeneous stateless connection pool, while Example 3-11 covers the use of heterogeneous pools.

Example 3-9 How to Use a StatelessConnectionPool

Because the pool size is dynamic, in response to changing user requirements, up to the specified maximum number of connections. Assume that a stateless connection pool is created with the following parameters:

- `minConn  =  5`

- `incrConn =  2`

- `maxConn  = 10`

Five connections are opened when the pool is created:

- `openConn =  5`

Using `get[AnyTagged][Proxy]Connection() `methods, the user consumes all 5 open connections:

- `openConn =  5`

- `busyConn =  5`

When the user wants another connection, the pool opens `2` new connections and returns one of them to the user.

- `openConn =  7`

- `busyConn =  6`

The upper limit for the number of connections that can be pooled is `maxConn` specified at the time of creation of the pool.

The user can also modify the pool parameters after the pool is created using the call to `setPoolSize()` method.

If a heterogeneous pool is created, the `incrConn` and `minConn` arguments are ignored.

Example 3-10 How to Create and Use a Homogeneous Stateless Connection Pool

To create a homogeneous stateless connection pool, follow these basic steps and pseudocode commands:

1.  Create a stateless connection pool in the `HOMOGENEOUS` mode of the `Environment` with a [createStatelessConnectionPool()](environment-class.md) call.

        StatelessConnectionPool *scp =
              env->createStatelessConnectionPool(
                 username, passwd, connectString, maxCon, minCon, incrCon,
                 StatelessConnectionPool::HOMOGENEOUS );

2.  Get a new or existing connection from the pool by calling the [getConnection()](statelessconnectionpool-class.md) method.

        Connection *conn=scp->getConnection(tag);

    During the execution of this call, the pool is searched for a connection with a matching tag. If such a connection exists, it is returned to the user. Otherwise, an untagged connection authenticated by the pool username and password is returned.

    Alternatively, you can obtain a connection with [getAnyTaggedConnection()](statelessconnectionpool-class.md) call. It returns a connection with a non-matching tag if neither a matching tag or `NULL `tag connections are available. You should verify the tag returned by a [getTag()](connection-class.md) call on `Connection`.

        Connection *conn=scp->getAnyTaggedConnection(tag);
        string tag=conn->getTag();

3.  Use the connection.

4.  Release the connection to the `StatelessConnectionPool` through the [releaseConnection()](statelessconnectionpool-class.md) call.

        scp->releaseConnection(conn, tag);

    An empty tag, `""`, untags the `Connection`.

    You have an option of retrieving the connection from the `StatelessConnectionPool` using the same `tag` parameter value in a [getConnection()](statelessconnectionpool-class.md) call.

        Connection *conn=scp->getConnection(tag);

    Instead of returning the `Connection` to the `StatelessConnectionPool,` you may want to destroy it using the [terminateConnection()](environment-class.md) call.

        scp->terminateConnection(conn);

5.  Destroy the pool through a[terminateStatelessConnectionPool()](environment-class.md) call on the `Environment` object.

        env->terminateStatelessConnectionPool(scp);

Example 3-11 How to Create and Use a Heterogeneous Stateless Connection Pool

To create a heterogeneous stateless connection pool, follow these basic steps and pseudocode commands:

1.  Create a stateless connection pool in the `HETEROGENEOUS` mode of the `Environment` with a [createStatelessConnectionPool()](environment-class.md) call.

        StatelessConnectionPool *scp =
              env->createStatelessConnectionPool(
                 username, passwd, connectString, maxCon, minCon, incrCon,
                 StatelessConnectionPool::HETEROGENEOUS);

    If you are enabling external authentication, you must also activate the `USES_EXT_AUTH` mode in the [createStatelessConnectionPool()](environment-class.md) call.

        StatelessConnectionPool *scp =
              env->createStatelessConnectionPool(
                 username, passwd, connectString, maxCon, minCon, incrCon,
                 StatelessConnectionPool::PoolType(
                    StatelessConnectionPool::USES_EXT_AUTH|
                    StatelessConnectionPool::HETEROGENEOUS));

2.  Get a new or existing connection from the pool by calling the [getConnection()](statelessconnectionpool-class.md) method of the `StatelessConnectionPool` that is overloaded for the heterogeneous pool option.

        Connection *conn=scp->getConnection(username, passwd, tag);

    During the execution of this call, the heterogeneous pool is searched for a connection with a matching tag. If such a connection exists, it is returned to the user. Otherwise, an appropriately authenticated untagged connection with a `NULL` tag is returned.

    Alternatively, you can obtain a connection with [getAnyTaggedConnection()](statelessconnectionpool-class.md) call that has been overloaded for heterogeneous pools. It returns a connection with a non-matching tag if neither a matching tag or `NULL `tag connections are available. You should verify the tag returned by a [getTag()](connection-class.md) call on `Connection`.

        Connection *conn=scp->getAnyTaggedConnection(username, passwd, tag);
        string tag=conn->getTag();

    You may also want to use proxy connections by [getProxyConnection()](statelessconnectionpool-class.md) or [getAnyTaggedProxyConnection()](statelessconnectionpool-class.md) calls on the `StatelessConnectionPool`.

        Connection *pconn = scp->getProxyConnection(proxyName, roles{},
                                                   nuRoles, tag, proxyType);
        Connection *pconn = scp->getAnyTaggedProxyConnection( proxyName, tag,
                                                             proxyType);

    If the pool supports external authentication, use the following [getConnection()](statelessconnectionpool-class.md) call:

        Connection *conn=scp->getConnection();

3.  Use the connection.

4.  Release the connection to the `StatelessConnectionPool` through the [releaseConnection()](statelessconnectionpool-class.md) call.

        scp->releaseConnection(conn, tag);

    An empty tag, `""`, untags the `Connection`.

    You have an option of retrieving the connection from the `StatelessConnectionPool` using the same `tag` parameter value in a [getConnection()](statelessconnectionpool-class.md) call.

        Connection *conn=scp->getConnection(tag);

    Instead of returning the `Connection` to the `StatelessConnectionPool,` you may want to destroy it using the [terminateConnection()](environment-class.md) call.

        scp->terminateConnection(conn);

5.  Destroy the pool through a [terminateStatelessConnectionPool()](environment-class.md) call on the `Environment` object.

        env->terminateStatelessConnectionPool(scp);

#### 3.2.3 About Database Resident Connection Pooling

Enterprise-level applications must typically handle a high volume of simultaneous user sessions that are implemented as persistent connections to the database. The memory overhead of creating and managing these connections has significant implications for the performance of the database.

Database Resident Connection Pooling solves the problem of too many persistent connections by providing a pool of dedicated servers for handling a large set of application connections, thus enabling the database to scale to tens of thousands of simultaneous connections. It significantly reduces the memory footprint on the database tier and increases the scalability of both the database and middle tiers. Database Resident Connection Pooling is designed for architectures with multi-process application servers and multiple middle tiers that cannot accommodate connection pooling in the middle tier.

Database Resident Connection Pooling architecture closely follows the default dedicated model for connecting to an Oracle Database instance; however, it removes the overhead of assigning a specific server to each connection. On the server tier, most connections are inactive at any given time, and each of these connections consumes memory. Therefore, database systems that support high connection volumes face the risk of quickly exhausting all available memory. Database Resident Connection Pooling allows a connection to use a dedicated server, which combines an Oracle server process and a user session. Once the connection becomes inactive, it returns its resources to the pool, for use by similar connections.

In multithreaded middle tiers that are capable of comprehensive connection pooling, the issue of unused connections is somewhat different. As the number of middle tiers increases, each middle tier privately holds several connections to the database; these connections cannot be shared with other middle tiers. Locating the connection pool on the database instead enables the sharing of connections across similar clients.

Database Resident Connection Pooling supports password-based authentication, statement caching, tagging, and [Fast Application Notification](../racad/ensuring-application-continuity.md). You can also use client-side stateless connection pooling with the database resident connection pooling.

Note that clients that hold connections from the database resident connection pool are persistently connected to a background Connection Broker process. The Connection Broker implements the pool functionality and multiplexes inbound client connections to a pool of dedicated server processes. Clients that do not use the connection pool use dedicated server processes instead.

**See Also:**

- [Oracle Database Concepts](../cncpt/application-and-networking-architecture.md) for details about the architecture of Database Resident Connection Pooling

- [Oracle Database Administrator’s Guide](../admin/managing-processes.md) for details on configuring Database Resident Connection Pooling

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_CONNECTION_POOL.md), for the `DBMS_CONNECTION_POOL` package

This section includes the following topics:

- Administrating Database Resident Connection Pools

- Using Database Resident Connection Pools

##### 3.2.3.1 Administrating Database Resident Connection Pools

To implement database resident connection pooling, it must first be enabled on the system by a user with `SYSDBA` privileges. See Example 3-12 for steps necessary to initiate and maintain a database resident connection pool.

Note that in Oracle RAC configurations, the database resident connection pool starts on all configured nodes. If the pool is not stopped, the starting configuration is persistent across instance restarts: the pool is started automatically when the instance comes up.

Example 3-12 How to Administer the Database Resident Connection Pools

A user with `SYSDBA` privileges must perform the next steps.

1.  Connect to the database.

        SQLPLUS / AS SYSDBA

2.  \[Optional\] Configure the parameters of the database resident connection pool. The default values of a pool are set in the following way:

        DBMS_CONNECTION_POOL.CONFIGURE_POOL( 'SYS_DEFAULT_CONNECTION_POOL',
                                              MIN=>10,
                                              MAX=>200);

3.  \[Optional\] Alter specific parameters of the database resident connection pool without affecting other parameters.

        DBMS_CONNECTION_POOL.ALTER_PARAM(  'SYS_DEFAULT_CONNECTION_POOL',
                                           'INACTIVITY_TIMEOUT',
                                            10);

4.  Start the connection pool. After this step, the connection pool is available to all qualified clients.

        DBMS_CONNECTION_POOL.START_POOL( 'SYS_DEFAULT_CONNECTION_POOL');

5.  \[Optional\] Change the parameters of the database resident connection pool.

        DBMS_CONNECTION_POOL.ALTER_PARAM( 'SYS_DEFAULT_CONNECTION_POOL',
                                          'MAXSIZE',
                                           20);

6.  \[Optional\] The configuration of the connection pool can be reset to default values.

        DBMS_CONNECTION_POOL.RESTORE_DEFAULTS ( 'SYS_DEFAULT_CONNECTION_POOL');

7.  Stop the pool. Note that pool information is persistent: stopping the pool does not destroy the pool name and configuration parameters.

        DBMS_CONNECTION_POOL.STOP_POOL();

##### 3.2.3.2 Using Database Resident Connection Pools

To use database resident connection pooling, you must specify the connection class and connection purity. If the application requests a connection that cannot be potentially tainted with prior connection state, it must specify purity as `NEW`; Oracle recommends this approach if clients from different geographic locale settings share the same database instance. When the application can use a previously used connection, the purity should be set to `SELF`. In conjunction with connection class and purity specifications, you can also use an application-specific tags to choose a previously used connection that has the desired state. The default connection pool name, as demonstrated in Example 3-12, is `SYS_DEFAULT_CONNECTION_POOL.`

This feature overloads [StatelessConnectionPool Class](statelessconnectionpool-class.md) and [Environment Class](environment-class.md) interfaces for retrieving a connection (`getConnection()` and `getProxyConnection()`) by adding the parameters that specify connection class and purity. Every connection request outside of a client-side connection pool has a default purity of `NEW`. Connection requests inside a client-side connection pool have a default purity of `SELF`.

Example 3-13 How to Get a Connection from a Database Resident Connection Pool

    conn1 = env->createConnection (/*username */"hr",
                  /*password*/ "password", /* database*/ "inst1_cmon",
                  /* connection class */"TESTCC", /* purity */Connection::SELF);
    stmt1 = conn1->createStatement("select count(*) from emp");
    rs=stmt1->executeQuery();
    while (rs->next())
         {
            int num = rs->getInt(1);
            sprintf((char *)tmp, "%d", num);
            cout << tmp << endl;
         }
    stmt1->closeResultSet(rs);
    conn1->terminateStatement(stmt1);
    env->terminateConnection(conn1);

Example 3-14 Using Client-Side Pool and Server-Side Pool

    StatelessConnectionPool *scPool;
    OCCIConnection *conn1, *conn2;
     scPool = env->createStatelessConnectionPool
          (poolUserName, poolPassword, connectString, maxConn,
           minConn, incrConn, StatelessConnectionPool::HOMOGENEOUS);

    conn1= scPool->getConnection( /* Connection class name */"TESTCC",
                                  /* Purity */ Connection::SELF);
     /* or, for proxy coonnections */
     conn2= scPool->getProxyConnection(/* username*/ "HR_PROXY",
                         /*Connection class */"TESTCC", /* Purity */Connection::SELF);
    /* or, for getting a tagged connection */
    conn3 = scPool->getConnection(/*connection class */"TESTCC",
                                  /*purity*/ Connection::SELF,
                                  /*tag*/ "TESTTAG");
    /* Releasing a tagged connection is done presently */
    scPool->releaseConnection(conn3, "TESTTAG");

    /* To specify purity as new */
    conn4 = scPool->getConnection(/* connection class */"TESTCC",/* purity of new */
                                  Connection::NEW);

    /* Get a connection using username and password */
    conn5 = scPool->getConnection (username, password,"TESTCC", Connection::SELF);

    /* Using roles when asking for a connection */
    conn6 = scPool->getProxyConnection (username, roles, nRoles,"TESTCC",
                                        Connection::SELF);

    ...

    /* The other code continues as is...writing for clarity */
       ...
        stmt1=conn1->createStatement  ("INSERT INTO emp values (:c1, :c2)");
        stmt1->setInt(1, thrid);
        stmt1->setString(2, "Test");
        int count = stmt1->executeUpdate ();
        conn1->commit();
        conn1->terminateStatement(stmt1);
    /* Release the connection */
        scPool->releaseConnection (conn1);
    ...
      env->terminateStatelessConnectionPool (scPool);

### 3.3 About Executing SQL DDL and DML Statements

SQL is the industry-wide language for working with relational databases. In OCCI you execute SQL commands through the `Statement` class.

This section includes the following topics:

- Creating a Statement Object

- Creating a Statement Object that Executes SQL Commands

- Reusing the Statement Object

- Terminating a Statement Object

#### 3.3.1 Creating a Statement Object

To create a `Statement` object, call the `createStatement()` method of the `Connection` object, as demonstrated in Example 3-15,

Example 3-15 How to Create a Statement

    Statement *stmt = conn->createStatement();

#### 3.3.2 Creating a Statement Object that Executes SQL Commands

Once you have created a `Statement` object, execute SQL commands by calling the [execute()](statement-class.md), [executeUpdate()](statement-class.md), [executeArrayUpdate()](statement-class.md), or [executeQuery()](statement-class.md) methods on the `Statement` object. These methods are used for the following purposes:

- [execute()](statement-class.md) executes all nonspecific statement types

- [executeUpdate()](statement-class.md) executes DML and DDL statements

- [executeArrayUpdate()](statement-class.md) executes multiple DML statements

- [executeQuery()](statement-class.md) executes a query

This section includes the following topics:

- Creating a Database Table

- Inserting Values into a Database Table

##### 3.3.2.1 Creating a Database Table

Example 3-16 demonstrates how you can create a database table using the [executeUpdate()](statement-class.md) method.

Example 3-16 How to Create a Database Table Using the executeUpdate() Method

    stmt->executeUpdate("CREATE TABLE shopping_basket
       (item_number VARCHAR2(30), quantity NUMBER(3))");

##### 3.3.2.2 Inserting Values into a Database Table

Similarly, you can execute a SQL `INSERT` statement by invoking the [executeUpdate()](statement-class.md) method, as demonstrated in Example 3-17.

The [executeUpdate()](statement-class.md) method returns the number of rows affected by the SQL statement.

**See Also:**

`$``ORACLE_HOME``/rdbms/demo` for a code example that demonstrates how to perform insert, select, update, and delete operations on table rows.

Example 3-17 How to Add Records Using the executeUpdate() Method

    stmt->executeUpdate("INSERT INTO shopping_basket
       VALUES('MANGO', 3)");

#### 3.3.3 Reusing the Statement Object

You can reuse a `Statement` object to execute SQL statements multiple times. To repeatedly execute the same statement with different parameters, you should specify the statement by the [setSQL()](statement-class.md) method of the `Statement` object, as demonstrated in Example 3-18.

You may now execute this `INSERT` statement as many times as required. If at a later time you want to execute a different SQL statement, you simply reset the statement object, as demonstrated in Example 3-19.

By using the [setSQL()](statement-class.md) method, OCCI statement objects and their associated resources are not allocated or freed unnecessarily. To retrieve the contents of the current statement object at any time, use the [getSQL()](statement-class.md) method.

Example 3-18 How to Specify a SQL Statement Using the setSQL() Method

    stmt->setSQL("INSERT INTO shopping_basket VALUES(:1,:2)");

Example 3-19 How to Reset a SQL Statement Using the setSQL() Method

    stmt->setSQL("SELECT * FROM shopping_basket WHERE quantity >= :1");

#### 3.3.4 Terminating a Statement Object

You should explicitly terminate and deallocate a `Statement` object using the [terminateStatement()](connection-class.md) method, as demonstrated in Example 3-20.

Example 3-20 How to Terminate a Statement Using the terminateStatement() Method

    Connection::conn->terminateStatement(Statement *stmt);

### 3.4 About Types of SQL Statements in the OCCI Environment

There are three types of SQL statements in the OCCI environment:

- About Standard Statements use SQL commands with specified values

- Using Parameterized Statements have parameters, or bind variables

- Using Callable Statements call stored PL/SQL procedures and functions

The methods of the [Statement Class](statement-class.md) are subdivided into those applicable to all statements, to parameterized statements, and to callable statements. Standard statements are a superset of parameterized statements, and parameterized statements are a superset of callable statements.

This section also includes the following topics:

- About Streamed Reads and Writes

- About Modifying Rows Iteratively

#### 3.4.1 About Standard Statements

Both Example 3-16 and Example 3-17 demonstrate **standard** **statement**s in which you must explicitly define the values of the statement. In Example 3-16, the `CREATE` `TABLE` statement specifies the name of the table `shopping_basket`. In Example 3-17, the `INSERT` statement stipulates the values that are inserted into the table, `('MANGO', 3)`.

#### 3.4.2 Using Parameterized Statements

You can execute the same statement with different parameters by setting placeholders for the input variables of the statement. These statements are referred to as parameterized statements because they can accept parameter input from a user or a program.

If you want to execute an `INSERT` statement with different parameters, you must first specify the statement by the [setSQL()](statement-class.md) method of the `Statement` object, as demonstrated in Example 3-18.

You then call the `set``xxx``()` methods to specify the parameters, where `xxx` stands for the type of the parameter. Provided that the value of the statement object is `"INSERT INTO shopping_basket VALUES(:1,:2)"`, as specified in Example 3-18, you can use the code in Example 3-21 to invoke the [setString()](statement-class.md) method and [setInt()](statement-class.md) method to input the values of these types into the first and second parameters, and the [executeUpdate()](statement-class.md) method to insert the new row into the table.You can reuse the statement object by re-setting the parameters and again calling the [executeUpdate()](statement-class.md) method. If your application is executing the same statement repeatedly, you should avoid changing the input parameter types because this initiates a rebind operation, and affects application performance.

Example 3-21 How to Use setxxx() Methods to Set Individual Column Values

    stmt->setString(1, "Banana");     // value for first parameter
    stmt->setInt(2, 5);               // value for second parameter
    stmt->executeUpdate();            // execute statement
    ...
    stmt->setString(1, "Apple");      // value for first parameter
    stmt->setInt(2, 9);               // value for second parameter
    stmt->executeUpdate();            // execute statement

#### 3.4.3 Using Callable Statements

PL/SQL stored procedures, as their name suggests, are procedures that are stored on the database server for reuse by an application. In OCCI, a callable statement is a call to a procedure which contains other SQL statements.

If you want to call a procedure `countGroceries()`, that returns the quantity of a specified kind of fruit, you must first specify the input parameters of a PL/SQL stored procedure through the `set``XXX``()`` `methods of the `Statement` class, as demonstrated in Example 3-22.

However, before calling a stored procedure, you must specify the type and size of any `OUT` parameters by calling the [registerOutParam()](statement-class.md) method, as demonstrated in Example 3-23. For `IN/OUT` parameters, use the `set``XXX``()` methods to pass in the parameter, and `get``XXX``()` methods to retrieve the results.

You now execute the statement by calling the procedure:

    stmt->executeUpdate();           // call the procedure

Finally, you obtain the output parameters by calling the relevant `get`xxx() method:

    quantity = stmt->getInt(2);     // get value of the second (OUT) parameter

Example 3-22 How to Specify the IN Parameters of a PL/SQL Stored Procedure

    stmt->setSQL("BEGIN countGroceries(:1, :2); END:");
    int quantity;
    stmt->setString(1, "Apple");   // specify the first (IN) parameter of procedure

Example 3-23 How to Specify OUT Parameters of a PL/SQL Stored Procedure

    stmt->registerOutParam(2, Type::OCCIINT, sizeof(quantity));
       // specify type and size of the second (OUT) parameter

This section includes the following topic: Using Callable Statements that Use Array Parameters.

##### 3.4.3.1 Using Callable Statements that Use Array Parameters

A PL/SQL stored procedure executed through a callable statement can have array of values as parameters. The number of elements in the array and the dimension of elements in the array are specified through the `setDataBufferArray()` method.

The following example shows the `setDataBufferArray()` method:

    void setDataBufferArray(
       unsigned int paramIndex,
       void *buffer,
       Type type,
       ub4 arraySize,
       ub4 *arrayLength,
       sb4 elementSize,
       ub2 *elementLength,
       sb2 *ind = NULL,
       ub2 *rc = NULL);

The following parameters are used in the previous method example:

- `paramIndex`: Parameter number

- `buffer`: Data buffer containing an array of values

- `Type`: Type of data in the data buffer

- `arraySize`: Maximum number of elements in the array

- `arrayLength`: Number of elements in the array

- `elementSize`: Size of the current element in the array

- `elementLength`: Pointer to an array of lengths. `elementLength[i]` has the current length of the `i`th element of the array

- `ind`: Indicator information

- `rc`: Returns code

#### 3.4.4 About Streamed Reads and Writes

OCCI supports a streaming interface for insertion and retrieval of very large columns by breaking the data into a series of small chunks. This approach minimizes client-side memory requirements. This streaming interface can be used with parameterized statements such as `SELECT` and various DML commands, and with callable statements in PL/SQL blocks. The data types supported by streams are `BLOB`, `CLOB`, `LONG`, `LONG RAW`, `RAW`, and `VARCHAR2`.

Streamed data is of three kinds:

- A writable stream corresponds to a bind variable in a `SELECT`/DML statement or an `IN` argument in a callable statement.

- A readable stream corresponds to a fetched column value in a `SELECT` statement or an `OUT` argument in a callable statement.

- A bidirectional stream corresponds to an `IN/OUT` bind variable.

Methods of the [Stream Class](stream-class.md) support the stream interface.

The [getStream()](statement-class.md) method of the [Statement Class](statement-class.md) returns a stream object that supports reading and writing for DML and callable statements:

- For writing, it passes data to a bind variable or to an `IN` or `IN/OUT` argument

- For reading, it fetches data from an `OUT` or `IN/OUT` argument

The [getStream()](resultset-class.md) method of the [ResultSet Class](resultset-class.md) returns a stream object that can be used for reading data.

The `status()` method of these classes determines the status of the streaming operation.

This section includes the following topics:

- Binding Data in Streaming Mode; SELECT/DML and PL/SQL

- Fetching Data in Streaming Mode: PL/SQL

- About Fetching Data in Streaming Mode: ResultSet

- Working with Multiple Streams

##### 3.4.4.1 Binding Data in Streaming Mode; SELECT/DML and PL/SQL

To bind data in a streaming mode, follow these steps and review Example 3-24:

1.  Create a `SELECT`/`DML` or PL/SQL statement with appropriate bind placeholders.
2.  Call the [setBinaryStreamMode()](statement-class.md) or [setCharacterStreamMode()](statement-class.md) method of the [Statement Class](statement-class.md) for each bind position that is used in the streaming mode. If the bind position is a PL/SQL `IN` or `IN/OUT` argument type, indicate this by calling the three-argument versions of these methods and setting the `inArg` parameter to `TRUE`.
    **Note:**

    For `setBinaryStreamMode()`, the `size` parameter is limited to 32KB (32,768 bytes).
3.  Execute the statement; the [status()](statement-class.md) method of the [Statement Class](statement-class.md) returns `NEEDS_STREAM_DATA`.
4.  Obtain the stream object through a [getStream()](statement-class.md) method of the [Statement Class](statement-class.md).
5.  Use [writeBuffer()](stream-class.md) and [writeLastBuffer()](stream-class.md) methods of the [Stream Class](stream-class.md) to write data.
6.  Close the stream with [closeStream()](statement-class.md) method of the [Statement Class](statement-class.md).
7.  After all streams are closed, the [status()](statement-class.md) method of the [Statement Class](statement-class.md) changes to an appropriate value, such as `UPDATE_COUNT_AVAILABLE`.

Example 3-24 How to Bind Data in a Streaming Mode

    Statement *stmt = conn->createStatement(
       "Insert Into testtab(longcol) values (:1)"); //longcol is LONG type column
    stmt->setCharacterStreamMode(1, 100000);
    stmt->executeUpdate();

    Stream *instream = stmt->getStream(1);
    char buffer[1000];
    instream->writeBuffer(buffer, len);             //write data
    instream->writeLastBuffer(buffer, len);         //repeat
    stmt->closeStream(instream);                    //stmt->status() is
                                                    //UPDATE_COUNT_AVAILABLE

    Statement *stmt = conn->createStatement("BEGIN testproc(:1); END;");

    //if the argument type to testproc is IN or IN/OUT then pass TRUE to
    //setCharacterStreamMode or setBinaryStreamMode
    stmt->setBinaryStreamMode(1, 32768, TRUE);

##### 3.4.4.2 Fetching Data in Streaming Mode: PL/SQL

To fetch data from a streaming mode, follow these steps and review Example 3-25:

1.  Create a `SELECT`/DML statement with appropriate bind placeholders.
2.  Call the [setBinaryStreamMode()](statement-class.md) or [setCharacterStreamMode()](statement-class.md) method of the [Statement Class](statement-class.md) for each bind position into which data is retrieved from the streaming mode.
3.  Execute the statement; the [status()](statement-class.md) method of the [Statement Class](statement-class.md) returns `STREAM_DATA_AVAILABLE`.
4.  Obtain the stream object through a [getStream()](statement-class.md) method of the [Statement Class](statement-class.md).
5.  Use [readBuffer()](stream-class.md) and [readLastBuffer()](stream-class.md) methods of the [Stream Class](stream-class.md) to read data.
6.  Close the stream with [closeStream()](statement-class.md) method of the [Statement Class](statement-class.md).

Example 3-25 How to Fetch Data in a Streaming Mode Using PL/SQL

    Statement *stmt = conn->createStatement("BEGIN testproc(:1); END;");
                   //argument 1 is OUT type
    stmt->setCharacterStreamMode(1, 100000);
    stmt->execute();

    Stream *outarg = stmt->getStream(1);
                   //use Stream::readBuffer/readLastBuffer to read data

##### 3.4.4.3 About Fetching Data in Streaming Mode: ResultSet

About Executing SQL Queries and Example 3-28 provide an explanation of how to use the streaming interface with result sets.

##### 3.4.4.4 Working with Multiple Streams

If you must work with multiple read and write streams, you must ensure that the read or write of one stream is completed before reading or writing on another stream. To determine stream position, use the [getCurrentStreamParam()](statement-class.md) method of the [Statement Class](statement-class.md) or the [getCurrentStreamColumn()](resultset-class.md) method of the [ResultSet Class](resultset-class.md). The [status()](stream-class.md) method of the [Stream Class](stream-class.md) returns `READY_FOR_READ` if there is data in the stream available for reading, or it returns `INACTIVE` if all the data has been read, as described in [Table 13-45](stream-class.md). The application can then read the next streaming column. Example 3-26 demonstrates how to read and write with two concurrent streams. Note that it is not possible to use these streaming interfaces with the `setDataBuffer()` method in the same `Statement` and `ResultSet` objects.

**See Also:**

"[About Application-Managed Data Buffering](optimizing-performance-of-cplusplus-applications.md)"

Example 3-26 How to Read and Write with Multiple Streams

    Statement *stmt = conn->createStatement(
      "Insert into testtab(longcol1, longcol2) values (:1,:2)");
          //longcol1 AND longcol2 are 2 columns inserted in streaming mode

    stmt->setBinaryStreamMode(1, 100000);
    stmt->setBinaryStreamMode(2, 32768);
    stmt->executeUpdate();

    Stream *col1 = stmt->getStream(1);
    Stream *col2 = stmt->getStream(2);

    col1->writeBuffer(buffer, len);        //first stream
    ...                                    //complete writing coll stream

    col1->writeLastBuffer(buffer, len);    //finish first stream and move to col2

    col2->writeBuffer(buffer, len);        //second stream

    //reading multiple streams
    stmt = conn->createStatement("select longcol1, longcol2 from testtab");
    ResultSet *rs = stmt->executeQuery();
    rs->setBinaryStreamMode(1, 100000);
    rs->setBinaryStreamMode(2, 100000);

    while (rs->next())
    {
       Stream *s1 = rs->getStream(1)
       while (s1->status() == Stream::READY_FOR_READ)
       {
          s1->readBuffer(buffer,size);    //process
       }                                  //first streaming column done
       rs->closeStream(s1);

    //move onto next column. rs->getCurrentStreamColumn() returns 2

       Stream *s2 = rs->getStream(2)
       while (s2->status() == Stream::READY_FOR_READ)
       {
          s2->readBuffer(buffer,size);    //process
       }                                  //close the stream
       rs->closeStream(s2);
    }

#### 3.4.5 About Modifying Rows Iteratively

While you can issue the `executeUpdate` method repeatedly for each row, OCCI provides an efficient mechanism for sending data for multiple rows in a single network round-trip. Use the `addIteration()` method of the `Statement` class to perform batch operations that modify a different row with each iteration.

To execute `INSERT`, `UPDATE`, and `DELETE` operations iteratively, you must:

- Set the maximum number of iterations

- Set the maximum parameter size for variable length parameters

This section includes the following topics:

- Setting the Maximum Number of Iterations

- Setting the Maximum Parameter Size

- Executing an Iterative Operation

##### 3.4.5.1 Setting the Maximum Number of Iterations

For iterative execution, first specify the maximum number of iterations that would be done for the statement by calling the `setMaxIterations()` method:

    Statement->setMaxIterations(int maxIterations);

You can retrieve the current maximum iterations setting by calling the `getMaxIterations() `method.

##### 3.4.5.2 Setting the Maximum Parameter Size

If the iterative execution involves variable-length data types, such as `string` and `Bytes`, then you must set the maximum parameter size so that OCCI can allocate the maximum size buffer:

    Statement->setMaxParamSize(int parameterIndex, int maxParamSize);

You do not have to set the maximum parameter size for fixed-length data types, such as `Number` and `Date`, or for parameters that use the `setDataBuffer()` method.

You can retrieve the current maximum parameter size setting by calling the `getMaxParamSize()` method.

##### 3.4.5.3 Executing an Iterative Operation

Once you have set the maximum number of iterations and (if necessary) the maximum parameter size, iterative execution using a parameterized statement is straightforward, as shown in Example 3-27.

Iterative execution is designed only for use in `INSERT`, `UPDATE` and `DELETE` operations that use either standard or parameterized statements. It cannot be used for callable statements and queries. Note that the data type cannot be changed between iterations. For example, if you use `setInt()` for parameter` 1`, then you cannot use `setString()` for the same parameter in a later iteration

As shown in the example, you call the `addIteration()` method after each iteration except the last, after which you invoke `executeUpdate()` method. Of course, if you did not have a second row to insert, then you would not have to call the `addIteration()` method or make the subsequent calls to the `set`xxx`()` methods.

In order to get the number of rows affected by each iteration in the DML execution in Example 3-27, use [setRowCountsOption()](statement-class.md) to enables the feature, followed by [getDMLRowCounts()](statement-class.md) to return the vector of the number of rows. For the total number of rows affected, you can use the return value of [executeUpdate()](statement-class.md), or call [getUb8RowCount()](statement-class.md).

Example 3-27 How to Execute an Iterative Operation

    stmt->setSQL("INSERT INTO basket_tab VALUES(:1, :2)");

    stmt->setString(1, "Apples");   // value for first parameter of first row
    stmt->setInt(2, 6);             // value for second parameter of first row
    stmt->addIteration();           // add the iteration

    stmt->setString(1, "Oranges");  // value for first parameter of second row
    stmt->setInt(1, 4);             // value for second parameter of second row

    stmt->executeUpdate();          // execute statement

### 3.5 About Executing SQL Queries

SQL query statements allow your applications to request information from a database based on any constraints specified. A result set is returned by the query.

This section includes the following topics:

- Using the Result Set

- About Specifying the Query

- About Optimizing Performance by Setting Prefetch Count

#### 3.5.1 Using the Result Set

Execution of a database query puts the results of the query into a set of rows called the result set. In OCCI, a SQL `SELECT` statement is executed by the `executeQuery` method of the `Statement` class. This method returns an `ResultSet` object that represents the results of a query.

    ResultSet *rs = stmt->executeQuery("SELECT * FROM basket_tab");

Once you have the data in the result set, you can perform operations on it. For example, suppose you wanted to print the contents of this table. The `next()` method of the `ResultSet` is used to fetch data, and the `get`xxx`()` methods are used to retrieve the individual columns of the result set, as shown in the following code example:

    cout << "The basket has:" << endl;

    while (rs->next())
    {
       string fruit = rs->getString(1);     // get the first column as string
       int quantity = rs->getInt(2);        // get the second column as int

       cout << quantity << " " << fruit << endl;
    }

The `next()` and `status()` methods of the `ResultSet` class return `Status`, as defined in [Table 13-38](resultset-class.md).

If data is available for the current row, then the status is `DATA_AVAILABLE`. After all the data has been read, the status changes to `END_OF_FETCH`. If there are any output streams to be read, then the status is `STREAM_DATA_AVAILABLE`, until all the streamed data are read successfully.

Example 3-28 illustrates how to fetch streaming data into a result set, while section "About Streamed Reads and Writes" provides the general background.

Example 3-28 How to Fetch Data in Streaming Mode Using ResultSet

    char buffer[4096];
    ResultSet *rs = stmt->executeQuery
       ("SELECT col1, col2 FROM tab1 WHERE col1 = 11");
    rs->setCharacterStreamMode(2, 10000);

    while (rs->next ())
    {
       unsigned int length = 0;
       unsigned int size = 500;
       Stream *stream = rs->getStream (2);
       while (stream->status () == Stream::READY_FOR_READ)
       {
          length += stream->readBuffer (buffer +length, size);
       }
       cout << "Read "  << length << " bytes into the buffer" << endl;
    }

#### 3.5.2 About Specifying the Query

The `IN` bind variables can be used with queries to specify constraints in the `WHERE` clause of a query. For example, the following program prints only those items that have a minimum quantity of `4`:

    stmt->setSQL("SELECT * FROM basket_tab WHERE quantity >= :1");
    int minimumQuantity = 4;
    stmt->setInt(1, minimumQuantity);     // set first parameter
    ResultSet *rs = stmt->executeQuery();
    cout << "The basket has:" << endl;

    while (rs->next())
       cout << rs->getInt(2) << " " << rs->getString(1) << endl;

#### 3.5.3 About Optimizing Performance by Setting Prefetch Count

Although the `ResultSet` method retrieves data one row at a time, the actual fetch of data from the server need not entail a network round-trip for each row queried. To maximize the performance, you can set the number of rows to prefetch in each round-trip to the server.

You effect this either by setting the number of rows to be prefetched through the `setPrefetchRowCount(``)` method, or by setting the memory size to be used for prefetching through the `setPrefetchMemorySize() `method.

If you set both of these attributes, then the specified number of rows are prefetched unless the specified memory limit is reached first. If the specified memory limit is reached first, then the prefetch returns as many rows as can fit in the memory space defined by the call to the `setPrefetchMemorySize()` method.

By default, prefetching is turned on and the database fetches an extra row all the time. To turn prefetching off, set both the prefetch row count and memory size to `0`.

Prefetching is not in effect if `LONG`, LOB or Opaque Type columns (such as `XMLType`) are part of the query.

### 3.6 About Executing Statements Dynamically

When you know that you must execute a DML operation, you use the `executeUpdate` method. Similarly, when you know that you must execute a query, you use `executeQuery()` method.

If your application must allow for dynamic events and you cannot be sure of which statement must be executed at run time, then OCCI provides the `execute()` method. Invoking the `execute()` method returns one of the following statuses:

- UNPREPARED

- PREPARED

- RESULT_SET_AVAILABLE

- UPDATE_COUNT_AVAILABLE

- NEEDS_STREAM_DATA

- STREAM_DATA_AVAILABLE

While invoking the `execute()` method returns one of these statuses, you can further 'interrogate' the statement by using the `status()` method.

    Statement stmt = conn->createStatement();
    Statement::Status status = stmt->status();       // status is UNPREPARED
    stmt->setSQL("select * from emp");
    status = stmt->status();                         // status is PREPARED

If a statement object is created with a SQL string, then it is created in a `PREPARED` state. For example:

    Statement stmt = conn->createStatement("insert into foo(id) values(99)");
    Statement::Status status = stmt->status();// status is PREPARED
    status = stmt->execute();                 // status is UPDATE_COUNT_AVAILABLE

When you set another SQL statement on the Statement, the status changes to `PREPARED`. For example:

    stmt->setSQL("select * from emp");        // status is PREPARED
    status = stmt->execute();                 // status is RESULT_SET_AVAILABLE

This section includes the following topic: About Statement Status Definitions.

#### 3.6.1 About Statement Status Definitions

This section describes the possible values of `Status` related to a statement object:

- UNPREPARED

- PREPARED

- RESULT_SET_AVAILABLE

- UPDATE_COUNT_AVAILABLE

- NEEDS_STREAM_DATA

- STREAM_DATA_AVAILABLE

##### 3.6.1.1 UNPREPARED

If you have not used the `setSQL()` method to attribute a SQL string to a statement object, then the statement is in an `UNPREPARED` state.

    Statement stmt = conn->createStatement();
    Statement::Status status = stmt->status(); // status is UNPREPARED

##### 3.6.1.2 PREPARED

If a Statement is created with an SQL string, then it is created in a `PREPARED` state. For example:

    Statement stmt = conn->createStatement("INSERT INTO demo_tab(id) VALUES(99)");
    Statement::Status status = stmt->status();    // status is PREPARED

Setting another SQL statement on the `Statement` changes the status to `PREPARED`. For example:

    status = stmt->execute();                 // status is UPDATE_COUNT_AVAILABLE
    stmt->setSQL("SELECT * FROM demo_tab");   // status is PREPARED

##### 3.6.1.3 RESULT_SET_AVAILABLE

A status of `RESULT_SET_AVAILABLE` indicates that a properly formulated query has been executed and the results are accessible through a result set.

When you set a statement object to a query, it is `PREPARED`. Once you have executed the query, the statement changes to `RESULT_SET_AVAILABLE`. For example:

    stmt->setSQL("SELECT * from EMP");          // status is PREPARED
    status = stmt->execute();                   // status is RESULT_SET_AVAILABLE

To access the data in the result set, issue the following statement:

    ResultSet *rs = Statement->getResultSet();

##### 3.6.1.4 UPDATE_COUNT_AVAILABLE

When a DDL or DML statement in a `PREPARED` state is executed, its state changes to `UPDATE_COUNT_AVAILABLE`, as shown in the following code example:

    Statement stmt = conn->createStatement("INSERT INTO demo_tab(id) VALUES(99)");
    Statemnt::Status status = stmt->status(); // status is PREPARED
    status = stmt->execute();                 // status is UPDATE_COUNT_AVAILABLE

This status refers to the number of rows affected by the execution of the statement. It indicates that:

- The statement did not include any input or output streams.

- The statement was not a query but either a DDL or DML statement.

You can obtain the number of rows affected by issuing the following statement:

    stmt->getUb8RowCount();

Note that a DDL statement results in an update count of zero (`0`). Similarly, an update that does not meet any matching conditions also produces a count of zero (`0`). In such a case, you cannot determine the kind of statement that has been executed from the reported status.

##### 3.6.1.5 NEEDS_STREAM_DATA

If there are any output streams to be written, the execute does not complete until all the stream data is completely provided. In this case, the status changes to `NEEDS_STREAM_DATA` to indicate that a stream must be written. After writing the stream, call the [status()](statement-class.md) method to find out if more stream data should be written, or whether the execution has completed.

In cases where your statement includes multiple streamed parameters, use the [getCurrentStreamParam()](statement-class.md) method to discover which parameter must be written.

If you are performing an iterative or array execute, the [getCurrentStreamIteration()](statement-class.md) method reveals to which iteration the data is to be written.

Once all the stream data has been processed, the status changes to either `RESULT_SET_AVAILABLE` or `UPDATE_COUNT_AVAILABLE`.

##### 3.6.1.6 STREAM_DATA_AVAILABLE

This status indicates that the application requires some stream data to be read in `OUT` or `IN/OUT` parameters before the execution can finish. After reading the stream, call the `status` method to find out if more stream data should be read, or whether the execution has completed.

In cases in which your statement includes multiple streamed parameters, use the `getCurrentStreamParam()` method to discover which parameter must be read.

If you are performing an iterative or array execute, then the `getCurrentStreamIteration()` method reveals from which iteration the data is to be read.

Once all the stream data has been handled, the status changes to `UPDATE_COUNT_REMOVE_AVAILABLE`.

The `ResultSet` class also has readable streams and it operates similar to the readable streams of the `Statement` class.

### 3.7 About Using Larger Row Count and Error Code Range Data Types

Starting with Oracle Database Release 12c, Oracle C++ Call Interface supports larger row count and error code range data types. The method that returns the larger row count is [getUb8RowCount()](statement-class.md) in [Statement Class](statement-class.md).

This has two benefits:

- Applications running a statement that affects more than UB4MAXVAL rows may now see the precise value for the number of rows affected.

- Oracle Database can correctly return newer error codes (above `ORA-65535`) to application clients, starting with Oracle Database Release 12c. Older clients receive an informative message that indicates error code overflow.

This section contains the following topics:

- "Using Larger Row Count in SELECT Operations"

- "Using Larger Row Count in INSERT, UPDATE, and DELETE Operations"

#### 3.7.1 Using Larger Row Count in SELECT Operations

Method [getUb8RowCount()](statement-class.md) returns the number of rows processed after executing the `SELECT` statement, as `ub8` type. The examples in this section illustrate how to use [getUb8RowCount()](statement-class.md) in various `SELECT` scenarios.

- In the simplest scenario in Example 3-29, the number of rows affected is the same as the number fetched.

- When the prefetch option is set, as demonstrated by Example 3-30, it includes the number of rows prefetched.

- When using an array fetching mechanism in Example 3-31 by invoking the [setDataBuffer()](statement-class.md) interface, [getUb8RowCount()](statement-class.md) returns the total number of rows fetched into user buffers, independent of prefetch option.

Example 3-29 SELECT with getUb8RowCount(); simple

The number of rows affected is the number of rows already fetched.

    oraub8 largeRowCount = 0;
    Statement *stmt = conn->createStatement("SELECT salary FROM employees");
    ResultSet *rs = stmt->executeQuery ();
    rs->next();
    largeRowCount = stmt->getUb8RowCount();

Example 3-30 SELECT with getUb8RowCount(); with prefetch

Here the number of rows affected is the same as those fetched in previous iterations, plus the number of rows prefetched in the `next()` call.

    oraub8 largeRowCount = 0;
    Statement *stmt = conn->createStatement("SELECT salary FROM employees");
    stmt -> setPrefetchRowCount(prefetch_count);
    ResultSet *rs = stmt->executeQuery ();
    rs->next();
    largeRowCount = stmt->getUb8RowCount();

Example 3-31 SELECT with getUb8RowCount(); array fetch with prefetch

Here number of rows affected, value of `largeRowCount`, is the number of rows fetched into user buffer in previous iterations, plus the number of rows fetched in either `next(max)` or `next()` call. It is independent of the value of prefetch.

    oraub8 largeRowCount = 0;
    Statement *stmt=conn->createStatement("SELECT col1 FROM table1");
    int max = 20;
    int prefetch_count = 10;
    ub2 lengthC1[max];
    ub4 c1[max];

    for (i = 0; i < max; ++i) {
       c1[i] = 0;
       lengthC1[i] = sizeof (c1[i]);
    }

    stmt -> setPrefetchRowCount(prefetch_count);
    ResultSet *rs = stmt->executeQuery();
    rs->setDataBuffer (1, c1, OCCIINT, sizeof (ub4), lengthC1);
    rs->next(max);

    largeRowCount = stmt->getUb8RowCount();

#### 3.7.2 Using Larger Row Count in INSERT, UPDATE, and DELETE Operations

For `INSERT`, `UPDATE`, and `DELETE` statements, method [getUb8RowCount()](statement-class.md) returns the number of rows processed by the most recent statement.

Example 3-32 INSERT with getUb8RowCount(); simple

The value of `largeRowCount` is the number of rows inserted, which is `1`.

    oraub8 largeRowCount = 0;
    Statement *stmt = conn->createStatement("INSERT INTO table1 values (:1)");
    stmt->setNumber(1, 100);
    stmt->executeUpdate();
    largeRowCount = stmt->getUb8RowCount();

Example 3-33 INSERT with getUb8RowCount(); with iterations

Here the value of `largeRowCount` is equal to `max`.

    int max;
    oraub8 largeRowCount = 0;
    Statement *stmt=conn->createStatement("INSERT INTO table1 values (:1)");
    stmt->setMaxIterations (max);

    for(i = 0; i < max-1; i++) {
       stmt->setNumber(1, 100);
       stmt->addIteration ();
    }

    stmt->setNumber(1, 100);
    stmt->executeUpdate();
    largeRowCount = stmt->getUb8RowCount();

Example 3-34 UPDATE with getUb8RowCount()

Here the value of `largeRowCount` is the number of rows updated.

    oraub8 largeRowCount = 0;
    Statement *stmt=conn->createStatement(
       "UPDATE table1 SET COL1 = COL1+100 WHERE COL1=:1");
    stmt->setNumber(1, 200);
    stmt->executeUpdate();
    largeRowCount = stmt->getUb8RowCount();

### 3.8 About Committing a Transaction

All SQL DML statements are executed in the context of a transaction. An application causes the changes made by these statement to become permanent by either committing the transaction, or undoing them by performing a rollback. While the SQL `COMMIT` and `ROLLBACK` statements can be executed with the `executeUpdate()` method, you can also call the `Connection::commit()` and `Connection::rollback()` methods.

If you want the DML changes that were made to be committed immediately, you can turn on the auto commit mode of the `Statement` class by issuing the following statement:

    Statement::setAutoCommit(TRUE);

Once auto commit is in effect, each change is automatically made permanent. This is similar to issuing a commit right after each execution.

To return to the default mode, auto commit off, issue the following statement:

    Statement::setAutoCommit(FALSE);

### 3.9 Caching Statements

The statement caching feature establishes and manages a cache of statements within a session. It improves performance and scalability of application by efficiently using prepared cursors on the server side and eliminating repetitive statement parsing.

Statement caching can be used with connection and session pooling, and also without connection pooling. Please review Example 3-35 and Example 3-36 for typical usage scenarios.

Example 3-35 Statement Caching without Connection Pooling

These steps and accompanying pseudocode implement the statement caching feature without use of connection pools:

1.  Create a `Connection` by making a [createConnection()](environment-class.md) call on the `Environment` object.

        Connection *conn = env->createConnection(
              username, password, connecstr);

2.  Enable statement caching on the `Connection` object by using a nonzero `size` parameter in the [setStmtCacheSize()](connection-class.md) call.

        conn->setStmtCacheSize(10);

    Subsequent calls to [getStmtCacheSize()](connection-class.md) would determine the size of the cache, while [setStmtCacheSize()](connection-class.md) call changes the size of the statement cache, or disables statement caching if the `size` parameter is set to zero.

3.  Create a `Statement` by making a [createStatement()](connection-class.md) call on the `Connection` object; the `Statement` is returned if it is in the cache, or a new `Statement` with a `NULL` tag is created for the user.

        Statement *stmt = conn->createStatement(sql);

    To retrieve a previously cached tagged statement, use the alternate form of the [createStatement()](connection-class.md) method:

        Statement *stmt = conn->createStatement(sql, tag);

4.  Use the statement to execute SQL commands and obtain results.

5.  Return the statement to cache.

        conn->terminateStatement(stmt, tag);

    If you do not want to cache this statement, use the [disableCaching()](statement-class.md) call and an alternate from of [terminateStatement()](connection-class.md):

        stmt->disableCaching();
        conn->terminateStatement(stmt);

    If you must verify whether a statement has been cached, issue an [isCached()](connection-class.md) call on the `Connection` object.

    You can choose to tag a statement at release time and then reuse it for another statement with the same tag. The tag is used to search the cache. An untagged statement, where tag is `NULL`, is a special case of a tagged statement. Two statements are considered different if they only differ in their tags, and if only one of them is tagged.

6.  Terminate the connection.

Example 3-36 Statement Caching with Connection Pooling

These steps and accompanying pseudocode implement the statement caching feature with connection pooling.

Statement caching is enabled only for connection created after the `setStmtCacheSize()` call.

If statement cac.hing is not enabled at the pool level, it can still be implemented for individual connections in the pool.

1.  Create a `ConnectionPool` by making a call to the [createConnectionPool()](environment-class.md) of the `Environment` object.

        ConnectionPool *conPool = env->createConnectionPool(
                                       username, password, connecstr,
                                       minConn, maxConn, incrConn);

    If using a `StatelessConnectionPool`, call [createStatelessConnectionPool()](environment-class.md) instead. Subsequent operations are the same for `ConnectionPool` and `StatelessConnectionPool` objects.

        Stateless ConnectionPool *conPool = env->createStatelessConnectionPool(
                                            username, password, connecstr,
                                            minConn, maxConn, incrConn, mode);

2.  Enable statement caching for all `Connection`s in the `ConnectionPool` by using a nonzero `size` parameter in the [setStmtCacheSize()](connection-class.md) call.

        conPool->setStmtCacheSize(10);

    Subsequent calls to [getStmtCacheSize()](connection-class.md) would determine the size of the cache, while [setStmtCacheSize()](connection-class.md) call changes the size of the statement cache, or disables statement caching if the `size` parameter is set to zero.

3.  Get a `Connection` from the pool by making a [createConnection()](connectionpool-class.md) call on the `ConnectionPool` object; the `Statement` is returned if it is in the cache, or a new `Statement` with a `NULL` tag is created for the user.

        Connection *conn = conPool->createConnection(username, password, connecstr);

    To retrieve a previously cached tagged statement, use the alternate form of the [createStatement()](connection-class.md) method:

        Statement *stmt = conn->createStatement(sql, tag);

4.  Create a `Statement` by making a [createStatement()](connection-class.md) call on the `Connection` object; the `Statement` is returned if it is in the cache, or a new `Statement` with a `NULL` tag is created for the user.

        Statement *stmt = conn->createStatement(sql);

    To retrieve a previously cached tagged statement, use the alternate form of the [createStatement()](connection-class.md) method:

        Statement *stmt = conn->createStatement(sql, tag);

5.  Use the statement to execute SQL commands and obtain results.

6.  Return the statement to cache.

        conn->terminateStatement(stmt, tag);

    If you do not want to cache this statement, use the [disableCaching()](statement-class.md) call and an alternate from of [terminateStatement()](connection-class.md):

        stmt->disableCaching();
        conn->terminateStatement(stmt);

    If you must verify whether a statement has been cached, issue an [isCached()](connection-class.md) call on the `Connection` object.

7.  Release the connection [terminateConnection()](connectionpool-class.md).

        conPool->terminateConnection(conn);

### 3.10 About Handling Exceptions

Each OCCI method can generate an exception if it is not successful. This exception is of type `SQLException`. OCCI uses the C++ Standard Template Library (STL), so any exception that can be thrown by the STL can also be thrown by OCCI methods.

The STL exceptions are derived from the standard exception class. The `exception::what()` method returns a pointer to the error text. The error text is guaranteed to be valid during the catch block

The `SQLException` class contains Oracle specific error numbers and messages. It is derived from the standard exception class, so it too can obtain the error text by using the `exception::what()` method.

In addition, the `SQLException` class has two methods it can use to obtain error information. The `getErrorCode()` method returns the Oracle error number. The same error text returned by `exception::what()` can be obtained by the `getMessage()` method. The `getMessage()` method returns an STL string so that it can be copied like any other STL string.

Based on your error handling strategy, you may choose to handle OCCI exceptions differently from standard exceptions, or you may choose not to distinguish between the two.

If you decide that it is not important to distinguish between OCCI exceptions and standard exceptions, your catch block might look similar to the following:

    catch (exception &excp)
    {
       cerr << excp.what() << endl;
    }

Should you decide to handle OCCI exceptions differently than standard exceptions, your catch block might look like the following:

    catch (SQLException &sqlExcp)
    {
       cerr <<sqlExcp.getErrorCode << ": " << sqlExcp.getErrorMessage() << endl;
    }
    catch (exception &excp)
    {
       cerr << excp.what() << endl;
    }

In the preceding catch block, SQL exceptions are caught by the first block and non-SQL exceptions are caught by the second block. If the order of these two blocks were to be reversed, SQL exceptions would never be caught. Since `SQLException` is derived from the standard exception, the standard exception catch block would handle the SQL exception as well.

**See Also:**

- Description of a special feature for handling errors that arise during batch updates, described in section "[Modifying Rows Iteratively](optimizing-performance-of-cplusplus-applications.md)" in [Optimizing Performance of C++ Applications](optimizing-performance-of-cplusplus-applications.md)

- [Oracle Database Error Messages Reference](../errmg/index.md)for more information about Oracle error messages.

This section includes the following topic: About Handling Null and Truncated Data.

#### 3.10.1 About Handling Null and Truncated Data

In general, OCCI does not cause an exception when the data value retrieved by using the `get``xxx``()` methods of the `ResultSet` class or `Statement` class is `NULL` or truncated. However, this behavior can be changed by calling the `setErrorOnNull()` method or `setErrorOnTruncate()` method. If the `setError``xxx``()` methods are called with `causeException=TRUE`, then an `SQLException` is raised when a data value is `NULL` or truncated.

The default behavior is not to raise an `SQLException`. A column or parameter value can also be `NULL`, as determined by a call to `isNull()` for a `ResultSet` or `Statement` object returning `TRUE`:

    rs->isNull(columnIndex);
    stmt->isNull(paramIndex);

If the column or parameter value is truncated, it also returns `TRUE` as determined by a `isTruncated()` call on a `ResultSet` or `Statement` object:

    rs->isTruncated(columnIndex);
    stmt->isTruncated(paramIndex);

For data retrieved through the `setDataBuffer()` method and `setDataBufferArray()` method, exception handling behavior is controlled by the presence or absence of indicator variables and return code variables as shown in Table 3-1, Table 3-2, and Table 3-3.

Table 3-1 Normal Data - Not Null and Not Truncated

| Return Code  | Indicator - not provided         | Indicator - provided                                |
|:-------------|:---------------------------------|:----------------------------------------------------|
| Not provided | `error = 0`                      | `error = 0`<br>`indicator = 0`                      |
| Provided     | `error = 0`<br>`return code = 0` | `error = 0`<br>`indicator = 0`<br>`return code = 0` |

Table 3-2 Null Data

| Return Code  | Indicator - not provided                                 | Indicator - provided                                    |
|:-------------|:---------------------------------------------------------|:--------------------------------------------------------|
| Not provided | `SQLException`<br>`error = 1405`                         | `error = 0`<br>`indicator = -1`                         |
| Provided     | `SQLException`<br>`error = 1405`<br>`return code = 1405` | `error = 0`<br>`indicator = -1`<br>`return code = 1405` |

Table 3-3 Truncated Data

| Return Code  | Indicator - not provided                | Indicator - provided                                              |
|:-------------|:----------------------------------------|:------------------------------------------------------------------|
| Not provided | `SQLException`<br>`error = 1406`        | `SQLException`<br>`error = 1406`<br>`indicator = data_len`        |
| Provided     | `error = 24345`<br>`return code = 1405` | `error = 24345`<br>`indicator = data_len`<br>`return code = 1406` |

In Table 3-3, `data_len` is the actual length of the data that has been truncated if this length is less than or equal to `SB2MAXVAL`. Otherwise, the indicator is set to `-2`.
