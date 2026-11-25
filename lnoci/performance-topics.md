This chapter describes topics about OCI performance features.

You can use OCI to access Oracle TimesTen In-Memory Database and Oracle TimesTen Application-Tier Database Cache.

This chapter includes the following topics:

- Statement Caching in OCI

- Implicit Fetching of ROWIDs

- OCI Support for Implicit Results

- Client Result Cache

- Client Statement Cache Auto-Tuning

### 15.1 Statement Caching in OCI

Statement caching refers to the feature that provides and manages a cache of statements for each session.

In the server, it means that cursors are ready to be used without the need to parse the statement again. You can use statement caching with connection pooling and with session pooling, and improve performance and scalability. You can use it without session pooling as well. OCI calls that implement statement caching are:

- `OCIStmtPrepare2()`

- `OCIStmtRelease()`

This section includes the following topics:

- Statement Caching Without Session Pooling in OCI

- Statement Caching with Session Pooling in OCI

- Rules for Statement Caching in OCI

- Bind and Define Optimization in Statement Caching

- OCI Statement Caching Code Example

**See Also:**

- [OCIStmtPrepare2()](statement-functions.md)

- [OCIStmtRelease()](statement-functions.md)

#### 15.1.1 Statement Caching Without Session Pooling in OCI

To perform statement caching without session pooling, users perform the usual OCI steps to log on.

The call to obtain a session has a mode that specifies whether statement caching is enabled for the session. Initially the statement cache is empty. Developers try to find a statement in the cache using the statement text. If the statement exists, the API returns a previously prepared statement handle; otherwise, it returns a newly prepared statement handle.

The application developer can perform binds and defines and then simply execute and fetch the statement before returning the statement to the cache. If the statement handle is not found in the cache, the developer must set different attributes on the handle in addition to the other steps.

`OCIStmtPrepare2()` takes a mode that determines if the developer wants a prepared statement handle or a null statement handle if the statement is not found in the cache.

The pseudocode looks like this:

    OCISessionBegin( userhp, ... OCI_STMT_CACHE)  ;
    OCIAttrset(svchp, userhp, ...);  /* Set the user handle in the service context */
    OCIStmtPrepare2(svchp, &stmthp, stmttext, key, ...);
    OCIBindByPos(stmthp, ...);
    OCIDefineByPos(stmthp, ...);
    OCIStmtExecute(svchp, stmthp, ...);
    OCIStmtFetch2(svchp, ...);
    OCIStmtRelease(stmthp, ...);
    ...

**See Also:**

[OCIStmtPrepare2()](statement-functions.md)

#### 15.1.2 Statement Caching with Session Pooling in OCI

For statement caching with session pooling, the concepts remain the same, except that the statement cache is enabled at the session pool layer rather than at the session layer.

The attribute `OCI_ATTR_SPOOL_STMTCACHESIZE` sets the default statement cache size for each of the sessions in the session pool. It is set on the `OCI_HTYPE_SPOOL` handle. The statement cache size for a particular session in the pool can be overridden at any time by using `OCI_ATTR_STMTCACHESIZE` on that session. The value of `OCI_ATTR_SPOOL_STMTCACHESIZE` can be changed at any time. You can use this attribute to enable or disable statement caching at the pool level, after creation, just as attribute `OCI_ATTR_STMTCACHESIZE` (on the service context) is used to enable or disable statement caching at the session level. This change is reflected on individual sessions in the pool, when they are provided to a user. Tagged sessions are an exception to this behavior. This is explained later in this section.

**Note:**

You can change the attributes after acquiring a session. However, once an attribute is changed, it will remain set on the underlying physical session. This value will not be reset back implicitly while releasing the session back to the session pool. Hence, it is the developer's responsibility to maintain the state of the sessions before releasing the session using `OCIStmtRelease()`.

Enabling or disabling of statement caching is allowed on individual pooled sessions as it is on nonpooled sessions.

A user can enable statement caching on a session retrieved from a non-statement cached pool in an `OCISessionGet()` or `OCILogon2()` call by specifying `OCI_SESSGET_STMTCACHE` or `OCI_LOGON2_STMTCACHE`, respectively, in the mode argument.

