This chapter discusses features, utilities, and tips to enhance performance of your SQLJ application and to debug your SQLJ source code at run time. The following topics are discussed:

- Performance Enhancement Features

- SQLJ Debugging Features

- SQLJ Support for Oracle Performance Monitoring

### 11.1 Performance Enhancement Features

The Oracle SQLJ implementation includes features to enhance performance by making data access more efficient. These include the following:

- Row Prefetching

- Statement Caching

- Update Batching

- Column Definitions

- Parameter Size Definitions

**See Also:**

[Oracle Database JDBC Developer's Guide](../jjdbc/data-access-and-manipulation.md)

Your application will likely benefit from the default Oracle-specific code generation. The generated code will be optimized with direct calls to Oracle Java Database Connectivity (JDBC) driver, eliminating the overhead of intermediate calls to the SQLJ run time, which in turn would call JDBC.

**See Also:**

"[Oracle-Specific Code Generation (No Profiles)](key-programming-considerations.md)"

**Note:**

The Oracle SQLJ implementation does not support batch fetches, which is the fetching of sets of rows into arrays of values. However, you may be able to use Oracle row prefetching to obtain some of the benefits of batch fetching.

In addition to the preceding SQLJ performance enhancements, you can use optimizer hints in the SQL operations within a SQLJ program, as you can in any Oracle SQL operations.

The Oracle SQL implementation enables you to tune your SQL statements by using "`/*+`" or "`--+`" comment notation to pass hints to Oracle SQL optimizer. The SQLJ translator recognizes and supports these optimizer hints, passing them at run time as part of your SQL statement.

You can also define cost and selectivity information for a SQLJ stored function, as for any other stored function, using the extensibility features for SQL optimization in Oracle Database 12c Release 2 (12.2). During SQL execution, the optimizer invokes the cost and selectivity methods for the stored function, evaluates alternate strategies for execution, and chooses an efficient execution plan.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/Introduction-to-Oracle-SQL.md) for more information

Note that using Oracle performance extensions in your code requires the following:

- Use one of Oracle JDBC drivers.

- Use the default Oracle-specific code generation, or customize profiles appropriately.

  For ISO standard code generation, the default customizer, `oracle.sqlj.runtime.util.OraCustomizer`, is recommended.

- Use Oracle SQLJ run time when your application runs.

Oracle SQLJ run time and an Oracle JDBC driver are required by your application whenever you customize profiles with Oracle customizer, even if you do not actually use Oracle extensions in your code.

#### 11.1.1 Row Prefetching

Standard JDBC receives the results of a query one row at a time, with each row requiring a separate round trip to the database. Row prefetching enables you to receive the results more efficiently, in groups of multiple rows each.

Use the `setFetchSize()` method of an `ExecutionContext` instance to set the number of rows to be prefetched whenever you execute a `SELECT` statement (for SQLJ statements using the particular `ExecutionContext` instance).

The `getFetchSize()` method of an `ExecutionContext` instance returns the current prefetch size, as an `int` value.

The following is an example of setting the prefetch size to 20 by getting the default execution context instance of the default connection context instance and calling the `setFetchSize()` method:

    DefaultContext.getDefaultContext().getExecutionContext().setFetchSize(20);

It is also possible to set the prefetch size directly on the underlying `OracleConnection` object using the JDBC application programming interface (API), but in SQLJ this is discouraged.

To specify the number of rows to prefetch for queries that use a given connection context instance, use the underlying JDBC connection, cast to an Oracle`Connection` instance. Following is an example that sets the prefetch value to 20 for your default connection:

    ((OracleConnection)DefaultContext.getDefaultContext().getConnection()).setDefaultRowPrefetch(20);

Also, please note that the prefetch size set on the SQLJ connection context overrides the prefetch size set on the underlying JDBC connection.

Each additional connection context instance you use must be set separately, as desired.The prefetch value needs to be setup on each individual connection context. For example, if `ctx` is an instance of a declared connection context class, set its prefetch value as follows:

    ((Connection)ctx.getConnection()).setDefaultRowPrefetch(20);

    ctx.getExecutionContext().setFetchSize(20);

There is no maximum row-prefetch value. The default is 10 in JDBC, and this is inherited by SQLJ. This value is effective in typical circumstances, although you might want to increase it if you receive a large number of rows.

#### 11.1.2 Statement Caching

SQLJ offers a statement caching feature that improves performance by saving executable statements that are used repeatedly, such as in a loop or in a method that is called repeatedly. When a statement is cached before it is reexecuted, the code does not have to be reparsed (either on the server or on the client), the statement object does not have to be recreated, and the parameter size definitions do not have to be recalculated. Without this feature, repeated statements would have to be reparsed on the client, and perhaps in the server as well, depending on whether a statement is still available in the general server-side SQL cache when it is encountered again.

For Oracle-specific code generation, SQLJ statement caching relies on Oracle JDBC driver, using the JDBC explicit caching mechanism. This is distinct from the JDBC implicit caching mechanism, although there are interdependencies. With Oracle-specific code, statement caching is controlled through connection methods.

**See Also:**

