Lists and describes connect, authorize, and initialize functions.

[Table 25-1](introduction-to-relational-functions.md) describes the OCI connect, authorize, and initialize functions that are described in this section.

Table 25-2 Connect, Authorize, and Initialize Functions  

| Function                   | Purpose                                                                                                                                                                     |
|:---------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| OCIAppCtxClearAll()        | Clear all attribute-value information in a namespace of an application context                                                                                              |
| OCIAppCtxSet()             | Set an attribute and its associated value in a namespace of an application context                                                                                          |
| OCIConnectionPoolCreate()  | Initialize the connection pool                                                                                                                                              |
| OCIConnectionPoolDestroy() | Destroy the connection pool                                                                                                                                                 |
| OCIDBShutdown()            | Shut down Oracle Database                                                                                                                                                   |
| OCIDBStartup()             | Start an Oracle Database instance                                                                                                                                           |
| OCIEnvCreate()             | Create and initialize an OCI environment handle                                                                                                                             |
| OCIEnvNlsCreate()          | Create and initialize an environment handle for OCI functions to work under. Enable you to set character set ID and national character set ID at environment creation time. |
| OCILogoff()                | Release a session that was retrieved using `OCILogon2()` or `OCILogon()`                                                                                                    |
| OCILogon()                 | Simplify single-session logon                                                                                                                                               |
| OCILogon2()                | Create a logon session in various modes                                                                                                                                     |
| OCIRequestDisableReplay()  | Disables application continuity replay for a session for the duration of the current database request.                                                                      |
| OCIServerAttach()          | Attach to a server; initialize server context handle                                                                                                                        |
| OCIServerDetach()          | Detach from a server; uninitialize server context handle                                                                                                                    |
| OCISessionBegin()          | Authenticate a user                                                                                                                                                         |
| OCISessionEnd()            | Terminate a user session                                                                                                                                                    |
| OCISessionGet()            | Get a session from a session pool                                                                                                                                           |
| OCISessionPoolCreate()     | Initialize a session pool                                                                                                                                                   |
| OCISessionPoolDestroy()    | Destroy a session pool                                                                                                                                                      |
| OCISessionRelease()        | Release a session                                                                                                                                                           |
| OCITerminate()             | Detach from a shared memory subsystem                                                                                                                                       |

### 25.2.1 OCIAppCtxClearAll()

Clears all attribute-value information in a namespace of an application context.

#### Purpose

Clears all attribute-value information in a namespace of an application context.

#### Syntax

    sword OCIAppCtxClearAll ( void      *sesshndl,
                              void      *nsptr,
                              ub4        nsptrlen,
                              OCIError  *errhp,
                              ub4        mode ;

#### Parameters

sesshndl (IN/OUT)
Pointer to a session handle.

nsptr (IN)
Pointer to the namespace string (currently only `CLIENTCONTEXT`).

nsptrlen (IN)
Length of the namespace string.

errhp (OUT)
An error handle that can be passed to `OCIErrorGet()`.

mode (IN)
Mode (`OCI_DEFAULT` is the default).

#### Returns

Returns an error number.

#### Comments

This cleans up the context information on the server side during the next call to the server. This namespace information is cleared from the session handle after the information has been sent to the server and must be set up again if needed.

**Related Topics**

- OCIAppCtxSet()
- [OCIErrorGet()](miscellaneous-functions.md)

### 25.2.2 OCIAppCtxSet()

Sets an attribute and its associated value in a namespace of an application context.

#### Purpose

Sets an attribute and its associated value in a namespace of an application context.

#### Syntax

    sword OCIAppCtxSet ( void      *sesshndl,
                         void      *nsptr,
                         ub4        nsptrlen,
                         void      *attrptr,
                         ub4        attrptrlen,
                         void      *valueptr,
                         ub4        valueptrlen,
                         OCIError  *errhp,
                         ub4        mode );

#### Parameters

sesshndl (IN/OUT)
Pointer to a session handle.

nsptr (IN)
Pointer to the namespace string (currently only `CLIENTCONTEXT`).

nsptrlen (IN)
Length of the namespace string.

attrptr (IN)
Pointer to the attribute string.

attrptrlen (IN)
The length of the string pointed to by `attrptr`.

valueptr (IN)
Pointer to the value string.

valueptrlen (IN)
The length of the string pointed to by `valueptr`.

errhp (OUT)
An error handle that can be passed to `OCIErrorGet()`.

mode (IN)
Mode (`OCI_DEFAULT` is the default).

#### Returns

Returns an error number.

#### Comments

The information set on the session handle is sent to the server during the next call to the server.

This information is cleared from the session handle after the information has been sent to the server and must be set up again if needed.

**Related Topics**

- OCIAppCtxClearAll()
- [OCIErrorGet()](miscellaneous-functions.md)

### 25.2.3 OCIConnectionPoolCreate()

Initializes the connection pool.

#### Purpose

Initializes the connection pool.

#### Syntax

    sword OCIConnectionPoolCreate ( OCIEnv         *envhp,
                                    OCIError       *errhp,
                                    OCICPool       *poolhp,
                                    OraText        **poolName,
                                    sb4            *poolNameLen,
                                    const OraText  *dblink,
                                    sb4             dblinkLen,
                                    ub4             connMin,
                                    ub4             connMax,
                                    ub4             connIncr,
                                    const OraText  *poolUsername,
                                    sb4             poolUserLen,
                                    const OraText  *poolPassword,
                                    sb4             poolPassLen,
                                    ub4             mode );

#### Parameters

envhp (IN)
A pointer to the environment where the connection pool is to be created

errhp (IN/OUT)
An error handle that can be passed to `OCIErrorGet()`.

poolhp (IN)
An allocated pool handle.

poolName (OUT)
The name of the connection pool connected to.

poolNameLen (OUT)
The length of the string pointed to by `poolName`.

dblink (IN)
Specifies the database (server) to connect to.

dblinkLen (IN)
The length of the string pointed to by `dblink`.

connMin (IN)
Specifies the minimum number of connections in the connection pool. Valid values are 0 and higher.

These connections are opened to the server by `OCIConnectionPoolCreate()`. After the connection pool is created, connections are opened only when necessary. Generally, this parameter should be set to the number of concurrent statements that the application is planning or expecting to run.

connMax (IN)
Specifies the maximum number of connections that can be opened to the database. After this value is reached, no more connections are opened. Valid values are 1 and higher.

connIncr (IN)
Allows the application to set the next increment for connections to be opened to the database if the current number of connections is less than `connMax`. Valid values are 0 and higher.

poolUsername (IN)
Connection pooling requires an implicit primary session. This attribute provides a user name for that session.

poolUserLen (IN)
The length of `poolUsername`.

poolPassword (IN)
The password for the user name `poolUsername`.

poolPassLen (IN)
The length of `poolPassword`.

mode (IN)
The modes supported are:

- `OCI_DEFAULT`

- `OCI_CPOOL_REINITIALIZE`

Ordinarily, `OCIConnectionPoolCreate()` is called with `mode` set to `OCI_DEFAULT`.

To change the pool attributes dynamically (for example, to change the `connMin`, `connMax`, and `connIncr` parameters), call `OCIConnectionPoolCreate()` with `mode` set to `OCI_CPOOL_REINITIALIZE`. When this is done, the other parameters are ignored.

#### Comments

The OUT parameters `poolName` and `poolNameLen` contain values to be used in subsequent `OCIServerAttach()` and `OCILogon2()` calls in place of the database name and the database name length arguments.

**Related Topics**

- OCIConnectionPoolDestroy()
- OCILogon2()
- OCIServerAttach()
- [OCIErrorGet()](miscellaneous-functions.md)
- [Connection Pool Handle Attributes](handle-and-descriptor-attributes.md)

### 25.2.4 OCIConnectionPoolDestroy()

Destroys the connection pool.

#### Purpose

Destroys the connection pool.

#### Syntax

    sword OCIConnectionPoolDestroy ( OCICPool     *poolhp,
                                     OCIError     *errhp,
                                     ub4           mode );

#### Parameters

poolhp (IN)
A pool handle for which a pool has been created.

errhp (IN/OUT)
An error handle that can be passed to `OCIErrorGet()`.

mode (IN)
Currently, this function supports only the `OCI_DEFAULT` mode.

**Related Topics**

- OCIConnectionPoolCreate()
- [OCIErrorGet()](miscellaneous-functions.md)

### 25.2.5 OCIDBShutdown()

Shuts down an Oracle Database instance.

#### Purpose

Shuts down an Oracle Database instance.

#### Syntax

    sword OCIDBShutdown ( OCISvcCtx     *svchp,
                          OCIError      *errhp,
                          OCIAdmin      *admhp,
                          ub4            mode);

#### Parameters

svchp (IN)
A handle to a service context. There must be a valid server handle and a valid user handle set in `svchp`.

errhp (IN/OUT)
An error handle that can be passed to `OCIErrorGet()` for diagnostic information when there is an error.

admhp (IN) - Optional
An instance administration handle. Currently not used; pass `(OCIAdmin *)0`.

mode (IN)
`OCI_DEFAULT` - Further connects are prohibited. Waits for users to disconnect from the database.

`OCI_DBSHUTDOWN_TRANSACTIONAL` - Further connects are prohibited and no new transactions are allowed. Waits for active transactions to complete.

`OCI_DBSHUTDOWN_TRANSACTIONAL_LOCAL` - Further connects are prohibited and no new transactions are allowed. Waits only for local transactions to complete.

`OCI_DBSHUTDOWN_IMMEDIATE` - Does not wait for current calls to complete or users to disconnect from the database. All uncommitted transactions are terminated and rolled back.

`OCI_DBSHUTDOWN_FINAL` - Shuts down the database. Should be used only in the second call to `OCIDBShutdown()` after the database is closed and dismounted.

`OCI_DBSHUTDOWN_ABORT` - Does not wait for current calls to complete or users to disconnect from the database. All uncommitted transactions are terminated and are not rolled back. This is the fastest possible way to shut down the database, but the next database startup may require instance recovery. Therefore, this option should be used only in unusual circumstances; for example, if a background process terminates abnormally.

#### Comments

To do a shut down, you must be connected to the database as `SYSOPER` or `SYSDBA`. You cannot be connected to a shared server through a dispatcher. When shutting down in any mode other than `OCI_DBSHUTDOWN_ABORT`, use the following procedure:

1.  Call `OCIDBShutdown()` in `OCI_DEFAULT`, `OCI_DBSHUTDOWN_TRANSACTIONAL`, `OCI_DBSHUTDOWN_TRANSACTIONAL_LOCAL`, or `OCI_DBSHUTDOWN_IMMEDIATE` mode to prohibit further connects.

2.  Issue the necessary `ALTER` `DATABASE` commands to close and dismount the database.

3.  Call `OCIDBShutdown()` in `OCI_DBSHUTDOWN_FINAL` mode to shut down the instance.

**Related Topics**

- [OCIAttrSet()](handle-and-descriptor-functions.md)
- OCIDBStartup()
- [OCIErrorGet()](miscellaneous-functions.md)
- [Database Startup and Shutdown](database-startup-and-shutdown.md)

### 25.2.6 OCIDBStartup()

Starts an Oracle Database instance.

#### Purpose

Starts an Oracle Database instance.

#### Syntax

    sword OCIDBStartup ( OCISvcCtx     *svchp,
                         OCIError      *errhp,
                         OCIAdmin      *admhp,
                         ub4            mode,
                         ub4            flags);

#### Parameters

svchp (IN)
A handle to a service context. There must be a valid server handle and user handle set in `svchp`.

errhp (IN/OUT)
An error handle that can be passed to `OCIErrorGet()` for diagnostic information when there is an error.

admhp (IN) - Optional
An instance administration handle. Use to pass additional arguments to the startup call, or pass `(OCIAdmin *)0` if you do not set `OCI_ATTR_ADMIN_PFILE`.

mode (IN)
`OCI_DEFAULT` - This is the only supported mode. It starts the instance, but does not mount or open the database. Same as `STARTUP` `NOMOUNT`.

flags (IN)
`OCI_DEFAULT` - Allows database access to all users.

`OCI_DBSTARTUPFLAG_RESTRICT` - Allows database access only to users with both the `CREATE` `SESSION` and `RESTRICTED` `SESSION` privileges (normally, the DBA).

`OCI_DBSTARTUPFLAG_FORCE` - Shuts down a running instance (if there is any) using `ABORT` before starting a new one. This mode should be used only in unusual circumstances.

#### Comments

You must be connected to the database as `SYSOPER` or `SYSDBA` in `OCI_PRELIM_AUTH` mode. You cannot be connected to a shared server through a dispatcher (that is, when you restart a running instance with `OCI_DBSTARTUPFLAG_FORCE`). To use a client-side parameter file (`pfile`), `OCI_ATTR_ADMIN_PFILE` must be set in the administration handle; otherwise, a server-side parameter file (`spfile`) is used. A call to `OCIDBStartup()` starts one instance on the server.

**Related Topics**

- [OCIAttrSet()](handle-and-descriptor-functions.md)
- OCIDBShutdown()
- OCIServerAttach()
- OCISessionBegin()
- [OCIErrorGet()](miscellaneous-functions.md)
- [Database Startup and Shutdown](database-startup-and-shutdown.md)

### 25.2.7 OCIEnvCreate()

Creates and initializes an environment handle for OCI functions to work under.

#### Purpose

Creates and initializes an environment handle for OCI functions to work under.

#### Syntax

    sword OCIEnvCreate   ( OCIEnv       **envhpp,
                           ub4            mode,
                           const void    *ctxp,
                           const void    *(*malocfp)
                                          (void  *ctxp,
                                          size_t size),
                           const void    *(*ralocfp)
                                          (void  *ctxp,
                                          void  *memptr,
                                          size_t newsize),
                           const void     (*mfreefp)
                                          (void  *ctxp,
                                          void  *memptr))
                           size_t         xtramemsz,
                           void         **usrmempp );