When a user asks for a session from a session pool, the statement cache size for that session defaults to that of the pool. This may also mean enabling or disabling statement caching in that session. For example, if a pooled session (Session A) has statement caching enabled, and statement caching is turned off in the pool, and a user asks for a session, and Session A is returned, then statement caching is turned off in Session A. As another example, if Session A in a pool does not have statement caching enabled, and statement caching at the pool level is turned on, then before returning Session A to a user, statement caching on Session A with size equal to that of the pool is turned on.

This does not hold true if a tagged session is asked for and retrieved. In this case, the size of the statement cache is not changed. Consequently, it is not turned on or off. Moreover, if the user specifies mode `OCI_SESSGET_STMTCACHE` in the `OCISessionGet()` call, this is ignored if the session is tagged. In our earlier example, if Session A was tagged, then it is returned as is to the user.

**See Also:**

- [OCISessionGet()](connect-authorize-and-initialize-functions.md)

- [OCILogon2()](connect-authorize-and-initialize-functions.md)

#### 15.1.3 Rules for Statement Caching in OCI

If you are using statement caching, follow these rules.

Here are some rules to follow for statement caching in OCI:

- Use the function `OCIStmtPrepare2()` instead of `OCIStmtPrepare()`. If you are using `OCIStmtPrepare()`, you are strongly urged not to use a statement handle across different service contexts. Doing so raises an error if the statement has been obtained by `OCIStmtPrepare2()`. Migration of a statement handle to a new service context actually closes the cursor associated with the old session and therefore no sharing is achieved. Client-side sharing is also not obtained, because OCI frees all buffers associated with the old session when the statement handle is migrated.

- You are required to keep one service context per session. Any statement handle obtained using `OCIStmtPrepare2()` with a certain service context should be subsequently used only in conjunction with the same service context, and never with a different service context.

- A call to `OCIStmtPrepare2()`, even if the session does not have a statement cache, also allocates the statement handle. Therefore, applications using only `OCIStmtPrepare2()` must not call `OCIHandleAlloc()` for the statement handle.

- A call to `OCIStmtPrepare2()` must be followed by a call to `OCIStmtRelease()` after the user is done with the statement handle. If statement caching is used, this releases the statement to the cache. If statement caching is not used, the statement is deallocated. Do not call `OCIHandleFree()` to free the memory.

- If the call to `OCIStmtPrepare2()` is made with the `OCI_PREP2_CACHE_SEARCHONLY` mode and a `NULL` statement was returned (statement was not found), the subsequent call to `OCIStmtRelease()` is not required and must not be performed.

- Do not call `OCIStmtRelease()` for a statement that was prepared using `OCIStmtPrepare()`.

- The statement cache has a maximum size (number of statements) that can be modified by an attribute on the service context, `OCI_ATTR_STMTCACHESIZE`. The default value is 20. This attribute can also be used to enable or disable statement caching for the session, pooled or nonpooled. If `OCISessionBegin()` is called without the mode set as `OCI_STMT_CACHE`, then `OCI_ATTR_STMTCACHESIZE` can be set on the service context to a nonzero attribute to turn on statement caching. If statement caching is not turned on at the session pool level, `OCISessionGet()` returns a non-statement cache-enabled session. You can use `OCI_ATTR_STMTCACHESIZE` to turn the caching on. Similarly, you can use the same attribute to turn off statement caching by setting the cache size to zero.

- You can tag a statement at the release time so that the next time you can request a statement of the same tag. The tag is used to search the cache. An untagged statement (tag is `NULL`) is a special case of a tagged statement. Two statements are considered different if they differ in their tags, or if one is untagged and the other is not.

**See Also:**

- [OCIStmtPrepare2()](statement-functions.md)

- [OCIHandleAlloc()](handle-and-descriptor-functions.md)

- [OCIStmtRelease()](statement-functions.md)

- [OCIHandleFree()](handle-and-descriptor-functions.md)

- [OCISessionBegin()](connect-authorize-and-initialize-functions.md)

- [OCISessionGet()](connect-authorize-and-initialize-functions.md)

- [Statement Functions](statement-functions.md)

- [Service Context Handle Attributes](handle-and-descriptor-attributes.md)

- [Session Pool Handle Attributes](handle-and-descriptor-attributes.md)

#### 15.1.4 Bind and Define Optimization in Statement Caching

To avoid repeated bind and define operations on statements in the cache by the application, the application can register an opaque context with a statement taken from the statement cache and register a callback function with the service context.