[Oracle Database JDBC Developer's Guide](../jjdbc/statement-and-resultset-caching.md)

For ISO code generation, SQLJ has its own statement caching mechanism through functionality of the SQLJ run time. With ISO code, statement caching is controlled through the Oracle customizer `stmtcache` option.

**Note:**

For Oracle-specific code generation, explicit caching is the only statement caching mechanism that can be manipulated through SQLJ APIs. For the discussion in this document, it will be referred to as SQLJ/explicit statement caching.

In Oracle Database 12c Release 1 (12.1), the default statement cache size is set to 5, provided the JDBC connection is being created by the connection context. If a connection context is created using an already available JDBC connection or data source, then the statement cache size will be set to that of the JDBC connection or the data source.

##### Connection Context Methods for Statement Caching (Oracle-Specific Code)

If you use Oracle-specific code generation, which is the case with the SQLJ translator default `-codegen=oracle` setting, use connection context methods for statement caching functionality. Note that any statement cache size greater than 0 results in SQLJ/explicit statement caching being enabled. By default, it is enabled with a cache size of 5, that is, five statements.

The following Oracle-specific (nonstandard) static methods have been added to the `sqlj.runtime.ref.DefaultContext` class, and are also included in any connection context classes you declare:

- `static void setDefaultStmtCacheSize(int)`

  This sets the default statement cache size for all connection contexts. This becomes the initial statement cache size for any subsequently created instance of any connection context class, not just the class upon which you call the method. The method call does not affect connection context instances that already exist.

  **Note:**

  `setDefaultStmtCacheSize(int)` affects the statement cache size only for the connections that are created using the SQLJ connection contexts. It does not affect the statement cache size for the connections that are created using JDBC connections.

  Consider the following two code snippets:

  Example 1:

      ...
      MyContext.setDefaultStmtCacheSize(10);
      OracleConnection conn = DriverManager.getConnection(url, user, passwd);
      myctx = new MyContext(conn);

  Example 2:

      ...
      MyContext.setDefaultStmtCacheSize(10);
      myctx = new MyContext(url, user, passwd,true);

  In the preceding two examples, the statement cache size will be set to 10 only in the second example. In the first example, the statement cache size corresponding to this connection will not be affected because the connection is created using the `getConnection` method of the `DriverManager` interface from JDBC specification.

- `static int getDefaultStmtCacheSize()`

  This retrieves the current default statement cache size for connection contexts.

And the following Oracle-specific instance methods have also been added to the `DefaultContext` class and are included in any other connection context classes:

- `void setStmtCacheSize(int) throws java.sql.SQLException`

  This sets the statement cache size for the underlying connection of the particular connection context instance (overrides the default).

**Note:**

If SQLJ/explicit caching is already disabled, then setting the size to 0 leaves it disabled. If it is already enabled, then setting the size to 0 leaves it enabled, but renders it nonfunctional.

- `int getStmtCacheSize()`

  This verifies whether SQLJ/explicit statement caching is enabled for the underlying connection of the connection context. If so, it returns the current statement cache size. It can also return either of the following integer constants:

      static int STMT_CACHE_NOT_ENABLED
      static int STMT_CACHE_EXCEPTION

  It is possible for a `getStmtCacheSize()` call to cause a SQL exception. However, for backward compatibility, this method does not throw the exception directly. When an exception occurs, the method returns the constant `STMT_CACHE_EXCEPTION`. In this case, you can call the `getStmtCacheException()` method to find out what exception occurred.

  If you call `getStmtCacheSize()` when SQLJ/explicit caching is disabled, then the method returns the constant `STMT_CACHE_NOT_ENABLED`. This is distinguished from a cache size of 0. Technically, it is possible for SQLJ/explicit caching to be enabled (though useless) with a cache size of 0.

- `java.sql.Exception getStmtCacheException()`

  See if there is a statement caching exception. There are two scenarios for using this method:

  - Call it if a `getStmtCacheSize()` call returns `STMT_CACHE_EXCEPTION`.

  - Call it whenever you create a connection context instance with which you want to use statement caching. This is because of automatic manipulation that occurs with respect to statement cache size whenever you create a connection context instance. If you care about statement caching for the connection context instance, call `getStmtCacheException()` after creating the instance, to verify there were no problems.

##### Enabling and Disabling Statement Caching (Oracle-Specific Code)

With Oracle-specific code, to reiterate what was stated earlier, any nonzero statement cache size results in SQLJ/explicit caching being enabled. Because the default size is 5, statement caching is enabled by default.

You cannot explicitly disable SQLJ/explicit statement caching through SQLJ APIs, although you can effectively disable it (render it nonfunctional) by setting the statement cache size to 0. In this case, the connection context `getStmtCacheSize()` method might return 0, not `STMT_CACHE_NOT_ENABLED`.

You can explicitly disable SQLJ/explicit statement caching or JDBC implicit caching, through JDBC connection APIs. Because SQLJ/explicit caching and JDBC implicit caching use the same cache size, there might sometimes be reason to do so. The following methods are available through the `OracleConnection` class:

- `void setExplicitCachingEnabled(boolean)`

- `boolean getExplicitCachingEnabled()`

- `void setImplicitCachingEnabled(boolean)`

- `boolean getImplicitCachingEnabled()`

You have access to these methods if you retrieve the `OracleConnection` instance from within a SQLJ connection context instance.

**See Also:**

"[SQLJ Connection Context and JDBC Connection Interoperability](advanced-language-features.md)"

**Note:**

In SQLJ, JDBC implicit caching is disabled by default and remains disabled unless you explicitly enable it through the `setImplicitCachingEnabled()` method.

##### Key Interactions Between SQLJ/Explicit Caching and JDBC Implicit Caching

With regard to statement caching in Oracle-specific code, this document naturally emphasizes SQLJ/explicit caching rather than JDBC implicit caching. If you do not use JDBC code in your application, SQLJ/explicit caching is the only statement caching that is relevant. However, there are situations where you might want to use both SQLJ and JDBC code in your application, and in these circumstances you might also want to use implicit caching.

SQLJ/explicit caching and JDBC implicit caching are enabled independently of each other. Furthermore, you do not have access to the implicit cache through SQLJ. However, there is a key interaction between the two, in that they share the same cache size. If, for example, the statement cache size is 5, then you can have a maximum of five statements cached for SQLJ/explicit caching and implicit caching combined.

An important point related to this is that if you choose to effectively disable SQLJ/explicit statement caching by setting the cache size to 0, then you have also effectively disabled implicit caching.

Also be aware that if SQLJ/explicit caching is disabled, changing the cache size to a value greater than 0 will enable it, but this does not affect whether implicit caching is enabled.

##### JDBC Support for Statement Caching (ISO Code)

With ISO standard code generation, specified through the SQLJ translator `-codegen=iso` setting, statement caching is a standard SQLJ feature that does not require any particular JDBC driver. However, using a driver that implements the `sqlj.runtime.profile.ref.ClientDataSupport` interface enables more robust caching. Oracle Database 12c Release 1 (12.1) JDBC drivers implement this interface, providing the following features:

- A separate cache for each database connection, instead of a single static cache for the entire application

- The ability to share cached statements between multiple instances of a connection context class that share the same underlying connection

When a single cache is used, as is the case with a generic JDBC driver that does not implement `ClientDataSupport`, a statement executed in one connection can cause a cached statement from another connection to be flushed (if the statement cache size, the maximum number of statements that can be cached, is exceeded).

##### Oracle Customizer Option for Statement Cache Size (ISO Code)

With ISO standard code generation, statement caching is enabled in your application by default with a cache size of 5 (the same default size as with Oracle-specific code) when you use Oracle customizer, which is typically executed as part of Oracle SQLJ translation.

You can alter the statement cache size as desired, or effectively disable statement caching with a cache size of 0, through the Oracle customizer `stmtcache` option. This is set as `-P-Cstmtcache=``n`, where `n` is an integer.

**See Also:**

"[Oracle Customizer Statement Cache Size Option (stmtcache)](appendix.md)"

If you use multiple connection context classes and, therefore, have multiple profiles, you can set their statement cache sizes individually by running SQLJ (actually, the customizer) separately for each profile.

At run time, the appropriate SQLJ profile determines the statement cache size for a connection. This would be the profile that corresponds to the first connection context class instantiated for this connection. Its statement cache size setting, if any, is determined according to how you set the Oracle customizer `stmtcache` option when you customized the profile. The run-time statement cache size for a connection is set when the first statement on that connection is executed.

##### Additional Statement Caching Behavior

When a SQLJ connection context object is instantiated, if the statement cache size on the underlying JDBC connection is smaller than the default size for the connection context class, then the SQLJ run time will attempt to increase the JDBC statement cache size to the connection context default value. This manipulation occurs even with ISO code generation, enabling explicit statement caching in the process, although this is actually of no relevance in the ISO code case.

If, on the other hand, the actual JDBC statement cache size is larger, then the SQLJ run time will not attempt to perform a change in the cache size. The SQLJ run time checks the actual JDBC cache size against the default size set whenever it creates a SQLJ connection context instance.

It is important to note that these methods have the same effect regardless of the context class on which they are issued, because they modify or report the same underlying static field.

As an example, assume the following connection context class declarations:

    #sql context CtxtA;
    #sql context CtxtB;

In this case, each of the following three code instructions has the effect that whenever a new SQLJ connection context instance is subsequently created, it will not try to enable SQLJ/explicit statement caching:

    sqlj.runtime.ref.DefaultContext.setDefaultStmtCacheSize(0);

    CtxtA.setDefaultStmtCacheSize(0);

    CtxtB.setDefaultStmtCacheSize(0);

**Note:**

If a SQLJ connection context instance is created on an underlying JDBC pooled connection, then SQLJ will not be able to change the JDBC statement cache size. For Oracle-specific code, you can retrieve the resulting exception through the connection context `getStmtCacheException()` method. In this case, the desired JDBC statement cache size must be set explicitly on the underlying physical connections. For data sources, the cache size is set through vendor-specific data source attributes.

SQLJ/explicit caching and JDBC implicit caching functionality have different semantics and behaviors. As noted earlier, SQLJ statement caching applies only to single statements used repeatedly, such as in a loop or through repeated calls to the same method. Consider the following example:

    ...
    #sql { same SQL operaton }; // occurrence #1
    ...
    Java code
    ...
    #sql { same SQL operaton }; // occurrence #2
    ...
    Java code
    ...
    #sql { same SQL operaton }; // occurrence #3
    ...

Assume the three SQL operations are identical, including white space.

SQLJ caching would consider these three occurrences of the same SQL operation to be three different statements. They will occupy three separate slots in the cache. JDBC implicit caching, however, would recognize these as identical statements, using only a single cache slot for all three. The statement would be reused for occurrence \#2 and occurrence \#3.

##### Statement Caching Limitations and Notes

Using a statement cache, even of size 1, will improve the performance of almost any SQLJ application. Be aware of the following, however:

- There is no benefit if each statement is executed only once.

- Try to avoid interleaving statements executed once with statements executed multiple times. The statements being executed only once would needlessly take up space in the statement cache, which becomes an issue when you reach the statement cache size limit. As an alternative, if you use ISO code generation you can use a separate connection context class for statements that are executed only once and disable statement caching for that connection context class.

- Distinct statements with identical SQL operations are treated the same way as any distinct statements. Each is processed and cached separately. As an alternative, put the SQL operation in a method and call the method repeatedly, instead of using distinct statements.

- Be careful in choosing an appropriate statement cache size. If it is too small, then the cache might fill up resulting in statements being flushed before they are reexecuted. If it is too large, then database resources or program resources may be exhausted.

Also be aware of the following general notes regarding statement caching:

- With Oracle-specific code generation, using separate SQLJ connection context instances to have separate statement caching behavior will not work if the connection contexts share the same underlying JDBC connection instance. This is because under Oracle-specific code generation, SQLJ uses the JDBC statement cache.

<!-- -->

- For Oracle applications, the statement cache size plus the maximum number of open JDBC statements in your application, both directly and through SQLJ, should be less than the maximum number of cursors available for a session. This is because the maximum number of cursors defines the maximum number of statements that can be open simultaneously.

- Using a statement cache generally does not change the execution semantics of an operation itself, although there are some scenarios where it does. For example, if you have a statement that throws an exception when its resources are released, then using a cache would mean that the exception would not be thrown until the connection is closed or the statement is flushed from the cache, which happens when the cache size is exceeded.

#### 11.1.3 Update Batching

Update batching, referred to as batch updates in the Sun Microsystems JDBC 2.0 specification, allows `UPDATE`, `DELETE`, and `INSERT` statements that are batchable and compatible to be collected into a batch and sent to the database for execution at once, saving round trips to the database. This feature is included in the JDBC and SQLJ specifications and is supported by the Oracle JDBC and SQLJ implementations. Update batching is typically used for an operation that is executed repeatedly within a loop.

In SQLJ, update batching is tied to execution context usage. This feature is enabled or disabled in each execution context, independently of any other execution context, and each execution context instance maintains its own batch.

**Note:**

Be aware of the following for update batching:

- You must use the default Oracle-specific code generation or, for ISO code generation, customize your application with Oracle customizer.

- It is highly advisable to disable auto-commit mode. This gives you control of what to commit and what to roll back in case of an error during batch execution.

##### Batchable and Compatible Statements

Two criteria determine whether a statement can be added to an existing batch of statements:

- Is it batchable? You cannot batch some kinds of statements under any circumstances.

- Is it compatible with statements in the existing batch?

For SQLJ, the following kinds of statements are batchable:

- `UPDATE`

- `INSERT`

- `DELETE`

However `UPDATE` and `INSERT` statements with one or more stream host expressions are not batchable.

In SQLJ, only multiple instances of the same statement are compatible. This can occur in either of two circumstances:

- A statement is executed repeatedly in a loop.

- A statement is executed in a method, and the method is called repeatedly.

##### Enabling and Disabling Update Batching

SQLJ performs update batching separately for each execution context instance. Each one can have update batching enabled independently of your other execution context instances, and each maintains its own batch.

To enable or disable update batching for a particular execution context instance, use the `setBatching()` method of that execution context instance. This method takes boolean input, as follows:

    ...
    ExecutionContext ec = new ExecutionContext();
    ec.setBatching(true);
    ...

or:

    ...
    ExecutionContext ec = new ExecutionContext();
    ec.setBatching(false);
    ...

Update batching is disabled by default.

**Note:**

The `setBatching()` method does not affect an existing statement batch. Neither enabling nor disabling update batching causes an existing batch to be executed or canceled.

Use the `isBatching()` method of an execution context instance to determine if update batching is enabled for that execution context:

    ExecutionContext ec = new ExecutionContext();
    ...
    boolean batchingOn = ec.isBatching();

This does not, however, indicate whether a batch is currently pending.

##### Explicit and Implicit Batch Execution

You can explicitly execute a pending update batch as desired, but it might also be implicitly executed under certain circumstances.

**Note:**

It is important to be aware of what happens when an exception occurs in the middle of a batch execution.

Use the `executeBatch()` method of the execution context instance to explicitly execute an update batch. This method returns an `int` array of update counts.

Following is an example of explicitly executing a batch:

    ...
    ExecutionContext ec = new ExecutionContext();
    ec.setBatching(true);
    ...
    double[] sals = ...;
    String[] empnos = ...;
    for (int i = 0; i < empnos.length; i++)
    {
       #sql [ec] { UPDATE employees SET salary = :(sals[i]) WHERE employee_id = :(empnos[i]) };
    }
    int[] updateCounts = ec.executeBatch();
    ...

**Note:**

If you invoke `executeBatch()` when the execution context instance has no pending batch, then the method returns `null`.

When a pending update batch exists, it is implicitly executed in the following circumstances:

- An executable statement is encountered that is not batchable. In this case the existing batch is executed first, then the nonbatchable statement is executed.

- An update statement is encountered that is batchable, but is not compatible with the statements in the existing batch, in other words, is not an instance of the same statement. In this case the batch is executed, then a new batch is created, starting with the incompatible statement.

- A predefined batch limit, that is, a specified number of statements, is reached.

Following is an example. First one batch is created and executed implicitly when an unbatchable statement is encountered, then a new batch is created and executed implicitly when a batchable, but incompatible, statement is encountered:

    ExecutionContext ec = new ExecutionContext();
    ec.setBatching(true);
    ...
    /* Statements in the following loop will be placed in a batch */
    double[] sals = ...;
    String[] empnos = ...;
    for (int i = 0; i < empnos.length; i++)
    {
       #sql [ec] { UPDATE employees SET salary = :(sals[i]) WHERE employee_id = :(empnos[i]) };
    }

    /* a SELECT is unbatchable so causes the batch to be executed */
    double avg;
    #sql [ec] { SELECT avg(salary) INTO :avg FROM employees };

    /* Statements in the following loop will be placed in a new batch */
    double[] comms = ...;
    for (int i = 0; i < empnos.length; i++)
    {
       #sql [ec] { UPDATE employees SET commission_pct = :(comms[i]) WHERE employee_id = :(empnos[i]) };
    }

    /* the following update is incompatible with the second batch, so causes it to be executed */
    int smithdeptno = ...;
    #sql [ec] { UPDATE employees SET department_no = :deptno WHERE first_name = 'Smith' };

To obtain the update count array for a batch executed implicitly, invoke the `getBatchUpdateCounts()` method of the execution context instance. This returns the update counts for the last batch to be executed successfully in this execution context instance. The following code statement could be inserted after the `SELECT` and after the last `UPDATE`:

    int[] updateCounts = ec.getBatchUpdateCounts();

**Note:**

If no update batch has been executed successfully for the execution context instance, then `getBatchUpdateCounts()` returns `null`.

##### Canceling a Batch

To cancel the batch that is pending in an execution context, use the `cancel()` method of the execution context instance. You can, for example, cancel a batch that has been executed, but not yet committed, in the event that an exception occurred during batch execution. Following is an example:

    ...
    ExecutionContext ec = new ExecutionContext();
    ec.setBatching(true);
    ...
    double[] sals = ...;
    String[] empnos = ...;
    for (int i = 0; i < empnos.length; i++)
    {
       #sql [ec] { UPDATE employees SET salary = :(sals[i]) WHERE employee_id = :(empnos[i]) };
       if (!check(sals[i], empnos[i])) //assume "check" is a user-supplied function
       {
          ec.cancel();
          throw new SQLException("Process canceled.");
       }
    }

    try
    {
       int[] updateCounts = ec.executeBatch();
    } catch ( SQLException exception) { ec.cancel(); }
    ...

When you cancel a batch, the next batchable statement will start a new batch.

**Note:**

- Calling `cancel()` will also cancel any statement currently executing.

- Canceling a batch does not disable update batching.

##### Execution Context Update Counts

In the Oracle Database 12c Release 1 (12.1) SQLJ implementation, the array of update counts returned by the `executeBatch()` or `getBatchUpdateCounts()` method of an execution context instance does not contain counts of the number of rows updated by the batched statements, but simply values indicating whether each statement was successful. So its functionality differs from that of the single update count returned by the `getUpdateCount()` method of the execution context instance when batching is not enabled. As statements are batched, and after batch execution, the single update count returned by `getUpdateCount()` is also affected.

In a batch-enabled environment, the value available from the `getUpdateCount()` method of the execution context instance is modified after each statement is encountered. It will be updated with one of several `ExecutionContext` class static `int` constant values, as follows:

- `NEW_BATCH_COUNT`: Indicates that a new batch was created for the last statement encountered.

- `ADD_BATCH_COUNT`: Indicates that the last statement encountered was added to an existing batch.

- `EXEC_BATCH_COUNT`: Indicates that the pending batch was executed, either explicitly or implicitly, after the last statement was encountered.

If you want to refer to these constants, then use the following qualified names:

    ExecutionContext.NEW_BATCH_COUNT
    ExecutionContext.ADD_BATCH_COUNT
    ExecutionContext.EXEC_BATCH_COUNT

After a batch has been executed, either explicitly or implicitly, the array of values returned by `executeBatch()` or `getBatchUpdateCounts()` indicates only whether the statements executed successfully. There is an array element for each batched statement. In accordance with the JDBC 2.0 specification, a value of `-2` for an array element indicates that the corresponding statement completed successfully, but that the number of rows it affected is unknown.

Checking all the array values after execution of a batch would not be meaningful. As currently implemented, the only useful test of this array would be to verify the number of statements that were in the batch prior to execution, by checking the number of elements in the array after a successful execution (essentially, after a batch execution that does not produce an exception).

Note that the update counts array is not modified as statements are batched, only as the batch is executed.

##### Setting a Batch Limit

You can specify that each update batch be executed after a predefined number of statements have been batched, before the next statement would be added. Use the `setBatchLimit()` method of the execution context instance, inputting a positive, nonzero integer as follows:

    ...
    ExecutionContext ec = new ExecutionContext();
    ec.setBatching(true);
    ec.setBatchLimit(10);
    ...
    double[] sals = ...;
    String[] empnos = ...;
    for (int i = 0; i < 20; i++)
    {
       #sql [ec] { UPDATE emp1 SET sal = :(sals[i]) WHERE empno = :(empnos[i]) };
    }

This loop is executed 20 times, with the statements being batched and the batch being executed during the 11th time through the loop, before the 11th statement would be added to the batch. Note that the batch would not be executed a second time in the loop, however. When your application exits the loop, the last ten statements would still be in the batch and would not be executed until another statement is encountered or you execute the batch explicitly.

You can use two special static `int` constants of the `ExecutionContext` class as input to the `setBatchLimit()` method:

- `AUTO_BATCH`: Enables the SQLJ run time to determine the batch limit.

- `UNLIMITED_BATCH` (default): Specifies that there is no batch limit.

For example:

    ...
    ExecutionContext ec = new ExecutionContext();
    ec.setBatching(true);
    ec.setBatchLimit(ExecutionContext.AUTO_BATCH);
    ...

or:

    ec.setBatchLimit(ExecutionContext.UNLIMITED_BATCH);
    ...

To check the current batch limit, use the `getBatchLimit()` method of the execution context instance.

##### Batching Incompatible Statements

If you want to batch a statement that is incompatible with statements in an existing batch, without implicitly executing the existing batch, then you will have to use a separate execution context instance. Following is an example:

    ...
    ExecutionContext ec1 = new ExecutionContext();
    ec1.setBatching(true);
    ExecutionContext ec2 = new ExecutionContext();
    ec2.setBatching(true);
    ...
    double[] sals = ...;
    String[] empnos = ...;
    for (int i = 0; i < empnos.length; i++)
    {
       #sql [ec1] { UPDATE emp1 SET sal = :(sals[i]) WHERE empno = :(empnos[i]) };
       #sql [ec2] { UPDATE emp2 SET sal = :(sals[i]) WHERE empno = :(empnos[i]) };
    }
    int[] updateCounts1 = ec1.executeBatch();
    int[] updateCounts2 = ec2.executeBatch();
    ...

**Note:**

This example assumes that the two `UPDATE` statements are completely independent of each other. Do not batch interdependent statements in different execution contexts because you cannot completely assure the order in which they will be executed.

An alternative is to use a single execution context and separate loops so that all the `EMP1` updates are batched and executed prior to the `EMP2` updates:

    ...
    ExecutionContext ec = new ExecutionContext();
    ec.setBatching(true);
    ...
    double[] sals = ...;
    String[] empnos = ...;
    for (int i = 0; i < empnos.length; i++)
    {
       #sql [ec] { UPDATE emp1 SET sal = :(sals[i]) WHERE empno = :(empnos[i]) };
    }
    for (int i = 0; i < empnos.length; i++)
    {
       #sql [ec] { UPDATE emp2 SET sal = :(sals[i]) WHERE empno = :(empnos[i]) };
    }
    ec.executeBatch();
    ...

This example executes the first batch implicitly and the second batch explicitly.

##### Using Implicit Execution Contexts for Update Batching

All the update batching examples so far have created and specified explicit execution context instances. This is not necessary, however, given that every connection context instance has an implicit execution context instance. For example, you can access the implicit execution context instance of the default connection as follows:

    DefaultContext.getDefaultContext().getExecutionContext().setBatching(true);
    ...
    double[] sals = ...;
    String[] empnos = ...;
    for (int i = 0; i < empnos.length; i++)
    {
       #sql { UPDATE employees SET salary = :(sals[i]) WHERE employee_id = :(empnos[i]) };
    }
    // implicitly execute the batch and commit
    #sql { COMMIT };

Or, you could execute the batch explicitly, as follows:

    DefaultContext.getDefaultContext().getExecutionContext().executeBatch();

##### General Cautions Regarding Update Batching

If you use update batching, especially if you mix statements using an unbatched execution context instance with statements using a batched execution context instance, then remember the following points:

- If an unbatched statement depends on a batched statement, then be sure the batch is executed prior to the unbatched statement.

- A JDBC `COMMIT` or `ROLLBACK` operation, that is, an auto-commit or any explicit use of the `commit()` or `rollback()` method of a JDBC `Connection` instance, does not execute pending statements in a batch.

  It is important to note, however, that using a SQLJ `COMMIT` or `ROLLBACK` statement, such as follows, will execute pending statements in a batch:

      #sql { COMMIT };

  or:

      #sql { ROLLBACK };

  This is another reason that you should always commit or roll back changes using `#sql` syntax, which cleans up both SQLJ resources and JDBC resources.

- When a batch is implicitly executed as a result of an unbatchable or incompatible statement being encountered, the batch is executed before the unbatchable or incompatible statement is executed, but after the input parameters of that statement have been evaluated and passed to the statement.

- If you no longer intend to use a particular batch-enabled execution context instance, then explicitly execute or cancel its pending batch to free resources.

##### Error Conditions During Batch Execution

In the event that a statement causes an exception in the middle of a batch execution, be aware of the following:

- Batched statements following the statement that caused the exception are not executed.

- Batched statements that had already been executed prior to the exception are not rolled back.

- If the batch where the exception occurred was executed implicitly as the result of another (unbatchable or incompatible) statement being encountered, that statement is not executed.

**Note:**

Presumably you have disabled auto-commit mode when using update batching. This gives you commit/rollback control in case of an error during batch execution.

When an exception occurs during batch execution under JDBC 2.0 or later, it is typically an instance of the standard `java.sql.BatchUpdateException` class, a subclass of the `java.sql.SQLException` class. The `BatchUpdateException` class has a `getUpdateCounts()` method that, for batched statements successfully executed before the exception occurred, returns an array of update counts equivalent to what would be returned by the `executeBatch()` or `getBatchUpdateCounts()` method of the `ExecutionContext` class.

##### Recursive Call-ins and Update Batching

Execution of SQLJ stored procedures, where one calls the other, can result in situations where the two procedures are simultaneously using the same execution context instance. The update-batching flag, set using the `setBatching()` method of the execution context instance, would act in the same way as other execution context attributes. Regardless of which stored procedure sets it, it would affect the next executable statement in either stored procedure.

For this reason, update batching is automatically disabled in the server whenever a recursive call-in occurs. The pending batch is executed, and no batching occurs in the recursively invoked procedure. To avoid this behavior, use explicit execution context instances in batch-enabled stored procedures.

#### 11.1.4 Column Definitions

The Oracle SQLJ implementation reflects Oracle JDBC support for column type and size definitions. Depending on the driver implementation, which differs somewhat among the different Oracle JDBC drivers, registering column types and sizes can save a trip to the database for each query. In particular, this is true for Oracle JDBC Thin driver and use of positional iterators.

##### Oracle Implementation of Column Definitions

If you enable column definitions, then the Oracle SQLJ implementation takes the following steps to automatically register column types and sizes:

- During customization or during translation when the default Oracle-specific code generation is used, SQLJ connects to a specified database schema to determine types and sizes of columns being retrieved. With ISO standard SQLJ code generation, the column defaults become part of the SQLJ profile. This can be accomplished during the customization step of source code translation or during separate customization of an existing profile.

- When your application executes, the SQLJ run time will use the column information to register the column types and sizes with the JDBC driver, using a call to the `defineColumnType()` method available in the Oracle JDBC statement classes.

##### Customizer and Translator Options for Column Definitions

To enable column definitions, set SQLJ options as follows:

- Enable the `optcols` flag. For Oracle-specific code generation, use the SQLJ translator `-optcols` option. For ISO standard code generation, use either the translator option or the Oracle customizer option (`-P-Coptcols` on the SQLJ command line).

- Set the user, password, and URL for a database connection. For Oracle-specific code generation, this is through the SQLJ translator `-user`, `-password`, and `-url` options. For ISO standard code generation, this can be through the translator options or you can separately use the customizer options (`-P-user`, `-P-password`, and `-P-url` on the SQLJ command line). In addition, set the JDBC driver class (`-P-driver` on the SQLJ command line) if you are not using the default `OracleDriver` class.

For information about the customizer options, refer to the `optcols` section under "[Overview of Customizer-Specific Options](appendix.md)", and the `user`, `password`, `url`, and `driver` sections under "[Overview of Customizer Harness Options](appendix.md)".

#### 11.1.5 Parameter Size Definitions

The Oracle JDBC and SQLJ implementations enable you to optimize JDBC resource allocation by defining parameter sizes (sizes of Java host variables) used as any of the following:

- Input or output parameters in stored procedure or function calls

- Return values from stored function calls

- Input or output parameters in SET statements

- Input or output parameters in PL/SQL blocks

##### Oracle Implementation of Parameter Size Definitions

Oracle implements parameter size definitions through option settings, in combination with hints embedded in source code comments. For ISO standard SQLJ code generation, Oracle customizer options are available. For the default Oracle-specific code generation, equivalent SQLJ translator options are available.

Use options and hints as follows:

- Enable parameter size definitions through the SQLJ translator or Oracle customizer parameter definition flag.

- Specify default sizes for particular data types through the SQLJ translator or Oracle customizer parameter default size option.

- Override data type default sizes for particular parameters by embedding hints in source code comments, following a prescribed format.

For any given host variable, when parameter size definitions are enabled, resources are allocated according to the source code hint if there is one. If there is no source code hint, then the default size for the corresponding data type is used if one was specified. If there is no source code hint or appropriate default size, then maximum resources are allocated according to the JDBC implementation.

When your application executes, the parameter sizes are registered through calls to the `defineParameterType()` and `registerOutParameter()` methods available in the Oracle JDBC statement classes.

**Note:**

If you do not enable the parameter definition flag, then parameter size defaults and source code hints will be ignored and maximum or default resources will be allocated according to the JDBC implementation.

##### Customizer and Translator Options for Parameter Size Definitions

Use the following SQLJ options for parameter size definitions:

- Use the `optparams` flag to enable parameter size definitions. For Oracle-specific code generation, use the SQLJ translator `-optparams` option. For ISO standard code generation, use either the translator option or the Oracle customizer option, `-P-Coptparams` on the SQLJ command line.

- Use `optparamdefaults` to set default sizes for particular data types. For Oracle-specific code generation, use the SQLJ translator `-optparamdefaults=``xxxx` option. For ISO standard code generation, use either the translator option or the Oracle customizer option, `-P-Coptparamdefaults=``xxxx` on the SQLJ command line.

##### Source Code Hints for Parameter Size Definitions

Embed source code hints for parameter size definitions within your SQLJ statements in the following format (you can add white space within the comment, as desired):

    /*(size)*/

The size is in bytes. Hints are ignored if the `optparams` flag is disabled.

You can override the default parameter size, without specifying a new size (leaving size allocation to the JDBC implementation), as follows:

    /*()*/

Here is an example:

    byte[] hash;
    String name=Tyrone;
    String street=2020 Meryl Street;
    String city=Wichita;
    String state=Kansas;
    String zipcode=77777;
    #sql hash = { /* (5) */ VALUES (ADDR_HASH(:name /* (20) */, :street /* () */,
                                   :city, :state, :INOUT zipcode /* (10) */ )) };