#### Parameters

envhpp (OUT)
A pointer to an environment handle whose encoding setting is specified by `mode`. The setting is inherited by statement handles derived from `envhpp`.

mode (IN)
Specifies initialization of the mode. Valid modes are:

- `OCI_DEFAULT` - The default value, which is non-`UTF-16` encoding.

- `OCI_THREADED` - Uses threaded environment. Internal data structures not exposed to the user are protected from concurrent accesses by multiple threads.

- `OCI_OBJECT` - Uses object features.

- `OCI_EVENTS` - Uses publish-subscribe notifications.

- `OCI_NO_UCB` - Suppresses the calling of the dynamic callback routine `OCIEnvCallback()`. The default behavior is to allow calling of `OCIEnvCallback()` when the environment is created.

  **See Also:**

  "[Dynamic Callback Registrations](user-defined-callback-functions.md)"

- `OCI_ENV_NO_MUTEX` - No mutual exclusion (mutex) locking occurs in this mode. All OCI calls done on the environment handle, or on handles derived from the environment handle, must be serialized. `OCI_THREADED` must also be specified when `OCI_ENV_NO_MUTEX` is specified.

- `OCI_SUPPRESS_NLS_VALIDATION` - Suppresses NLS character validation; NLS character validation suppression is on by default beginning with Oracle Database 11g Release 1 (11.1). Use `OCI_ENABLE_NLS_VALIDATION` to enable NLS character validation. See Comments for more information.

- `OCI_NEW_LENGTH_SEMANTICS` - Byte-length semantics is used consistently for all handles, regardless of character sets.

- `OCI_NCHAR_LITERAL_REPLACE_ON` - Turns on N' substitution.

- `OCI_NCHAR_LITERAL_REPLACE_OFF` - Turns off N' substitution. If neither this mode nor `OCI_NCHAR_LITERAL_REPLACE_ON` is used, the substitution is determined by the environment variable `ORA_NCHAR_LITERAL_REPLACE`, which can be set to `TRUE` or `FALSE`. When it is set to `TRUE`, the replacement is turned on; otherwise it is turned off, which is the default setting in OCI.

- `OCI_ENABLE_NLS_VALIDATION` - Enables NLS character validation. See Comments for more information.

ctxp (IN)
Specifies the user-defined context for the memory callback routines.

malocfp (IN)
Specifies the user-defined memory allocation function. If mode is `OCI_THREADED`, this memory allocation routine must be thread-safe.

ctxp (IN)
Specifies the context pointer for the user-defined memory allocation function.

size (IN)
Specifies the size of memory to be allocated by the user-defined memory allocation function.

ralocfp (IN)
Specifies the user-defined memory reallocation function. If the mode is `OCI_THREADED`, this memory allocation routine must be thread-safe.

ctxp (IN)
Specifies the context pointer for the user-defined memory reallocation function.

memptr (IN)
Pointer to memory block.

newsize (IN)
Specifies the new size of memory to be allocated.

mfreefp (IN)
Specifies the user-defined memory free function. If the mode is `OCI_THREADED`, this memory free routine must be thread-safe.

ctxp (IN)
Specifies the context pointer for the user-defined memory free function.

memptr (IN)
Pointer to memory to be freed.

xtramemsz (IN)
Specifies the amount of user memory to be allocated for the duration of the environment.

usrmempp (OUT)
Returns a pointer to the user memory of size `xtramemsz` allocated by the call for the user.

#### Comments

This call creates an environment for all the OCI calls using the modes specified by the user.

**Note:**

This call should be invoked before any other OCI call and should be used instead of the `OCIInitialize()` call.

This call returns an environment handle, which is then used by the remaining OCI functions. There can be multiple environments in OCI, each with its own environment modes. This function also performs any process level initialization if required by any mode. For example, if you want to initialize an environment as `OCI_THREADED`, then all libraries that are used by OCI are also initialized in the threaded mode.

If N' substitution is turned on, the `OCIStmtPrepare2()` function performs the N' substitution on the SQL text and stores the resulting SQL text in the statement handle. Thus, if the application uses `OCI_ATTR_STATEMENT` to retrieve the SQL text from the OCI statement handle, the modified SQL text, instead of the original SQL text, is returned.

To turn on N' substitution in `ksh` shell:

    export ORA_NCHAR_LITERAL_REPLACE=TRUE

To turn on N' substitution in `csh` shell:

    setenv ORA_NCHAR_LITERAL_REPLACE TRUE

If a remote database is of a release before 10.2, N' substitution is not performed.

If you are writing a DLL or a shared library using the OCI library, then use this call instead of the deprecated `OCIInitialize()` call.

**See Also:**

"[User Memory Allocation](oci-programming-basics.md)" for more information about the `xtramemsz` parameter and user memory allocation

Regarding `OCI_SUPPRESS_NLS_VALIDATION` and `OCI_ENABLE_NLS_VALIDATION` modes, by default, when client and server character sets are identical, and client and server releases are both Oracle Database 11g Release 1 (11.1) or later, OCI does not validate character data in the interest of better performance. This means that if the application inserts a character string with partial multibyte characters (for example, at the end of a bind variable), then such strings could get persisted in the database as is.

Note that if either the client or the server release is older than Oracle Database 11g Release 1 (11.1), then OCI does not allow partial characters.

The `OCI_ENABLE_NLS_VALIDATION` mode, which was the default until Oracle Database 10g Release 2 (10.2), ensures that partial multibyte characters are not persisted in the database (when client and server character sets are identical). If the application can produce partial multibyte characters, and if the application can run in an environment where the client and server character sets are identical, then Oracle recommends using the `OCI_ENABLE_NLS_VALIDATION` mode explicitly in order to ensure that such partial characters get stripped out.