The application data such as bind and define buffers can be enclosed in the opaque context. This context is registered with the statement the first time it is taken from the cache. When a statement is taken from the cache the second time and onwards, the application can reuse the bind and define buffers, that it had registered with that statement. It is still the application's responsibility to manage the bind and defines. It can reuse both the bind and define data and the buffers, or it can change only the data and reuse the buffers, or it can free and reallocate the buffers if the current size is not enough. In the last case, it must rebind and redefine. To clean up the memory allocated by the application toward these bind and define buffers, the callback function is called during aging out of the statement or purging of the whole cache as part of session closure. The callback is called for every statement being purged. The application frees the memory and does any other cleanup required, inside the callback function. Example 15-1 shows the pseudocode.

Example 15-1 Optimizing Bind and Define Operations on Statements in the Cache

    Get the statement using OCIStmtPrepare2(...)

    Get the opaque context from the statement if it exists

    If opaque context does not exist

    {

      Allocate fetch buffers, do the OCIBindByPos, OCIDefineByPos, and so forth

      Enclose the buffer addresses inside a context and set the context and
      callback function on the statement

    }
    Execute/Fetch using the statement, and process the data in the fetch buffers.

    OCIStmtRelease() that statement

    Next OCIStmtPrepare2()

    OCIAttrGet() opaque application context from statement handle

    Execute/Fetch using the statement and process the data in the fetch buffers.

    OCIStmtRelease()

    . . .

    void callback_fn (context, statement, mode)

    {

       /* mode= OCI_CBK_STMTCACHE_STMTPURGE means this was called when statement was
          aging out of the statement cache or if the session is ended */

      <free the buffers in the context.>

    }

**See Also:**

- [OCI_ATTR_STMTCACHE_CBKCTX](handle-and-descriptor-attributes.md)

- [OCI_ATTR_STMTCACHE_CBK](handle-and-descriptor-attributes.md)

#### 15.1.5 OCI Statement Caching Code Example

Indicates where to find a working example of statement caching.

See `cdemostc.c` in directory `demo` for a working example of statement caching.

### 15.2 Implicit Fetching of ROWIDs

This section describes the following topics:

- About Implicit Fetching of ROWIDs

- Example of Implicit Fetching of ROWIDs

#### 15.2.1 About Implicit Fetching of ROWIDs

`ROWID` is a globally unique identifier for a row in a database. It is created at the time the row is inserted into the table, and destroyed when it is removed.

`ROWID` values have several important uses. They are unique identifiers for rows in a table. They are the fastest way to access a single row and can show how the rows in the table are stored.

Implicit fetching of `ROWID`s in `SELECT` `...` `FOR` `UPDATE` statements means that the `ROWID` is retrieved at the client side, even if it is not one of the columns named in the select statement. The `position` parameter of `OCIDefineByPos()` is set to zero (0). These host variables can be specified for retrieving the `ROWID` pseudocolumn values:

- `SQLT_CHR` (`VARCHAR2`)

- `SQLT_VCS` (`VARCHAR`)

- `SQLT_STR` (`NULL`-terminated string)

- `SQLT_LVC` (`LONG` `VARCHAR`)

- `SQLT_AFC` (`CHAR`)

- `SQLT_AVC` (`CHARZ`)

- `SQLT_VST` (OCI String)

- `SQLT_RDD` (`ROWID` descriptor)

The `SELECT` `...` `FOR` `UPDATE` statement identifies the rows that are to be updated and then locks each row in the result set. This is useful when you want to base an update on the existing values in a row. In that case, you must ensure that another user does not change the row.

When you specify character buffers for storing the values of the `ROWID`s (for example, if getting it in `SQLT_STR` format), allocate enough memory for storing `ROWID`s. Remember the differences between the `ROWID` data type and the `UROWID` data type. The `ROWID` data type can only store physical `ROWID`s, but `UROWID` can store logical `ROWID`s (identifiers for the rows of index-organized tables) as well. The maximum internal length for the `ROWID` type is 10 bytes; it is 3950 bytes for the `UROWID` data type.

Dynamic define is equivalent to calling `OCIDefineByPos()` or `OCIDefineByPos2()` with `mode` set as `OCI_DYNAMIC_FETCH`. Dynamic defines enable you to set up additional attributes for a particular define handle. It specifies a callback function that is invoked at runtime to get a pointer to the buffer into which the fetched data or a piece of it is to be retrieved.