A hint for a result expression, such as the result expression `hash` in the example, must be the first item appearing inside the brackets of the SQLJ statement, as shown. Hints for input and output host variables must immediately follow the variables, as shown.

The example sets parameter sizes as follows:

- `hash`: 5 bytes

- `name`: 20 bytes

- `street`: override default, but with no setting (leave allocation up to JDBC)

- `city`: none (use appropriate data type default, if any)

- `state`: none (use appropriate data type default, if any)

- `zipcode`: 10 bytes

**Note:**

If any parameter size is altered such that its actual size exceeds its registered size at run time, then a SQL exception will be thrown.

### 11.2 SQLJ Debugging Features

This section summarizes debugging features in the Oracle SQLJ implementation. It covers the following topics:

- SQLJ -linemap Flag for Debugging

- Overview of the AuditorInstaller Specialized Customizer

- Overview of Developing and Debugging in Oracle10g JDeveloper

#### 11.2.1 SQLJ -linemap Flag for Debugging

The `-linemap` flag instructs SQLJ to map line numbers from a SQLJ source code file to locations in the corresponding `.class` file. This will be the `.class` file created during compilation of the `.java` file generated by the SQLJ translator. As a result of this, when Java run-time errors occur, the line number reported by the Java virtual machine (JVM) is the line number in the SQLJ source code, making it much easier to debug.

