This chapter describes a few suggestions that lead to better performance for your OCCI custom applications.

This chapter contains these topics:

- About Transparent Application Failover

- About Connection Sharing

- About Application-Managed Data Buffering

- Using the Array Fetch Using next() Method

- Modifying Rows Iteratively

- About Using Oracle Connection Manager in Traffic Director Mode

- About Run-time Load Balancing of the Stateless Connection Pool

- About Fault Diagnosability

- Using Client Result Cache

- About Client-Side Deployment Parameters and Auto Tuning

**See Also:**

- [OCCI Application Programming Interface](occi-application-programing-interface.md)

### 12.1 About Transparent Application Failover

OCCI Transparent Application Failover (TAF) enables OCCI to be more robust in handling database instance failures in distributed applications at run time. If a server node becomes unavailable, applications automatically reconnect to another surviving node.

TAF occurs when the client application, during a roundtrip operation, detects that the database instance is down. It establishes a connection to the backup database configured for TAF. This backup can be another node in an Oracle RAC configuration, a hot standby database, or the same database instance itself.

The OCCI/OCI API responsible for the roundtrip on the failed connection will typically return one of the following errors:

- `ORA-25401: can not continue fetches`

- `ORA-25402: transaction must roll back`

- `ORA-25408: can not safely replay call`

The new connection is may be used for subsequent application requests and for any ongoing work that must be restarted.Idle connections in the application are not affected.

Some design options should be considered when including Transparent Application Failover in an application:

- Because of the delays inherent to failover processing, the design of the application may include a notice to the user that a failover is in progress and that normal operation should resume shortly.

- If the session on the initial instance received `ALTER SESSION` commands before the failover began, they are not automatically replayed on the second instance.

  Consequently, the developer may want to replay these `ALTER SESSION` commands on the second instance.

It is the user's responsibility to track changes to the `SESSION` parameters.

To address these problems, the application can register a failover callback function. After a failover, the callback function is invoked at different times while reestablishing the user's session.

- The first call to the callback function occurs when Oracle first detects an instance connection loss. This callback is intended to allow the application to inform the user of an upcoming delay.

- If failover is successful, a second call to the callback function occurs when the connection is reestablished and usable. At this time the client may want to replay `ALTER SESSION` commands and inform the user that failover has happened. Note that you must keep track of `SESSION` parameter changes and then replay them after the failover is complete.

  If failover is unsuccessful, then the callback function is called to inform the application that failover cannot take place.