#### Example

Creating a Thread-Safe OCI Environment with N' Substitution Turned On

    OCIEnv *envhp;
    ...
    /* Create a thread-safe OCI environment with N' substitution turned on.  */
    if(OCIEnvCreate((OCIEnv **)&envhp,
             (ub4)OCI_THREADED | OCI_NCHAR_LITERAL_REPLACE_ON,
             (void  *)0, (void  * (*)(void  *, size_t))0,
             (void  * (*)(void  *, void  *, size_t))0,
             (void (*)(void  *, void  *))0,
             (size_t)0, (void  **)0))
    {
      printf("Failed: OCIEnvCreate()\n");
      return 1;
    }
    ...

**Related Topics**

- [OCIHandleAlloc()](handle-and-descriptor-functions.md)
- [OCIHandleFree()](handle-and-descriptor-functions.md)
- OCIEnvNlsCreate()
- OCITerminate()
- [OCIStmtPrepare2()](statement-functions.md)

### 25.2.8 OCIEnvNlsCreate()

Creates and initializes an environment handle for OCI functions to work under.

#### Purpose

This function is an enhanced version of the `OCIEnvCreate()` function.

#### Syntax

    sword OCIEnvNlsCreate   ( OCIEnv        **envhpp,
                              ub4             mode,
                              void           *ctxp,
                              void          *(*malocfp)
                                                 (void  *ctxp,
                                                  size_t size),
                              void          *(*ralocfp)
                                                 (void  *ctxp,
                                                  void  *memptr,
                                                  size_t newsize),
                              void          (*mfreefp)
                                                 (void  *ctxp,
                                                  void  *memptr))
                              size_t          xtramemsz,
                              void          **usrmempp
                              ub2             charset,
                              ub2             ncharset );

#### Parameters

envhpp (OUT)
A pointer to an environment handle whose encoding setting is specified by `mode`. The setting is inherited by statement handles derived from `envhpp`.

mode (IN)
Specifies initialization of the mode. Valid modes are:

- `OCI_DEFAULT` - The default value, which is non-`UTF-16` encoding.

- `OCI_THREADED` - Uses threaded environment. Internal data structures not exposed to the user are protected from concurrent accesses by multiple threads.

- `OCI_OBJECT` - Uses object features.

- `OCI_EVENTS` - Uses publish-subscribe notifications.

- `OCI_NO_UCB` - Suppresses the calling of the dynamic callback routine `OCIEnvCallback()`. The default behavior is to allow calling of `OCIEnvCallback()` when the environment is created.

  **See Also:**

  [Dynamic Callback Registrations](user-defined-callback-functions.md)

<!-- -->

- `OCI_ENV_NO_MUTEX` - No mutual exclusion (mutex) locking occurs in this mode. All OCI calls done on the environment handle, or on handles derived from the environment handle, must be serialized. `OCI_THREADED` must also be specified when `OCI_ENV_NO_MUTEX` is specified.

- `OCI_SUPPRESS_NLS_VALIDATION` - Suppresses NLS character validation; NLS character validation suppression is on by default beginning with Oracle Database 11g Release 1 (11.1). Use `OCI_ENABLE_NLS_VALIDATION` to enable NLS character validation. See Comments for more information.

- `OCI_NCHAR_LITERAL_REPLACE_ON` - Turns on N' substitution.

- `OCI_NCHAR_LITERAL_REPLACE_OFF` - Turns off N' substitution. If neither this mode nor `OCI_NCHAR_LITERAL_REPLACE_ON` is used, the substitution is determined by the environment variable `ORA_NCHAR_LITERAL_REPLACE`, which can be set to `TRUE` or `FALSE`. When it is set to `TRUE`, the replacement is turned on; otherwise it is turned off, the default setting in OCI.

- `OCI_ENABLE_NLS_VALIDATION` - Enables NLS character validation. See Comments for more information.

ctxp (IN)
Specifies the user-defined context for the memory callback routines.

malocfp (IN)
Specifies the user-defined memory allocation function. If `mode` is `OCI_THREADED`, this memory allocation routine must be thread-safe.

ctxp (IN)
Specifies the context pointer for the user-defined memory allocation function.

size (IN)
Specifies the size of memory to be allocated by the user-defined memory allocation function.

ralocfp (IN)
Specifies the user-defined memory reallocation function. If the mode is `OCI_THREADED`, this memory allocation routine must be thread-safe.

ctxp (IN)
Specifies the context pointer for the user-defined memory reallocation function.

memptr (IN)
Pointer to memory block.

newsize (IN)
Specifies the new size of memory to be allocated.

mfreefp (IN)
Specifies the user-defined memory free function. If the mode is `OCI_THREADED`, this memory free routine must be thread-safe.

ctxp (IN)
Specifies the context pointer for the user-defined memory free function.

memptr (IN)
Pointer to memory to be freed.

xtramemsz (IN)
Specifies the amount of user memory to be allocated for the duration of the environment.

usrmempp (OUT)
Returns a pointer to the user memory of size `xtramemsz` allocated by the call for the user.

charset (IN)
The client-side character set for the current environment handle. If it is 0, the `NLS_LANG` setting is used. `OCI_UTF16ID` is a valid setting; it is used by the metadata and the `CHAR` data.

ncharset (IN)
The client-side national character set for the current environment handle. If it is 0, `NLS_NCHAR` setting is used. `OCI_UTF16ID` is a valid setting; it is used by the `NCHAR` data.

#### Returns

`OCI_SUCCESS` - Environment handle has been successfully created.

`OCI_ERROR` - An error occurred.

#### Comments

This call creates an environment for all the OCI calls using the modes you specify.

After you use `OCIEnvNlsCreate()` to create the environment handle, the actual lengths and returned lengths of bind and define handles are always expressed in number of bytes. This applies to the following calls:

- `OCIBindByName()` and `OCIBindByName2()`

- `OCIBindByPos()` and `OCIBindByPos2()`

- `OCIBindDynamic()`

- `OCIDefineByPos()` and `OCIDefineByPos2()`

- `OCIDefineDynamic()`

This function enables you to set `charset` and `ncharset` IDs at environment creation time. It is an enhanced version of the `OCIEnvCreate()` function.

`OCIEnvNlsCreate()` must be called with `charset` and `ncharset` either both zero or both non-zero. Failure to do so results in an error (`ORA-24820`).

This function sets nonzero `charset` and `ncharset` as client-side database and national character sets, replacing the ones specified by `NLS_LANG` and `NLS_NCHAR`. When `charset` and `ncharset` are 0, the function behaves exactly the same as `OCIEnvCreate()`. Specifically, `charset` controls the encoding for metadata and data with implicit form attribute, and `ncharset` controls the encoding for data with `SQLCS_NCHAR` form attribute.

Although `OCI_UTF16ID` can be set by `OCIEnvNlsCreate()`, it cannot be set in `NLS_LANG` or `NLS_NCHAR`. To access the character set IDs in `NLS_LANG` and `NLS_NCHAR`, use `OCINlsEnvironmentVariableGet()`.

This call returns an environment handle, which is then used by the remaining OCI functions. There can be multiple environments in OCI, each with its own environment modes. This function also performs any process level initialization if required by any mode. For example, if you want to initialize an environment as `OCI_THREADED`, then all libraries that are used by OCI are also initialized in the threaded mode.

If N' substitution is turned on, the `OCIStmtPrepare2()` function performs the N' substitution on the SQL text and stores the resulting SQL text in the statement handle. Thus, if the application uses `OCI_ATTR_STATEMENT` to retrieve the SQL text from the OCI statement handle, the modified SQL text, instead of the original SQL text, is returned.

To turn on N' substitution in `ksh` shell:

    export ORA_NCHAR_LITERAL_REPLACE=TRUE

To turn on N' substitution in `csh` shell:

    setenv ORA_NCHAR_LITERAL_REPLACE TRUE

If a remote database is of a release before 10.2, N' substitution is not performed.

If you are writing a DLL or a shared library using the OCI library, then use this call instead of the deprecated `OCIInitialize()` call.

**See Also:**

- [User Memory Allocation](oci-programming-basics.md) for more information about the `xtramemsz` parameter and user memory allocation

- `OCIEnvCreate()` for a code example illustrating setting N' substitution in a related function

Regarding `OCI_SUPPRESS_NLS_VALIDATION` and `OCI_ENABLE_NLS_VALIDATION` modes, by default, when client and server character sets are identical, and client and server releases are both Oracle Database 11g Release 1 (11.1) or later, OCI does not validate character data in the interest of better performance. This means that if the application inserts a character string with partial multibyte characters (for example, at the end of a bind variable), then such strings could get persisted in the database as is.

Note that if either the client or the server release is older than Oracle Database 11g Release 1 (11.1), then OCI does not allow partial characters.

The `OCI_ENABLE_NLS_VALIDATION` mode, which was the default until Oracle Database 10g Release 2 (10.2), ensures that partial multibyte characters are not persisted in the database (when client and server character sets are identical). If the application can produce partial multibyte characters, and if the application can run in an environment where the client and server character sets are identical, then Oracle recommends using the `OCI_ENABLE_NLS_VALIDATION` mode explicitly in order to ensure that such partial characters get stripped out.

**Related Topics**

- [OCIHandleAlloc()](handle-and-descriptor-functions.md)
- [OCIHandleFree()](handle-and-descriptor-functions.md)
- OCITerminate()
- [OCINlsEnvironmentVariableGet()](oci-locale-functions.md)
- OCIEnvCreate()
- [OCIStmtPrepare2()](statement-functions.md)

### 25.2.9 OCILogoff()

Releases a session that was retrieved using `OCILogon2()` or `OCILogon()`.

#### Purpose

Releases a session that was retrieved using `OCILogon2()` or `OCILogon()`.