If you are using the Sun Microsystems `jdb` debugger, then use the `-jdblinemap` option instead of the `-linemap` option. The options are equivalent, except that `-jdblinemap` does some special processing, necessitated by the fact that `jdb` does not support Java source files with file name extensions other than the `.java` extension.

**Note:**

If you are translating in the server, then class schema objects created during server-side translation automatically reference line numbers that map to the SQLJ source code. This is equivalent to enabling the `-linemap` option when you translate on a client.

#### 11.2.2 Overview of the AuditorInstaller Specialized Customizer

For ISO code generation, SQLJ provides a special customizer, `AuditorInstaller`. This customizer will insert sets of debugging statements, known as auditors, into profiles specified on the SQLJ command line. These profiles must already exist from previous customization. The debugging statements will execute during SQLJ run time (when someone runs your application), displaying a trace of method calls and values returned.

Use the customizer harness `debug` option, preceded by `-P-` as with any general customization option, to insert the debugging statements.

**See Also:**

"[AuditorInstaller Customizer for Debugging](appendix.md)"

#### 11.2.3 Overview of Developing and Debugging in Oracle10g JDeveloper

The Oracle SQLJ product is fully integrated into the Oracle10g JDeveloper visual programming tool.

JDeveloper also includes an integrated debugger that supports SQLJ. SQLJ statements, as with standard Java statements, can be debugged in-line as your application executes. Reported line numbers are according to the line numbers in your SQLJ source code (as opposed to in the generated Java code).