- An initial attempt at failover may not always successful. The failover callback should return `FO_RETRY` to indicate that the failover should be attempted again.

  **See Also:**

  - Definition of `FailOverType` and `FailOverEventType` in [Table 13-11](connection-class.md) in [OCCI Application Programming Interface](occi-application-programing-interface.md)

  - [Oracle Database Net Services Administrator's Guide](../netag/enabling-advanced-features.md) for more detailed information about application failover.

This section includes the following topics:

- Using Transparent Application Failover

- About Objects and Transparent Application Failover

- Using Connection Pooling and Transparent Application Failover

#### 12.1.1 Using Transparent Application Failover

To enable TAF, the connect string has to be configured for failover and registered on `Connection` (created from `Environment`, `ConnectionPool` and `StatelessConnectionPool`). To register the callback function, use the [Connection Class](connection-class.md) interface [setTAFNotify()](connection-class.md):

    void Connection::setTAFNotify(
       int (*notifyFn)(
          Environment *env,
          Connection *conn,
          void *ctx,
          FailOverType foType,
          FailOverEventType foEvent),
       void *ctxTAF);

Note that TAF support for `ConnectionPool`s does not include `BACKUP` and `PRECONNECT` clauses; these should not be used in the connect string.

#### 12.1.2 About Objects and Transparent Application Failover

Transparent application failover works with the OCCI navigational and associative access models and the object cache. In a non-Oracle RAC setup, you must ensure that the object type definitions and object OIDs in primary and backup instances are identical.

If the application receives `ORA-25402: transaction must roll back` error after the failover, then it must initiate a rollback to correctly reset the object cache on the client. If a transaction has not started before the failover, the application should still initiate a rollback after the failover to refresh the objects on the client object cache from the new instance.

#### 12.1.3 Using Connection Pooling and Transparent Application Failover

If the transparent application failover feature is activated, connections created in a connection pool are also failed over. The application failover callback must be specified for each connection obtained from the connection pool; these connections are failed over when used after the primary instance failure.

Note that connections in a custom connection pool must be explicitly cleaned and repaired. Consider an application that has 500 connections in a pool; 10 of the connections are busy (doing a round-trip) and 490 are free or idle. If the database instance fails, then TAF will work on 10 active connections, and client requests on these connections must be restarted. When each of the other 490 connections are picked up by the application, TAF is performed and OCCI returns one of error codes `ORA-25401`, `ORA-24502`, or `ORA-25408`, forcing a restart of the user request. The application can avoid these errors on the 490 idle connections by repairing or purging these connections by using the knowledge that TAF was previously activated on 10 connections in the connection pool.

To repair connections in OCCI, use the [Connection Class](connection-class.md) interface [getServerVersion()](connection-class.md), a light-weight, data-neutral database call for starting TAF on connections to failed instances:

    string getServerVersion() const;

In the OCCI TAF callback, applications may invoke [getServerVersion()](connection-class.md) on idle connections in the custom pool, to start and complete failover for these connections.

Example 12-1 demonstrates how to use OCCI for TAF callbacks and for repairing bad connections. Note that the example does not show custom pool data structure or mutexing and concurrency control.

Note that TAF behavior is the same for standalone connections and connections in a custom connection pool.

Example 12-1 How to Enable TAF for Connection Pooling

    #include <occi.h>
    #include <iostream>
    #include <time.h>

    using namespace std;
    using namespace oracle::occi;

    //Application custom pool of 3 connections
    Environment *env;
    Connection *conn1,*conn2,*conn3;
    bool conn1free,conn2free,conn3free;
    bool repairing = false;

    int taf_callback(Environment *env, Connection *conn, void *ctx,
      Connection::FailOverType foType, Connection::FailOverEventType foEvent)
    {
       cout << "TAF callback for connection " << conn << endl;

       if(foEvent == Connection::FO_ERROR)
       {
          cout << "Retrying" << endl;
          return FO_RETRY;
       }

       if (foEvent ==  Connection::FO_END)
       {
         cout << "TAF complete for connnection " << conn << endl;
         if (repairing == false)
         {
          repairing = true;
          cout << "repairing other idle connections" << endl;

          //ignore errors during TAF
          try
          {
             if (conn1free) conn1->getServerVersion();
          }
          catch (...)
          {
          }
          try
          {
             if (conn2free) conn2->getServerVersion();
          }
          catch (...)
          {
          }
          try
          {
             if (conn3free) conn3->getServerVersion();
          }
          catch (...)
          {
          }
          repairing = false;
         }//if
       }//if

       return 0; //continue failover
    }

    main()
    {
    try
    {
    env = Environment::createEnvironment(Environment::THREADED_MUTEXED);
    //open 3 connections;
     conn1 = env->createConnection("hr","password","inst1_failback");
     conn2 = env->createConnection("hr","password","inst1_failback");
     conn3 = env->createConnection("hr","password","inst1_failback");

    //all connections are 'free'
    conn1free = conn2free = conn3free = true;

    //set TAF callbacks on all connection
    conn1->setTAFNotify(taf_callback,NULL);
    conn2->setTAFNotify(taf_callback,NULL);
    conn3->setTAFNotify(taf_callback,NULL);

    //use 1 connection
    conn1free=false;
    cout << "Using conn1" << endl;
    Statement *stmt = conn1->createStatement ("select * from employees");
    ResultSet *rs  = stmt->executeQuery();
    while (rs->next())
    {
       cout << (rs->getString(2)) << endl;
    }
    stmt->closeResultSet(rs);
    conn1->terminateStatement(stmt);

    cout << "Shutdown and restart the database" << endl;
    string buf;
    cin >> buf;

    Statement *stmt2;
    try
    {
       cout << "Trying a update on EMP table" << endl;
       stmt2 = conn1->createStatement("delete from employees");
       stmt2->executeUpdate();
    }
    catch (SQLException &ex)
    {
       cout << "Update EMPLOYEES returned error : " << ex.getMessage() << endl;
       cin >> buf;
    }

    cout << "Done" << endl;
    env->terminateConnection(conn1);
    env->terminateConnection(conn2);
    env->terminateConnection(conn3);
    Environment::terminateEnvironment(env);
    }
    catch(SQLException &ex)
    {
    cout << ex.getMessage() << endl;
    }
    }

### 12.2 About Connection Sharing

This section covers the following topics:

- Introduction to Thread Safety

- Implementing Thread Safety

- About Serialization

- Operating System Considerations

#### 12.2.1 Introduction to Thread Safety

Threads are lightweight processes that exist within a larger process. Threads each share the same code and data segments, but have their own program counters, system registers, and stack. Global and static variables are common to all threads, and a mutual exclusivity mechanism may be required to manage access to these variables from multiple threads within an application.

Once spawned, threads run asynchronously to one another. They can access common data elements and make OCCI calls in any order. Because of this shared access to data elements, a mechanism is required to maintain the integrity of data being accessed by multiple threads. The mechanism to manage data access takes the form of mutexes (mutual exclusivity locks), which ensure that no conflicts arise between multiple threads that are accessing shared resources within an application. In OCCI, mutexes are granted on an OCCI environment basis.

This thread safety feature of the Oracle database server and OCCI library enables developers to use OCCI in a multithreaded application with these added benefits:

- Multiple threads of execution can make OCCI calls with the same result as successive calls made by a single thread.

- When multiple threads make OCCI calls, there are no side effects between threads.

- Even if you do not write a multithreaded program, you do not pay any performance penalty for including thread-safe OCCI calls.

- Use of multiple threads can improve program performance. You can discern gains on multiprocessor systems where threads run concurrently on separate processors, and on single processor systems where overlap can occur between slower operations and faster operations.

In addition to client/server applications, where the client can be a multithreaded program, thread safety is typically used in three-tier or client/agent/server architectures. In this architecture, the client is concerned only with presentation services. The agent (or application server) processes the application logic for the client application. Typically, this relationship is a many-to-one relationship, with multiple clients sharing the same application server.

The server tier in the three-tier architecture is an Oracle database server. The applications server (agent) supports multithreading, with each thread serving a separate client application. In an Oracle environment, this middle-tier application server is an OCCI or precompiler program.

#### 12.2.2 Implementing Thread Safety

To take advantage of thread safety by using OCCI, an application must be running in a thread-safe operating system. Then the application must inform OCCI that the application is running in multithreaded mode by specifying `THREADED_MUTEXED` or `THREADED_UNMUTEXED` for the mode parameter of the `createEnvironment()` method. For example, to turn on mutual exclusivity locking, issue the following statement:

    Environment *env = Environment::createEnvironment(
              Environment::THREADED_MUTEXED);

Note that once `createEnvironment` is called with `THREADED_MUTEXED` or `THREADED_UNMUTEXED`, all subsequent calls to the `createEnvironment` method must also be made with `THREADED_MUTEXED` or `THREADED_UNMUTEXED` modes.

If a multithreaded application is running in a thread-safe operating system, then the OCCI library manages mutexes for the application on a for each-OCCI-environment basis. However, you can override this feature and have your application maintain its own mutex scheme. This is done by specifying a mode value of `THREADED_UNMUTEXED` to the `createEnvironment()` method.

Applications that run on non-thread-safe platforms should not pass a value of `THREADED_MUTEXED` or `THREADED_UNMUTEXED` to the `createEnvironment()` method.

If an application is single threaded, regardless of whether the platform is thread safe, the application should pass a value of `Environment::DEFAULT` to the `createEnvironment()` method. This is also the default value for the mode parameter. Single threaded applications which run in `THREADED_MUTEXED` mode may incur performance degradation.

OCCI does not support nonblocking mode.

#### 12.2.3 About Serialization

As an application programmer, you have two basic options regarding concurrency in a multithreaded application:

- Automatic Serialization, in which you use OTIS's transparent mechanisms

- Application-Provided Serialization, in which you manage the contingencies involved in maintaining multiple threads

##### 12.2.3.1 Automatic Serialization

In cases where there are multiple threads operating on objects (connections and connection pools) derived from an OCCI environment, you can elect to let OCCI serialize access to those objects. The first step is to pass a value of `THREADED_MUTEXED` to the `createEnvironment` method. At this point, the OCCI library automatically acquires a mutex on thread-safe objects in the environment.

When the OCCI environment is created with `THREADED_MUTEXED` mode, then only the `Environment`, `Map`, `ConnectionPool`, `StatelessConnectionPool` and `Connection` objects are thread-safe. That is, if two threads make simultaneous calls on one of these objects, then OCCI serializes them internally. However, note that all other OCCI objects, such as `Statement`, `ResultSet`, `SQLException`, `Stream`, and so on, are not thread-safe as, applications should not operate on these objects simultaneously from multiple threads.

Note that the bulk of processing for an OCCI call happens on the server, so if two threads that use OCCI calls go to the same connection, then one of them could be blocked while the other finishes processing at the server.

##### 12.2.3.2 Application-Provided Serialization

In cases where there are multiple threads operating on objects derived from an OCCI environment, you can chose to manage serialization. The first step is to pass a value of `THREADED_UNMUTEXED` for the `createEnvironment` mode. In this case the application must mutual exclusively lock OCCI calls made on objects derived from the same OCCI environment. This has the advantage that the mutex scheme can be optimized based on the application design to gain greater concurrency.

When an OCCI environment is created in this mode, OCCI recognizes that the application is running in a multithreaded application, but that OCCI need not acquire its internal mutexes. OCCI assumes that all calls to methods of objects derived from that OCCI environment are serialized by the application. You can achieve this two different ways:

- Each thread has its own environment. That is, the environment and all objects derived from it (connections, connection pools, statements, result sets, and so on) are not shared across threads. In this case your application need not apply any mutexes.

- If the application shares an OCCI environment or any object derived from the environment across threads, then it must serialize access to those objects (by using a mutex, and so on) such that only one thread is calling an OCCI method on any of those objects.

In both cases, no mutexes are acquired by OCCI. You must ensure that only one OCCI call is in process on any object derived from the OCCI environment at any given time when `THREADED_UNMUTEXED` is used.

OCCI is optimized to reuse objects as much as possible. Since each environment has its own heap, multiple environments result in increased consumption of memory. Having multiple environments may imply duplicating work regarding connections, connection pools, statements, and result set objects. This results in further memory consumption.

Having multiple connections to the server results in more resource consumption on both the server and the network. Having multiple environments normally entails more connections.

#### 12.2.4 Operating System Considerations

Some operating systems provide facilities for spawning processes that allow child processes to reuse states created by their parent process.

After a parent process spawns a child process, the child process must not use the database connection created by the parent. Because SQL\*Net expects only one user process to use a particular connection to the database, attempts by the child process to use the same database connection as the parent may cause undesired connection interference, and result in intermittent `ORA-03137` errors.

When the application requires multiple concurrent connections, Oracle recommends using threads on platforms that support threading. Oracle supports concurrent connections in both single-threaded and multi-threaded applications.

See "Introduction to Thread Safety" and "Implementing Thread Safety" for more information about threads.

For improving performance with many concurrently opened connections, see "[About Pooling Connections](accessing-oracle-database-using-cplusplus.md)".

### 12.3 About Application-Managed Data Buffering

When you provide data for bind parameters by the `set`xxx methods in parameterized statements, the values are copied into an internal data buffer, and the copied values are then provided to the database server for insertion. To reduce overhead of copying `string` type data that is available in user buffers, use the [setDataBuffer()](resultset-class.md) and [next()](resultset-class.md) methods of the [ResultSet Class](resultset-class.md) and the [execute()](statement-class.md) method of the [Statement Class](statement-class.md).

This section includes the following topics:

- Using the setDataBuffer() Method

- Using the executeArrayUpdate() Method

#### 12.3.1 Using the setDataBuffer() Method

For high performance applications, OCCI provides the `setDataBuffer` method whereby the data buffer is managed by the application. The following example shows the [setDataBuffer()](resultset-class.md) method:

    void setDataBuffer(int paramIndex,
       void *buffer,
       Type type,
       sb4 size,
       ub2 *length,
       sb2 *ind = NULL,
       ub2 *rc = NULL);

The following parameters are used in the previous method example:

- `paramIndex`: Parameter number

- `buffer`: Data buffer containing data

- `type`: Type of the data in the data buffer

- `size`: Size of the data buffer

- `length`: Current length of data in the data buffer

- `ind`: Indicator information. This indicates whether the data is `NULL` or not. For parameterized statements, a value of `-1` means a `NULL` value is to be inserted. For data returned from callable statements, a value of `-1` means `NULL` data is retrieved.

- `rc`: Return code. This variable is not applicable to data provided to the `Statement` method. However, for data returned from callable statements, the return code specifies parameter-specific error numbers.

Not all data types can be provided and retrieved by the `setDataBuffer()` method. For instance, C++ Standard Library strings cannot be provided with the `setDataBuffer()` interface.

**See Also:**

[Table 5-2](data-types.md) in [Data Types](data-types.md) for specific cases

There is an important difference between the data provided by the `set`xxx`() `methods and `setDataBuffer()` method. When data is copied in the `set`xxx`()` methods, the original can change once the data is copied. For example, you can use a `setString(str1)` method, then change the value of `str1` before execute. The value of `str1` that is used is the value at the time `setString(str1)` is called. However, for data provided by the `setDataBuffer()` method, the buffer must remain valid until the execution is completed.

If iterative executes or the `executeArrayUpdate()` method is used, then data for multiple rows and iterations can be provided in a single buffer. In this case, the data for the ith iteration is at `buffer + (i-1) *size address` and the length, indicator, and return codes are at `*(length + i)`, `*(ind + i)`, and `*(rc + i)` respectively.

This interface is also meant for use with array executions and callable statements that have array or `OUT` bind parameters.

The same method is available in the `ResultSet` class to retrieve data without re-allocating the buffer for each fetch.

#### 12.3.2 Using the executeArrayUpdate() Method

If all data is provided with the `setDataBuffer()` methods or output streams (that is, no `set`xxx() methods besides `setDataBuffer()` or `getStream()` are called), then there is a simplified way of doing iterative execution.

In this case, you should not call `setMaxIterations()` and `setMaxParamSize()`. Instead, call the `setDataBuffer()` or `getStream()` method for each parameter with the appropriate size arrays to provide data for each iteration, followed by the `executeArrayUpdate(int` `arrayLength)` method. The `arrayLength` parameter specifies the number of elements provided in each buffer. Essentially, this is same as setting the number of iterations to `arrayLength` and executing the statement.

Since the stream parameters are specified only once, they can be used with array executes as well. However, if any `set`xxx`()` methods are used, then the `addIteration()` method is called to provide data for multiple rows. To compare the two approaches, consider Example 12-2 that inserts two employees in the `employees` table:

However, if the first parameter could also be provided through the `setDataBuffer()` interface, then, instead of the `addIteration()` method, you would use the `executeArrayUpdate()` method, as shown in Example 12-3:

Example 12-2 How to Insert Records Using the addIteration() method

    Statement *stmt = conn->createStatement(
      "insert into departments (department_id, department_name) values(:1, :2)");
    char dnames[][100] = {"Community Outreach", "University Recruiting"};
    ub2 dnameLen[2];

    for (int i = 0; i < 2; i++)
      dnameLen[i] = strlen(dnames[i] + 1);

    stmt->setMaxIterations(2);    // set maximum number of iterations

    stmt->setInt(1, 7369);        // specify data for the first row
    stmt->setDataBuffer(2, dnames, OCCI_SQLT_STR, sizeof(dnames[0]), dnameLen);
    stmt->addIteration();

    stmt->setInt(1, 7654);        // specify data for the second row
                                  // a setDatBuffer is unnecessary for the second
                                  // bind parameter as data provided through
                                  // setDataBuffer is specified only once.
    stmt->executeUpdate();

Example 12-3 How to Insert Records Using the executeArrayUpdate() Method

    Statement *stmt = conn->createStatement(
      "insert into departments (department_id, department_name) values(:1, :2)");
    char dnames[][100] = {"Community Outreach", "University Recruiting"};
    ub2 dnameLen[2];

    for (int i = 0; i < 2; i++)
      dnameLen[i] = strlen(dnames[i] + 1);

    int ids[2] = {7369, 7654};
    ub2 idLen[2] = {sizeof(ids[0]), sizeof(ids[1])};
    stmt->setDataBuffer(1, ids, OCCIINT, sizeof(ids[0]), idLen);
    stmt->setDataBuffer(2, dnames, OCCI_SQLT_STR, sizeof(dnames[0]), dnameLen);

    stmt->executeArrayUpdate(2);      // data for two rows is inserted.

### 12.4 Using the Array Fetch Using next() Method

If the application is fetching data with only the `setDataBuffer()` interface or the stream interface, then an array fetch can be executed. The array fetch is implemented through the `next(`) method of the `ResultSet` class. You must process the results obtained through next() before calling it again.