The attribute `OCI_ATTR_FETCH_ROWID` must be set on the statement handle before you can use implicit fetching of `ROWID`s, in this way:

    OCIAttrSet(stmthp, OCI_HTYPE_STMT, 0, 0 , OCI_ATTR_FETCH_ROWID, errhp);

Dynamic define is not compatible with implicit fetching of `ROWID`s. In normal scenarios this mode allows the application to provide buffers for a column, for each row; that is, a callback is invoked every time a column value is fetched.

This feature, using `OCIDefineByPos()` or `OCIDefineByPos2()` for position 0, is for fetching an array of data simultaneously into the user buffers and getting their respective `ROWID`s at the same time. It allows for fetching of `ROWID`s with `SELECT....FOR UPDATE` statements even when `ROWID` is not one of the columns in the `SELECT` query. When fetching the data one by one into the user buffers, you can use the existing attribute `OCI_ATTR_ROWID`.

If you use this feature to fetch the `ROWID`s, the attribute `OCI_ATTR_ROWID` on the statement handle cannot be used simultaneously to get the `ROWID`s. You can only use one of them at a time for a particular statement handle.

**See Also:**

- [OCI_ATTR_FETCH_ROWID](handle-and-descriptor-attributes.md)

- [OCIDefineByPos()](bind-define-describe-functions.md) or [OCIDefineByPos2()](bind-define-describe-functions.md)

#### 15.2.2 Example of Implicit Fetching of ROWIDs

Shows an example of implicit fetching of ROWIDs.

Use the fragment of a C program in Example 15-2 to build upon.

Example 15-2 Implicit Fetching of ROWIDs

    #include <oci.h>

    int main()
    {
     ...
     text *mySql = (text *) "SELECT emp_name FROM emp FOR UPDATE";
     text rowid[100][15] = {0};
     text empName[100][15] = {0};
     ...

     /* Set up the environment, error handle, etc. */
     ...

     /* Prepare the statement -  select ... for update. */


      if (OCIStmtPrepare (select_p, errhp,
                          mySql, strlen(mySql), OCI_NTV_SYNTAX, OCI_DEFAULT))
      {
        printf ("Prepare failed \n");
        return (OCI_ERROR);
      }

     /* Set attribute for implicit fetching of ROWIDs on the statement handle. */
     if (OCIAttrSet(select_p, OCI_HTYPE_STMT, 0, 0, OCI_ATTR_FETCH_ROWID, errhp))
     {
       printf ("Unable to set the attribute - OCI_ATTR_FETCH_ROWID \n");
       return OCI_ERROR;
     }
      /*
       * Define the positions: 0 for getting ROWIDs and other positions
       * to fetch other columns.
       * Also, get the define conversion done implicitly by fetching
       * the ROWIDs in the string format.
       */

      if (OCIDefineByPos ( select_p,
                           &defnp0,
                           errhp,
                           0,
                           rowid[0],
                           15,
                           SQLT_STR,
                           (void *) ind,
                           (void *) 0,
                           (void *) 0,
                           OCI_DEFAULT) ||
           OCIDefineByPos(select_p,
                           &defnp1,
                           errhp,
                           1,
                           empName[0],
                           15,
                           SQLT_STR,
                           (void *) 0,
                           (void *) 0,
                           (void *) 0,
                           OCI_DEFAULT)
                           )
      {
        printf ("Failed to define\n");
        return (OCI_ERROR);
      }


      /* Execute the statement. */

     if (errr = OCIStmtExecute(svchp,
                                select_p,
                                errhp,
                                (ub4) 5,
                                (ub4) 0,
                                (OCISnapshot *) NULL,
                                (OCISnapshot *) NULL,
                                (ub4) OCI_DEFAULT))
      {
        if (errr != OCI_NO_DATA)
           return errr;
      }

      printf ("Column 0  \t Column 1\n");
      printf ("_________ \t ________\n");

      for (i =0 ;i<5 i++)
       {
         printf("%s \t %s \n", rowid[i], empName[i]);
       }

     return OCI_SUCCESS;
    }

### 15.3 OCI Support for Implicit Results

Beginning with Oracle Database 12c Release 1 (12.1) , PL/SQL can return results (cursors) implicitly from stored procedures and anonymous PL/SQL blocks. `OCIStmtGetNextResult()` is provided to retrieve and process the implicit results.