### 11.3 SQLJ Support for Oracle Performance Monitoring

FUTURE (post-10i/10.1): SQLJ DMS monitoring stored locally as hierarchy; -sqlmonitor.dms=false setting (for storing locally instead of sending to DMS);use of SQLJ DMS APIs (to access results stored locally).

FUTURE (post-10i/10.1): SQLJ -components=append; multiple translation runs for DMS.

FUTURE: Update Oracle9iAS to Oracle10iAS when appropriate.

The following sections discuss Oracle SQLJ implementation support for Oracle Dynamic Monitoring Service (DMS):

- Overview of SQLJ DMS Support

- Summary of SQLJ Command-Line Options for DMS

- SQLJ Run-Time Commands and Properties File Settings for DMS

- SQLJ DMS Sensors and Metrics

- SQLJ DMS Examples

#### 11.3.1 Overview of SQLJ DMS Support

DMS enables users to measure performance statistics for SQLJ programs. SQLJ support for DMS focuses on the overall performance per SQL statement, such as its execution time, but can also provide method-level or class-level performance information, such as with Oracle JDBC support for DMS. You can choose a client-side perspective, such as the overall performance of each `#sql` statement, a server-side perspective, such as server-side tracing of each SQL operation, or both.

Instrumenting a program, which is specified at translation time through SQLJ options, is required in order to enable DMS setup. Specifically, instrumenting is the process of inserting DMS calls into system or application code for measuring its performance.