#### Syntax

    sword OCILogoff ( OCISvcCtx      *svchp
                      OCIError       *errhp );

#### Parameters

svchp (IN)
The service context handle that was used in the call to `OCILogon()` or `OCILogon2()`.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

#### Comments

This function is used to release a session that was retrieved using `OCILogon2()` or `OCILogon()`. If `OCILogon()` was used, then this function terminates the connection and session. If `OCILogon2()` was used, then the exact behavior of this call is determined by the `mode` in which the corresponding `OCILogon2()` function was called. In the default case, this function closes the session or connection. For connection pooling, it closes the session and returns the connection to the pool. For session pooling, it returns the session or connection pair to the pool.

**Related Topics**

- OCILogon()
- OCILogon2()
- [OCIErrorGet()](miscellaneous-functions.md)

**See Also:**

"[Application Initialization, Connection, and Session Creation](oci-programming-basics.md)" for more information about logging on and off in an application

### 25.2.10 OCILogon()

Creates a simple logon session.

#### Purpose

Creates a simple logon session.

#### Syntax

    sword OCILogon ( OCIEnv          *envhp,
                     OCIError        *errhp,
                     OCISvcCtx      **svchp,
                     const OraText   *username,
                     ub4              uname_len,
                     const OraText   *password,
                     ub4              passwd_len,
                     const OraText   *dbname,
                     ub4              dbname_len );

#### Parameters

envhp (IN)
The OCI environment handle.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

svchp (IN/OUT)
The service context pointer.

username (IN)
The user name. Must be in the encoding specified by the `charset` parameter of a previous call to `OCIEnvNlsCreate()`.

uname_len (IN)
The length of `username`, in number of bytes, regardless of the encoding.

password (IN)
The user's password. Must be in the encoding specified by the `charset` parameter of a previous call to `OCIEnvNlsCreate()`.

passwd_len (IN)
The length of `password`, in number of bytes, regardless of the encoding.

dbname (IN)
The name of the database to connect to. Must be in the encoding specified by the `charset` parameter of a previous call to `OCIEnvNlsCreate()`.

dbname_len (IN)
The length of `dbname`, in number of bytes, regardless of the encoding.

#### Comments

This function is used to create a simple logon session for an application.

**Note:**

Users requiring more complex sessions, such as TP monitor applications, should see "[Application Initialization, Connection, and Session Creation](oci-programming-basics.md)".

This call allocates the service context handles that are passed to it. This call also implicitly allocates server and user session handles associated with the session. These handles can be retrieved by calling `OCIArrayDescriptorAlloc()` on the service context handle.

**Related Topics**

- OCILogoff()
- OCIEnvNlsCreate()
- [OCIArrayDescriptorAlloc()](handle-and-descriptor-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 25.2.11 OCILogon2()

Gets a session.

#### Purpose

This session may be a new one with a new underlying connection, or one that is started over a virtual connection from an existing connection pool, or one from an existing session pool. The `mode` that the function is called with determines its behavior.

#### Syntax

    sword OCILogon2 ( OCIEnv          *envhp,
                      OCIError        *errhp,
                      OCISvcCtx      **svchp,
                      const OraText   *username,
                      ub4              uname_len,
                      const OraText   *password,
                      ub4              passwd_len,
                      const OraText   *dbname,
                      ub4              dbname_len );
                      ub4              mode );

#### Parameters

envhp (IN)
The OCI environment handle. For connection pooling and session pooling, this must be the one that the respective pool was created in.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

svchp (IN/OUT)
Address of an OCI service context pointer. This is filled with a server and session handle.

In the default case, a new session and server handle is allocated, the connection and session are started, and the service context is populated with these handles.

For connection pooling, a new session handle is allocated, and the session is started over a virtual connection from the connection pool.

For session pooling, the service context is populated with an existing session or server handle pair from the session pool.

Note that you must not change any attributes of the server and user or session handles associated with the service context pointer. Doing so results in an error being returned by the `OCIAttrSet()` call.

The only attribute of the service context that can be altered is `OCI_ATTR_STMTCACHESIZE`.

username (IN)
The user name used to authenticate the session. Must be in the encoding specified by the `charset` parameter of a previous call to `OCIEnvNlsCreate()`.

uname_len (IN)
The length of `username`, in number of bytes, regardless of the encoding.

password (IN)
The user's password. For connection pooling, if this parameter is `NULL` then `OCILogon2()` assumes that the logon is for a proxy user. It implicitly creates a proxy connection in such a case, using the pool user to authenticate the proxy user. Must be in the encoding specified by the `charset` parameter of a previous call to `OCIEnvNlsCreate()`.

passwd_len (IN)
The length of `password`, in number of bytes, regardless of the encoding.

dbname (IN)
For the default case, this indicates the connect string to use to connect to the Oracle Database.

For connection pooling, this indicates the connection pool from which to retrieve the virtual connection to start the session. This value is returned by the `OCIConnectionPoolCreate()` call.

For session pooling, it indicates the pool to get the session from. It is returned by the `OCISessionPoolCreate()` call.

The `dbname` must be in the encoding specified by the `charset` parameter of a previous call to `OCIEnvNlsCreate()`.

dbname_len (IN)
The length of `dbname`. For session pooling and connection pooling, this value is returned by the `OCISessionPoolCreate()` or `OCIConnectionPoolCreate()` call respectively.

mode (IN)
The values accepted are:

- `OCI_DEFAULT`

- `OCI_LOGON2_CPOOL`

- `OCI_LOGON2_SPOOL`

- `OCI_LOGON2_STMTCACHE`

- `OCI_LOGON2_PROXY`

For the default (nonpooling case), the following modes are valid:

`OCI_DEFAULT` - Equivalent to calling `OCILogon()`.

`OCI_LOGON2_STMTCACHE` - Enable statement caching.

For connection pooling, the following modes are valid:

`OCI_LOGON2_CPOOL` or `OCI_CPOOL` - This must be set to use connection pooling.

`OCI_LOGON2_STMTCACHE` - Enable statement caching.

To use proxy authentication for connection pooling, the password must be set to `NULL`. You are then given a session that is authenticated by the user name provided in the `OCILogon2()` call, through the proxy credentials supplied in the `OCIConnectionPoolCreate()` call.

For session pooling, the following modes are valid:

`OCI_LOGON2_SPOOL` - This must be set to use session pooling.

`OCI_LOGON2_STMTCACHE` - Enable statement caching.

`OCI_LOGON2_PROXY` - Use proxy authentication. You are given a session that is authenticated by the user name provided in the `OCILogon2()` call, through the proxy credentials supplied in the `OCISessionPoolCreate()` call.

#### Comments

None.

**Related Topics**

- OCILogon()
- OCILogoff()
- OCISessionGet()
- OCISessionRelease()
- [OCIAttrSet()](handle-and-descriptor-functions.md)
- OCIEnvNlsCreate()
- OCIConnectionPoolCreate()
- OCISessionPoolCreate()
- [OCIErrorGet()](miscellaneous-functions.md)

### 25.2.12 OCIRequestDisableReplay()

Disables application continuity replay for a session for the duration of the current database request.

#### Purpose

Triggers OCI to stop recording calls until the end of an application request (the end of a request is marked by `OCISessionRelease()`). Use this call when Application Continuity for OCI is enabled but the application is entering a section of code that is not replayable.

#### Syntax

    OCIRequestDisableReplay(OCISvcCtx *svchp,
                            OCIError  *errhp,
                            ub4        mode);

#### Parameters

svchp (IN/OUT)
The service context; the service context handle must be initialized and have a session handle associated with it.

errhp (IN/OUT)
The error handle.

mode (IN)
This call supports the following modes:

- `OCI_DEFAULT`

#### Usage Notes

See [OCI and Application Continuity](high-availability-in-oci.md) for more information. See [Oracle Real Application Clusters Administration and Deployment Guide](../racad/ensuring-application-continuity.md) for information about enabling Application Continuity.

### 25.2.13 OCIServerAttach()

Creates an access path to a data source for OCI operations.

#### Purpose

Creates an access path to a data source for OCI operations.

#### Syntax

    sword OCIServerAttach ( OCIServer     *srvhp,
                            OCIError      *errhp,
                            const OraText *dblink,
                            sb4            dblink_len,
                            ub4            mode );

#### Parameters

srvhp (IN/OUT)
An uninitialized server handle, which is initialized by this call. Passing in an initialized server handle causes an error.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

dblink (IN)
Specifies the database server to use. This parameter points to a character string that specifies a connect string or a service point. If the connect string is `NULL`, then this call attaches to the default host. The string itself could be in `UTF-16` encoding mode or not, depending on the `mode` or the setting in application's environment handle. The length of `dblink` is specified in `dblink_len`. The `dblink` pointer may be freed by the caller on return.

The name of the connection pool to connect to when `mode `= `OCI_CPOOL`. This must be the same as the `poolName` parameter of the connection pool created by `OCIConnectionPoolCreate()`. Must be in the encoding specified by the `charset` parameter of a previous call to `OCIEnvNlsCreate()`.

dblink_len (IN)
The length of the string pointed to by `dblink`. For a valid connect string name or alias, `dblink_len` must be nonzero. Its value is in number of bytes.

The length of `poolName`, in number of bytes, regardless of the encoding, when `mode `= `OCI_CPOOL`.

mode (IN)
Specifies the various modes of operation. The valid modes are:

- `OCI_DEFAULT` - For encoding, this value tells the server handle to use the setting in the environment handle.

- `OCI_CPOOL` - Use connection pooling.

Because an attached server handle can be set for any connection session handle, the `mode` value here does not contribute to any session handle.

#### Comments

This call is used to create an association between an OCI application and a particular server.

This call assumes that `OCIConnectionPoolCreate()` has been called, giving `poolName`, when connection pooling is in effect.