This causes up to `numRows` amount of data to be fetched for each column. The buffers specified with the `setDataBuffer()` interface should large enough to hold at least `numRows` of data.

Example 12-4 How to use Array Fetch with a ResultSet

    ResultSet *resultSet = stmt->executeQuery(...);
    resultSet->setDataBuffer(...);
    while (resultSet->next(numRows) == DATA_AVAILABLE)
       process(resultSet->getNumArrayRows() );

### 12.5 Modifying Rows Iteratively

To process batch errors, specify that the `Statement` object is in a `batchMode` of execution using the [setBatchErrorMode()](statement-class.md) method. Once the `batchMode` is set and a batch update runs, any resulting errors are reported through the [BatchSQLException Class](batchsqlexcept-class.md).

The `BatchSQLException` class provides methods that handle batch errors. Example 12-5 illustrates how batch handling can be implemented within any OCCI application.

Example 12-5 How to Modify Rows Iteratively and Handle Errors

1.  Create the Statement object and set its batch error mode to `TRUE`.

        Statement *stmt = conn->createStatement ("...");
        stmt->setBatchErrorMode (true);

2.  Perform programmatic changes necessary by the application.

3.  Update the statement.

        try {
          updateCount = stmt->executeUpdate ();
        }

4.  Catch and handle any errors generated during the batch insert or update.

        catch (BatchSQLException &batchEx)
        {
          cout<<"Batch Exception: "<<batchEx.what()<<endl;
          int errCount = batchEx.getFailedRowCount();
          cout << "Number of rows failed " << errCount <endl;
          for (int i = 0; i < errCount; i++ )
          {
            SQLException err = batchEx.getException(i);
            unsigned int rowIndex = batchEx.getRowNum(i);
            cout<<"Row " << rowIndex << " failed because of "
               << err.getErrorCode() << endl;
          }
          // take recovery action on the failed rows
        }