At run time, any components that were instrumented during translation can be monitored during execution, according to instructions in a SQLJ DMS properties file. During run time, statistics are sent to DMS through DMS APIs. This requires a running DMS system in your environment. You can then access the statistics through DMS tools.

The statistics are intended to help you track and understand SQL statement performance and are reported according to the following hierarchy (from top to bottom):

1.  Application: The application, in this context, is defined to consist of the SQLJ and Java components specified in the SQLJ command line for translation. However, only the SQLJ components can be instrumented.

2.  Module: A module corresponds to a Java package.

3.  Action: An action maps to a Java class defined in a SQLJ program.

4.  Statement: A statement is a SQL statement in a SQLJ program.

The following DMS statistics are measured for client-side monitoring:

- Elapsed time for each `#sql` statement, including parsing and execution

- Get-next time, the time to execute each `next()` call

- Get-XXX time, the time to extract a database column through each `get``XXX``()` call

These statistics require the DMS library to be in your classpath at both translation time and run time, so are not supported on the server, where the DMS library is not available. Server-side SQLJ code cannot be monitored in the way that client-side code can.

The following statistics are measured for server-side SQL monitoring of your SQLJ client program:

- Parsing time

- Execution time

- Fetching time

These statistics are available from the Oracle Database 12c Release 1 (12.1) trace file, through SQL tracing functionality. This is independent of DMS, but you can enable it through the SQLJ DMS properties file `sqlmonitor.servertracing` setting.