This call initializes a server context handle, which must have been previously allocated with a call to `OCIHandleAlloc()`. The server context handle initialized by this call can be associated with a service context through a call to `OCIAttrSet()`. After that association has been made, OCI operations can be performed against the server.

If an application is operating against multiple servers, multiple server context handles can be maintained. OCI operations are performed against whichever server context is currently associated with the service context.

When `OCIServerAttach()` is successfully completed, an Oracle Database shadow process is started. `OCISessionEnd()` and `OCIServerDetach()` should be called to clean up the Oracle Database shadow process. Otherwise, the shadow processes accumulate and cause the Linux or UNIX system to run out of processes. If the database is restarted and there are not enough processes, the database may not start up.

See [OCI and Application Continuity](high-availability-in-oci.md) for more information about Application Continuity. See [Oracle Real Application Clusters Administration and Deployment Guide](../racad/ensuring-application-continuity.md) for information about enabling Application Continuity.

#### Example

The following code example demonstrates the use of `OCIServerAttach()`. This code segment allocates the server handle, makes the attach call, allocates the service context handle, and then sets the server context into it.

Using the OCIServerAttach() Call

    OCIHandleAlloc( (void  *) envhp, (void  **) &srvhp, (ub4)
         OCI_HTYPE_SERVER, 0, (void  **) 0);
    OCIServerAttach( srvhp, errhp, (text *) 0, (sb4) 0, (ub4) OCI_DEFAULT);
    OCIHandleAlloc( (void  *) envhp, (void  **) &svchp, (ub4)
         OCI_HTYPE_SVCCTX, 0, (void  **) 0);
    /* set attribute server context in the service context */
    OCIAttrSet( (void  *) svchp, (ub4) OCI_HTYPE_SVCCTX, (void  *) srvhp,
         (ub4) 0, (ub4) OCI_ATTR_SERVER, (OCIError *) errhp);

**Related Topics**

- OCIServerDetach()
- OCIConnectionPoolCreate()
- OCIEnvNlsCreate()
- [OCIHandleAlloc()](handle-and-descriptor-functions.md)
- [OCIAttrSet()](handle-and-descriptor-functions.md)
- OCISessionEnd()
- [OCIErrorGet()](miscellaneous-functions.md)

### 25.2.14 OCIServerDetach()

Deletes an access path to a data source for OCI operations.

#### Purpose

Deletes an access path to a data source for OCI operations.

#### Syntax

    sword OCIServerDetach ( OCIServer   *srvhp,
                            OCIError    *errhp,
                            ub4          mode );

#### Parameters

srvhp (IN)
A handle to an initialized server context, which is reset to an uninitialized state. The handle is not deallocated.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

mode (IN)
Specifies the various modes of operation. The only valid mode is `OCI_DEFAULT` for the default mode.

#### Comments

This call deletes an access path a to data source for OCI operations. The access path was established by a call to `OCIServerAttach()`.

**Related Topics**

- OCIServerAttach()
- [OCIErrorGet()](miscellaneous-functions.md)

### 25.2.15 OCISessionBegin()

Creates a user session and begins a user session for a given server.

#### Purpose

Creates a user session and begins a user session for a given server.

#### Syntax

    sword OCISessionBegin ( OCISvcCtx     *svchp,
                            OCIError      *errhp,
                            OCISession    *usrhp,
                            ub4            credt,
                            ub4            mode );

#### Parameters

svchp (IN)
A handle to a service context. There must be a valid server handle set in `svchp`.

errhp (IN)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

usrhp (IN/OUT)
A handle to a user session context, which is initialized by this call.

credt (IN)
Specifies the type of credentials to use for establishing the user session. Valid values for `credt` are:

- `OCI_CRED_RDBMS` - Authenticate using a database user name and password pair as credentials. The attributes `OCI_ATTR_USERNAME` and `OCI_ATTR_PASSWORD` should be set on the user session context before this call.

- `OCI_CRED_EXT` - Authenticate using external credentials. No user name or password is provided.

mode (IN)
Specifies the various modes of operation. Valid modes are:

- `OCI_DEFAULT` - In this mode, the user session context returned can only ever be set with the server context specified in `svchp`. For encoding, the server handle uses the setting in the environment handle.

- `OCI_MIGRATE` - In this mode, the new user session context can be set in a service handle with a different server handle. This mode establishes the user session context. To create a migratable session, the service handle must already be set with a nonmigratable user session, which becomes the "creator" session of the migratable session. That is, a migratable session must have a nonmigratable parent session.

  `OCI_MIGRATE` should not be used when the session uses connection pool underneath. The session migration and multiplexing happens transparently to the user.

- `OCI_SYSDBA` - In this mode, you are authenticated for SYSDBA access.

- `OCI_SYSOPER` - In this mode, you are authenticated for SYSOPER access.

- `OCI_SYSASM` - In this mode, you are authenticated for SYSASM access.

- `OCI_SYSBKB` - In this mode, you are authenticated for SYSBACKUP access.

- `OCI_SYSDGD` - In this mode, you are authenticated for SYSDG access.

- `OCI_SYSKMT` - In this mode, you are authenticated for SYSKM access.

- `OCI_SYSRAC` - In this mode, you are authenticated for SYSRAC access.

- `OCI_PRELIM_AUTH` - This mode can only be used with `OCI_SYSDBA` or `OCI_SYSOPER` to authenticate for certain administration tasks.

- `OCI_STMT_CACHE` - Enables statement caching with default size on the given service handle. It is optional to pass this mode if the application is going to explicitly set the size later using `OCI_ATTR_STMTCACHESIZE` on that service handle.

#### Comments

The `OCISessionBegin()` call is used to authenticate a user against the server set in the service context handle.

**Note:**

Check for any errors returned when trying to start a session. For example, if the password for the account has expired, an ORA-28001 error is returned.

For release 8.1 or later, `OCISessionBegin()` must be called for any given server handle before requests can be made against it. `OCISessionBegin()` only supports authenticating the user for access to the Oracle database specified by the server handle in the service context. In other words, after `OCIServerAttach()` is called to initialize a server handle, `OCISessionBegin()` must be called to authenticate the user for that given server.

If Application Continuity for OCI is enabled, `OCISessionBegin()` implicitly marks the beginning of an application request. When using the OCI session pool APIs, it is not necessary to call `OCIRequestBegin()` and `OCIRequestEnd()`.

When using Unicode, when the `mode` or the environment handle has the appropriate setting, the user name and password that have been set in the session handle `usrhp` should be in Unicode. Before calling this function to start a session with a user name and password, you must have called `OCIAttrSet()` to set these two Unicode strings into the session handle with corresponding length in bytes, because `OCIAttrSet()` only takes `void `pointers. The string buffers then are interpreted by `OCISessionBegin()`.

When `OCISessionBegin()` is called for the first time for a given server handle, the user session may not be created in migratable (`OCI_MIGRATE`) mode.

After `OCISessionBegin()` has been called for a server handle, the application may call `OCISessionBegin()` again to initialize another user session handle with different (or the same) credentials and different (or the same) operation modes. If an application wants to authenticate a user in `OCI_MIGRATE` mode, the service handle must be associated with a nonmigratable user handle. The user ID of that user handle becomes the ownership ID of the migratable user session. Every migratable session must have a nonmigratable parent session.

If the `OCI_MIGRATE` mode is not specified, then the user session context can only be used with the same server handle set in `svchp`. If the `OCI_MIGRATE` mode is specified, then the user authentication can be set with different server handles. However, the user session context can only be used with server handles that resolve to the same database instance. Security checking is done during session switching. A session can migrate to another process only if there is a nonmigratable session currently connected to that process whose userid is the same as that of the creator's userid or its own userid.

Do not set the `OCI_MIGRATE` flag in the call to `OCISessionBegin()` when the virtual server handle points to a connection pool (`OCIServerAttach()` called with `mode` set to `OCI_CPOOL`). Oracle Database supports passing this flag only for compatibility reasons. Do not use the `OCI_MIGRATE` flag, as the perception that you get when using a connection pool is of sessions having their own dedicated (virtual) connections that are transparently multiplexed onto real connections.

`OCI_SYSDBA`, `OCI_SYSOPER`, and `OCI_PRELIM_AUTH` can only be used with a primary user session context.

To provide credentials for a call to `OCISessionBegin()`, two methods are supported. The first method is to provide a valid user name and password pair for database authentication in the user session handle passed to `OCISessionBegin()`. This involves using `OCIAttrSet()` to set the `OCI_ATTR_USERNAME` and `OCI_ATTR_PASSWORD` attributes on the user session handle. Then `OCISessionBegin()` is called with `OCI_CRED_RDBMS`.

**Note:**

When the user session handle is terminated using `OCISessionEnd()`, the user name and password attributes remain unchanged and thus can be reused in a future call to `OCISessionBegin()`. Otherwise, they must be reset to new values before the next `OCISessionBegin()` call.

The second method is to use external credentials. No attributes need to be set on the user session handle before calling `OCISessionBegin()`. The credential type is `OCI_CRED_EXT`. This is equivalent to the Oracle7 'connect /' syntax. If values have been set for `OCI_ATTR_USERNAME` and `OCI_ATTR_PASSWORD`, then these are ignored if `OCI_CRED_EXT` is used.

Another way of setting credentials is to use the session ID of an authenticated user with the `OCI_MIGSESSION` attribute. This ID can be extracted from the session handle of an authenticated user using the `OCIAttrGet()` call.

#### Example

The following code example demonstrates the use of `OCISessionBegin()`. This code segment allocates the user session handle, sets the user name and password attributes, calls `OCISessionBegin()`, and then sets the user session into the service context.