5.  Catch and handle other errors generated during the statement update. Note that statement-level errors are still thrown as instances of a `SQLException`.

        catch( SQLException &ex) // to catch other SQLExceptions.
        {
           cout << "SQLException: " << e.what() << endl;
        }

### 12.6 About Using Oracle Connection Manager in Traffic Director Mode

Oracle Connection Manager in Traffic Director Mode is a proxy that is placed between supported database clients and database instances.

Supported clients from Oracle Database 11g Release 2 (11.2) and later can connect to Oracle Connection Manager in Traffic Director Mode. Oracle Connection Manager in Traffic Director Mode provides improved high availability (HA) for planned and unplanned database server outages, connection multiplexing support, and load balancing. Support for Oracle Connection Manager in Traffic Director Mode is described in more detail in the following sections

- Modes of Operation

- Key Features

#### Modes of Operation

Oracle Connection Manager in Traffic Director Mode supports the following modes of operation:

- In pooled connection mode, Oracle Connection Manager in Traffic Director Mode supports any application using the following database client releases:
  - OCI, OCCI, and Open Source Drivers (Oracle Database 11g release 2 (11.2.0.4) and later))

  - JDBC (Oracle Database 12c release 1 (12.1) and later)

  - ODP.NET (Oracle Database 12c release 2 (12.2) and later)

  In addition, applications must use DRCP. That is, the application must enable DRCP in the connect string (or in the `tnsnames.ora` alias).