**See Also:**

"SQLJ Run-Time Commands and Properties File Settings for DMS"

For a client-side SQLJ program, you can use both DMS statistics and server-side tracing. For example, from DMS you can get the total time required for a `#sql` statement that consists of a query, then from server-side tracing you can find out how much of that time was actually spent executing the SQL query in the server.

**Note:**

- DMS support currently requires Oracle-specific code generation, which is enabled by default.

- In Oracle Database 12c Release 1 (12.1), instrumented code requires Java Development Kit (JDK) 6.

- Only SQLJ declarations and statements are instrumented.

- The DMS library is in the file `dms.jar`, in `ORACLE_HOME``/oc4j/lib` in Oracle Database 12c Release 1 (12.1)

#### 11.3.2 Summary of SQLJ Command-Line Options for DMS

FUTURE (post-10i/10.1): -components=append; multiple translation runs.

The Oracle SQLJ implementation provides following translator front-end options to support DMS:

- `-instrument`: Enable instrumentation and designate a name for the application (the collective of the components being translated).

- `-components`: Specify the components (packages and classes) to be instrumented.

Typically you would enable instrumentation by specifying a desired application name in the `-instrument` setting, optionally specifying a package as well. Or specify a setting of `true` to use the default application, `defaultApp`. For DMS instrumentation, the term application refers to all the SQLJ and Java components specified for translation in the SQLJ command line.

If instrumentation is enabled, a SQLJ DMS properties file is created according to the `-instrument` setting, starting from the current directory, and also according to any setting of the SQLJ `-d` option. For a setting of `true`, the properties file is named `sqlmonitor.properties` in the current directory.

**Note:**

A setting of `-instrument` is equivalent to `-instrument=true`. A setting of `-instrument=false` (the default) disables instrumentation.

As a simple example, a setting of `-instrument=myapp` will result in creation of the properties file `myapp.properties`. Now consider the following example, for an application name of `stock` and a package name of `com.acme`:

    % sqlj -instrument=com.acme/stock -d /home Stock.sqlj Trading.sqlj

Because of the `-d` option, the `/home/com/acme/stock.properties` file is created.

When instrumentation is enabled through the` -instrument` option, use the `-components` option to specify the subset of translated components to be instrumented for DMS monitoring, typically most or all of them to allow flexibility in what you can monitor during run time. Specify a comma-delimited list of packages (to instrument all classes in each package) or specific classes, or use the default `all` setting to instrument all components being translated.

For example, to instrument the classes `Stock` and `Trading`:

    % sqlj ... -components=com.acme.Stock,com.acme.Trading

At run time, instrumented components are monitored according to what is specified in the SQLJ DMS properties file. Any components that are not instrumented during translation cannot be monitored during run time, regardless of what is specified in the properties file.

#### 11.3.3 SQLJ Run-Time Commands and Properties File Settings for DMS

While the SQLJ `-instrument` option specifies whether the SQLJ translator instruments files for monitoring capability, it is the SQLJ DMS properties file that actually determines what is monitored and how, at run time.

This properties file is created by SQLJ during translation, and then you can modify it as desired. Be aware that if you run SQLJ again, however, SQLJ overwrites the properties file. Any changes that you made are lost.

Settings in the SQLJ DMS properties file are as follows:

- `sqlmonitor.components`: This is a comma-delimited list of components (packages or classes) that have been instrumented. This is set automatically by the translator to reflect the setting of the SQLJ `-components` option.

- `sqlmonitor.monitorcomp`: This is a comma-delimited list of components (packages or classes) to be monitored and denotes a subset of the components in the `sqlmonitor.components` setting. The setting for `sqlmonitor.monitorcomp` is initially determined during translation to reflect the `sqlmonitor.components` setting, but you can then adjust it as desired. A setting of `all` means to monitor all components listed in the `sqlmonitor.components` setting.

- `sqlmonitor.dms`: This boolean flag, with a default value of `true`, specifies whether to deliver collected statistics to DMS. This requires a running Oracle Application Server 10g instance where you can use DMS tools. Statistics can be accessed through a Web browser or written into a file.

  **Note:**

  A setting of `sqlmonitor.dms=false` is not currently supported.

  FUTURE (post-10i/10.1): Support for sqlmonitor.dms=false. (Is DMS library still required if sqlmonitor.dms=false?)

- `sqlmonitor.sysurl`: For server-side tracing, this specifies the database URL.

- `sqlmonitor.sysuser`: For server-side tracing, this specifies the database user. This user must have `sysdba` privileges.

- `sqlmonitor.syspassword`: For server-side tracing, this specifies the password for the `sysuser`.

  **Note:**

  For `sysurl`, `sysuser`, and `syspassword`, default values are according to the `user`, `password`, and `url` values supplied to SQLJ, either through the SQLJ command line or through the SQLJ properties file.

- `sqlmonitor.servertracing`: Use this to enable server-side tracing, to collect performance statistics in the server, such as for SQL operations. Supported settings are `true` or `false` (the default).

- `sqlmonitor.dumpfile`: If delivering statistics to DMS, then you can use this option to specify a file into which the DMS tool writes the statistics. The default is `application_name``.mtr`, where `application_name` is according to the `-instrument` option setting (or is `defaultApp` by default).

#### 11.3.4 SQLJ DMS Sensors and Metrics

Sensors are used by DMS to calculate performance metrics during the execution of instrumented SQLJ programs and delivered to DMS. They are organized as a hierarchy, with each sensor having a path name. Here are typical sensor formats:

    /SQLJ/application_name/sensor_name
    /SQLJ/application_name/module/sensor_name
    /SQLJ/application_name/module/class/sensor_name
    /SQLJ/application_name/module/class/linenum/sensor_name

A sensor is an instance of the `oracle.dms.instrument.Sensor` class, which has methods for calculating and organizing performance statistics. For example, there are methods to instruct the sensor to derive additional metrics and to get the value of one of the metrics.

Be aware that before the end of an instrumented application, there must be a call to the `close()` method of the `oracle.sqlj.runtime.sqlmonitor.SQLMonitor` class, such as in the following example (which also uses the `Oracle` class `close()` method to close the connection context):

    try
    {
       Oracle.close();
       oracle.sqlj.runtime.sqlmonitor.SQLMonitor.close();
    }
    catch( Throwable e ) { ... }

Note the following terms:

- The `application_name` is the name of the application according to the SQLJ `-instrument` option, or `defaultApp` by default.

- If a sensor is associated with a package, then the item `module` is the package name. The setting `*TopLevel*` is used if the package name is empty.

- If a sensor is associated with a class, then `class` is the class name.

- If a sensor is associated with a SQL statement, then `linenum` denotes the line number of the SQL statement in the SQLJ program being instrumented. If multiple SQL statements appear in the same line, then their starting column positions are used to distinguish them. For example, a `linenum` value of 8.13 indicates that 8 is the line number and 13 is the column number.

The following sensors and associated metrics are typically of particular interest:

- Sensor name: `ContextType`

      /SQLJ/application_name/module/class/linenum/ContextType

  Metrics:

  - `value`: A string indicating the connection context type