PL/SQL provides a subprogram `RETURN_RESULT` in the `DBMS_SQL` package to return the result of an executed statement as shown in Example 15-3. In the current release, only `SELECT` query result-sets can be implicitly returned by a PL/SQL procedure block. `OCIStmtGetNextResult()` returns an OCI statement handle on which the usual OCI define and fetch calls are done to retrieve the rows.

Example 15-4 shows a PL/SQL stored procedure to implicitly return result-sets (cursors) to the client.

Example 15-5 shows the same approach using an anonymous PL/SQL block sent by the client. This example shows how applications can use the implicit results feature to implement batching of SQL statements from an OCI application. An OCI application can dynamically form a PL/SQL anonymous block to execute multiple and variable `SELECT` statements and return the corresponding cursors using `DBMS_SQL.RETURN_RESULT`.

Example 15-6 lists an OCI program showing how to use the `OCIStmtGetNextResult()` call to retrieve and process the implicit results returned by a PL/SQL stored procedure (see Example 15-4) or an anonymous PL/SQL block (see Example 15-5).

`OCIStmtGetNextResult()` can be called iteratively by the application to retrieve each implicit result from an executed PL/SQL statement. Applications retrieve each result-set sequentially but can fetch rows from any result-set independently. The top-level OCI statement handle tracks all the associated result-set statement handles. Freeing or releasing the top-level OCI statement handle automatically closes and frees all the implicit result-sets.

The attribute `OCI_ATTR_IMPLICIT_RESULT_COUNT` is provided on the OCI statement handle to determine the number of implicit results available.

The `rtype` parameter of `OCIStmtGetNextResult()` returns the type of the result. In this release only the type: `OCI_RESULT_TYPE_SELECT` is supported. The describe metadata of the returned result set can be accessed similar to any `SELECT` ResultSet.

**Note:**

The following OCI code can be used in external procedures too, to fetch from the implicit results. In that case, `OCI_PREP2_IMPL_RESULTS_CLIENT` should be passed as the mode to the `OCIStmtPrepare2()` call.

Example 15-3 DBMS_SQL RETURN_RESULT Subprogram

    procedure return_result(rc        in out sys_refcursor,
                            to_client in boolean default true);

    procedure return_result(rc        in out integer,
                            to_client in boolean default true);

Example 15-4 A PL/SQL Stored Procedure to Implicitly Return Result-Sets (Cursors) to the Client

    CREATE PROCEDURE foo AS
      c1 sys_refcursor;
      c2 sys_refcursor;
    begin
      open c1 for select * from emp;
      dbms_sql.return_result(c1); --return to client
      -- open 1 more cursor
      open c2 for select * from dept;
      dbms_sql.return_result (c2); --return to client
    end;

Example 15-5 An Anonymous PL/SQL Block to Implicitly Return Result-Sets (Cursors) to the Client

    declare
      c1 sys_refcursor;
      c2 sys_refcursor;
    begin
      open c1 for select * from emp;
      dbms_sql.return_result (c1); --return to client
      -- open 1 more cursor
      open c2 for select * from dept;
      dbms_sql.return_result (c2); --return to client
    end;

Example 15-6 Using OCIStmtGetNextResult() to Retrieve and Process the Implicit Results Returned by Either a PL/SQL Stored Procedure or Anonymous Block

      OCIStmt *stmthp;
      ub4      rsetcnt;
      void    *result;
      ub4      rtype;
      char    *sql = "begin foo; end;";

      /* Prepare and execute the PL/SQL procedure. */
      OCIStmtPrepare2(svchp, &stmthp, errhp, (oratext *)sql, strlen(sql),
                     NULL, 0, OCI_NTV_SYNTAX, OCI_DEFAULT);
      OCIStmtExecute(svchp, stmthp, errhp, 1, 0,
                     (const OCISnapshot *)0,
                     (OCISnapshot *)0, OCI_DEFAULT);

      /* Now check if any implicit results are available. */
      OCIAttrGet((void *)stmthp, OCI_HTYPE_STMT, &rsetcnt, 0,
                 OCI_ATTR_IMPLICIT_RESULT_COUNT, errhp);

      /* Loop and retrieve the implicit result-sets.
       * ResultSets are returned in the same order as in the PL/SQL
       * procedure/block.
       */
      while (OCIStmtGetNextResult(stmthp, errhp, &result, &rtype,
                                  OCI_DEFAULT) == OCI_SUCCESS)
      {
        /* Check the type of implicit ResultSet, currently
         * only supported type is OCI_RESULT_TYPE_SELECT
         */
        if (rtype == OCI_RESULT_TYPE_SELECT)
        {
          OCIStmt *rsethp = (OCIStmt *)result;

          /* Perform normal OCI actions to define and fetch rows. */
        }
        else
          printf("unknown result type %d\n", rtype);

        /* The result set handle should not be freed by the user. */
      }

      OCIStmtRelease(stmthp, errhp, NULL, 0, OCI_DEFAULT); /* Releases the statement handle. */