Using the OCISessionBegin() Call

    /* allocate a user session handle */
    OCIHandleAlloc((void  *)envhp, (void  **)&usrhp, (ub4)
         OCI_HTYPE_SESSION, (size_t) 0, (void  **) 0);
    OCIAttrSet((void  *)usrhp, (ub4)OCI_HTYPE_SESSION, (void  *)"hr",
         (ub4)strlen("hr"), OCI_ATTR_USERNAME, errhp);
    OCIAttrSet((void  *)usrhp, (ub4)OCI_HTYPE_SESSION, (void  *)"hr",
         (ub4)strlen("hr"), OCI_ATTR_PASSWORD, errhp);
    checkerr(errhp, OCISessionBegin (svchp, errhp, usrhp, OCI_CRED_RDBMS,
         OCI_DEFAULT));
    OCIAttrSet((void  *)svchp, (ub4)OCI_HTYPE_SVCCTX, (void  *)usrhp,
         (ub4)0, OCI_ATTR_SESSION, errhp);

**Related Topics**

- OCISessionEnd()
- OCIServerAttach()
- [OCIAttrSet()](handle-and-descriptor-functions.md)
- [OCIAttrGet()](handle-and-descriptor-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 25.2.16 OCISessionEnd()

Terminates a user session context created by `OCISessionBegin()`.

#### Purpose

Terminates a user session context created by `OCISessionBegin()`.

#### Syntax

    sword OCISessionEnd ( OCISvcCtx       *svchp,
                          OCIError        *errhp,
                          OCISession      *usrhp,
                          ub4              mode );

#### Parameters

svchp (IN/OUT)
The service context handle. There must be a valid server handle and user session handle associated with `svchp`.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

usrhp (IN)
Deauthenticate this user. If this parameter is passed as `NULL`, the user in the service context handle is deauthenticated.

mode (IN)
The only valid mode is `OCI_DEFAULT`.

#### Comments

The user security context associated with the service context is invalidated by this call. Storage for the user session context is not freed. The transaction specified by the service context is implicitly committed. The transaction handle, if explicitly allocated, may be freed if it is not being used. Resources allocated on the server for this user are freed. The user session handle can be reused in a new call to `OCISessionBegin()`.

If Application Continuity for OCI is enabled, `OCISessionEnd()` implicitly marks the end of an application request. OCI stops recording calls and purges its call history. When using the OCI session pool APIs, it is not necessary to call `OCIRequestBegin()` and `OCIRequestEnd()`.

**Related Topics**

- OCISessionBegin()
- [OCIErrorGet()](miscellaneous-functions.md)

### 25.2.17 OCISessionGet()

Gets a session.

#### Purpose

This session may be a new one with a new underlying connection, or one that is started over a virtual connection from an existing connection pool, or one from an existing session pool. The `mode` that the function is called with determines its behavior.

#### Syntax

    sword OCISessionGet ( OCIenv            *envhp,
                          OCIError          *errhp,
                          OCISvcCtx        **svchp,
                          OCIAuthInfo       *authInfop,
                          OraText           *dbName,
                          ub4                dbName_len,
                          const OraText     *tagInfo,
                          ub4                tagInfo_len,
                          OraText          **retTagInfo,
                          ub4               *retTagInfo_len,
                          boolean           *found,
                          ub4                mode );

#### Parameters

envhp (IN/OUT)
OCI environment handle. For connection pooling and session pooling, the environment handle in which the respective pool was created.

errhp (IN/OUT)
OCI error handle. Multithreaded OCI clients should pass a unique `errhp` to the `OCISessionGet()` call.

svchp (OUT)
Address of an OCI service context pointer. This is filled with a server and session handle.

In the default case, a new session and server handle are allocated, the connection and session are started, and the service context is populated with these handles.

For connection pooling, a new session handle is allocated, and the session is started over a virtual connection from the connection pool.

For session pooling, the service context is populated with an existing session and server handle pair from the session pool.

Do not change any attributes of the server and user and session handles associated with the service context pointer. Doing so results in an error being returned by the `OCIAttrSet()` call.

The only attribute of the service context that can be altered is `OCI_ATTR_STMTCACHESIZE`.

authInfop (IN)
Authentication information handle to be used while getting the session.

In the default and connection pooling cases, this handle can take all the attributes of the session handle.

For session pooling, the authentication information handle is considered only if the session pool mode is not set to `OCI_SPC_HOMOGENEOUS`. In other words, setting the mode to `OCI_SPC_HOMOGENEOUS`, the authentication information is not used, while all other possible specified attributes are used.

The attributes that can be set on the `OCIAuthInfo` handle can be categorized into pre-session-creation attributes and post-session-creation attributes. The pre-session-creation attributes are:

Pre-session-creation attributes

Pre-session-creation attributes are those OCI attributes that must be specified before a session is created. These attributes are used to create a session and cannot be changed after a session is created. The pre-session creation attributes are:

`OCI_ATTR_USERNAME`

`OCI_ATTR_PASSWORD`

`OCI_ATTR_CONNECTION_CLASS`

`OCI_ATTR_PURITY`

`OCI_ATTR_DISTINGUISHED_NAME`

`OCI_ATTR_CERTIFICATE`

`OCI_ATTR_INITIAL_CLIENT_ROLES`

`OCI_ATTR_APPCTX_SIZE`

`OCI_ATTR_EDITION`

`OCI_ATTR_DRIVER_NAME`

Post-session-creation attributes

Post-session-creation attributes are those that can be specified after a session is created. They can be changed freely after a session is created as many times as desired. The following attributes can be set on the `OCISession` handle after the session has been created:

`OCI_ATTR_CLIENT_IDENTIFIER`

`OCI_ATTR_CURRENT_SCHEMA`

`OCI_ATTR_MODULE`

`OCI_ATTR_ACTION`

`OCI_ATTR_DBOP`

`OCI_ATTR_CLIENT_INFO`

`OCI_ATTR_COLLECT_CALL_TIME`

`OCI_ATTR_DEFAULT_LOBPREFETCH_SIZE`

`OCI_ATTR_SESSION_STATE`

**See Also:**

- [Session Pooling in OCI](session-and-connection-pooling.md)

- `cdemosp.c` in the `demo` directory

- [User Session Handle Attributes](handle-and-descriptor-attributes.md) for more information about the attributes

- The Comments section

dbName (IN)
For the default case, this indicates the connect string to use to connect to the Oracle database.

For connection pooling, it indicates the connection pool to retrieve the virtual connection from, to start the session. This value is returned by the `OCIConnectionPoolCreate()` call.

For session pooling, it indicates the pool to get the session from. It is returned by the `OCISessionPoolCreate()` call.

dbName_len (IN)
The length of `dbName`. For session pooling and connection pooling, this value is returned by the call to `OCISessionPoolCreate()` or `OCIConnectionPoolCreate()`, respectively.

tagInfo (IN)
This parameter is used only for session pooling.

This indicates the type of session that the user wants. If you want a default session, you must set this to `NULL`. See the Comments for a detailed explanation of this parameter.

Beginning with 12c Release 2 (12.2), a tag can have multiple properties. This is referred to as a multi-property tag. A multi-property tag is comprised of one or more \<property-name\>=\<property-value\> pairs separated by a semi-colon, where \<property-name\>=\<property-value\> are both strings. See [About Using Tags in Session Pools](session-and-connection-pooling.md) for more information.

tagInfo_len (IN)
The length, in bytes, of `tagInfo`. Used for session pooling only.

retTagInfo (OUT)
This parameter is used only for session pooling. This indicates the type of session that is returned to the user. See the Comments for a detailed explanation of this parameter.

retTagInfo_len (OUT)
The length, in bytes, of `retTagInfo`. Used for session pooling only.

found (OUT)
This parameter is used only for session pooling. If the type of session that the user requested was returned (that is, the value of `tagInfo` and `retTagInfo` is the same), then `found` is set to `TRUE`. Otherwise, `found` is set to `FALSE`.

mode (IN)
The valid modes are:

- `OCI_DEFAULT`

- `OCI_SESSGET_CPOOL`

- `OCI_SESSGET_SPOOL`

- `OCI_SESSGET_CREDPROXY`

- `OCI_SESSGET_CREDEXT` - Supported only for heterogeneous pools.

- `OCI_SESSGET_CUSTOM_POOL`

- `OCI_SESSGET_MULTIPROPERTY_TAG`

- `OCI_SESSGET_PURITY_NEW`

- `OCI_SESSGET_PURITY_SELF`

- `OCI_SESSGET_SPOOL_MATCHANY`

- `OCI_SESSGET_STMTCACHE`

- `OCI_SESSGET_SYSDBA`

In thedefault (nonpooling) case, the following modes are valid:

`OCI_SESSGET_STMTCACHE` - Enables statement caching in the session.

`OCI_SESSGET_CREDEXT` - Returns a session authenticated with external credentials.

`OCI_SESSGET_SYSDBA` - Returns a session with `SYSDBA` privilege for either nonpooling or for session pooling.

For connection pooling, the following modes are valid:

`OCI_SESSGET_CPOOL` - Must be set to use connection pooling.

`OCI_SESSGET_STMTCACHE` - Enables statement caching in the session.

`OCI_SESSGET_CREDPROXY` - Returns a proxy session. The user is given a session that is authenticated by the user name provided in the `OCISessionGet()` call, through the proxy credentials supplied in the `OCIConnectionPoolCreate(`) call.

`OCI_SESSGET_CREDEXT` - Returns a session authenticated with external credentials.

For session pooling, the following modes are valid:

`OCI_SESSGET_SPOOL` - Must be set to use session pooling.

`OCI_SESSGET_SYSDBA` - Returns a session with `SYSDBA` privilege for either nonpooling or for session pooling.

`OCI_SESSGET_CREDEXT` - Returns a session authenticated with external credentials.

`OCI_SESSGET_CREDPROXY` - In this case, the user is given a session that is authenticated by the user name provided in the `OCISessionGet()` call, through the proxy credentials supplied in the `OCISessionPoolCreate()` call.