- Sensor name: `SQLString`

      /SQLJ/application_name/module/class/linenum/SQLString

  Metrics:

  - `value`: A string consisting of the SQL statement

    This is the exact string that is passed to JDBC, including any transformations made from the original `#sql` statement.

- Sensor name: `Execute`

      /SQLJ/application_name/module/class/linenum/Execute

  Metrics:

  - `time`: The total time, in milliseconds, of all the executions of the JDBC `execute()` method for this statement

    If the statement executes five times, for example, then `time` would be the total time spent in the `execute()` method for the five executions.

  - `completed`: The number of executions completed (such as 5)

  - `minTime`: The shortest time of any single execution

  - `maxTime`: The longest time of any single execution

  - `avg`: The average execution time, which is `time` divided by `completed`

  - `active`: The number of threads executing the statement at the end of program execution, typically 0.

  - `maxActive`: The maximum number of threads that executed the statement during program execution

  To measure the execution time of a JDBC statement, the clock is started immediately before the statement is executed and stopped when a result set is obtained or the statement otherwise finishes executing, or when an exception is caught.

- Sensor name: `ServerExecute`

      /SQLJ/application_name/module/class/linenum/ServerExecute

  Metrics:

  - `value`: The total execution time in the server, in milliseconds, for all executions of this SQL statement

  - `count`: The number of executions completed

  - `minValue`: The shortest time of any single execution

  - `maxValue`: The longest time of any single execution

- Sensor name: `ServerFetch`

      /SQLJ/application_name/module/class/linenum/ServerFetch

  Metrics:

  - `value`: The total fetch time in the server, in milliseconds, for all executions of this SQL statement

  - `count`: The number of executions completed

  - `minValue`: The shortest time of any single execution

  - `maxValue`: The longest time of any single execution

- Sensor name: `ServerParse`

      /SQLJ/application_name/module/class/linenum/ServerParse

  Metrics:

  - `value`: The total time spent parsing the SQL statement in the server, in milliseconds, for all executions of this SQL statement

  - `count`: The number of executions completed

  - `minValue`: The shortest time of any single execution

  - `maxValue`: The longest time of any single execution

- Sensor name: `Next`

      /SQLJ/application_name/module/class/linenum/Next

  Metrics:

  - `time`: The total time, in milliseconds, spent in the `next()` method of the result set iterator for all executions of this SQL statement

  - `completed`: The number of executions completed (such as 5)

  - `minTime`: The shortest time of any single execution

  - `maxTime`: The longest time of any single execution

  - `avg`: The average execution time, which is `time` divided by `count`.

  - `active`: The number of threads executing the statement at the end of program execution, typically 0.

  - `maxActive`: The maximum number of threads that executed the statement during program execution

#### 11.3.5 SQLJ DMS Examples

Following is a sample command line (a single wraparound line) to instrument the SQLJ program `ExprDemo.sqlj`:

    % sqlj -dir=. -instrument=a.b.c/app -components=all
           -user=HR -url=jdbc:oracle:oci:@ ExprDemo.sqlj
    Password: password

**Note:**

Ensure that `dms.jar` is in your classpath.

This command results in generation of the following files:

- `./a/b/c/ExprDemo.java` (due to the `-dir` option setting and because package `a.b.c` is declared in `ExprDemo.sqlj`)

- `./a/b/c/app.properties` (due to the `-instrument` option setting)

##### Sample SQLJ DMS Properties File

The following is sample content for `app.properties`. This assumes you edited the file after SQLJ created it, given that some of the settings here are nondefault.

    sqlmonitor.components=all
    sqlmonitor.monitorcomp=all
    sqlmonitor.dms=true
    sqlmonitor.servertracing=true
    sqlmonitor.sysurl=jdbc:oracle:oci:@
    sqlmonitor.sysuser=HR
    sqlmonitor.syspassword=hr
    sqlmonitor.dumpfile=a/b/c/app.mtr

**Note:**

If you run the SQLJ translator again, then `app.properties` is overwritten and you will lose any changes you made.

##### Sample Statistics

The `sqlmonitor.dms=true` setting specifies that monitoring statistics are to be delivered to DMS. Given the `sqlmonitor.dumpfile` value, the DMS tool writes the statistics to the `./a/b/c/app.mtr` file when you compile and run the program.

To examine statistics for a particular code sample, here is a segment of `ExprDemo.sqlj`:

         #sql
         {
           DECLARE
             n NUMBER;
             s NUMBER;
           BEGIN
             n := 0;
             s := 0;
             WHILE n < 100 LOOP
               n := n + 1;
               s := s + :IN (indx++);
             END LOOP;
             :OUT total := s;
           END;
         };

And here is a segment of statistics from `app.mtr`, relating to the preceding code example and showing the execution time and server execution times:

           SQLString.value:      DECLARE         n NUMBER;        s NUMBER;
           BEGIN         n :=  0;         s := 0;       WHILE n < 100 LOOP
                 n := n + 1;
                 s := s +  :1 ;
           END LOOP;          :2  := s;       END; statement SQL string
                ServerExecute.maxValue:       20.0 server_execute_time
                ServerExecute.minValue:       20.0 server_execute_time
                ServerExecute.count:  0 ops
                ServerExecute.value:  20.0 server execute time
                ServerFetch.maxValue: 0.0 server_fetch_time
                ServerFetch.minValue: 0.0 server_fetch_time
                ServerFetch.count:    0 ops
                ServerFetch.value:    0.0 server fetch time
                ServerParse.maxValue: 0.0 server_parse_time
                ServerParse.minValue: 0.0 server_parse_time
                ServerParse.count:    0 ops
                ServerParse.value:    0.0 server parse time
               193.5
                ContextType.value:    class sqlj.runtime.ref.DefaultContext
           statement connection context
                Execute.maxActive:    1 threads
                Execute.active:       0 threads
                Execute.avg:  37.0 msecs
                Execute.maxTime:      37 msecs
                Execute.minTime:      37 msecs
                Execute.completed:    1 ops
                Execute.time: 37 msecs

These statistics indicate that the total execution time at the JDBC client was 37 milliseconds (in one execution), while the execution time in the server was 20 milliseconds.

##### Sample Statistics for Iterators

`ExprDemo.sqlj` also defines and executes an iterator type, `Iter`, as follows:

       #sql public static iterator Iter(String ename);

          ....

         Iter iter;
         #sql iter = { select first_name from employees};
         while (iter.next())
         {
          System.out.println(iter.ename());
         }

For iterators, DMS collects the execution time for the `next()` operation. Here is a sample DMS result for the iterator type `Iter`:

             Iter
              Next.time:    5 msecs

This shows that the total time spent on the `next()` operation while iterating through the `Iter` instance was 5 milliseconds.

##### Sample Statistics for Connection Contexts

The `#sql` statements in `ExprDemo.sqlj` use the default connection context. For the `DefaultContext` instance used throughout the program, DMS returns the following statistics:

             class_sqlj.runtime.ref.DefaultContext
             StmtCacheSize.value:  5 statement cache size
             StmtsExecuted.count:  7 ops
             StmtsCacheExecuted.count:     7 ops

This shows that the context has a statement cache size of five statements. Altogether, seven SQL statements are executed.