**See Also:**

- [OCIStmtGetNextResult()](statement-functions.md)

- [Statement Handle Attributes](handle-and-descriptor-attributes.md) for more information about the attribute `OCI_ATTR_IMPLICIT_RESULT_COUNT`.

- [OCIStmtPrepare2()](statement-functions.md)

### 15.4 Client Result Cache

OCI applications can use client memory to take advantage of the OCI result cache to improve response times of repeated queries.

**See Also:**

[Oracle Database Development Guide](../adfns/performance-and-scalability.md) for complete information about using the OCI client result cache

### 15.5 Client Statement Cache Auto-Tuning

Describes topics about client statement cache auto-tuning.

This section describes the following topics:

- About Auto-Tuning Client Statement Cache

- Benefit of Auto-Tuning Client Statement Cache

- Client Statement Cache Auto-Tuning Parameters

- Usage Examples of Client Statement Cache Auto Tuning

- Enabling and Disabling OCI Client Auto-Tuning

- Usage Guidelines for Auto-Tuning Client Statement Cache

#### 15.5.1 About Auto-Tuning Client Statement Cache

Auto-tuning optimizes OCI client session features of mid-tier applications to gain higher performance without the need to reprogram your OCI application.

Auto tuning operations like increasing or decreasing cache memory happens implicitly during `OCIStmtPrepare2()` and `OCIStmtRelease()` calls on a periodic basis. Calling `OCIAttrGet()` with `OCI_ATTR_STMTCACHESIZE` on the service handle gives the current cache size being used, if you need to check.

It is possible for the coded OCI client statement cache size setting to be sub optimal. This can happen, for example, with changing the workload causing a different working set of SQL statements. If the size is too low, it will cause excess network activity and more parses at the server. If the size is too high, there will be excess memory used. It can be difficult for the client side application to always keep this cache size optimal.

Auto-tuning automatically reconfigures the OCI statement cache size on a periodic basis. Auto-tuning is achieved by providing a deployment time setting that provides an option to reconfigure OCI statement caching to resolve this potential performance issue.

These settings are provided as connect string based deployment settings in the client `oraaccess.xml` file that overrides manual settings to the user configuration of OCI features.

**See Also:**

- [OCIStmtPrepare2()](statement-functions.md)

- [OCIStmtRelease()](statement-functions.md)

#### 15.5.2 Benefit of Auto-Tuning Client Statement Cache

The more specific benefit of auto-tuning client statement cache is to transparently detect, monitor, and adjust the statement cache size to improve performance or decrease memory usage.

Developers and DBAs can expect to see the following benefits of using auto-tuning for their OCI client applications:

- Reduced time and effort in diagnosing and fixing performance problems with each part of their system, such as statement caching

- Minimized manual modifications needed to configurations of this OCI feature to improve performance. Usually, this manual correction requires applications to restart more than once with different configuration parameters, thus further reducing the high availability of the client

- One solution that can be used by all OCI applications to improve performance right out-of-the-box without having to make any application changes

- OCI applications are freed from making custom implementations (that can be error prone) to auto-tune their OCI application to optimize performance and memory usage. Here auto-tuning is limited to internal automatic tuning of OCI Client-side statement cache size only.

#### 15.5.3 Client Statement Cache Auto-Tuning Parameters

The following connection specific parameters in `oraccess.xml` can be set per configuration alias or across all connect strings using default connection specific parameters.

Values specified in the client `oraaccess.xml` configuration file override programmatic settings.

This section includes the following topics:

- \<statement_cache\>

- \<auto_tune\>

- Comparison of the Connection Specific Auto-Tuning Parameters

**See Also:**

[About Specifying Defaults for Connection Parameters](build-and-configure-oci-applications.md) for more information about setting per configuration alias or across all connect strings using default connection specific parameters

##### 15.5.3.1 \<statement_cache\>

This parameter is optional and sets the limit for the statement caching tunable component.

    <statement_cache>
      <size>100</size>
    </statement_cache>