- In non-pooled connection (or dedicated) mode, Oracle Connection Manager in Traffic Director Mode supports any application using database client releases Oracle Database 11g release 2 (11.2.0.4) and later. In this mode, some capabilities, such as connection multiplexing are not available.

#### Key Features

Oracle Connection Manager in Traffic Director Mode furnishes support for the following:

- Transparent performance enhancements and connection multiplexing, which includes:
  - Statement caching, rows prefetching, and result set caching are auto-enabled for all modes of operation.

  - Database session multiplexing (pooled mode only) using the proxy resident connection pool (PRCP), where PRCP is a proxy mode of Database Resident Connection Pooling (DRCP). Applications get transparent connect-time load balancing and run-time load balancing between Oracle Connection Manager in Traffic Director Mode and the database.

  - For multiple Oracle Connection Manager in Traffic Director Mode instances, applications get increased scalability through client-side connect time load balancing or with a load balancer (BIG-IP, NGINX, and others)
- Zero application downtime
  - Planned database maintenance or pluggable database (PDB) relocation
    - Pooled mode

      Oracle Connection Manager in Traffic Director Mode responds to Oracle Notification Service (ONS) events for planned outages and redirects work. Connections are drained from the pool on Oracle Connection Manager in Traffic Director Mode when the request completes. Service relocation is supported for Oracle Database 11g release 2 (11.2.0.4) and later.

      For PDB relocation, Oracle Connection Manager in Traffic Director Mode responds to in-band notifications when a PDB is relocated, that is even when ONS is not configured (for Oracle Database release 18c, version 18.1 and later server only) 

    - Non-pooled or dedicated mode

      When there is no request boundary information from the client, Oracle Connection Manager in Traffic Director Mode supports planned outage for many applications (as long as only simple session state and cursor state need to be preserved across the request/transaction boundaries). This support includes:
      - Stop service/PDB at the transaction boundary or it leverages Oracle Database release 18c continuous application availability to stop the service at the request boundary

      - Oracle Connection Manager in Traffic Director Mode leverages Transparent Application Failover (TAF) failover restore to reconnect and restore simple states.

  - Unplanned database outages for read-mostly workloads