`OCI_SESSGET_SPOOL_MATCHANY` - Refers to the tagging behavior. If this mode is set, then a session that has a different tag than what was asked for, may be returned. See the Comments section.

`OCI_SESSGET_MULTIPROPERTY_TAG` - Must be set when using multiple properties in case applications previously used a (;) semi-colon character was in a tag name; the semi-colon character is used as a separator for specifying multiple properties. See the Comments section.

For database resident connection pooling, the following modes are valid:

`OCI_SESSGET_MULTIPROPERTY_TAG` - Must be set when using multiple properties in case applications used a (;) semi-colon character was in a tag name; the semi-colon character is used as a separator for specifying multiple properties. See the Comments section.

`OCI_SESSGET_PURITY_SELF` - The application can use a session that has been used before. You can also specify application-specific tags.

`OCI_SESSGET_PURITY_NEW` - The application requires a new session that is not tainted with any prior session state. This is the default.

For custom pools, the following modes are valid:

`OCI_SESSGET_CUSTOM_POOL` - Must be set by applications that are not using OCI session pool, but instead are using custom pools. This attribute is set to support shard key lookup in custom pools.

#### Comments

The tags provide a way for users to customize sessions in the pool. A client can get a default or untagged session from a pool, set certain attributes on the session (such as globalization settings), and return the session to the pool, labeling it with an appropriate tag in the `OCISessionRelease()` call.

The user, or some other user, can request a session with the same attributes, and can do so by providing the same tag in the `OCISessionGet()` call.

If a user asks for a session with tag 'A', and a matching session is not available, an appropriately authenticated untagged session (session with a `NULL` tag) is returned, if such a session is free. If even an untagged session is not free and `OCI_SESSGET_SPOOL_MATCHANY` has been specified, then an appropriately authenticated session with a different tag is returned. If `OCI_SESSGET_SPOOL_MATCHANY` is not set, then a session with a different tag is never returned.

The following code example demonstrates the use of `OCI_ATTR_MODULE` with session pooling.