The limit is the maximum number of statements that can be cached per session. If auto-tuning is enabled or not, this setting in `oraaccess.xml` overrides the programmatic setting of OCI statement cache size.

If auto-tuning is enabled, this setting will be the upper bound on statement cache size while its being dynamically tuned.

If the session is not using statement caching APIs as in `OCIStmtPrepare2()` and `OCIStmtRelease()`, this setting is ignored.

Default values are as follows:

- If auto-tuning is enabled, statement caching is dynamically tuned and the initial statement cache size is set to 100 statements.

- If auto-tuning is disabled, this setting serves as the deployment setting of statement caching size, overriding any programmatic setting.

**See Also:**

- [OCIStmtPrepare2()](statement-functions.md)

- [OCIStmtRelease()](statement-functions.md)

- Enabling and Disabling OCI Client Auto-Tuning

##### 15.5.3.2 \<auto_tune\>

This section specifies auto tune parameters.

If the OCI session is not using statement caching APIs as in `OCIStmtPrepare2()` or `OCIStmtRelease()`, auto tuning parameters are ignored for that session. It is possible in a process that some sessions or connections can have auto-tuning enabled and some disabled.

This section includes the following topics:

- \<enable\>true\</enable\>

- \<ram_threshold\>

- \<memory_target\>

**See Also:**

- [OCIStmtPrepare2()](statement-functions.md)

- [OCIStmtRelease()](statement-functions.md)

###### 15.5.3.2.1 \<enable\>true\</enable\>

This parameter turns auto tuning on or off.

The default is auto tuning off `(FALSE)` or disabled.

    <auto_tune>
      <enable>true</enable>
    </auto_tune>

Auto-tuning is enabled along with internal default settings.

**See Also:**

\<statement_cache\> for more information about auto-tuning is enabled along with internal default settings

###### 15.5.3.2.2 \<ram_threshold\>

This parameter is optional.

    <auto_tune>
       <enable>true</enable>
       <ram_threshold>0.1</ram_threshold>
    </auto_tune>

The default value is 0.01%. It is specified as percentage of installed RAM. This specifies the total memory available across the auto tuning sessions in a process sharing this setting. This setting can be specified per process or per connect string alias.

Note that if specified per connect string alias, the total auto tuning memory used by a client process can add up.

Therefore, it may be preferable to specify auto tuning limits in the `<default_parameters>` section of `oraaccess.xml` file. This way you have a common pool of memory for all sessions in a client process.

A smaller limit uses less RAM for auto tuning, but minimizes the chance other programs running on the system do not degrade in performance.

This parameter must be specified within the `<auto_tune></auto_tune>` deployment setting.

**See Also:**

[About oraaccess.xml](build-and-configure-oci-applications.md)

###### 15.5.3.2.3 \<memory_target\>

This parameter is optional.

    <auto_tune>
      <enable>true</enable>
      <memory_target>40M</memory_target>
    </auto_tune>

Specified in bytes. Default is undefined. It specifies the total memory available across the auto tuning sessions in a process sharing this setting. This setting can be specified per process or per connect string alias.

Note that if specified per connect string alias, the total auto tuning memory used by a client process can add up.

Therefore, it may be preferable to specify auto tuning limits in the `<default_parameters>` section of `oraaccess.xml` file. This way you have a common pool of memory for all sessions in a client process.

This parameter must be specified within the `<auto_tune></auto_tune>` deployment setting.

Using this parameter ensures the use of a consistent memory limit for auto tuning irrespective of installed RAM on that system.

If not specified, the auto tuning memory limit is based on the `<ram_threshold>` parameter setting.

If both `<ram_threshold>` and `<memory_target>` parameters are specified, the effective limit is the minimum of the two parameters.

**See Also:**

[About oraaccess.xml](build-and-configure-oci-applications.md)

##### 15.5.3.3 Comparison of the Connection Specific Auto-Tuning Parameters

Lists and describes a comparison of all auto-tuning parameters.

Table 15-1 shows a comparison of the connection specific auto-tuning parameters.

Table 15-1 Comparison of Some Connection Specific Auto-Tuning Parameters