- High Availability of Oracle Connection Manager in Traffic Director Mode to avoid a single point of failure. This is supported by:
  - Multiple instances of Oracle Connection Manager in Traffic Director Mode using a load balancer or client side load balancing/failover in the connect string

  - Rolling upgrade of Oracle Connection Manager in Traffic Director Mode instances

  - Graceful close of existing connections from client to Oracle Connection Manager in Traffic Director Mode for planned outages

  - In-band notifications to Oracle Database release 18c and later clients

  - For older clients, notifications are sent with the response of the current request
- For security and isolation, Oracle Connection Manager in Traffic Director Mode furnishes:
  - Database Proxy supporting transmission control protocol/transmission control protocol secure (TCP/TCPS) and protocol conversion

  - Firewall based on the IP address, service name, and secure socket layer/transport layer security (SSL/TLS) wallets

  - Tenant isolation in a multi-tenant environment

  - Protection against denial-of-service and fuzzing attacks

  - Secure tunneling of database traffic across Oracle Database on-premises and Oracle Cloud

**See Also:**

- [Oracle Database Net Services Administrator's Guide](../netag/configuring-oracle-connection-manager.md) for information about configuring `cman.ora` configuration file to set up Oracle Connection Manager in Traffic Director Mode

- [Oracle Database Net Services Administrator's Guide](../netag/configuring-oracle-connection-manager.md) for information about configuring databases for Oracle Connection Manager in Traffic Director Mode proxy authentication

- [Oracle Database Net Services Administrator's Guide](../netag/configuring-oracle-connection-manager.md) for information about configuring Oracle Connection Manager in Traffic Director Mode for unplanned down events

- [Oracle Database Net Services Administrator's Guide](../netag/configuring-oracle-connection-manager.md) for information about configuring Oracle Connection Manager in Traffic Director Mode for planned down events

- [Oracle Database Net Services Administrator's Guide](../netag/configuring-oracle-connection-manager.md) for information about configuring proxy resident connection pools for use by Oracle Connection Manager in Traffic Director Mode

- [Oracle Database Net Services Administrator's Guide](../netag/configuring-oracle-connection-manager.md) for information about functionality not supported for all drivers with Oracle Connection Manager in Traffic Director Mode

- [Oracle Database Net Services Reference](../netrf/index.md) for an overview of Oracle CMAN configuration file

### 12.7 About Run-time Load Balancing of the Stateless Connection Pool

Run-time load balancing in a stateless connection pool dynamically routs connection requests to the least loaded instance of the database. This is achieved by use of service metrics, which are distributed by the Oracle RAC load-balancing advisory.

The feature modifies the stateless connection pool in the following ways:

- The pool receives periodic notifications about the instance load.

- When a request for a connection is received, the pool picks the best possible connection for the type of request, based on the load of the instance.

- The stateless connection pool periodically terminates connections of overloaded instances, maintaining the connection topology that corresponds to the instance load.

- Since the connections to overloaded instances may be terminated, the pool creates new connections to maintain the concurrency requirement. These new connections are created using the connect-time load balancing of the Oracle RAC listener.

Run-time load balancing is turned on by default when the OCCI environment is created in `THREADED_MUTEXED` and `EVENTS` modes, and when the server is configured to issue event notifications.

**See Also:**

[Oracle Call Interface Programmer's Guide](../lnoci/index.md)

This section includes the following topic: API Support.

#### 12.7.1 API Support

New `NO_RLB` option for the `PoolType` attribute of the [StatelessConnectionPool Class](statelessconnectionpool-class.md) disables run-time load balancing.

### 12.8 About Fault Diagnosability

Fault diagnosability captures diagnostic data, such as dump files or core dump files, on the OCCI client when a problem incident occurs. For each incident, the fault diagnosability feature creates an Automatic Diagnostic Repository (ADR) subdirectory for storing this diagnostic data. For example, if either a Linux or a UNIX application fails with a null pointer reference, then the core file appears in the ADR home directory (if it exists), not in the operating system directory. This section discusses the ADR subdirectory structure and the utility to manage its output, the ADR Command Interpreter (ADRCI).

An ADR home is the root directory for all diagnostic data for an instance of a product, such as OCCI, and a particular operating system user. All ADR homes appear under the same root directory, the ADR base.

**See Also:**

[Oracle Database Administrator’s Guide](../admin/diagnosing-and-resolving-problems.md)

This section includes the following topics:

- Using ADR Base Location

- Using ADRCI

- Controlling ADR Creation and Disabling Fault Diagnosability

#### 12.8.1 Using ADR Base Location

The location of the ADR base is determined in the following order:

1.  In the `sqlnet.ora` file (on Windows, in the `%TNS_ADMIN%` directory, or on Linux or UNIX, in the `$TNS_ADMIN` directory).
    If there is no `TNS_ADMIN` directory, then `sqlnet.ora` is stored in the current directory.

    If the ADR base is listed in the `sqlnet.ora` file, it is a statement of the type:

        ADR_BASE=/directory/adr

    where:

    - The `adr` argument is a directory that must exist and be writable by all operating system users who execute OCCI applications and want to share the same ADR base.

    - The `directory` argument is the path name

    If `ADR_BASE` is set, and if all users share a single `sqlnet.ora` file, then OCCI stops searching when directory `adr` does not exist or if it is not writable. If `ADR_BASE` is not set, then OCCI continues the search, testing for the existence of other specific directories.

    For example, if `sqlnet.ora` contains the entry `ADR_BASE=/home/chuck/test` then:

    - ADR base is:

          /home/chuck/test/oradiag_chuck

    - ADR home may be:

          /home/chuck/test/oradiag_chuck/diag/clients/user_chuck/host_4144260688_11
2.  If the Oracle base exists (on Windows: `%ORACLE_BASE%`, or on Linux and UNIX: `$ORACLE_BASE`), the client subdirectory also exists because it is created by the Oracle Universal Installer when the database is installed.
    For example, if `$ORACLE_BASE` is `/home/chuck/obase` , then:

    - ADR base is:

          /home/chuck/obase

    - ADR home may be:

          /home/chuck/obase/diag/clients/user_chuck/host_4144260688_11
3.  If the Oracle home exists (on Windows: `%ORACLE_HOME%`, or on Linux and UNIX: `$ORACLE_HOME`), the client subdirectory also exists because it is created by the Oracle Universal Installer when the database is installed.
    For example, if `$ORACLE_HOME` is `/ade/chuck_l1/oracle` , then:

    - ADR base is:

          /ade/chuck_l1/oracle/log

    - ADR home may be:

          /ade/chuck_l1/oracle/log/diag/clients/user_chuck/host_4144260688_11
4.  On the operating system home directory.
    - On Windows, the operating system home directory is `%USERPROFILE%`.

      The location of folder `Oracle` is at:

          C:\Documents and Settings\chuck

      If the application runs as a service, the home directory option is skipped.

    - On Linux and UNIX, the operating system home directory is `$HOME`.

      The location may be:

          /home/chuck/oradiag_chuck

    For example, in an Instant Client, if `$HOME` is `/home/chuck`, then:

    - ADR base is:

          /home/chuck/oradiag_chuck

    - ADR home may be:

          /home/chuck/oradiag_chuck/diag/clients/user_chuck/host_4144260688_11

    **See Also:**

    "[About the Instant Client](installation-and-upgrading.md)"
5.  In the temporary directory.
    - On Windows, the temporary directories are searched in the following order:

      - `%TMP%`

      - `%TEMP%`

      - `%USERPROFILE%`

      - Windows system directory

    - On Linux and UNIX, the temporary directory is in `/var/tmp`.

    For example, in an Instant Client, if `$HOME` is not writable, then:

    - ADR base is:

          /var/tmp/oradiag_chuck

    - ADR home may be:

          /var/tmp/oradiag_chuck/diag/clients/user_chuck/host_4144260688_11

If none of these directory choices are available and writable, ADR is not created and diagnostics are not stored.

**See Also:**

[Oracle Database Net Services Reference](../netrf/index.md)

#### 12.8.2 Using ADRCI

ADRCI is a command-line tool that enables you to view diagnostic data within the ADR, and to package incident and problem information into a zip file that can be shared with Oracle Support. ADRCI can be used either interactively and through a script.

A problem is a critical error in OCI or the client. Each problem has a problem key. An incident is a single occurrence of a problem, and it is identified by a unique numeric incident ID. Each incident has a problem key which has a set of attributes: the `ORA` error number, error parameter values, and similar information. Two incidents have the same root cause if their problem keys match.

The following examples demonstrate how to use ADRCI on a Linux operating system. Note that ARDCI commands are case-insensitive. All user input is in bold typeface.

**See Also:**

- [Oracle Database Utilities](../sutil/oracle-adr-command-interpreter-adrci.md)for an introduction to the ADRCI

- "[About the Instant Client](installation-and-upgrading.md)"

Example 12-6 How to Use ADRCI for OCCI Application Incidents

To launch ADRCI in a Linux system, use the `adrci` command. Once ADRCI starts, find out the particulars of the `show base` command with `help`, and then determine the base of a particular client using the `-product client` option (necessary for OCCI applications). To set the ADRCI base, use the set base command. Once `ADRCI` starts, then the default ADR base is for the `rdbms` server. The `$ORACLE_HOME` is set to `/ade/chuck_l3/oracle`. To view the incidents, use the `show incidents` command. to exit ADRCI, use the `quit` command.

    % adrci

    ADRCI: Release 11.2. - on Wed November 25 16:16:55 2008

    Copyright (c) 1982, 2008, Oracle.  All rights reserved.

    adrci> help show base

      Usage: SHOW BASE [-product <product_name>]

      Purpose: Show the current ADR base setting.

      Options:
        [-product <product_name>]: This option allows users to show the
        given product's ADR Base location. The current registered products are
        "CLIENT" and "ADRCI".

      Examples:
        show base -product client
        show base

    adrci> show base -product client
    ADR base is "/ade/chuck_l3/oracle/log"

    adrci> help set base

      Usage:  SET BASE <base_str>

      Purpose: Set the ADR base to use in the current ADRCI session.
               If there are valid ADR homes under the base, all homes
               are added to the current ADRCI session.

      Arguments:
        <base_str>: It is the ADR base directory, which is a system-dependent
        directory path string.

      Notes:
        On platforms that use "." to signify current working directory,
        it can be used as base_str.

      Example:
        set base /net/sttttd1/scratch/someone/view_storage/someone_v1/log
        set base .

    adrci> set base /ade/chuck_l3/oracle/log

    adrci> show incidents
    ...
    adrci> quit

Example 12-7 How to Use ADRCI for Instant Client

Because Instant Client does not use `$ORACLE_HOME`, the default ADR base is the user's home directory.

    adrci> show base -product client
    ADR base is "/home/chuck/oradiag_chuck"
    adrci> set base /home/chuck/oradiag_chuck
    adrci> show incidents

    ADR Home = /home/chuck/oradiag_chuck/diag/clients/user_chuck/host_4144260688_11:
    *************************************************************************
    INCIDENT_ID    PROBLEM_KEY           CREATE_TIME
    -------------------------------------------------------------------------
    1                     oci 24550 [6]              2007-05-01 17:20:02.803697 -07:00
    1 rows fetched

    adrci> quit

#### 12.8.3 Controlling ADR Creation and Disabling Fault Diagnosability

To disable the fault diagnosability feature, you must turn off the capture of diagnostics. Edit the `sqlnet.ora` file by changing the values of the `DIAG_ADR_ENABLED` and `DIAG_DDE_ENABLED` parameters to either `FALSE` or `OFF`; the default values are either `TRUE` or `ON`.

To turn off the OCCI signal handler and to re-enable standard operating system failure processing, edit the `sqlnet.ora` file by adding the corresponding parameter: `DIAG_SIGHANDLER_ENABLED=FALSE`.

**See Also:**

[Oracle Call Interface Programmer's Guide](../lnoci/build-and-configure-oci-applications.md)

### 12.9 Using Client Result Cache

The Client Result Cache improves the response times of queries that are executed repeatedly. This feature uses client memory to cache results of SQL queries executed and fetched from the database. Subsequent execution of the same query fetches the results from the client cache, reducing server CPU usage. Because database round-trips are eliminated, applications have improved response times.

OCCI applications may transparently use the Client Result Cache feature by enabling OCCI statement caching. Note that `SELECT` queries that must be cached are annotated with a `/*+ result_cache */` hint. Example 12-8 shows how to create a OCCI Statement object that uses such a `SELECT` query.

For usage guidelines, cache consistency, and restrictions, see [Oracle Call Interface Programmer's Guide](../lnoci/performance-topics.md).

Example 12-8 How to Enable and Use the Client Result Cache

    Connection *conn;
    Statement *stmt;
    ResultSet *rs;

    ...
    //enable OCCI Statement Caching
    conn->setStmtCacheSize(20);

    //Specify the hint in the SELECT query
    stmt = conn->createStatement("select /*+ result_cache */ * from products \
                                  where product_id = :1");

    //the following execute fetches rows from the client cache if
    //the query results are cached. If this is the first execute
    //of the query, the results fetched from the server are
    //cached on the client side.
    rs = stmt->executeQuery();

### 12.10 About Client-Side Deployment Parameters and Auto Tuning

Starting with Oracle Database Release 12c Release 1 (12.1), Oracle provides `oraaccess.xml`, a client-side configuration file that can be used to configure selected properties, allowing the application behavior to be changed during deployment without modifying the source code.

**Note:**

Do not use the prefetch deployment parameter if the OCCI application is already using the `setPrefetchRowCount()` or `setPrefetchMemorySize()` methods.

**See:**

[Oracle Call Interface Programmer's Guide](../lnoci/index.md) for more information about client-side deployment parameters and auto tuning