Using the OCI_ATTR_MODULE Attribute with OCI Session Pooling

    Oratext *module = (Oratext*) "mymodule";
    /* Allocate the pool handle */
     checkerr(errhp,OCIHandleAlloc(envhp,(void**)&poolhp,
                                 OCI_HTYPE_SPOOL,0,0));

     checkerr(errhp,OCISessionPoolCreate(envhp,
                                 errhp,poolhp,&poolname,&pnamelen,
                                 (oratext*)conn_str,
                                 len,min,max,incr,0,0,0,0,OCI_DEFAULT));

     /* Allocate the auth handle for session get */
     checkerr(errhp, OCIHandleAlloc(envhp,
                     (void**)&authp, OCI_HTYPE_AUTHINFO, 0,0));

     checkerr(errhp,OCIAttrSet(authp, OCI_HTYPE_AUTHINFO,
                      username, strlen((char*)username), OCI_ATTR_USERNAME,errhp);
     checkerr(errhp,OCIAttrSet(authp, OCI_HTYPE_AUTHINFO,
                      password, strlen((char*)password), OCI_ATTR_PASSWORD,
                      errhp));

     checkerr(errhp,OCISessionGet(envhp,errhp,
                  &svchp,authp,poolname, pnamelen,0,0,0,0,0,
                  OCI_SESSGET_SPOOL));

    /* Get the user handle from the service context handle */
    checkerr(errhp, OCIAttrGet(svhcp, OCI_HTYPE_SVCCTX, &usrhp_svc,
                   0,OCI_ATTR_SESSION,errhp));

    /* Set module name on the user handle that you obtained */
    checkerr (errhp, OCIAttrSet(usrhp_svc, OCI_HTYPE_SESSION, module,
                   strlen((char*)module), OCI_ATTR_MODULE,errhp));
    /* Make Database calls. */

Restrictions on Attributes Supported for OCI Session Pools

You can use the following pre-session-creation attributes with OCI session pools:

    OCI_ATTR_EDITION
    OCI_ATTR_DRIVER_NAME
    OCI_ATTR_USERNAME,
    OCI_ATTR_PASSWORD,
    OCI_ATTR_CONNECTION_CLASS,
    OCI_ATTR_PURITY

However, `OCI_ATTR_EDITION` and `OCI_ATTR_DRIVERNAME` can only be specified during `OCISessionPoolCreate()` by setting them on the `OCIAuthInfo` handle that is an attribute of `OCISPool` handle. They cannot be specified on the `OCIAuthInfo` handle passed into individual `OCISessionGet()` calls. This ensures that all sessions that are part of an OCI session pool have uniform values for these attributes.

The following code example shows how to use the `OCI_ATTR_EDITION` attribute with an OCI session pool.

Using the OCI_ATTR_EDITION Attribute with OCI Session Pooling

    /* allocate the auth handle to be set on the spool handle */
      checkerr(errhp, OCIHandleAlloc(envhp,(void**)&authp_sp,
                      OCI_HTYPE_AUTHINFO, 0,0));

      /* Set the edition on the auth handle */

      checkerr(errhp,OCIAttrSet(authp_sp, OCI_HTYPE_AUTHINFO,
                       "Patch_Bug_12345", strlen("Patch_Bug_12345"),
                      OCI_ATTR_EDITION,errhp));

    /* Allocate the pool handle */
     checkerr(errhp,OCIHandleAlloc(envhp,(void**)&poolhp,
                                 OCI_HTYPE_SPOOL,0,0));

      /* Set the auth handle created above on the spool handle */
     checkerr(errhp,OCIAttrSet(poolhp, OCI_HTYPE_SPOOL,authp_sp,
                      0,OCI_ATTR_SPOOL_AUTH,errhp));
    checkerr(errhp,OCISessionPoolCreate(envhp,
                                 errhp,poolhp,&poolname,&pnamelen,
                                 (oratext*)conn_str,
                                 len,min,max,incr,0,0,0,0,OCI_DEFAULT));

      /* Allocate the auth handle for session get */
      checkerr(errhp, OCIHandleAlloc(envhp,
                     (void**)&authp_sessget, OCI_HTYPE_AUTHINFO, 0,0));

      checkerr(errhp,OCIAttrSet(authp_sessget, OCI_HTYPE_AUTHINFO,
                      username, strlen((char*)username), OCI_ATTR_USERNAME,errhp);
      checkerr(errhp,OCIAttrSet(authp_sessget, OCI_HTYPE_AUTHINFO,
                      password, strlen((char*)password), OCI_ATTR_PASSWORD,
                      errhp));

      checkerr(errhp,OCISessionGet(envhp,errhp,
                  &svchp,authp_sessget,poolname, pnamelen,0,0,0,0,0,
                  OCI_SESSGET_SPOOL));

You can use all post-session-creation attributes with OCI session pool. However, as a session pool can age out sessions, reuse preexisting sessions in the pool, or re-create new sessions transparently, Oracle recommends that the application explicitly set any post-session-creation attributes that it needs after getting a session from a pool. This ensures that the application logic works irrespective of the specific session returned by the OCI session pool.

When you specify the `OCI_SESSGET_MULTIPROPERTY_TAG`, the parameter `retTagInfo` needs to be interpreted in conjunction with the `found` parameter and the `mode` parameter values specified during `OCISessionGet()`. The following table specifies these semantics:

| Specified Modes                                                                 | refTagInfo Parameter                                                                                          | found Parameter                                                                                                                                                                                                                  |
|:--------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OCI_SESSGET_SPOOL | OCI_SESSGET_MULTIPROPERTY_TAG`                             | All the properties set on the found session are returned as one composite string delimited by (;) semi-colon. | TRUE, only if the found session matches all requested properties and the session has no additional properties set.<br>FALSE, if no matching session was found. In this case, a new session, with no properties set, is returned. |
| `OCI_SESSGET_SPOOL | OCI_SESSGET_MULTIPROPERTY_TAG | OCISESSGET_SPOOL_MATCHANY` | All the properties set on the found session are returned as one composite string delimited by (;) semi-colon. | TRUE, if the found session matches all requested properties (but may have additional properties).<br>FALSE, if the found session did not match at least one property.                                                            |

There is a difference in the manner in which `retTagInfo` is returned in the case of multi-property tags as compared to non multi-property tags. In a non multi-property tag scenario,`retTagInfo` will be the same as the requested tag when the `found` parameter is returned as `TRUE`. Whereas in the case of a multi-property tag, the `retTagInfo` contains the complete set of properties associated with the returned session and further information should be deduced by the application from the `found` flag as shown in the previous table.

Note that `OCI_SESSGET_MULTIPROPERTY_TAG` (with `OCISessionGet()`) or `OCI_SESSRLS_MULTIPROPERTY_TAG` (with `OCISessionRelease()`) are only supported with OCI Session Pool (with or without DRCP). Thus, these modes cannot be used with standalone connections or with OCI Connection Pool.

**Related Topics**

- OCISessionRelease()
- OCISessionPoolCreate()
- OCISessionPoolDestroy()
- [OCIAttrSet()](handle-and-descriptor-functions.md)
- OCIConnectionPoolCreate()

### 25.2.18 OCISessionPoolCreate()

Initializes a session pool for use with OCI session pooling and database resident connection pooling (DRCP).

#### Purpose

It starts `sessMin` number of sessions and connections to the database. Before making this call, make a call to `OCIHandleAlloc()` to allocate memory for the session pool handle.

#### Syntax

    sword OCISessionPoolCreate ( OCIEnv           *envhp,
                                 OCIError         *errhp,
                                 OCISPool         *spoolhp,
                                 OraText         **poolName,
                                 ub4              *poolNameLen,
                                 const OraText    *connStr,
                                 ub4               connStrLen,
                                 ub4               sessMin,
                                 ub4               sessMax,
                                 ub4               sessIncr,
                                 OraText          *userid,
                                 ub4               useridLen,
                                 OraText          *password,
                                 ub4               passwordLen,
                                 ub4               mode );

#### Parameters

envhp (IN)
A pointer to the environment handle in which the session pool is to be created.

errhp (IN/OUT)
An error handle that can be passed to `OCIErrorGet()`.

spoolhp (IN/OUT)
A pointer to the session pool handle that is initialized.

poolName (OUT)
The name of the session pool returned. It is unique across all session pools in an environment. This value must be passed to the `OCISessionGet()` call.

poolNameLen (OUT)
Length of `poolName` in bytes.

connStr (IN)
The TNS alias of the database to connect to.

connStrLen (IN)
The length of `connStr` in bytes.

sessMin (IN)
Specifies the minimum number of sessions in the session pool.

This number of sessions are started by `OCISessionPoolCreate()`. After the sessions are started, sessions are opened only when necessary.

This value is used when `mode` is set to `OCI_SPC_HOMOGENEOUS`. Otherwise, it is ignored.

sessMax (IN)
Specifies the maximum number of sessions that can be opened in the session pool. After this value is reached, no more sessions are opened. The valid values are 1 and higher.

sessIncr (IN)
Allows applications to set the next increment for sessions to be started if the current number of sessions is less than `sessMax`. The valid values are 0 and higher.

userid (IN)
Specifies the userid with which to start the sessions.

**See Also:**

Authentication Note in the Comments Section.

useridLen (IN)
Length of the userid in bytes.

password (IN)
The password for the corresponding userid.

passwordLen (IN)
The length of the password in bytes.

mode (IN)
The modes supported are:

- `OCI_DEFAULT` - For a new session pool creation.

- `OCI_SPC_REINITIALIZE` - After creating a session pool, if you want to change the pool attributes dynamically (change the `sessMin`, `sessMax`, and `sessIncr` parameters), call `OCISessionPoolCreate()` with `mode` set to `OCI_SPC_REINITIALIZE`. When `mode` is set to `OCI_SPC_REINITIALIZE`, then `connStr`, `userid`, and `password` are ignored.

- `OCI_SPC_STMTCACHE` - An OCI statement cache is created for the session pool. If the pool is not created with OCI statement caching turned on, server-side statement caching is automatically used. Note that in general, client-side statement caching gives better performance.

  **See Also:**

  [Statement Caching in OCI](performance-topics.md)

<!-- -->

- `OCI_SPC_HOMOGENEOUS` - All sessions in the pool are authenticated with the user name and password passed to `OCISessionPoolCreate()`. The authentication handle (parameter `authInfop`) passed into `OCISessionGet()` is ignored in this case. Moreover, the `sessMin` and the `SessIncr` values are considered only in this case. No proxy session can be created in this mode. This mode can be used in database resident connection pooling (DRCP).

- `OCI_SPC_NO_RLB` - By default, the runtime connection load balancing is enabled in the session pool if the client and the server are capable of supporting it. To turn it off, use the new mode, `OCI_SPC_NO_RLB` mode of `OCISessionPoolCreate()`. You can only use this mode at the time of pool creation. If this mode is passed for a pool that has been created, an error, ORA-24411, is thrown.

#### Comments

Authentication Note
A session pool can contain two types of connections to the database: direct connections and proxy connections. To make a proxy connection, a user must have Connect through Proxy privilege.

**See Also:**

For more information about proxy connections, see

- [Client Access Through a Proxy](oci-programming-basics.md)

- [Oracle Database SQL Language Reference](../sqlrf/ALTER-USER.md)

When the session pool is created, the `userid` and `password` may or may not be specified. If these values are `NULL`, no proxy connections can exist in this pool. If `mode` is set to `OCI_SPC_HOMOGENEOUS`, no proxy connection can exist.

A `userid` and `password` pair may also be specified through the authentication handle in the `OCISessionGet()` call. If this call is made with `mode` set to `OCI_SESSGET_CREDPROXY`, then the user is given a session that is authenticated by the `userid` provided in the `OCISessionGet()` call, through the proxy credentials supplied in the `OCISessionPoolCreate()` call. In this case, the password in the `OCISessionGet()` call is ignored.

If `OCISessionGet()` is called with `mode` not set to `OCI_SESSGET_CREDPROXY`, then the user gets a direct session that is authenticated by the credentials provided in the `OCISessionGet()` call. If none have been provided in this call, the user gets a session authenticated by the credentials in the `OCISessionPoolCreate()` call.

#### Example

The following code example shows how to disable runtime load balancing.

Disabling Runtime Load Balancing

    OCISessionPoolCreate(envhp, errhp, spoolhp, (OraText **)&poolName,
                         (ub4 *)&poolNameLen,
                         database, (ub4) strlen ((const signed char *) database),
                         sessMin, sessMax, sessIncr, (OraText *) appusername,
                         (ub4) strlen ((const signed char *) appusername),
                         (OraText *) apppassword,
                         (ub4) strlen ((const signed char *) apppassword),
                         OCI_SPC_HOMOGENEOUS | OCI_SPC_NO_RLB);

**Related Topics**

- OCISessionRelease()
- OCISessionGet()
- OCISessionPoolDestroy()
- [OCIHandleAlloc()](handle-and-descriptor-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 25.2.19 OCISessionPoolDestroy()

Destroys a session pool.

#### Purpose

Destroys a session pool.

#### Syntax

    sword OCISessionPoolDestroy ( OCISPool     *spoolhp,
                                  OCIError     *errhp,
                                  ub4           mode );

spoolhp (IN/OUT)
The session pool handle for the session pool to be destroyed.

errhp (IN/OUT)
An error handle that can be passed to `OCIErrorGet()`.

mode (IN)
Currently, `OCISessionPoolDestroy()` supports modes `OCI_DEFAULT` and `OCI_SPD_FORCE`.

If this call is made with `mode` set to `OCI_SPD_FORCE`, and there are active sessions in the pool, the sessions are closed and the pool is destroyed. However, if this mode is not set, and there are busy sessions in the pool, an error is returned.

**Related Topics**

- OCISessionPoolCreate()
- OCISessionRelease()
- OCISessionGet()

### 25.2.20 OCISessionRelease()

Releases a session that was retrieved using `OCISessionGet()`.

#### Purpose

Releases a session that was retrieved using `OCISessionGet()`. The exact behavior of this call is determined by the `mode` in which the corresponding `OCISessionGet()` function was called. In the default case, it closes the session or connection. For connection pooling, it closes the session and returns the connection to the pool. For session pooling, it returns the session or connection pair to the pool, and any pending transaction is committed.

#### Syntax

    sword OCISessionRelease ( OCISvcCtx       *svchp,
                              OCIError        *errhp,
                              OraText         *tag,
                              ub4              tag_len,
                              ub4              mode );

#### Parameters

svchp (IN)
The service context that was populated during the corresponding `OCISessionGet()` call.

In the default case, the session and connection associated with this handle is closed.

In the connection pooling case, the session is closed and the connection released to the pool.

For session pooling, the session or connection pair associated with this service context is released to the pool.

errhp (IN/OUT)
The OCI error handle.

tag (IN)
This parameter is used only for session pooling.

This parameter is ignored unless mode `OCI_SESSRLS_RETAG` is specified. In this case, the session is labeled with this tag and returned to the pool. If this is `NULL`, then the session is not tagged.

tag_len (IN)
This parameter is used only for session pooling.

Length of the tag. This is ignored unless mode `OCI_SESSRLS_RETAG` is set.

mode (IN)
The supported modes are:

- `OCI_DEFAULT`

- `OCI_SESSRLS_DROPSESS`

- `OCI_SESSRLS_MULTIPROPERTY_TAG`

- `OCI_SESSRLS_RETAG`

You can only use `OCI_DEFAULT` for the default case and for connection pooling.

`OCI_SESSRLS_DROPSESS` and `OCI_SESSRLS_RETAG` are only used for session pooling.

When `OCI_SESSRLS_DROPSESS` is specified, the session is removed from the session pool.

Set `OCI_SESSRLS_MULTIPROPERTY_TAG`, if the tag is a multi-property tag. For more information, see [Multi-Property Tags](session-and-connection-pooling.md).

The tag on the session is altered if and only if `OCI_SESSRLS_RETAG` is set. If this mode is not set, the `tag` and `tag_len` parameters are ignored.

#### Comments

Be careful to pass in the correct tag when using the `tag` parameter. If a default session is requested and the user sets certain properties on this session (probably through an `ALTER SESSION` command), then the user must label this session appropriately by tagging it as such.

If, however, the user requested a tagged session and got one, and has changed the properties on the session, then the user must pass in a different tag if appropriate.

For the correct working of the session pool layer, the application developer must be very careful to pass in the correct tag to the `OCISessionGet()` and `OCISessionRelease()` calls.

**Related Topics**

- OCISessionGet()
- OCISessionPoolCreate()
- OCISessionPoolDestroy()
- OCILogon2()

### 25.2.21 OCITerminate()

Detaches the process from the shared memory subsystem and releases the shared memory.

#### Purpose

Detaches the process from the shared memory subsystem and releases the shared memory.

#### Syntax

    sword OCITerminate ( ub4    mode);

#### Parameters

mode (IN)
Call-specific mode. Valid value:

- `OCI_DEFAULT` - Executes the default call.

#### Comments

`OCITerminate()` should be called only once for each process and is the counterpart of the `OCIEnvCreate()`, `OCIEnvNlsCreate()`, deprecated `OCIInitialize()` calls. The call tries to detach the process from the shared memory subsystem and shut it down. It also performs additional process cleanup operations. When two or more processes connecting to the same shared memory call `OCITerminate()` simultaneously, the fastest one releases the shared memory subsystem completely and the slower ones must terminate.

**Related Topics**

- [OCIInitialize()](deprecated-oci-functions.md)
- OCIEnvCreate()
- OCIEnvNlsCreate()