| Parameter                                | Setting and Semantics                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | For Auto-Tuning or Deployment Setting                                                                                                                                                                                                                |
|:-----------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `<statement_cache>`                      | Optional setting.<br>Per session cache size.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | If auto-tuning is enabled (see "Enabling and Disabling OCI Client Auto-Tuning"), this is the upper bound of each sessions statement cache size while its tuned by auto tuning.<br>Or else it refers to the deployment setting for statement caching. |
| `<auto_tune>`                            | Optional setting.<br>Specify this parameter to use auto-tuning. Applies to all connections using this connect string or all connections if null connect string is specified.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | Only auto-tuning related                                                                                                                                                                                                                             |
| `<ram_threshold>``0.1</ram_threshold>`   | Optional setting.<br>Converts the percentage setting to a memory value based on installed RAM on that client or mid-tier system.<br>This is the upper limit of memory used for auto tuning within a client process.<br>For installed RAM of 8GB, not specifying this parameter gives 800 KB of memory among the sessions.<br>Note each connection can potentially have its own setting of auto tuning parameters so these values can add up for the whole process based on configuration settings. It is preferable to use this parameter hence in the `<default_parameters>` section of the `oraaccess.xml` file. See "[File (oraaccess.xml) Properties](build-and-configure-oci-applications.md)" for a description of the syntax. | Only auto-tuning related. If auto-tuning is disabled, this parameter setting is ignored. This parameter must be specified within the `<auto_tune></auto_tune>` deployment setting.                                                                   |
| `<memory_target>1048576</memory_target>` | Optional setting.<br>This is the upper limit of memory used for auto tuning within a client process.<br>Note each connection can potentially have its own setting of auto tuning parameters so these values can add up for the whole process based on configuration settings. It is preferable to use this parameter hence in the `<default_parameters>` section of the `oraaccess.xml` file.<br>See "[File (oraaccess.xml) Properties](build-and-configure-oci-applications.md)" for a description of the syntax.<br>Value is in bytes. 1,048,576 bytes is 1 MB.                                                                                                                                                                    | Only auto-tuning related. If auto-tuning is disabled, this parameter setting is ignored. This parameter must be specified within the `<auto_tune></auto_tune>` deployment setting.                                                                   |

#### 15.5.4 Usage Examples of Client Statement Cache Auto Tuning

The following are some usage examples showing use and interaction of client statement cache auto-tuning parameters that are also connection specific parameters.

    <statement_cache>
      <size>100</size>
    </statement_cache>

The programmatic statement cache size will be replaced by this setting. Auto-tuning is disabled and cache is managed per LRU. In this case, the application developer believes the OCI application statement prefetching programmatic settings do not need to be overridden.

    <auto_tune>
      <enable>true</enable>
    </auto_tune>

Auto-tuning is enabled along with internal default settings.

    <statement_cache>
      <size>100</size>
    </statement_cache>
    <auto_tune>
      <enable>true</enable>
      <memory_target>40M</memory_target>
    </auto_tune>

This statement caching deployment setting of 100 will replace the programmatic statement cache size and because auto-tuning is enabled, statement caching will be auto-tuned. The memory target setting is in effect because auto-tuning is enabled.

Auto tuning will always try to limit total statement cache memory used around a memory target. If a memory target is not specified, it is based on the percentage of total installed RAM.

In this case, the memory limit is the specified memory target.

**See Also:**

\<statement_cache\> for more information about auto-tuning is enabled along with internal default settings

#### 15.5.5 Enabling and Disabling OCI Client Auto-Tuning

Describes conditions that enable and disable OCI client auto-tuning.

The following conditions enable and disable OCI client auto-tuning:

- Auto-tuning is enabled when the client `oraaccess.xml` `<auto_tune>` section is added with enable specified as true, `<enable>true</enable>`

- Auto-tuning is disabled by default or when enable is set to false, \<enable\>false\</enable\> in `oraaccess.xml` under the `<auto_tune>` section.

#### 15.5.6 Usage Guidelines for Auto-Tuning Client Statement Cache

Describes guidelines to use when setting the auto-tuning parameters.

The following are some guidelines to use when setting the auto-tuning parameters:

- When either client response, memory allocation, or client CPU is high and you want to gain performance without rebuilding the OCI application, you can use `<auto_tune>` settings or deployment `<statement_cache>` settings. Auto tuning may also decrease the network bytes transferred between client and server.

- When AWR or ADDM reports lots of parses and you cannot or you may prefer not to programmatically modify the statement cache size, you can specify auto-tuning for statement cache or use the deployment statement cache setting `<statement_cache>`.
