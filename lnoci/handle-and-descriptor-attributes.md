This appendix describes the attributes for OCI handles and descriptors.

OCI handles and descriptors can be read with `OCIAttrGet()`, and modified with `OCIAttrSet()`.

This appendix contains these topics:

- Conventions

- Environment Handle Attributes

- Error Handle Attributes

- Service Context Handle Attributes

- Server Handle Attributes

  - Authentication Information Handle Attributes

  - User Session Handle Attributes

- Administration Handle Attributes

- Connection Pool Handle Attributes

- Session Pool Handle Attributes

- Transaction Handle Attributes

- Statement Handle Attributes

- Bind Handle Attributes

- Define Handle Attributes

- Describe Handle Attributes

- Parameter Descriptor Attributes

- Shard Instance Descriptor Attributes

- SODA Document Handle Attributes

- SODA Collection Handle Attributes

- SODA Output Options Handle Attributes

- SODA Operation Options Handle Attributes

- LOB Descriptor and LOB Locator Attributes

- Complex Object Attributes

  - Complex Object Retrieval Handle Attributes

  - Complex Object Retrieval Descriptor Attributes

- Database Advanced Queuing Descriptor Attributes

  - OCIAQEnqOptions Descriptor Attributes

  - OCIAQDeqOptions Descriptor Attributes

  - OCIAQMsgProperties Descriptor Attributes

  - OCIAQAgent Descriptor Attributes

  - OCIServerDNs Descriptor Attributes

- Subscription Handle Attributes

  - Continuous Query Notification Attributes

  - Continuous Query Notification Descriptor Attributes

  - Notification Descriptor Attributes

  - Invalidated Query Attributes

- Direct Path Loading Handle Attributes

  - Direct Path Context Handle (OCIDirPathCtx) Attributes

  - Direct Path Function Context Handle (OCIDirPathFuncCtx) Attributes

  - Direct Path Function Column Array Handle (OCIDirPathColArray) Attributes

  - Direct Path Stream Handle (OCIDirPathStream) Attributes

  - Direct Path Column Parameter Attributes

- Process Handle Attributes

- Event Handle Attributes

### A.1 Conventions

For each handle type, the attributes that can be read or changed are listed.

Each attribute listing includes the following information:

Mode
The following modes are valid:

READ - The attribute can be read using `OCIAttrGet()`.

WRITE - The attribute can be modified using `OCIAttrSet()`.

READ/WRITE - The attribute can be read using `OCIAttrGet()`, and it can be modified using `OCIAttrSet()`.

Description
This is a description of the purpose of the attribute.

Attribute Data Type
This is the data type of the attribute. If necessary, a distinction is made between the data type for READ and WRITE modes.

Valid Values
In some cases, only certain values are allowed, and they are listed here.

Example
In some cases an example is included.

### A.2 Environment Handle Attributes

Lists and describes environment handle attributes.

The following attributes are used for the environment handle.

#### OCI_ATTR_ALLOC_DURATION

Mode
READ/WRITE

Description
This attribute sets the value of `OCI_DURATION_DEFAULT` for allocation durations for the application associated with the environment handle.

Attribute Data Type
`OCIDuration */OCIDuration`

#### OCI_ATTR_BIND_DN

Mode
READ/WRITE

Description
The login name (DN) to use when connecting to the LDAP server.

Attribute Data Type
`oratext **/oratext *`

#### OCI_ATTR_CACHE_ARRAYFLUSH

Mode
READ/WRITE

Description
When this attribute is set to `TRUE`, during `OCICacheFlush()` the objects that belong to the same table are flushed, which can considerably improve performance. An attribute value of `TRUE` should only be used when the order in which the objects are flushed is not important. When the attribute value is set to `TRUE`, it is not guaranteed that the order in which the objects are marked dirty is preserved.

**See Also:**

[Object Cache Parameters](object-advanced-topics-in-oci.md) and [About Flushing Changes to the Server](object-advanced-topics-in-oci.md)

Attribute Data Type
`boolean */boolean `

#### OCI_ATTR_CACHE_MAX_SIZE

Mode
READ/WRITE

Description
Sets the maximum size (high watermark) for the client-side object cache as a percentage of the optimal size. Usually you can set the value at 10%, the default, of the optimal size, `OCI_ATTR_CACHE_OPT_SIZE`. Setting this attribute to 0 results in a value of 10 being used. The object cache uses the maximum and optimal values for freeing unused memory in the object cache.

**See Also:**

[Object Cache Parameters](object-advanced-topics-in-oci.md)

Attribute Data Type
`ub4 */ub4`

#### OCI_ATTR_CACHE_OPT_SIZE

Mode
READ/WRITE

Description
Sets the optimal size for the client-side object cache in bytes. The default value is 8 megabytes (MB). Setting this attribute to 0 results in a value of 8 MB being used.

**See Also:**

[Object Cache Parameters](object-advanced-topics-in-oci.md)

Attribute Data Type
`ub4 */ub4`

#### OCI_ATTR_ENV_CHARSET_ID

Mode
READ

Description
Local (client-side) character set ID. Users can update this setting only after creating the environment handle but before calling any other OCI functions. This restriction ensures the consistency among data and metadata in the same environment handle. When character set ID is UTF-16, an attempt to get this attribute is invalid.

Attribute Data Type
`ub2 *`

#### OCI_ATTR_ENV_NCHARSET_ID

Mode
READ

Description
Local (client-side) national character set ID. Users can update this setting only after creating the environment handle but before calling any other OCI functions. This restriction ensures the consistency among data and metadata in the same environment handle. When character set ID is UTF-16, an attempt to get this attribute is invalid.

Attribute Data Type
`ub2 *`

#### OCI_ATTR_ENV_NLS_LANGUAGE

Mode
READ/WRITE

Description
The name of the language used for the database sessions created from the current environment handle. While getting this value, users should pass an allocated buffer, which will be filled with the language name.

Attribute Data Type
`oratext **` or `oratext *`

#### OCI_ATTR_ENV_NLS_TERRITORY

Mode
READ/WRITE

Description
The name of the territory used for the database sessions created from the current environment handle. While getting this value, users should pass an allocated buffer, which will be filled with the territory name.

Attribute Data Type
`oratext **` or `oratext *`

#### OCI_ATTR_ENV_UTF16

Mode
READ

Description
Encoding method is UTF-16. The value 1 means that the environment handle is created when the encoding method is UTF-16, whereas 0 means that it is not. This attribute value can only be set by the call to `OCIEnvCreate()` and cannot be changed later.

Attribute Data Type
`ub1 *`

#### OCI_ATTR_EVTCBK

Mode
WRITE

Description
This attribute registers an event callback function.

**See Also:**

[HA Event Notification](high-availability-in-oci.md)

Attribute Data Type
`OCIEventCallback`

#### OCI_ATTR_EVTCTX

Mode
WRITE

Description
This attribute registers a context passed to an event callback.

**See Also:**

[HA Event Notification](high-availability-in-oci.md)

Attribute Data Type
void \*

#### OCI_ATTR_HEAPALLOC

Mode
READ

Description
The current size of the memory allocated from the environment handle. This may help you track where memory is being used most in an application.

Attribute Data Type
`ub4 *`

#### OCI_ATTR_LDAP_AUTH

Mode
READ/WRITE

Description
The authentication mode. The following are the valid values:

0x0: No authentication; anonymous bind.

0x1: Simple authentication; user name and password authentication.

0x5: SSL connection with no authentication.

0x6: SSL: only server authentication required.

0x7: SSL: both server authentication and client authentication are required.

0x8: Authentication method is determined at run time.

Attribute Data Type
`ub2 */ub2`

#### OCI_ATTR_LDAP_CRED

Mode
READ/WRITE

Description
If the authentication method is "simple authentication" (user name and password authentication), then this attribute holds the password to use when connecting to the LDAP server.

Attribute Data Type
`oratext **/oratext *`

#### OCI_ATTR_LDAP_CTX

Mode
READ/WRITE

Description
The administrative context of the client. This is usually the root of the Oracle Database LDAP schema in the LDAP server.

Attribute Data Type
`oratext **/oratext *`

#### OCI_ATTR_LDAP_HOST

Mode
READ/WRITE

Description
The name of the host on which the LDAP server runs.

Attribute Data Type
`oratext **/oratext *`

#### OCI_ATTR_LDAP_PORT

Mode
READ/WRITE

Description
The port on which the LDAP server is listening.

Attribute Data Type
`ub2 */ub2`

#### OCI_ATTR_SODA_METADATA_CACHE

Mode
READ/WRITE

<!-- -->

Description
By default, SODA metadata caching is not enabled. If this attribute value is set to `TRUE`, then it turns on caching of collection descriptors. If the value is set to `FALSE`, then it disables and purges any pre-existing collection descriptor cache entries.

<!-- -->

Attribute Data Type
`boolean */boolean`

#### OCI_ATTR_OBJECT

Mode
READ

Description
Returns `TRUE` if the environment was initialized in object mode.

Attribute Data Type
`boolean *`

#### OCI_ATTR_PINOPTION

Mode
READ/WRITE

Description
This attribute sets the value of `OCI_PIN_DEFAULT` for the application associated with the environment handle.

For example, if `OCI_ATTR_PINOPTION` is set to `OCI_PIN_RECENT`, and `OCIObjectPin()` is called with the `pin_option` parameter set to `OCI_PIN_DEFAULT`, the object is pinned in `OCI_PIN_RECENT` mode.

Attribute Data Type
`OCIPinOpt */OCIPinOpt`

#### OCI_ATTR_OBJECT_NEWNOTNULL

Mode
READ/WRITE

Description
When this attribute is set to `TRUE`, newly created objects have non-`NULL` attributes.

**See Also:**

[About Creating Objects](oci-object-relational-programming.md)

Attribute Data Type
`boolean */boolean`

#### OCI_ATTR_OBJECT_DETECTCHANGE

Mode
READ/WRITE

Description
When this attribute is set to `TRUE`, applications receive an ORA-08179 error when attempting to flush an object that has been modified in the server by another committed transaction.

**See Also:**

[About Implementing Optimistic Locking](object-advanced-topics-in-oci.md)

Attribute Data Type
`boolean */boolean`

#### OCI_ATTR_PIN_DURATION

Mode
READ/WRITE

Description
This attribute sets the value of `OCI_DURATION_DEFAULT` for pin durations for the application associated with the environment handle.

Attribute Data Type
`OCIDuration */OCIDuration`

#### OCI_ATTR_SHARED_HEAPALLOC

Mode
READ

Description
Returns the size of the memory currently allocated from the shared pool. This attribute works on any environment handle, but the process must be initialized in shared mode to return a meaningful value. This attribute is read as follows:

    ub4 heapsz = 0;
    OCIAttrGet((void *)envhp, (ub4)OCI_HTYPE_ENV,
               (void *) &heapsz, (ub4 *) 0,
               (ub4)OCI_ATTR_SHARED_HEAPALLOC, errhp);

Attribute Data Type
`ub4 *`

#### OCI_ATTR_SUBSCR_PORTNO

Mode
READ/WRITE

Description
The client port used to receive notifications. It is set on the client's environment handle.

Attribute Data Type
`ub4 *`

#### OCI_ATTR_WALL_LOC

Mode
READ/WRITE

Description
If the authentication method is SSL authentication, this attribute contains the location of the client wallet.

Attribute Data Type
`oratext **/oratext *`

### A.3 Error Handle Attributes

Lists and describes error handle attributes.

The following attributes are used for the error handle.

#### OCI_ATTR_DML_ROW_OFFSET

Mode
READ

Description
Returns the offset (into the DML array) at which the error occurred.

Attribute Data Type
`ub4 *`

#### OCI_ATTR_ERROR_IS_RECOVERABLE

Mode
READ

Description
This attribute is set to `TRUE` if the error in the error handle is recoverable. If the error is not recoverable, it is set to `FALSE`.

Attribute Data Type
`Boolean *`

### A.4 Service Context Handle Attributes

Lists and describes service context handle attributes.

The following attributes are used for service context handle.

#### OCI_ATTR_CALL_TIMEOUT

Mode
READ/WRITE

Description
A database round-trip call using the service context times out within the specified time in milli-seconds, if not completed. When the call times out, a network timeout error is returned. This attribute can be set dynamically. Setting this value stays effective for all subsequent round-trip calls executed using the same service context until a different value is set. To remove the timeout, the value must be set to 0.

This is a client-only change. So, for using this feature, you must use a release 18c client. This feature is database version agnostic, that is, you can use this feature with any supported version of the database.

Timeout values set in different places are effective according to the following order of precedence (where 1 is the highest precedence):

1.  Call timeout set on the OCI handle using `OCIAttrSet()`.

2.  Timeout set with the OCI attributes, `OCI_ATTR_SEND_TIMEOUT` and `OCI_ATTR_RECEIVE_TIMEOUT`.

3.  Timeout set in the `sqlnet.ora` file with the parameters, `SQLNET.RECV_TIMEOUT` and `SQLNET.SEND_TIMEOUT`.

Error returned to the application:

    ORA-03156 "OCI call timed out"

The Call timeout is on each individual round-trip between OCI and Oracle Database. Each OCI method or operation may require zero or more round-trips to Oracle Database. The timeout value applies to each round-trip individually, not to the sum of all round-trips. Time spent processing in OCI before or after the completion of each round-trip is not counted.

- If the time from the start of any round-trip to the completion of the same round-trip exceeds the timeout value, then the operation is halted and an Oracle error is returned.

- In the case where an OCI operation requires more than one round-trip and each round-trip takes less than the timeout value, then no timeout occurs, even if the sum of all round-trip calls exceeds the timeout value.

- If no round-trip is required, the operation will never be interrupted.

After a timeout occurs, OCI attempts to clean up the internal connection state. The cleanup is allowed to take another timeout value. If the cleanup was successful, an `ORA-3156` will be returned and the application can continue to use the connection.

For small values of the timeout value, the connection cleanup may not complete successfully within the additional timeout period. In this case an `ORA-3113` is returned, and the following OCI call using the same connection gets an ORA-3114 and the connection will no longer be usable. It should be released.

Alternatively, the `OCI_ATTR_BREAK_ON_NET_TIMEOUT` attribute can additionally be set to `FALSE`. This setting drops the connection, eliminating calls to `OCIBreak()` and `OCIReset()` when a timeout occurs.

**Note:**

When call timeout is set, then ora-12161 may be returned while reading a large amount of data. This error must be treated as ora-3136.

Attribute Data Type
`ub4*/ub4`

Example
    static void func1( )
    {
    sword status = 0;
      OCIStmt *stmthp = (OCIStmt *)0;
      OraText *sqlStmt = (OraText *)"SELECT EMPNO FROM SCOTT.EMP";
      ub4 set_timeout= 200; /* in milliseconds */
      ub4 get_timeout = 0;

      Checkerr (errhp, \
          OCIStmtPrepare2 ((OCISvcCtx *)svchp, (OCIStmt **)&stmthp, \
          (OCIError *)errhp, (OraText *)sqlStmt, (ub4)strlen((char *)sqlStmt), \
          (OraText *)NULL, (ub4) 0, (ub4)OCI_NTV_SYNTAX, (ub4)OCI_DEFAULT), \
          (OraText *)"OCIStmtPrepare2");

      /* Set the call Timeout (in milliseconds) */
        Checkerr (errhp,
        OCIAttrSet(svchp, (ub4) OCI_HTYPE_SVCCTX,
         (dvoid *) &set_timeout, (ub4) 0,
         (ub4) OCI_ATTR_CALL_TIMEOUT, errhp),
         "OCIAttrSet OCI_ATTR_CALL_TIMEOUT");

        if ((status = OCIStmtExecute ((OCISvcCtx *)svchp, \
          (OCIStmt *)stmthp, (OCIError *)errhp, (ub4)1, (ub4)0, \
          (OCISnapshot *)0, (OCISnapshot *)0, (ub4)OCI_DEFAULT)) \
          != OCI_SUCCESS)
        {
          printf ( "OCIStmtExecute Failed with timeout: %dms\n", set_timeout);
          Checkerr (errhp, status,(OraText *)"OCIStmtExecute");
        }

      /* Get the call Timeout (in milliseconds) */
        Checkerr (errhp,
        OCIAttrGet(svchp, (ub4) OCI_HTYPE_SVCCTX,
         (dvoid *) &get_timeout, (ub4) 0,
         (ub4) OCI_ATTR_CALL_TIMEOUT, errhp),
         "OCIAttrGet OCI_ATTR_CALL_TIMEOUT");

      Checkerr (errhp, \
          OCIStmtRelease ((OCIStmt *)stmthp, (OCIError *)errhp,(dvoid *)NULL, \
          0, OCI_DEFAULT), (oratext *)"StmtRelease");
    } /* End of func1 */

#### OCI_ATTR_ENV

Mode
READ

Description
Returns the environment context associated with the service context.

Attribute Data Type
`OCIEnv **`

#### OCI_ATTR_INSTNAME

See the `OCI_ATTR_INSTNAME` attribute in Shard Instance Descriptor Attributes for more information about its use on the service context.

#### OCI_ATTR_IN_V8_MODE

Mode
READ

Description
Allows you to determine whether an application has switched to Oracle release 7 mode (for example, through an `OCISvcCtxToLda()` call). A nonzero (`TRUE`) return value indicates that the application is currently running in Oracle release 8 mode, a zero (false) return value indicates that the application is currently running in Oracle release 7 mode.

Attribute Data Type
`ub1 *`

Example
The following code sample shows how this attribute is used:

    in_v8_mode = 0;
    OCIAttrGet ((void *)svchp, (ub4)OCI_HTYPE_SVCCTX, (ub1 *)&in_v8_mode,
                        (ub4) 0, OCI_ATTR_IN_V8_MODE, errhp);
    if (in_v8_mode)
         fprintf (stdout, "In V8 mode\n");
    else
         fprintf (stdout, "In V7 mode\n");

#### OCI_ATTR_MAX_CHARSET_RATIO

Mode
READ

Description
Returns the maximum character set expansion ratio from server to client character set. Using these attributes is useful in scenarios where there are different character sets between server and client. This is useful to allocate optimal memory of buffers before conversion so that when data is returned from the database, sufficient space can be allocated to hold it.

Attribute Data Type
ub4 \*

Example
    size_t   cratio;
    OCIAttrGet((void *)svchp, (ub4)OCI_HTYPE_SVCCTX, (size_t *)&cratio, (ub4) 0, OCI_ATTR_MAX_CHARSET_RATIO, errhp);
    printf("Conversion ratio from server to client character set is %d\n", cratio);

#### OCI_ATTR_MAX_NCHARSET_RATIO

Mode
READ

Description
Returns the maximum character set expansion ratio from server to client national character set. Using these attributes is useful in scenarios where there are different national character sets between server and client. This is useful to allocate optimal memory of buffers before conversion so that when data is returned from the database, sufficient space can be allocated to hold it.

Attribute Data Type
ub4 \*

Example
    size_t   cratio;
    OCIAttrGet((void *)svchp, (ub4)OCI_HTYPE_SVCCTX, (size_t *)&cratio, (ub4) 0, OCI_ATTR_MAX_NCHARSET_RATIO, errhp);
    printf("Conversion ratio from server to client ncharset is %d\n", cratio);

#### OCI_ATTR_SERVER

Mode
READ/WRITE

Description
When read, returns the pointer to the server context attribute of the service context.

When changed, sets the server context attribute of the service context.

Attribute Data Type
`OCIServer **` / `OCIServer * `

#### OCI_ATTR_SESSION

Mode
READ/WRITE

Description
When read, returns the pointer to the authentication context attribute of the service context.

When changed, sets the authentication context attribute of the service context.

Attribute Data Type
`OCISession **`/ `OCISession *`

#### OCI_ATTR_STMTCACHE_CBK

Mode
READ/WRITE

Description
Used to get and set the application's callback function on the `OCISvcCtx` handle. This function, if registered on `OCISvcCtx`, is called when a statement in the statement cache belonging to this service context is purged or when the session is ended.

The callback function must be of this prototype:

    sword (*OCICallbackStmtCache)(void *ctx, OCIStmt *stmt, ub4 mode)

`ctx`: IN argument. This is the same as the context the application has set on the current statement handle.

`stmt`: IN argument. This is the statement handle that is being purged from the cache.

`mode`: IN argument. This is the mode in which the callback function is being called. Currently only one value is supported, `OCI_CBK_STMTCACHE_STMTPURGE`, which means the callback is being called during purging of the current statement.

Attribute Data Type
    sword (*OCICallbackStmtCache)(void *ctx, OCIStmt *stmt, ub4 mode)

#### OCI_ATTR_STMTCACHESIZE

Mode
READ/WRITE

Description
The default value of the statement cache size is 20 statements, for a statement cache-enabled session. The user can increase or decrease this value by setting this attribute on the service context handle. This attribute can also be used to enable or disable statement caching for the session, pooled or nonpooled. Statement caching can be enabled by setting the attribute to a nonzero size and disabled by setting it to zero.

Attribute Data Type
`ub4 *`/ `ub4`

#### OCI_ATTR_TRANS

Mode
READ/WRITE

Description
When read, returns the pointer to the transaction context attribute of the service context.

When changed, sets the transaction context attribute of the service context.

Attribute Data Type
`OCITrans **` / `OCITrans *`

#### OCI_ATTR_VARTYPE_MAXLEN_COMPAT

Mode
READ

Description
Returns `OCI_ATTR_MAXLEN_COMPAT_EXTENDED` if the `init.ora` parameter `max_string_size = extended` or returns `OCI_ATTR_MAXLEN_COMPAT_STANDARD` if the `init.ora` parameter `max_string_size = standard`.

Attribute Data Type
`ub1 *`

#### OCI_ATTR_SESSGET_FLAGS

Mode
READ

<!-- -->

Description
Specifies the type of connection returned by `OCISessionGet`.

<!-- -->

Attribute Data Type
ub4

<!-- -->

Example
    ub4 sessgetFlags = 0;
    if (!(lstat = OCISessionGet(envhp, errhp2, &svchp, authp,(OraText  *)poolName,
            (ub4)poolNameLen, NULL, 0,  NULL, NULL, NULL,
             OCI_SESSGET_SPOOL)))
    {
      checkerr(errhp2, OCIAttrGet(svchp, OCI_HTYPE_SVCCTX,
        (dvoid *) &sessgetFlags, NULL, OCI_ATTR_SESSGET_FLAGS, errhp2));
      if  (sessgetFlags & OCI_SESSGET_FLAGS_NEW)
      {
        printf("Yes,  it's new connection\n");
      }
    }

Valid Flags
Following flags are set:

- `OCI_SESSGET_FLAGS_NEW`: A new connection is created and this is not an existing connection from the pool.
- `OCI_SESSGET_FLAGS_POOLED_SERVER`: Connection is to a Database Resident Connection Pool.
- `OCI_SESSGET_FLAGS_RAC_DATA_AFFN`: Connection is to a RAC Affinity Enabled Database.
- `OCI_SESSGET_FLAGS_SHARD`: Connection is to a sharded database.

### A.5 Server Handle Attributes

Lists and describes server handle attributes.

The following attributes are used for the server handle.

**See Also:**

The following event handle attributes are also available for the server handle:

- OCI_ATTR_DBDOMAIN

- OCI_ATTR_DBNAME

- OCI_ATTR_INSTNAME

- OCI_ATTR_INSTSTARTTIME

- OCI_ATTR_SERVICENAME

[OCIXStreamOutLCRReceive()](oci-XStream-functions.md) for more information about using the following attributes

#### OCI_ATTR_ACCESS_BANNER

Mode
READ

Description
Displays an unauthorized access banner from a file.

Attribute Data Type
oratext \*\*

#### OCI_ATTR_BREAK_ON_NET_TIMEOUT

Mode
READ/WRITE

Description
This attribute determines whether OCI sends a break after a network time out or not.

Attribute Data Type
ub1 \*

#### OCI_ATTR_ENV

Mode
READ

Description
Returns the environment context associated with the server context.

Attribute Data Type
`OCIEnv **`

#### OCI_ATTR_EXTERNAL_NAME

Mode
READ/WRITE

Description
The external name is the user-friendly global name stored in `sys.props$.value$,` where `name = 'GLOBAL_DB_NAME'`. It is not guaranteed to be unique unless all databases register their names with a network directory service.

Database names can be exchanged with the server for distributed transaction coordination. Server database names can only be accessed only if the database is open at the time the `OCISessionBegin()` call is issued.

Attribute Data Type
`oratext **`/ `oratext *`

#### OCI_ATTR_FOCBK

Mode
READ/WRITE

Description
Sets the failover callback to the callback definition structure of type `OCIFocbkStruct` as part of failover callback registration and unregistration on the server context handle.

**See Also:**

[Transparent Application Failover in OCI](high-availability-in-oci.md)

Attribute Data Type
`OCIFocbkStruct *`

#### OCI_ATTR_INTERNAL_NAME

Mode
READ/WRITE

Description
Sets the client database name that is recorded when performing global transactions. The DBA can use the name to track transactions that may be pending in a prepared state due to failures.

Attribute Data Type
`oratext **` / `oratext *`

#### OCI_ATTR_INSTNAME

See the `OCI_ATTR_INSTNAME` attribute in Shard Instance Descriptor Attributes for more information about its use as a server handle attribute.

#### OCI_ATTR_IN_V8_MODE

Mode
READ

Description
Allows you to determine whether an application has switched to Oracle release 7 mode (for example, through an `OCISvcCtxToLda()` call). A nonzero (`TRUE`) return value indicates that the application is currently running in Oracle release 8 mode, a zero (`FALSE`) return value indicates that the application is currently running in Oracle release 7 mode.

Attribute Data Type
`ub1 *`

#### OCI_ATTR_NONBLOCKING_MODE

Mode
READ/WRITE

Description
This attribute determines the blocking mode. When read, the attribute value returns `TRUE` if the server context is in nonblocking mode. When set, it toggles the nonblocking mode attribute. You must set this attribute only after `OCISessionBegin()` or `OCILogon2()` has been called. Otherwise, an error is returned.

Attribute Data Type
ub1 \*/ub1

**See Also:**

[Nonblocking Mode in OCI](oci-programming-basics.md)

#### OCI_ATTR_RECEIVE_TIMEOUT

Mode
READ/WRITE

Description
Time specified in milliseconds that a client waits for response data from the database server. When set to a value of zero, the timeout functionality is disabled and the client may wait a long period of time for a response from a database server.

The semantics of this attribute is the same as that of `SQLNET.RECV_TIMEOUT` that can be specified in the `sqlnet.ora` file. When set on the server handle, the value overrides the one specified in the `sqlnet.ora` file.

Attribute Data Type
`ub4*/ub4`

#### OCI_ATTR_SEND_TIMEOUT

Mode
READ/WRITE

Description
Time specified in milliseconds that a client waits to complete send operations to the database server. When set to a value of zero, the timeout functionality is disabled and the client may wait a long period of time to complete sending the data to the database server.

The semantics of this attribute is the same as that of `SQLNET.SEND_TIMEOUT` that can be specified in the `sqlnet.ora` file. When set on the server handle, the value overrides the one specified in the `sqlnet.ora` file.

Attribute Data Type
`ub4*/ub4`

#### OCI_ATTR_SERVER_GROUP

Mode
READ/WRITE

Description
An alphanumeric string not exceeding 30 characters specifying the server group. This attribute can only be set after calling `OCIServerAttach()`.

**See Also:**

[Password and Session Management](managing-scalable-platforms.md)

Attribute Data Type
`oratext **/oratext *`

#### OCI_ATTR_SERVER_STATUS

Mode
READ

Description
Returns the current status of the connection by doing a light weight connection health check. Values are:

- `OCI_SERVER_NORMAL` - The connection is alive.

- `OCI_SERVER_NOT_CONNECTED` - The connection has been terminated.

Attribute Data Type
ub4 \*

Example
The following code sample shows how this parameter is used:

    ub4 serverStatus = 0
    OCIAttrGet((void *)srvhp, OCI_HTYPE_SERVER,
            (void *)&serverStatus, (ub4 *)0, OCI_ATTR_SERVER_STATUS, errhp);
    if (serverStatus == OCI_SERVER_NORMAL)
            printf("Connection is up.\n");
    else if (serverStatus == OCI_SERVER_NOT_CONNECTED)
            printf("Connection is down.\n");

#### OCI_ATTR_TAF_ENABLED

Mode
READ

Description
Set to `TRUE` if the server handle is TAF-enabled and `FALSE` if not.

**See Also:**

[Custom Pooling: Tagged Server Handles](high-availability-in-oci.md)

Attribute Data Type
boolean \*

#### OCI_ATTR_USER_MEMORY

Mode
READ

Description
If the handle was allocated with extra memory, this attribute returns a pointer to the user memory. A `NULL` pointer is returned for those handles not allocated with extra memory.

**See Also:**

[Custom Pooling: Tagged Server Handles](high-availability-in-oci.md)

Attribute Data Type
void \*

#### A.5.1 Authentication Information Handle Attributes

Lists and describes authentication information handle attributes.

These attributes also apply to the user session handle.

**See Also:**

User Session Handle Attributes

##### OCI_ATTR_IAM_PRIVKEY

Mode
WRITE

Description
This attribute specifies the private key value to be used for the connection creation when using IAM-based token authentication. It can be set on both authentication handles (`OCIAuthInfo`) and user session handles (`OCISession`).

Attribute Data type
`oratext *`

Example Usage
                                                                                                                                                                                                                                                                                                                                                                                                                                    1`
    OCIAttrSet((dvoid *) usrhp, (ub4) OCI_HTYPE_SESSION,
               (dvoid *) privKeyBuf, (ub4) privKeyLength,
               OCI_ATTR_IAM_PRIVKEY, errhp);

    OCIAttrSet((dvoid *) authp, (ub4) OCI_HTYPE_AUTHINFO,
               (dvoid *) privKeyBuf, (ub4) privKeyLength,
               OCI_ATTR_IAM_PRIVKEY, errhp);

##### OCI_ATTR_TOKEN

Mode
WRITE

Description
This attribute specifies the DB token value to be used for the connection creation. It can be set on both authentication (`OCIAuthInfo`) and user session (`OCISession`) handles. `OCI_ATTR_IAM_TOKEN` attribute is deprecated.

Through this attriute, IAM token or Azure AD Access token type can be provided.

**Note:**

Two types of DB tokens are supported:

- IAM Token: Both `OCI_ATTR_TOKEN` and `OCI_ATTR_IAM_PRIVKEY` attributes must to be provided.

- Azure OAuth2 Token: Both `OCI_ATTR_TOKEN` and `OCI_ATTR_TOKEN_ISBEARER = TRUE` must be provided.

  Maximum size of the token supported is 16k.

**See Also:**

- [Authenticating and Authorizing IAM Users for Oracle DBaaS Databases](../dbseg/authenticating-and-authorizing-iam-users-oracle-dbaas-databases.md)
- [Authenticating and Authorizing Microsoft Azure Active Directory Users for Oracle Databases](../dbseg/authenticating-and-authorizing-microsoft-entra-id-ms-ei-users-oracle-databases-oracle-exadata.md)

Attribute Data Type
`oratext *`

Example Usage
    OCIAttrSet((dvoid *) usrhp, (ub4) OCI_HTYPE_SESSION,
               (dvoid *) tokenBuf, (ub4) tokenLength,
               OCI_ATTR_TOKEN, errhp);

    OCIAttrSet((dvoid *) authp, (ub4) OCI_HTYPE_AUTHINFO,
               (dvoid *) tokenBuf, (ub4) tokenLength,
               OCI_ATTR_TOKEN, errhp);

##### OCI_ATTR_TOKEN_CBK

Mode
WRITE

Description
This OCIAuthInfo handle attribute enables an application to register a callback function that can renew an expired token. The callback function must be implemented by the application. During session pool expansion, if the token provided by the application during pool creation has expired, then the OCI driver invokes this application registered callback to renew the expired token (and private key for IAM token). The callback function needs to use the `OCIAttrSet()` function on the supplied authentication handle to set the renewed DB token (and private key for IAM token). This enables the session pool to continue creating new sessions successfully. Before the pool is created, the application must set the callback function pointer as an attribute on the `OCIAuthInfo` handle of the session pool. `OCI_ATTR_IAM_CBK` attribute is deprecated. Oracle recommends that this token callback should avoid blocking calls.

**Note:**

This attribute can be used for both IAM token and Azure AD OAuth2 token.

<!-- -->

Attribute Data type
`sword (*OCICallbackSetToken)(void *ctx, OCIAuthInfo *authp, ub4 mode);`

Where:

- `ctx`: IN argument, is an opaque context that the application has set on the same authentication handle.
- `authp`: IN argument, is the session pool’s authentication handle that OCI passes to the callback, so that the application can set the latest DB token and private key attributes.
- `mode`: IN argument: Currently `OCI_DEFAULT` is passed to the callback, indicating this callback is being called as the DB token (or private key for IAM token) has expired and new values need to be provided.
  **Note:**

  This attribute can be used for both IAM and OAuth2 tokens.

Returns
`OCI_SUCCESS` if the DB token settings succeed. Otherwise, it should return `OCI_ERROR`.

Example Usage
    OCIAttrSet((dvoid *) authp, (ub4) OCI_HTYPE_AUTHINFO,
               (dvoid *) appCbkFnPtr,
               (ub4) 0, OCI_ATTR_TOKEN_CBK, errhp);

Sample Callback code that the application needs to write:

    sword *callback_fn(void *ctx, OCIAuthInfo *authp, ub4 mode)
    {
      OCIError *ehp;
      sword status=OCI_SUCCESS;
      /* Code to procure the renewed token */
              …
      /* Set the renewed token value and key value on the auth handle */
      /* Use a pre-allocated error handle exclusively for these calls */
      status = OCIAttrSet((dvoid *) authp, (ub4) OCI_HTYPE_AUTHINFO,
                          (dvoid *) newtokenBuf, (ub4) newtokenLength,
                          OCI_ATTR_TOKEN, ehp);
      if (!status)
       status = OCIAttrSet((dvoid *) authp, (ub4) OCI_HTYPE_AUTHINFO,
                           (dvoid *) newprivKeyBuf, (ub4) newprivKeyLength,
                           OCI_ATTR_IAM_PRIVKEY, ehp);
       return status;
    }

##### OCI_ATTR_TOKEN_CBKCTX

Mode
WRITE

Description
This attribute specifies the opaque context pointer to be passed into the token refreshing callback when it is called by OCI. A pre allocated error handle exclusively for this purpose could be embedded in this context. `OCI_ATTR_TOKEN_CBKCTX` attribute is deprecated.

Attribute Data type
void \*

Example Usage
    OCIAttrSet((dvoid *) authp, (ub4) OCI_HTYPE_AUTHINFO,
               (dvoid *) appCbkCtx, (ub4) 0, OCI_ATTR_TOKEN_CBKCTX, errhp);
               (dvoid *) appCbkCtx, (ub4) 0, OCI_ATTR_TOKEN_CBKCTX, errhp);

##### OCI_ATTR_TOKEN_ISBEARER

Mode
Write

Description
This attribute determines if the token set using `OCI_ATTR_TOKEN` is an IAM or a Bearer token. By default, IAM is the default authentication and so, the value of this attribute is set to `false.`The value of this attribute must be set to `true`, if the value of `OCI_ATTR_TOKEN` attribute is set to Azure AD Access token.

If the value of this attribute is set to true, then it implies that the token is a bearer token.

Attribute Data Type
boolean

<!-- -->

Example Usage
    boolean isBearerToken  = TRUE;
    OCIAttrSet((dvoid *) usrhp, (ub4) OCI_HTYPE_SESSION,
               (dvoid *) &isBearerToken, (ub4)0,
               OCI_ATTR_TOKEN_ISBEARER, errhp);

##### OCI_ATTR_FIXUP_CALLBACK

Mode
READ/WRITE

Description
Specifies on the authentication handle attribute the callback passed to `OCISessionGet()` for applications not using an OCISessionPool or using custom pools. For applications using OCISessionPool, this attribute must be set on the authentication handle, which in turn must be set on the session pool handle as the attribute `OCI_ATTR_SPOOL_AUTH`.

**See Also:**

- Session Pool Handle Attributes for more information

- [PL/SQL Callback for Session State Fix Up](session-and-connection-pooling.md) for more information

Attribute Data Type
`oratext *` to be provided in the format `schma.package.callback_function`

**See Also:**

[Identity and Access Management (IAM) Token-Based Authentication](introduction.md)

#### A.5.2 User Session Handle Attributes

Lists and describes user session handle attributes.

The following user session handle attributes also apply to the authentication information handle.

##### OCI_ATTR_ACTION

Mode
WRITE

Description
The name of the current action within the current module. Can be set to `NULL`. When the current action terminates, set this attribute again with the name of the next action, or `NULL` if there is no next action. Can be up to 32 bytes long.

Attribute Data Type
`oratext *`

Example
    OCIAttrSet(session, OCI_HTYPE_SESSION,(void *)"insert into employees",
               (ub4)strlen("insert into employees"), OCI_ATTR_ACTION, error_handle);

##### OCI_ATTR_APPCTX_ATTR

**Note:**

This attribute is not supported with database resident connection pooling.

Mode
WRITE

Description
Specifies an attribute name of the externally initialized context.

**See Also:**

[Session Handle Attributes Used to Set an Externally Initialized Context](managing-scalable-platforms.md)

Attribute Data Type
`oratext *`

##### OCI_ATTR_APPCTX_LIST

**Note:**

This attribute is not supported with database resident connection pooling.

Mode
READ

Description
Gets the application context list descriptor for the session.

Attribute Data Type
`OCIParam **`

##### OCI_ATTR_APPCTX_NAME

**Note:**

This attribute is not supported with database resident connection pooling.

Mode
WRITE

**See Also:**

[Session Handle Attributes Used to Set an Externally Initialized Context](managing-scalable-platforms.md)

Description
Specifies the namespace of the externally initialized context.

Attribute Data Type
`oratext *`

##### OCI_ATTR_APPCTX_SIZE

**Note:**

This attribute is not supported with database resident connection pooling.

Mode
WRITE

Description
Initializes the externally initialized context array size with the number of attributes.

Attribute Data Type
`ub4`

##### OCI_ATTR_APPCTX_VALUE

**Note:**

This attribute is not supported with database resident connection pooling.

Mode
WRITE

Description
Specifies a value of the externally initialized context.

Attribute Data Type
`oratext *`

**See Also:**

[Session Handle Attributes Used to Set an Externally Initialized Context](managing-scalable-platforms.md)

##### OCI_ATTR_AUDIT_BANNER

Mode
READ

Description
Displays a user actions auditing banner from a file.

Attribute Data Type
oratext \*\*

##### OCI_ATTR_AUTOTUNING_ENABLED

Mode
READ

Description
Checks if the client session has OCI auto tuning enabled on OCI client statement caching.

Attribute Data Type
`ub4 *`

##### OCI_ATTR_CALL_TIME

Mode
READ

Description
Returns the server-side time for the preceding call in microseconds.

Attribute Data Type
`ub8 *`

##### OCI_ATTR_CERTIFICATE

Mode
WRITE

Description
Specifies the certificate of the client for use in proxy authentication. Certificate-based proxy authentication using `OCI_ATTR_CERTIFICATE` will not be supported in future Oracle Database releases. Use `OCI_ATTR_DISTINGUISHED_NAME` or `OCI_ATTR_USERNAME` attribute instead.

Attribute Data Type
`ub1 *`

##### OCI_ATTR_CLIENT_IDENTIFIER

Mode
WRITE

Description
Specifies the user identifier in the session handle. Can be up to 64 bytes long. The value is automatically truncated if the supplied input is more than 64 bytes. It can contain the user name, but do not include the password for security reasons. The first character of the identifier should not be ':'. If it is, the behavior is unspecified.

Attribute Data Type
`oratext *`

Example
    OCIAttrSet(session, OCI_HTYPE_SESSION,(void *)"janedoe",
                (ub4)strlen("janedoe"), OCI_ATTR_CLIENT_IDENTIFIER,
                error_handle);

##### OCI_ATTR_CLIENT_INFO

Mode
WRITE

Description
Stores additional client application information. Can also be set by the `DBMS_APPLICATION_INFO` package. It is stored in the `V$SESSION` view. Can be up to 64 bytes long.

Attribute Data Type
`oratext *`

##### OCI_ATTR_COLLECT_CALL_TIME

Mode
READ/WRITE

Description
When set to `TRUE`, causes the server to measure call time, in milliseconds, for each subsequent OCI call.

Attribute Data Type
boolean \*/boolean

##### OCI_ATTR_CONNECTION_CLASS

Mode
READ/WRITE

Description
This attribute of `OCIAuthInfo` handle explicitly names the connection class (a string of up to 128 characters) for a database resident connection pool.

Attribute Data Type
oratext \*\*/oratext \*

##### OCI_ATTR_CURRENT_SCHEMA

Mode
READ/WRITE

Description
Calling `OCIAttrSet()` with this attribute has the same effect as the SQL command `ALTER` `SESSION` `SET` `CURRENT_SCHEMA`, if the schema name and the session exist. The schema is altered on the next OCI call that does a round-trip to the server, avoiding an extra round-trip. If the new schema name does not exist, the same error is returned as the error returned from `ALTER` `SESSION` `SET` `CURRENT_SCHEMA`. The new schema name is placed before database objects in DML or DDL commands that you then enter.

When a client using this attribute communicates with a server that has a software release earlier than Oracle Database 10g Release 2, the `OCIAttrSet()` call is ignored. This attribute is also readable by `OCIAttrGet()`.

Attribute Data Type
`oratext */oratext *`

Example
    text schema[] = "hr";
    err = OCIAttrSet( (void ) mysessp, OCI_HTYPE_SESSION, (void *)schema,
          (ub4)strlen( (char *)schema), OCI_ATTR_CURRENT_SCHEMA, (OCIError *)myerrhp);

##### OCI_ATTR_DBOP

Mode
Write

Description
The name of the database operation set by the client application to be monitored in the database. When you want to end monitoring the current running database operation, set the value to `NULL`. Can be up to 30 bytes long.

**See Also:**

[Attributes for End-to-End Application Tracing](managing-scalable-platforms.md)

[Oracle Database SQL Tuning Guide](../tgsql/monitoring-database-operations.md)

[Oracle Database 2 Day + Performance Tuning Guide](../tdppt/monitoring-real-time-database-performance.md)

Attribute Data Type
`oratext *`

Example
    (void) OCIAttrSet((dvoid *) sess1, (ub4) OCI_HTYPE_SESSION,
                      (dvoid *) dbopname, (ub4) strlen((char *)dbopname),
                      (ub4) OCI_ATTR_DBOP, errhp);

##### OCI_ATTR_DEFAULT_LOBPREFETCH_SIZE

Mode
READ/WRITE

Description
Allows the user to enable prefetching for all the LOB locators fetched in the session. Specifies the default prefetch buffer size for each LOB locator.

Attribute Data Type
`ub4 *``/ub4`

##### OCI_ATTR_DISTINGUISHED_NAME

Mode
WRITE

Description
Specifies the distinguished name of the client for use in proxy authentication.

Attribute Data Type
`oratext *`

##### OCI_ATTR_DRIVER_NAME

Mode
READ/WRITE

Description
Specifies the name of the driver layer using OCI, such as JDBC, ODBC, PHP, SQL\*Plus, and so on. Names starting with "ORA\$" are reserved also. A future application can choose its own name and set it as an aid to fault diagnosability. Set this attribute before executing `OCISessionBegin()`. Pass an array containing up to 9 single-byte characters, including the null terminator. This data is not validated and is passed directly to the server to be displayed in a `V$SESSION_CONNECT_INFO` or `GV$SESSION_CONNECT_INFO` view. OCI accepts driver names of up to 30 characters, which are displayed in these views. For older databases, only the first 8 characters are displayed.

Attribute Data Type
`oratext **/oratext *`

Example
    ...
    oratext client_driver[9];
    ...
    checkerr(errhp, OCIAttrSet(authp, OCI_HTYPE_SESSION,
                    client_driver, (ub4)(strlen(client_driver)),
                    OCI_ATTR_DRIVER_NAME, errhp));

    checkerr(errhp, OCISessionBegin(svchp, errhp, authp, OCI_CRED_RDBMS, OCI_DEFAULT);
    ...

##### OCI_ATTR_EDITION

Mode
READ/WRITE

Description
Specifies the edition to be used for this session. If a value for this attribute has not been set explicitly, then the value in the environment variable `ORA_EDITION` is returned.

Attribute Data Type
oratext \*

##### OCI_ATTR_INITIAL_CLIENT_ROLES

Mode
WRITE

Description
Specifies the role or roles that the client is to initially possess when the application server connects to an Oracle database on its behalf.

Attribute Data Type
`oratext **`.

##### OCI_ATTR_LTXID

Mode
READ

Description
This attribute is defined for the session handle and is used to override the default LTXID (logical transaction ID). Applications that associate the logical session with the web user may want to explicitly attach the LTXID to a physical session and explicitly detach the LTXID when the request is complete.

In `READ` mode, this attribute is used to retrieve the LTXID embedded in the OCISession handle.

Attribute Data Type
`ub1 *` (with length; value is copied; is really a `ub1` array)

##### OCI_ATTR_MAX_OPEN_CURSORS

Mode
READ

Description
The maximum number of SQL statements that can be opened in one session. On the server's parameter file, this value is set using the parameter `open_cursors`. The OCI user should leave some threshold and not reach this limit because the server can also open internal statements (cursors) as part of processing user calls. Applications can use this attribute to limit the number of statement handles opened on a given session. This attribute returns a proper value only when connected to a 12.1 server or later.

If the cursors in the server session exceed the open cursor setting, then the server returns an error to the client saying that the value for max cursors is exceeded.

Also, note that this value should only be looked at from the session handle after an `OCISessionGet()` or equivalent login call has been done.

Attribute Data Type
`ub4 *`

Example
    OCIAttrGet((void *)usrhp, OCI_HTYPE_SESSION,
     (void *)&ub4localvariable, (ub4 *)0, OCI_ATTR_MAX_OPEN_CURSORS, errhp);

##### OCI_ATTR_MIGSESSION

Mode
READ/WRITE

Description
Specifies the session identified for the session handle. Allows you to clone a session from one environment to another, in the same process or between processes. These processes can be on the same system or different systems. For a session to be cloned, the session must be authenticated as migratable.

**See Also:**

[Password and Session Management](managing-scalable-platforms.md)

Attribute Data Type
`ub1 *`

Example
The following code sample shows how this attribute is used:

    OCIAttrSet ((void *) authp, (ub4)OCI_HTYPE_SESSION, (void *) mig_session,
                (ub4) sz, (ub4)OCI_ATTR_MIGSESSION, errhp);

##### OCI_ATTR_MODULE

Mode
WRITE

Description
The name of the current module running in the client application. When the current module terminates, call with the name of the new module, or use `NULL` if there is no new module. Can be up to 48 bytes long.

Attribute Data Type
`oratext *`

Example
    OCIAttrSet(session, OCI_HTYPE_SESSION,(void *)"add_employee",
               (ub4)strlen("add_employee"), OCI_ATTR_MODULE, error_handle);

##### OCI_ATTR_ORA_DEBUG_JDWP

Mode
WRITE

Description
Specifies the external debugger's location the database session is to connect to after logon. This allows the user to initiate debugging of the database application.

The format of the attribute is a list of parameter names and values separated by semi-colons. The parameters will be passed to the `DBMS_ DEBUG_JDWP_CUSTOM.CONNECT_DEBUGGER` package API to connect the database session to the debugger. The parameter name can be a quoted or unquoted PL/SQL identifier. The parameter value is a character string, either quoted by single-quotes, or unquoted, which is terminated by a semi-colon. To escape a single quote in a quoted string, use two consecutive single quotes. No space is allowed anywhere between the parameter names and their values.

The attribute should contain at least the `host` and `port` parameters that specify the Internet Protocol dotted address or host name of the computer the debugger is running, and the TCP port number the debugger is listening to for debug connections.

Attribute Data Type
`oratext *`

Example
    OCIAttrSet(session,
               OCI_HTYPE_SESSION,
              (void *)"janedoe",
              (ub4)strlen("janedoe"),
               OCI_ATTR_CLIENT_IDENTIFIER,
               error_handle);

##### OCI_ATTR_PASSWORD

Mode
WRITE

Description
Specifies a password to use for authentication.

Attribute Data Type
`oratext *`

##### OCI_ATTR_PROXY_CLIENT

Mode
WRITE

Description
Specifies the target user name for access through a proxy.

Attribute Data Type
`oratext *`

##### OCI_ATTR_PROXY_CREDENTIALS

Mode
WRITE

Description
Specifies that the credentials of the application server are to be used for proxy authentication.

Attribute Data Type
`OCISession`

##### OCI_ATTR_PURITY

Mode
READ/WRITE

Description
An attribute of the `OCIAuthInfo` handle for database resident connection pooling. Values are `OCI_ATTR_PURITY_NEW`, the application requires a session not tainted with any prior session state; or `OCI_ATTR_PURITY_SELF`, the session can have been used before. If the application does not specify the purity when invoking `OCISessionGet()`, then the purity value `OCI_ATTR_PURITY_DEFAULT` is assumed. This later translates to either `OCI_ATTR_PURITY_NEW` or `OCI_ATTR_PURITY_SELF` depending upon whether the application logic is set up to use a new session or to reuse a pooled session.

Attribute Data Type
ub4 \*/ub4

##### OCI_ATTR_SESSION_STATE

Mode
READ/WRITE

Description
Specifies the current state of the database session. Set to `OCI_SESSION_STATEFUL` if the session is required to perform a database task. If the application is no longer dependent on the current session for subsequent database activity, set to `OCI_SESSION_STATELESS`. This attribute is currently applicable only when connected to a Database Resident Connection Pool. It should be used if the application does custom session pooling and does not use `OCISessionPool()`.

Attribute Data Type
ub1 \*/ ub1

##### OCI_ATTR_SHARDING_KEY

Mode
WRITE

Description
For the shard and chunk, specifies the sharding key for the connection request from an OCI session pool or standalone connection.

The `OCIShardingKey *` supplied to `OCIAttrSet()` needs to be created with `OCIDescriptorAlloc()` specifying the sharding descriptor and then using as many calls as is needed to `OCIShardingKeyColumnAdd()` to create the compound sharding key. See [OCIShardingKeyColumnAdd()](shard-functions.md) for more information and an example.

For custom pools, this attribute associates a sharding key to a given connection.

Attribute Data Type
`OCIShardingKey *`

Example
    /* Allocate the super sharding key descriptor. */
    OCIDescriptorAlloc(envhp,(dvoid **)&shardKey,
                   OCI_DTYPE_SHARDING_KEY, 0,(dvoid **)0)))
    text *name = “KK”;
    text *gname = “GOLD”;
    int  empid = 150;

    /* Add all the columns of the key to form the final shard key. */
    OCIShardingKeyColumnAdd(shardKey,(ub1*)&empid, sizeof(empid),
                                   SQLT_INT, errhp, OCI_DEFAULT);
    OCIShardingKeyColumnAdd(shardKey, name, strlen(name),
                                   SQLT_CHAR, errhp, OCI_DEFAULT));

    OCIShardingKey *shardKey;
    OCIAttrSet(authp, OCI_HTYPE_AUTHINFO,
               shardKey, sizeof(shardKey),
               OCI_ATTR_SHARDING_KEY, errhp);

##### OCI_ATTR_SHARDING_KEY_B64

Mode
WRITE

Description
Gets the base64 representation of sharding key and super sharding key values for diagnostic purposes.

Attribute Data Type
`Oratext *`

Example
    char * skeyValue;
    ub4    skeyValueLen;
    OCIAttrGet((dvoid *)     OCIShardingKey,
               (ub4)         OCI_DTYPE_SHARDING_KEY,
               (dvoid *)     &skeyValue,
               (ub4 *)       &skeyValueLen,
                             OCI_ATTR_SHARDING_KEY_B64,
               (OCIError * ) errhp);

##### OCI_ATTR_SUPER_SHARDING_KEY

Mode
WRITE

Description
For the shard and group of chunks, specifies the super sharding key for the connection request from an OCI session pool or standalone connection.

The `OCIShardingKey *` supplied to `OCIAttrSet()` needs to be created with `OCIDescriptorAlloc()` specifying the sharding descriptor and then using as many calls as is needed to `OCIShardingKeyColumnAdd()` to create the compound shard key. See [OCIShardingKeyColumnAdd()](shard-functions.md) for more information and an example.

For custom pools, this attribute associates a shard group key to a given connection.

Attribute Data Type
`OCIShardingKey *`

Example
    /* Allocate the sharding key descriptor. */
    OCIDescriptorAlloc(envhp,(dvoid **)&shardGroupKey,
                       OCI_DTYPE_SHARDING_KEY, 0, (dvoid **)0));

    /* Add the column of the key to form the final super sharding key. */
    OCIShardingKeyColumnAdd(shardGroupKey, errhp, gname, strlen(gname),
                         SQLT_CHAR, OCI_DEFAULT));

    OCIShardingKey *shardGroupKey;
    OCIAttrSet(authp, OCI_HTYPE_AUTHINFO,
               shardGroupKey, sizeof(shardGroupKey),
               OCI_ATTR_SUPER_SHARDING_KEY, errhp));

##### OCI_ATTR_TRANS_PROFILE_FOREIGN

Mode
READ

Description
Specifies whether a SQL translation profile for translation of foreign SQL syntax is set in the current session or not.

Attribute Data Type
`boolean`

Example
    status = OCIAttrGet(authp,
                        OCI_HTYPE_SESSION,
                        (void *)&foreign_sql_syntax,
                        (ub4 *)NULL,
                        OCI_ATTR_TRANS_PROFILE_FOREIGN,
                        errhp);

##### OCI_ATTR_TRANSACTION_IN_PROGRESS

Mode
READ

Description
If `TRUE`, then the referenced session has a currently active transaction.

If `FALSE`, then the referenced session does not have a currently active transaction.

Attribute Data Type
`boolean *`

Example
    {  boolean txnInProgress;

      OCIAttrGet(usrhp, OCI_HTYPE_SESSION,
                 &txnInProgress, (ub4 *)0,
                 OCI_ATTR_TRANSACTION_IN_PROGRESS,
                 errhp);
    }

##### OCI_ATTR_USERNAME

Mode
READ/WRITE

Description
Specifies a user name to use for authentication.

Attribute Data Type
`oratext **/oratext *`

### A.6 Administration Handle Attributes

Lists and describes administration handle attributes.

The following attributes are used for the administration handle.

#### OCI_ATTR_ADMIN_PFILE

Mode
READ/WRITE

Description
Set this attribute before a call to `OCIDBStartup()` to specify the location of the client-side parameter file that is used to start the database. If this attribute is not set, then the server-side parameter file is used. If the server-side parameter file does not exist, an error is returned.

Attribute Data Type
`oratext */oratext *`

### A.7 Connection Pool Handle Attributes

Lists and describes connection pool handle attributes.

The following attributes are used for the connection pool handle.

#### OCI_ATTR_CONN_TIMEOUT

**Note:**

Shrinkage of the pool only occurs when there is a network round-trip. If there are no operations, then the connections remain active.

Mode
READ/WRITE

Description
Connections idle for more than this time value (in seconds) are terminated to maintain an optimum number of open connections. This attribute can be set dynamically. If this attribute is not set, the connections are never timed out.

Attribute Data Type
`ub4 */ub4`

#### OCI_ATTR_CONN_NOWAIT

Mode
READ/WRITE

Description
This attribute determines if retrial for a connection must be performed when all connections in the pool are found to be busy and the number of connections has reached the maximum.

If this attribute is set, an error is thrown when all the connections are busy and no more connections can be opened. Otherwise, the call waits until it gets a connection.

When read, the attribute value is returned as `TRUE` if it has been set.

Attribute Data Type
`ub1 */ub1`

#### OCI_ATTR_CONN_BUSY_COUNT

Mode
READ

Description
Returns the number of busy connections.

Attribute Data Type
`ub4 *`

#### OCI_ATTR_CONN_OPEN_COUNT

Mode
READ

Description
Returns the number of open connections.

Attribute Data Type
`ub4 *`

#### OCI_ATTR_CONN_MIN

Mode
READ

Description
Returns the number of minimum connections.

Attribute Data Type
`ub4 *`

#### OCI_ATTR_CONN_MAX

Mode
READ

Description
Returns the number of maximum connections.

Attribute Data Type
`ub4 *`

#### OCI_ATTR_CONN_INCR

Mode
READ

Description
Returns the connection increment parameter.

Attribute Data Type
`ub4 *`

#### A.7.1 Session Pool Handle Attributes

Lists and describes session pool handle attributes.

The following attributes are used for the session pool handle.

##### OCI_ATTR_SPOOL_AUTH

Mode
WRITE

Description
To make pre-session creation attributes effective on the sessions being retrieved from the session pool, this attribute can be set on the session pool handle. Currently only the following attributes can be set on this `OCIAuthInfo` handle:

`OCI_ATTR_DRIVER_NAME`

`OCI_ATTR_EDITION`

`OCI_ATTR_FIXUP_CALLBACK`

If any other attributes are set on the `OCIAuthInfo` handle and the `OCIAuthInfo` handle is set on the session pool handle, an error results. Moreover, the `OCIAuthInfo` handle should be set on the session pool handle only before calling `OCISessionPoolCreate()` with the session pool handle. Setting it after `OCISessionPoolCreate()` results in an error.

Attribute Data Type
`OCIAuthInfo *`

##### OCI_ATTR_SPOOL_BUSY_COUNT

Mode
READ

Description
Returns the number of busy sessions checked out from the pool.

Attribute Data Type
`ub4 *`

##### OCI_ATTR_FOCBK

Mode
READ/WRITE

Description
On `OCIAttrSet()`, defines a TAF callback and context to be associated with each session in the OCI session pool.

On `OCIAttrGet()`, populates the `OCIFocbkStruct` with the TAF callback and context defined for the session pool.

**Note:**

- This attribute is already supported for handles of type OCIServer and OCICPool.

- A TAF callback set on the server handle will override the callback set on the session pool.

Attribute Data Type
`OCIFocbkStruct *`

##### OCI_ATTR_SPOOL_GETMODE

Mode
READ/WRITE

Description
This attribute determines the behavior of the session pool when all sessions in the pool are found to be busy and the number of sessions has reached the maximum or the pool must create new connections. Values are:

- `OCI_SPOOL_ATTRVAL_WAIT` - The thread waits and blocks until a session is freed or a new one is created. This is the default value.

- `OCI_SPOOL_ATTRVAL_TIMEDWAIT` - Keep trying internally for a free session until the time out set by `OCI_ATTR_SPOOL_WAIT_TIMEOUT` expires.

- `OCI_SPOOL_ATTRVAL_NOWAIT` - An error is returned if there are no free connections or if the pool must create a new connection.

- `OCI_SPOOL_ATTRVAL_FORCEGET` - A new session is created even though all the sessions are busy and the maximum number of sessions has been reached. `OCISessionGet()` returns a warning. In this case, if new sessions are created that have exceeded the maximum, `OCISessionGet()` returns a warning.

  Note that if this value is set, it is possible that there can be an attempt to create more sessions than can be supported by the instance of the Oracle database. In this case, the server returns the following error:

      ORA 00018 - Maximum number of sessions exceeded

  In this case, the error is propagated to the session pool user.

  When read, the appropriate attribute value is returned.

Attribute Data Type
`ub1 */ ub1`

##### OCI_ATTR_SPOOL_INCR

Mode
READ

Description
Returns the session increment parameter.

Attribute Data Type
`ub4 *`

##### OCI_ATTR_SPOOL_MAX

Mode
READ

Description
Returns the number of maximum sessions.

Attribute Data Type
`ub4 *`

##### OCI_ATTR_SPOOL_MAX_LIFETIME_SESSION

Mode
READ/WRITE

Description
This attribute sets the lifetime (in seconds) for all the sessions in the pool. Sessions in the pool are terminated when they have reached their lifetime. In the case when `OCI_ATTR_SPOOL_TIMEOUT` is also set, the session will be terminated if either the idle time out happens or the max lifetime setting is exceeded.

Attribute Data Type
ub4 \*/ ub4

##### OCI_ATTR_SPOOL_MAX_USE_SESSION

#####

Mode
WRITE

Description
Sets the maximum number of times one session can be checked out of the session pool, after which the session is automatically destroyed. The default value is 0, which means there is no limit. This value can also be set in the `oraaccess.xml` client-side configuration file under the `<session_pool>` section as `<max_use_session>`.

Attribute Data Type
`ub4`

##### OCI_ATTR_SPOOL_MIN

Mode
READ

Description
Returns the number of minimum sessions.

Attribute Data Type
`ub4 *`

##### OCI_ATTR_SPOOL_OPEN_COUNT

Mode
READ

Description
Returns the number of open sessions.

Attribute Data Type
`ub4 *`

##### OCI_ATTR_SPOOL_STMTCACHESIZE

Mode
READ/WRITE

Description
Sets the default statement cache size to this value for each of the sessions in a session pool. The statement cache size for a particular session in the pool can, at any time, be overridden by using `OCI_ATTR_STMTCACHESIZE` on that session.

**See Also:**

[Statement Caching in OCI](performance-topics.md)

Attribute Data Type
`ub4 *`/ `ub4`

##### OCI_ATTR_SPOOL_TIMEOUT

Mode
READ/WRITE

Description
The sessions idle for more than this time (in seconds) are terminated periodically to maintain an optimum number of open sessions. This attribute can be set dynamically. If this attribute is not set, the least recently used sessions may be timed out if and when space in the pool is required. OCI only checks for timed out sessions when it releases one back to the pool. See OCI_ATTR_SPOOL_MAX_LIFETIME_SESSION for more information.

Attribute Data Type
`ub4 */ ub4`

##### OCI_ATTR_SPOOL_WAIT_TIMEOUT

Mode
READ/WRITE

Description
This is the time out (in milliseconds) applied for the `OCISessionGet()` call while waiting for a free session, when the `OCI_ATTR_SPOOL_GETMODE` property is set to `OCI_SPOOL_ATTRVAL_TIMEDWAIT`. This is also applicable in case of sharding, where the `OCISessionGet()` call waits for a free session to an instance with writable chunks.

Attribute Data Type
`ub4 */ ub4`

##### OCI_ATTR_SPOOL_MAX_PER_SHARD

Mode
READ/WRITE

Description
Sets the maximum number of sessions per shard. This attribute is set to ensure that the pool is balanced towards each shard.

Attribute Data Type
`ub4 *`

### A.8 Transaction Handle Attributes

Lists and describes transaction handle attributes.

The following attributes are used for the transaction handle.

#### OCI_ATTR_TRANS_NAME

Mode
READ/WRITE

Description
Can be used to establish or read a text string that identifies a transaction. This is an alternative to using the XID to identify the transaction. The oratext string can be up to 64 bytes long.

Attribute Data Type
`oratext **` (READ) / `oratext *` (WRITE)

#### OCI_ATTR_TRANS_TIMEOUT

Mode
READ/WRITE

Description
Can set or read a timeout interval value used at prepare time.

Attribute Data Type
`ub4 *` (READ) / `ub4` (WRITE)

#### OCI_ATTR_XID

Mode
READ/WRITE

Description
Can set or read an XID that identifies a transaction.

Attribute Data Type
`XID **` (READ) / `XID *` (WRITE)

### A.9 Statement Handle Attributes

Lists and describes statement handle attributes.

The following attributes are used for the statement handle.

#### OCI_ATTR_BIND_COUNT

Mode
READ

Description
Returns the number of bind positions on the statement handle.

Attribute Data Type
ub4 \*

Example
    OCIHandleAlloc(env,(void **) &pStatement, OCI_HTYPE_STMT, (size_t)0, (void **)0);
    OCIStmtPrepare (pStatement, err, pszQuery, (ub4)strlen(pszQuery),
                    (ub4)OCI_NTV_SYNTAX, (ub4)OCI_DEFAULT);
    OCIAttrGet(pStatement, OCI_HTYPE_STMT, &iNbParameters, NULL, OCI_ATTR_BIND_COUNT,
               err);

#### OCI_ATTR_CHNF_REGHANDLE

Mode
WRITE

Description
When this attribute is set to the appropriate subscription handle, execution of the query also creates the registration of the query for continuous query notification.

**See Also:**

Continuous Query Notification Attributes

Attribute Data Type
`OCISubscription *`

Example
    /* Associate the statement with the subscription handle */
    OCIAttrSet (stmthp, OCI_HTYPE_STMT, subscrhp, 0,
                OCI_ATTR_CHNF_REGHANDLE, errhp);

#### OCI_ATTR_CQ_QUERYID

Mode
READ

Description
Obtains the query ID of a registered query after registration is made by the call to `OCIStmtExecute()`.

Attribute Data Type
`ub8 *`

#### OCI_ATTR_CURRENT_POSITION

Mode
READ

Description
Indicates the current position in the result set. This attribute can only be retrieved. It cannot be set.

Attribute Data Type
`ub4 *`

#### OCI_ATTR_ENV

Mode
READ

Description
Returns the environment context associated with the statement.

Attribute Data Type
`OCIEnv **`

#### OCI_ATTR_FETCH_ROWID

Mode
READ/WRITE

Description
Specifies that the `ROWID`s are fetched after doing a define at `position` 0, and a `SELECT...FOR UPDATE` statement.

**See Also:**

[Implicit Fetching of ROWIDs](performance-topics.md)

Attribute Data Type
boolean \*/boolean

#### OCI_ATTR_IMPLICIT_RESULT_COUNT

Mode
READ

Description
Returns the total number of implicit results available on the top-level OCI statement handle.

Attribute Data Type
`ub4 *`

#### OCI_ATTR_NUM_DML_ERRORS

Mode
READ

Description
Returns the number of errors in the DML operation.

Attribute Data Type
`ub4 *`

#### OCI_ATTR_PARAM_COUNT

Mode
READ

Description
Gets the number of columns in the select-list for the statement associated with the statement handle.

Attribute Data Type
`ub4 *`

<!-- -->

Example
    ...
    int i = 0;
    ub4 parmcnt = 0;
    ub2 type = 0;
    OCIParam *colhd = (OCIParam *) 0;   /* column handle */

    /* Describe of a select-list */
    OraText *sqlstmt = (OraText *)"SELECT * FROM employees WHERE employee_id = 100";

    checkerr(errhp, OCIStmtPrepare(stmthp, errhp, (OraText *)sqlstmt,
                        (ub4)strlen((char *)sqlstmt),
                        (ub4) OCI_NTV_SYNTAX, (ub4) OCI_DEFAULT));

    checkerr(errhp, OCIStmtExecute(svchp, stmthp, errhp, 1, 0,
            (OCISnapshot *)0, (OCISnapshot *)0, OCI_DESCRIBE_ONLY));

    /* Get the number of columns in the select list */
    checkerr(errhp, OCIAttrGet((void *)stmthp, OCI_HTYPE_STMT, (void *)&parmcnt,
                          (ub4 *)0, OCI_ATTR_PARAM_COUNT, errhp));

    /* Go through the column list and retrieve the data type of each column. You
       start from pos = 1 */
    for (i = 1; i <= parmcnt; i++)
    {
      /* Get parameter for column i */
      checkerr(errhp, OCIParamGet((void *)stmthp, OCI_HTYPE_STMT, errhp,
               (void **)&colhd, i));

      /* Get data-type of column i */
      type = 0;
      checkerr(errhp, OCIAttrGet((void *)colhd, OCI_DTYPE_PARAM,
              (void *)&type, (ub4 *)0, OCI_ATTR_DATA_TYPE, errhp));

    }
    ...

#### OCI_ATTR_PARSE_ERROR_OFFSET

Mode
READ

Description
Returns the parse error offset for a statement.

Attribute Data Type
`ub2 *`

#### OCI_ATTR_PREFETCH_MEMORY

Mode
WRITE

Description
Sets the memory level for top-level rows to be prefetched. Rows up to the specified top-level row count are fetched if the memory level occupies no more than the specified memory usage limit. The default value is 0, which means that memory size is not included in computing the number of rows to prefetch.

Attribute Data Type
`ub4 *`

#### OCI_ATTR_PREFETCH_ROWS

Mode
WRITE

Description
Sets the number of top-level rows to be prefetched. The default value is 1 row.

Attribute Data Type
`ub4 *`

#### OCI_ATTR_ROW_COUNT

Mode
READ

Description
Returns the number of rows processed so far after `SELECT` statements. For `INSERT`, `UPDATE`, and `DELETE` statements, it is the number of rows processed by the most recent statement. The default value is 1.

For nonscrollable cursors, `OCI_ATTR_ROW_COUNT` is the total number of rows fetched into user buffers with the `OCIStmtFetch2()` calls issued since this statement handle was executed. Because they are forward sequential only, this also represents the highest row number seen by the application.

For scrollable cursors, `OCI_ATTR_ROW_COUNT` represents the maximum (absolute) row number fetched into the user buffers. Because the application can arbitrarily position the fetches, this need not be the total number of rows fetched into the user's buffers since the (scrollable) statement was executed.

Beginning with Oracle Database Release 12.1, using the attribute `OCI_ATTR_UB8_ROW_COUNT` is preferred to using the attribute `OCI_ATTR_ROW_COUNT` if row count values can exceed the value of `UB4MAXVAL` for an OCI application. If the row count exceeds the value of `UB4MAXVAL` and the application uses the attribute `OCI_ATTR_ROW_COUNT`, a call using `OCIAttrGet()` will return an error.

Attribute Data Type
`ub4 *`

#### OCI_ATTR_DML_ROW_COUNT_ARRAY

Mode
READ

Description
Returns an array of row counts affected by each iteration of an array DML statement. The row count for iteration i can be obtained by looking up array\[i-1\].

Without `OCI_BATCH_ERRORS` mode, [OCIStmtExecute()](statement-functions.md) stops execution with the first erroneous iteration. In such a scenario, the array returned by the `OCI_ATTR_DML_ROW_COUNT_ARRAY` attribute only contains valid row counts up to and including the last successful iteration. When `OCI_RETURN_ROW_COUNT_ARRAY` mode is used in conjunction with `OCI_BATCH_ERRORS` mode, the returned row-count array contains the actual number of rows affected per successful iteration and 0 for iterations that resulted in errors.

This attribute works only when the statement is executed in mode `OCI_RETURN_ROW_COUNT_ARRAY` at the time of using [OCIStmtExecute()](statement-functions.md).

Use this attribute only after an array DML operation and while using `OCI_RETURN_ROW_COUNT_ARRAY` mode in [OCIStmtExecute()](statement-functions.md).

Any attempt to query this attribute after any other operation (other than an array DML) or without passing this mode will result in an `OCI_ERROR` (`ORA-24349`).

Attribute Data Type
`ub8 *`

Example
    int deptarray[]={10,20,30};
    int iters = 3;
    ub8 *rowcounts;
    ub4 rowCountArraySize;
    /*Statement prepare */
    text *updatesal = (text *)"UPDATE EMP set sal = sal+100 where deptno = :dept"
    OCIStmtPrepare2 ((OCISvcCtx *)svchp,(OCIStmt **)&stmthp,
    (OCIError *)errhp, (text *)updatesal, (ub4)sizeof(updatesal)-1,
    (oratext *)NULL, (ub4) 0, (ub4)OCI_NTV_SYNTAX, (ub4)OCI_DEFAULT);
    /*Array bind*/
    OCIBindByPos (stmthp, &bndhp, errhp, 1, deptarray,  sizeof(deptarray[0]),
             SQLT_INT, (ub2 *) 0, (ub2 *) 0, (ub4)   0, (ub4)   0, (ub4 *) 0,
             (ub4)   OCI_DEFAULT);
    /* Pass new MODE for Array DML rowcounts; also, if an error occurred for any iteration and you want to get the number of rows updated for the rest of the iterations.*/
    OCIStmtExecute(svchp, stmthp, errhp, iters,  (ub4) 0, 0, 0, OCI_BATCH_ERRORS | OCI_RETURN_ROWCOUNT_ARRAY);
    OCIAttrGet (stmthp, (ub4) OCI_HTYPE_STMT,
                (ub8 *)&rowcounts, &rowCountArraySize,
                OCI_ATTR_DML_ROW_COUNT_ARRAY, errhp);

#### OCI_ATTR_ROWID

Mode
READ

Description
Returns the `ROWID` descriptor allocated with `OCIDescriptorAlloc()`.

**See Also:**

[Positioned Updates and Deletes](oci-programming-basics.md) and [ROWID Descriptor](data-types.md)

Attribute Data Type
OCIRowid \*

#### OCI_ATTR_ROWS_FETCHED

Mode
READ

Description
Indicates the number of rows that were successfully fetched into the user's buffers in the last fetch or execute with nonzero iterations. It can be used for both scrollable and nonscrollable statement handles.

Attribute Data Type
`ub4 *`

Example
    ub4 rows;
    ub4 sizep = sizeof(ub4);
    OCIAttrGet((void *) stmhp, (ub4) OCI_HTYPE_STMT,
               (void *)& rows, (ub4 *) &sizep, (ub4)OCI_ATTR_ROWS_FETCHED,
               errhp);

#### OCI_ATTR_SQL_ID

Mode
READ

Dexcription
Gets the `SQL_ID` for a specific SQL statement from the server and makes it available on the client in a statement handle.

Attribute Data Type
`ub4 *`

Example
In an `OCIStmtPrepare2()`, specify `OCI_PREP2_GET_SQL_ID` as the mode. This `OCI_PREP2_GET_SQL_ID` mode should be ORed with any other mode. For example:

    OCIStmtPrepare2((dvoid *)ctxptr->svchp, &stmthp,
                                   (dvoid *)ctxptr->errhp,
                                   insStmt, sizeof(insStmt),
                                   (const oratext *)0, (ub4)0,
                                   OCI_NTV_SYNTAX,
                                   OCI_DEFAULT | OCI_PREP2_GET_SQL_ID);

You can do a bind or define operation and then execute on the statement.

The following code example shows how to obtain the `SQL_ID`.

      ub4         sqlidLen;
      oratext    *sqlid;
                     OCIAttrGet(stmthp, OCI_HTYPE_STMT,
                                     &sqlid, (ub4 *)&sqlidLen,
                                     OCI_ATTR_SQL_ID,
                                     ctxptr->errhp);

#### OCI_ATTR_SQLFNCODE

Mode
READ

Description
Returns the function code of the SQL command associated with the statement.

Attribute Data Type
`ub2 *`

Notes
Table A-1 lists the SQL command codes.

Table A-1 Function Code of the SQL Command Associated with the SQL Statement

| Function Code | SQL Statement            | Function Code | SQL Statement           | Function Code | SQL Statement           |
|:--------------|:-------------------------|:--------------|:------------------------|:--------------|:------------------------|
| 01            | CREATE TABLE             | 43            | DROP EXTERNAL DATABASE  | 85            | TRUNCATE TABLE          |
| 02            | SET ROLE                 | 44            | CREATE DATABASE         | 86            | TRUNCATE CLUSTER        |
| 03            | INSERT                   | 45            | ALTER DATABASE          | 87            | CREATE BITMAPFILE       |
| 04            | SELECT                   | 46            | CREATE ROLLBACK SEGMENT | 88            | ALTER VIEW              |
| 05            | UPDATE                   | 47            | ALTER ROLLBACK SEGMENT  | 89            | DROP BITMAPFILE         |
| 06            | DROP ROLE                | 48            | DROP ROLLBACK SEGMENT   | 90            | SET CONSTRAINTS         |
| 07            | DROP VIEW                | 49            | CREATE TABLESPACE       | 91            | CREATE FUNCTION         |
| 08            | DROP TABLE               | 50            | ALTER TABLESPACE        | 92            | ALTER FUNCTION          |
| 09            | DELETE                   | 51            | DROP TABLESPACE         | 93            | DROP FUNCTION           |
| 10            | CREATE VIEW              | 52            | ALTER SESSION           | 94            | CREATE PACKAGE          |
| 11            | DROP USER                | 53            | ALTER USER              | 95            | ALTER PACKAGE           |
| 12            | CREATE ROLE              | 54            | COMMIT (WORK)           | 96            | DROP PACKAGE            |
| 13            | CREATE SEQUENCE          | 55            | ROLLBACK                | 97            | CREATE PACKAGE BODY     |
| 14            | ALTER SEQUENCE           | 56            | SAVEPOINT               | 98            | ALTER PACKAGE BODY      |
| 15            | (NOT USED)               | 57            | CREATE CONTROL FILE     | 99            | DROP PACKAGE BODY       |
| 16            | DROP SEQUENCE            | 58            | ALTER TRACING           | 157           | CREATE DIRECTORY        |
| 17            | CREATE SCHEMA            | 59            | CREATE TRIGGER          | 158           | DROP DIRECTORY          |
| 18            | CREATE CLUSTER           | 60            | ALTER TRIGGER           | 159           | CREATE LIBRARY          |
| 19            | CREATE USER              | 61            | DROP TRIGGER            | 160           | CREATE JAVA             |
| 20            | CREATE INDEX             | 62            | ANALYZE TABLE           | 161           | ALTER JAVA              |
| 21            | DROP INDEX               | 63            | ANALYZE INDEX           | 162           | DROP JAVA               |
| 22            | DROP CLUSTER             | 64            | ANALYZE CLUSTER         | 163           | CREATE OPERATOR         |
| 23            | VALIDATE INDEX           | 65            | CREATE PROFILE          | 164           | CREATE INDEXTYPE        |
| 24            | CREATE PROCEDURE         | 66            | DROP PROFILE            | 165           | DROP INDEXTYPE          |
| 25            | ALTER PROCEDURE          | 67            | ALTER PROFILE           | 166           | ALTER INDEXTYPE         |
| 26            | ALTER TABLE              | 68            | DROP PROCEDURE          | 167           | DROP OPERATOR           |
| 27            | EXPLAIN                  | 69            | (NOT USED)              | 168           | ASSOCIATE STATISTICS    |
| 28            | GRANT                    | 70            | ALTER RESOURCE COST     | 169           | DISASSOCIATE STATISTICS |
| 29            | REVOKE                   | 71            | CREATE SNAPSHOT LOG     | 170           | CALL METHOD             |
| 30            | CREATE SYNONYM           | 72            | ALTER SNAPSHOT LOG      | 171           | CREATE SUMMARY          |
| 31            | DROP SYNONYM             | 73            | DROP SNAPSHOT LOG       | 172           | ALTER SUMMARY           |
| 32            | ALTER SYSTEM SWITCH LOG  | 74            | CREATE SNAPSHOT         | 173           | DROP SUMMARY            |
| 33            | SET TRANSACTION          | 75            | ALTER SNAPSHOT          | 174           | CREATE DIMENSION        |
| 34            | PL/SQL EXECUTE           | 76            | DROP SNAPSHOT           | 175           | ALTER DIMENSION         |
| 35            | LOCK                     | 77            | CREATE TYPE             | 176           | DROP DIMENSION          |
| 36            | NOOP                     | 78            | DROP TYPE               | 177           | CREATE CONTEXT          |
| 37            | RENAME                   | 79            | ALTER ROLE              | 178           | DROP CONTEXT            |
| 38            | COMMENT                  | 80            | ALTER TYPE              | 179           | ALTER OUTLINE           |
| 39            | AUDIT                    | 81            | CREATE TYPE BODY        | 180           | CREATE OUTLINE          |
| 40            | NO AUDIT                 | 82            | ALTER TYPE BODY         | 181           | DROP OUTLINE            |
| 41            | ALTER INDEX              | 83            | DROP TYPE BODY          | 182           | UPDATE INDEXES          |
| 42            | CREATE EXTERNAL DATABASE | 84            | DROP LIBRARY            | 183           | ALTER OPERATOR          |

#### OCI_ATTR_STATEMENT

Mode
READ

Description
Returns the text of the SQL statement prepared in a statement handle. In UTF-16 mode, the returned statement is in UTF-16 encoding. The length is always in bytes.

Attribute Data Type
`oratext *`

#### OCI_ATTR_STMTCACHE_CBKCTX

Mode
READ/WRITE

Description
Used to get and set the application's opaque context on the statement handle. This context can be of any type that the application defines. It is primarily used for encompassing the bind and define buffer addresses.

Attribute Data Type
`void *`

#### OCI_ATTR_STMT_IS_RETURNING

Mode
READ

Description
Determines whether the given SQL Statement has a `RETURNING INTO` clause.

Attribute Data Type
`ub1`

Example
    returning_into_clause = OCIAttrGet ( stmthp, OCI_HTYPE_STMT, (ub1*)&isReturning, NULL, OCI_ATTR_STMT_IS_RETURNING, errhp);

#### OCI_ATTR_STMT_STATE

Mode
READ

Description
Returns the fetch state of that statement. This attribute can be used by the caller to determine if the session can be used in another service context or if it is still needed in the current set of data access calls. Basically, if you are in the middle of a fetch-execute cycle, then you do not want to release the session handle for another statement execution. Valid values are:

- `OCI_STMT_STATE_INITIALIZED`

- `OCI_STMT_STATE_EXECUTED`

- `OCI_STMT_STATE_END_OF_FETCH`

Attribute Data Type
`ub4 *`

#### OCI_ATTR_STMT_TYPE

Mode
READ

Description
The type of statement associated with the handle. Valid values are:

- `OCI_STMT_SELECT`

- `OCI_STMT_UPDATE`

- `OCI_STMT_DELETE`

- `OCI_STMT_INSERT`

- `OCI_STMT_CREATE`

- `OCI_STMT_DROP`

- `OCI_STMT_ALTER`

- `OCI_STMT_BEGIN` (PL/SQL statement)

- `OCI_STMT_DECLARE` (PL/SQL statement)

- `OCI_STMT_CALL` (PL/SQL statement)

- `OCI_STMT_MERGE` (PL/SQL statement)

Attribute Data Type
`ub2 *`

#### OCI_ATTR_UB8_ROW_COUNT (Recommended over OCI_ATTR_ROW_COUNT)

Mode
READ

Description
For `SELECT` statements, returns the cumulative number of rows fetched from a result set. For `INSERT`, `UPDATE`, and `DELETE` statements, this attribute returns the number of rows processed by the statement. The default value is 1.

For non-scrollable cursors, `OCI_ATTR_UB8_ROW_COUNT` is the total number of rows fetched into user buffers with the `OCIStmtFrtch()` or [OCIStmtFetch2()](statement-functions.md) calls issued since this statement handle was executed. For these non-scrollable cursors, this also represents the highest row number seen by the application.

If using the attribute `OCI_ATTR_ROW_COUNT` and the row count returned is larger than `UB4MAXVAL`, then one or both of the following errors may be returned:

    ORA-03148. OCI_ATTR_ROW_COUNT cannot see row counts larger than UB4MAXVAL

Attribute Data Type
`ub8 *`

### A.10 Bind Handle Attributes

Lists and describes bind handle attributes.

The following attributes are used for the bind handle.

#### OCI_ATTR_CHAR_COUNT

Mode
WRITE

Description
Sets the number of characters in character type data.

**See Also:**

[Buffer Expansion During OCI Binding](binding-and-defining-in-oci.md)

Attribute Data Type
`ub4 *`

#### OCI_ATTR_CHARSET_FORM

Mode
READ/WRITE

Description
Character set form of the bind handle. The default form is `SQLCS_IMPLICIT`. Setting this attribute causes the bind handle to use the database or national character set on the client side. Set this attribute to `SQLCS_NCHAR` for the national character set or `SQLCS_IMPLICIT` for the database character set.

Attribute Data Type
`ub1 *`

#### OCI_ATTR_CHARSET_ID

Mode
READ/WRITE

Description
Character set ID of the bind handle. If the character set of the input data is UTF-16, the user must set the character set ID to `OCI_UTF16ID` (replaces the deprecated `OCI_UC2SID`, which is retained for backward compatibility). The bind value buffer is assumed to be a `utext` buffer, so length semantics for input length pointers and return values changes to character semantics (number of `utext`s). However, the size of the bind value buffer in the preceding `OCIBind` call must be stated in bytes.

If `OCI_ATTR_CHARSET_FORM` is set, then `OCI_ATTR_CHARSET_ID` should be set only afterward. Setting `OCI_ATTR_CHARSET_ID` before setting `OCI_ATTR_CHARSET_FORM` causes unexpected results.

**See Also:**

[Character Conversion in OCI Binding and Defining](binding-and-defining-in-oci.md)

Attribute Data Type
`ub2 *`

#### OCI_ATTR_COLLATION_ID

####

Mode
READ/WRITE

Description
Sets the derived collation of a placeholder expression corresponding to this bind handle in a SQL statement. The attribute is relevant only for bind variables with character data types.

You can set the `OCI_ATTR_COLLATION_ID` attribute on a bind variable handle to any of the supported collation IDs. Collation IDs of both named collations and pseudo-collations are allowed. The attribute value is passed to the server with other bind information and the corresponding bind variable reference, formally known as SQL placeholder expression, assumes the provided collation at the coercibility level 0. If the attribute value is `OCI_COLLATION_NONE` (the default value), the collation of the bind variable is `USING_NLS_COMP` at the coercibility level 4.

OCI does not check whether the collation is valid for a given data type of a bind variable. If `OCI_ATTR_COLLATION_ID` is set for a non-character data type variable, it is ignored by the server.

Collation of bind variables is currently ignored in PL/SQL expressions. For forward compatibility reasons, the `OCI_ATTR_COLLATION_ID` attribute should not be set for bind variables passed to an anonymous PL/SQL block, unless the variables are referenced exclusively in SQL statements.

**Note:**

You can use the SQL built-in functions `NLS_COLLATION_ID` and `NLS_COLLATION_NAME` to map between values of the attribute, which are collation IDs, and collation names used in SQL syntax.

**See Also:**

- [Column Attributes](describing-schema-metadata.md)

- [Oracle Database Globalization Support Guide](../nlspg/appendix-C-collation-derivation-and-determination-rules-for-SQL-operations.md) for information on how this set collation influences query processing

Attribute Data Type
`ub4 *`

#### OCI_ATTR_MAXCHAR_SIZE

Mode
WRITE

Description
Sets the number of characters that an application reserves on the server to store the data being bound.

**See Also:**

[About Using the OCI_ATTR_MAXCHAR_SIZE Attribute](binding-and-defining-in-oci.md)

Attribute Data Type
`sb4 *`

#### OCI_ATTR_MAXDATA_SIZE

Mode
READ/WRITE

Description
Sets the maximum number of bytes allowed in the buffer on the server side to accommodate client-side bind data after character set conversions.

**See Also:**

[About Using the OCI_ATTR_MAXDATA_SIZE Attribute](binding-and-defining-in-oci.md)

Attribute Data Type
`sb4 *`

#### OCI_ATTR_PDPRC

Mode
WRITE

Description
Specifies packed decimal precision. For `SQLT_PDN` values, the precision should be equal to `2*(value_sz-1)`. For `SQLT_SLS` values, the precision should be equal to `(value_sz-1)`.

After a bind or define, this value is initialized to zero. The `OCI_ATTR_PDPRC` attribute should be set first, followed by `OCI_ATTR_PDSCL`. If either of these values must be changed, first perform a rebind/redefine operation, and then reset the two attributes in order.

Attribute Data Type
`ub2 *`

#### OCI_ATTR_PDSCL

Mode
WRITE

Description
Specifies the scale for packed decimal values.

After a bind or define, this value is initialized to zero. The `OCI_ATTR_PDPRC` attribute should be set first, followed by `OCI_ATTR_PDSCL`. If either of these values must be changed, first perform a rebind/redefine operation, and then reset the two attributes in order.

Attribute Data Type
`sb2 *`

#### OCI_ATTR_ROWS_RETURNED

Mode
READ

Description
This attribute returns the number of rows that will be returned in the current iteration when you are in the `OUT` callback function for binding a DML statement with a `RETURNING` clause.

Attribute Data Type
`ub4 *`

### A.11 Define Handle Attributes

Lists and describes define handle attributes.

The following attributes are used for the define handle.

#### OCI_ATTR_CHAR_COUNT

Mode
WRITE

Description
This attribute is deprecated.

Sets the number of characters in character type data. This specifies the number of characters desired in the define buffer. The define buffer length as specified in the define call must be greater than number of characters.

Attribute Data Type
`ub4 *`

#### OCI_ATTR_CHARSET_FORM

Mode
READ/WRITE

Description
The character set form of the define handle. The default form is `SQLCS_IMPLICIT`. Setting this attribute causes the define handle to use the database or national character set on the client side. Set this attribute to `SQLCS_NCHAR` for the national character set or `SQLCS_IMPLICIT` for the database character set.

Attribute Data Type
`ub1 *`

#### OCI_ATTR_CHARSET_ID

Mode
READ/WRITE

Description
The character set ID of the define handle. If the character set of the output data should be UTF-16, the user must set the character set IDOTT to `OCI_UTF16ID`. The define value buffer is assumed to be a `utext` buffer, so length semantics for indicators and return values changes to character semantics (number of utexts). However, the size of the define value buffer in the preceding `OCIDefine` call must be stated in bytes.

If `OCI_ATTR_CHARSET_FORM` is set, then `OCI_ATTR_CHARSET_ID` should be set only afterward. Setting `OCI_ATTR_CHARSET_ID` before setting `OCI_ATTR_CHARSET_FORM` causes unexpected results.

**See Also:**

[Character Conversion in OCI Binding and Defining](binding-and-defining-in-oci.md)

Attribute Data Type
`ub2 *`

#### OCI_ATTR_LOBPREFETCH_LENGTH

Mode
READ/WRITE

Description
Specifies if the LOB length and the chunk size for the LOB locators should be prefetched along with the descriptor if the column is a LOB column. Setting it to `TRUE` will enable the prefetching and this attribute setting is also required for prefetching the LOB data using the attribute `OCI_ATTR_LOBPREFETCH_SIZE`.

Attribute Data Type
`boolean */boolean`

#### OCI_ATTR_LOBPREFETCH_SIZE

Mode
READ/WRITE

Description
Overrides the default cache buffer size for the LOB locators to be fetched from a particular column along with the descriptor. This requires the attribute `OCI_ATTR_LOBPREFETCH_LENGTH` to be set to `TRUE`.

Attribute Data Type
`ub4 *``/ub4`

#### OCI_ATTR_MAXCHAR_SIZE

Mode
WRITE

Description
Specifies the maximum number of characters that the client application allows in the define buffer.

**See Also:**

[About Using the OCI_ATTR_MAXCHAR_SIZE Attribute](binding-and-defining-in-oci.md)

Attribute Data Type
`sb4 *`

#### OCI_ATTR_PDPRC

Mode
WRITE

Description
Specifies packed decimal precision. For SQLT_PDN values, the precision should be equal to `2*(value_sz-1)`. For SQLT_SLS values, the precision should be equal to `(value_sz-1)`.

After a bind or define, this value is initialized to zero. The `OCI_ATTR_PDPRC` attribute should be set first, followed by `OCI_ATTR_PDSCL`. If either of these values must be changed, first perform a rebind/redefine operation, and then reset the two attributes in order.

Attribute Data Type
`ub2 *`

#### OCI_ATTR_PDSCL

Mode
WRITE

Description
Specifies the scale for packed decimal values.

After a bind or define, this value is initialized to zero. The `OCI_ATTR_PDPRC` attribute should be set first, followed by `OCI_ATTR_PDSCL`. If either of these values must be changed, first perform a rebind/redefine operation, and then reset the two attributes in order.

Attribute Data Type
`sb2 *`

### A.12 Describe Handle Attributes

Lists and describes describe handle attributes.

The following attributes are used for the describe handle.

#### OCI_ATTR_PARAM

Mode
READ

Description
Points to the root of the description. Used for subsequent calls to [OCIAttrGet()](handle-and-descriptor-functions.md) and [OCIParamGet()](handle-and-descriptor-functions.md).

Attribute Data Type
`ub4 *`

#### OCI_ATTR_PARAM_COUNT

Mode
READ

Description
Returns the number of parameters in the describe handle. When the describe handle is a description of the select list, this refers to the number of columns in the select list.

Attribute Data Type
`ub4 *`

#### OCI_ATTR_SHOW_INVISIBLE_COLUMNS

Mode
WRITE

Description
This attribute requests [OCIDescribeAny()](bind-define-describe-functions.md) to also get the metadata for invisible columns. You can use [OCIAttrGet()](handle-and-descriptor-functions.md) to determine whether a column is invisible or not.

Attribute Data Type
`boolean *`

Example
    boolean showInvisibleCols = TRUE;
    ub1 colInvisible[MAX_COLS];
    OCIAttrSet(descHandle, OCI_HTYPE_DESCRIBE, &showInvisibleCols, 0,
                OCI_ATTR_SHOW_INVISIBLE_COLUMNS, errHandle);
    if (rc = OCIDescribeAny(svcHandle, errHandle, (dvoid*)table,
                            strlen(table), OCI_OTYPE_NAME, 1,
                            OCI_PTYPE_TABLE, descHandle))
    {
      OCIHandleFree(descHandle, OCI_HTYPE_DESCRIBE);
      return OCI_ERROR;
    }

    /* Get the number of columns. */

    OCIAttrGet(parHandle, OCI_DTYPE_PARAM, &nCols, 0,
               OCI_ATTR_NUM_COLS, errHandle);

    /* Get the column list. */

    OCIAttrGet(parHandle, OCI_DTYPE_PARAM, &lstHandle, 0,
               OCI_ATTR_LIST_COLUMNS, errHandle);

    /* Loop through the columns. */
    for (i = 1; i <= nCols; i++)
    {
      OCIParamGet(lstHandle, OCI_DTYPE_PARAM, errHandle,
                  (dvoid*)&colHandle, i);
      OCIAttrGet(colHandle, OCI_DTYPE_PARAM, &colName[i-1], &len,
                  OCI_ATTR_NAME, errHandle);
      OCIAttrGet(colHandle, OCI_DTYPE_PARAM, &(colType[i-1]), 0,
                  OCI_ATTR_DATA_TYPE, errHandle);
      OCIAttrGet(colHandle, OCI_DTYPE_PARAM, &colInvisible[i-1], 0,
                  OCI_ATTR_SHOW_INVISIBLE_COLUMNS, errHandle);
      if (colInvisible & OCI_ATTR_SHOW_INVISIBLE_COLUMNS)
         printf("Column is invisible\n");
    }

### A.13 Parameter Descriptor Attributes

Lists and describes parameter descriptor attributes.

The following attributes are used for the parameter descriptor.

**See Also:**

[Describing Schema Metadata](describing-schema-metadata.md) for a detailed list of parameter descriptor attributes.

### A.14 Shard Instance Descriptor Attributes

Lists and describes shard instance descriptor attributes.

This descriptor is returned by `OCIShardInstancesGet()` used only by custom pools, which essentially contains the instance name where the data matching the provided sharding key resides, and an indication if that shard is writable on that instance.

The following attributes are used for the shard instance descriptor.

#### OCI_ATTR_INSTNAME

Mode
READ

Description
This attribute can be used to find the shard instance name out of a shard instance descriptor that is filed by an `OCIShardInstancesGet()` call. This attribute can also be used on the service context to return the shard instance name for a given connection. When called as an event handle attribute, `OCIAttrGet()` retrieves the name of the instance that has been affected by this event. This is also a server handle attribute.

Attribute Data Type
`oratext **`

Example
     OCIAttrGet(shardInstance,
               (ub4) OCI_DTYPE_SHARD_INST,(dvoid *)&iName, (ub4 *)&iNameLen,
               OCI_ATTR_INSTNAME, (OCIError *)errhp);

#### OCI_ATTR_SHARD_HAS_WRITABLECHUNK

Mode
READ

Description
Returns `TRUE` if the shard instance has writable chunks. For custom pool implementations, this helps the pool to determine if a connection to that particular shard instance can be dispensed. If the application can work with read only shards instead of writable chunks, the pool can dispense it; otherwise, it can implement a retrial logic to try `OCIShardInstancesGet()` until it returns shard instance information having writable chunks. This feature is helpful during chunk migrations.

Attribute Data Type
`boolean *`

### A.15 SODA Document Handle Attributes

The `OCISodaDoc` document handle has the following attributes. The key, last-modified time stamp, creation time stamp, version, content, and media type attributes represent document components. JSON charset ID is a read-only character set ID set by SODA. Detect JSON Encoding is a flag for working with Unicode encoding JSON content.

The following attributes are document components:

- Key — `OCI_ATTR_SODA_KEY`

- Last-modified time stamp — `OCI_ATTR_SODA_LASTMOD_TIMESTAMP`

- Creation time stamp — `OCI_ATTR_SODA_CREATE_TIMESTAMP`

- Version — `OCI_ATTR_SODA_VERSION`

- Content — `OCI_ATTR_SODA_CONTENT`

- Media type ("application/json" for JSON documents) — `OCI_ATTR_SODA_MEDIA_TYPE`

The following attributes are not document components, but instead used to describe other characteristics of the document:

- JSON character set ID — `OCI_ATTR_SODA_JSON_CHARSET_ID`

- Detect JSON encoding — `OCI_ATTR_SODA_DETECT_JSON_ENC`

#### OCI_ATTR_SODA_KEY

Mode
READ/WRITE

Description
The unique key for the document.

Attribute Data Type
`oratext *`

#### OCI_ATTR_SODA_LASTMOD_TIMESTAMP

Mode
READ

Description
The last-modified time stamp for the document in ISO format. The value is `NULL` if the metadata of the collection does not support it.

Attribute Data Type
`oratext *`

#### OCI_ATTR_SODA_CREATE_TIMESTAMP

Mode
READ

Description
The creation time stamp for the document in ISO format. The value is `NULL` if the metadata of the collection does not support it.

Attribute Data Type
`oratext *`

#### OCI_ATTR_SODA_VERSION

Mode
READ

Description
The document version. The value is `NULL` if the metadata of the collection does not support it.

Attribute Data Type
`oratext *`

#### OCI_ATTR_SODA_CONTENT

Mode
READ/WRITE

Description
The document content. Note that for `OCISodaInsertAndGet()`, `OCISodaInsertAndGetWithCtnt()`, and `OCISodaReplOneAndGetWithKey()`, these functions return the handle to the result document containing all components except the content, so this attribute is not needed for these calls.

Attribute Data Type
`oratext *`

#### OCI_ATTR_SODA_JSON_CHARSET_ID

Mode
READ

Description
The character set ID of the document's content. This could potentially be different from the local (client-side) character set ID.

Attribute Data Type
`ub2`

#### OCI_ATTR_SODA_DETECT_JSON_ENC

Mode
READ/WRITE

Description
Returns `TRUE` if the document is in detect encoding mode.

Attribute Data Type
`boolean`

#### OCI_ATTR_SODA_MEDIA_TYPE

Mode
READ/WRITE

Description
The media type for the document.

Attribute Data Type
`oratext *`

### A.16 SODA Collection Handle Attributes

Lists and describes the OCI SODA collection handle attributes.

Collection is composed of multiple components. `OCI_ATTR_SODA_DESCRIPTOR` is a special case. When you pass `OCI_ATTR_SODA_DESCRIPTOR` to `OCIAttrGet()`, you get metadata for the collection in one chunk, in JSON form. In addition, `OCI_ATTR_SODA_COLL_NAME`, the collection name, is not part of collection metadata (it is not a collection metadata component). It is stored separately in SODA, so it is also a special case. If you use `OCI_ATTR_SODA_DESCRIPTOR` to fetch collection metadata in JSON, the collection name is not included.

The rest of these attributes fetch individual metadata components. They are provided for convenience (alternatively, you could get collection metadata using `OCI_ATTR_SODA_DESCRIPTOR`. That metadata contains all of the components, but it is in JSON form, so your application might need to parse the JSON to retrieve values of specific components). All of these attributes are `READ` only and allow you to examine the metadata for your existing collection.

**See Also:**

[Oracle Database Introduction to Simple Oracle Document Access (SODA)](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDI-GUID-BE42F8D3-B86B-43B4-B2A3-5760A4DF79FB) for reference information about these SODA collection metadata components. All the metadata components that correspond to these collection handle attributes (except for `OCI_ATTR_SODA_DESCRIPTOR` and `OCI_ATTR_SODA_COLL_NAME`), are described in this chapter.

The following is a list of all collection attributes followed by descriptions of each.

- Collection Name — `OCI_ATTR_SODA_COLL_NAME`

- Descriptor — `OCI_ATTR_SODA_DESCRIPTOR`

- Schema — `OCI_ATTR_SODA_SCHEMA`

- Table Name — `OCI_ATTR_SODA_TABLE_NAME`

- View Name — `OCI_ATTR_SODA_VIEW_NAME`

- Key Column Name — `OCI_ATTR_SODA_KEY_COL_NAME`

- Key Column SQL Type — `OCI_ATTR_SODA_KEY_SQL_TYPE`

- Key Column Max Length — `OCI_ATTR_SODA_KEY_MAX_LEN`

- Key Column Assignment Method — `OCI_ATTR_SODA_KEY_ASSIGN_METHOD`

- Key Column Sequence Name — `OCI_ATTR_SODA_KEY_SEQ_NAME`

- Content Column Name — `OCI_ATTR_SODA_CTNT_COL_NAME`

- Content Column SQL Type — `OCI_ATTR_SODA_CTNT_SQL_TYPE`

- Content Column Max Length — `OCI_ATTR_SODA_CTNT_MAX_LEN`

- Content Column JSON Validation — `OCI_ATTR_SODA_CTNT_VALIDATION`

- Content Column SecureFiles LOB Compression — `OCI_ATTR_SODA_CTNT_COMPRESS`

- Content Column SecureFiles LOB Cache — `OCI_ATTR_SODA_CTNT_CACHE`

- Content Column SecureFiles LOB Encryption — `OCI_ATTR_SODA_CTNT_ENCRYPT`

- Version Column Name — `OCI_ATTR_SODA_VERSION_COL_NAME`

- Version Generation Method — `OCI_ATTR_SODA_VERSION_METHOD`

- Last-Modified Time Stamp Column Name — `OCI_ATTR_SODA_MODTIME_COL_NAME`

- Last-Modified Column Index Name — `OCI_ATTR_SODA_MODTIME_INDEX`

- Creation Time Stamp Column Name — `OCI_ATTR_SODA_CRTIME_COL_NAME`

- Media Type Column Name — `OCI_ATTR_SODA_MTYPE_COL_NAME`

- Read Only — `OCI_ATTR_SODA_READONLY`

#### OCI_ATTR_SODA_COLL_NAME

Mode
READ

Description
Specifies the name of the collection.

Attribute Data Type
`oratext *`

#### OCI_ATTR_SODA_DESCRIPTOR

Mode
READ

Description
Specifies the descriptor to which the collection is mapped.

Attribute Data Type
`oratext *`

#### OCI_ATTR_SODA_SCHEMA

Mode
READ

Description
Specifies the name of the Oracle Database schema that owns the table or view to which the collection is mapped.

Attribute Data Type
`oratext *`

#### OCI_ATTR_SODA_TABLE_NAME

Mode
READ

Description
Specifies the name of the table to which the collection is mapped.

Attribute Data Type
`oratext *`

#### OCI_ATTR_SODA_VIEW_NAME

Mode
READ

Description
Specifies the name of the view to which the collection is mapped.

Attribute Data Type
`oratext *`

#### OCI_ATTR_SODA_KEY_COL_NAME

Mode
READ

Description
Specifies the name of the column that stores the document key.

Attribute Data Type
`oratext *`

#### OCI_ATTR_SODA_KEY_SQL_TYPE

Mode
READ

Description
Specifies the SQL data type of the column that stores the document key. Valid values include:

- `SQLT_CHR` for `VARCHAR2`

- `SLQT_BIN` for `RAW`

- `SQLT_NUM` for `NUMBER`

Attribute Data Type
`ub1`

#### OCI_ATTR_SODA_KEY_MAX_LEN

Mode
READ

Description
Specifies the maximum length of the key column in bytes. This component applies only to keys of type `VARCHAR2`. At least 32 bytes if key assignment method is `UUID` or `GUID`. See OCI_ATTR_SODA_KEY_ASSIGN_METHOD.

**See Also:**

OCI_ATTR_SODA_KEY_SQL_TYPE

Attribute Data Type
`ub4`

#### OCI_ATTR_SODA_KEY_ASSIGN_METHOD

Mode
READ

Description
Specifies the OCI value for the corresponding value for this component method used to assign keys to objects that are inserted into the collection. `UUID`, `GUID`, `SEQUENCE`, and `CLIENT` are the corresponding valid values for this component, as it would appear in the JSON metadata. The valid values for this attribute include:

- `OCI_SODA_KEY_METHOD_UUID` for `UUID`, which is the corresponding value for this component, as it would appear in the JSON metadata.

- `OCI_SODA_KEY_METHOD_GUID` for `GUID`, which is the corresponding value for this component, as it would appear in the JSON metadata.

- `OCI_SODA_KEY_METHOD_SEQUENCE` for `SEQUENCE`, which is the corresponding value for this component, as it would appear in the JSON metadata.

- `OCI_SODA_KEY_METHOD_CLIENT` for `CLIENT`, which is the corresponding value for this component, as it would appear in the JSON metadata.

See [Oracle Database Introduction to Simple Oracle Document Access (SODA)](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDI-GUID-BE42F8D3-B86B-43B4-B2A3-5760A4DF79FB) for more information about key assignment methods for the collection metadata component Key Column Assignment Method.

Attribute Data Type
`ub1`

#### OCI_ATTR_SODA_KEY_SEQ_NAME

Mode
READ

Description
Specifies the name of the database sequence that generates keys for documents that are inserted into a collection if the key assignment method is SEQUENCE.

**Note:**

If you drop a collection using SODA for OCI, the sequence used for key generation is not dropped. This is because it might not have been created using SODA for OCI. To drop the sequence, use SQL command `DROP SEQUENCE`, after first dropping the collection.

**See Also:**

- OCI_ATTR_SODA_KEY_ASSIGN_METHOD

- [Oracle Database SQL Language Reference](../sqlrf/DROP-SEQUENCE.md) for information about `DROP SEQUENCE`

- [Oracle Database Concepts](../cncpt/partitions-views-and-other-schema-objects.md)

Attribute Data Type
`oratext *`

#### OCI_ATTR_SODA_CTNT_COL_NAME

Mode
READ

Description
Specifies the name of the column that stores the document content.

Attribute Data Type
`oratext *`

#### OCI_ATTR_SODA_CTNT_SQL_TYPE

Mode
READ

Description
Specifies the SQL data type of the column that stores the document content. Valid values include:

- `SQLT_CHR` for `VARCHAR2`

- `SQLT_CLOB` for `CLOB`,

- `SQLT_BLOB` for `BLOB`

- `SQLT_JSON` for `JSON`

Attribute Data Type
`ub1`

#### OCI_ATTR_SODA_CTNT_MAX_LEN

Mode
READ

Description
Specifies the maximum length of the content column in bytes. This component applies only to content of type `VARCHAR2`. The default value is 4000 bytes.

**See Also:**

- OCI_ATTR_SODA_CTNT_SQL_TYPE

- [Oracle Database SQL Language Reference](../sqlrf/Data-Types.md) for information about extended data types

Attribute Data Type
`ub4`

#### OCI_ATTR_SODA_CTNT_VALIDATION

Mode
READ

Description
Specifies the OCI value for the corresponding syntax to which JSON content must conform. The valid values for this attribute include:

- `OCI_SODA_JSON_VALIDATION_STRICT` for `STRICT`, which is the corresponding value as it appears in the JSON collection metadata.

  See [Oracle Database Introduction to Simple Oracle Document Access (SODA)](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDI-GUID-BE42F8D3-B86B-43B4-B2A3-5760A4DF79FB) for more information about the `STRICT` syntax.

- `OCI_COLL_JSON_VALIDATION_LAX` for `LAX`, which is the corresponding value as it appears in the JSON collection metadata.

  See [Oracle Database Introduction to Simple Oracle Document Access (SODA)](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDI-GUID-BE42F8D3-B86B-43B4-B2A3-5760A4DF79FB) for more information about the `LAX` syntax.

- `OCI_SODA_JSON_VALIDATION_STD` for `STANDARD`, which is the corresponding value as it appears in the JSON collection metadata.

  See [Oracle Database Introduction to Simple Oracle Document Access (SODA)](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDI-GUID-BE42F8D3-B86B-43B4-B2A3-5760A4DF79FB) for more information about the `STANDARD` syntax.

Attribute Data Type
`ub4`

#### OCI_ATTR_SODA_CTNT_COMPRESS

Mode
READ

Description
Specifies the OCI value for the corresponding value for the SecureFiles LOB compression setting as it appears in the JSON collection metadata. The valid values for this attribute include:

- `OCI_SODA_LOB_COMPRESS_NONE` for `NONE`, which is the corresponding value as it appears in the JSON collection metadata.

- `OCI_SODA_LOB_COMPRESS_HIGH` for `HIGH`, which is the corresponding value as it appears in the JSON collection metadata.

- `OCI_SODA_LOB_COMPRESS_MEDIUM` for `MEDIUM`, which is the corresponding value as it appears in the JSON collection metadata.

- `OCI_SODA_LOB_COMPRESS_LOW` for `LOW`, which is the corresponding value as it appears in the JSON collection metadata.

**See Also:**

[Oracle Database SecureFiles and Large Objects Developer's Guide](../adlob/using-oracle-LOBs-storage.md) for information about SecureFiles LOB storage

Attribute Data Type
`ub1`

#### OCI_ATTR_SODA_CTNT_CACHE

Mode
READ

Description
Specifies the SecureFiles LOB cache setting.

**See Also:**

[Oracle Database SecureFiles and Large Objects Developer's Guide](../adlob/using-oracle-LOBs-storage.md) for information about SecureFiles LOB storage

Attribute Data Type
`boolean`

#### OCI_ATTR_SODA_CTNT_ENCRYPT

**Note:**

The deprecated algorithms for `DBMS_CRYPTO` and native network encryption include MD4, MD5, DES, 3DES, and RC4-related algorithms as well as 3DES for Transparent Data Encryption (TDE). Removing older, less secure cryptography algorithms prevents accidental use of these algorithms. To meet your security requirements, Oracle recommends that you use more modern cryptography algorithms, such as the Advanced Encryption Standard (AES).

As a consequence of this deprecation, Oracle recommends that you review your network encryption configuration to see if you have specified use of any of the deprecated algorithms. If any are found, then switch to using a more modern cipher, such as AES. Also, if you are currently using 3DES encryption for your TDE deployment, then you should plan to migrate to a more modern algorithm such as AES. For more information, refer to Oracle Database Security Guide

Mode
READ

Description
Specifies the OCI value for the corresponding value for the SecureFiles LOB encryption setting as it appears in the JSON collection metadata. The valid values for this attribute include:

- `OCI_SODA_LOB_ENCRYPT_NONE` for `NONE`, which is the corresponding value as it appears in the JSON collection metadata.

- `OCI_SODA_LOB_ENCRYPT_3DES168` for `3DES168`, which is the corresponding value as it appears in the JSON collection metadata.

- `OCI_SODA_LOB_ENCRYPT_AES128` for `AES128`, which is the corresponding value as it appears in the JSON collection metadata.

- `OCI_SODA_LOB_ENCRYPT_AES192` for `AES192`, which is the corresponding value as it appears in the JSON collection metadata.

- `OCI_SODA_LOB_ENCRYPT_AES256` for `AES256`, which is the corresponding value as it appears in the JSON collection metadata.

**See Also:**

[Oracle Database SecureFiles and Large Objects Developer's Guide](../adlob/using-oracle-LOBs-storage.md) for information about SecureFiles LOB storage

Attribute Data Type
`ub1`

#### OCI_ATTR_SODA_VERSION_COL_NAME

Mode
READ

Description
Specifies the name of the column that stores the document version.

Attribute Data Type
`oratext *`

#### OCI_ATTR_SODA_VERSION_METHOD

Mode
READ

Description
Specifies the OCI value for the corresponding method used to compute version values for objects when they are inserted into a collection or replaced as it appears in the JSON collection metadata. The valid values for this attribute include:

- `OCI_SODA_VERSION_UUID` for `UUID`, which is the corresponding value as it appears in the JSON collection metadata

- `OCI_SODA_VERSION_TIMESTAMP` for `TIMESTAMP`, which is the corresponding value as it appears in the JSON collection metadata

- `OCI_SODA_VERSION_MD5` for `MD5`, which is the corresponding value as it appears in the JSON collection metadata

- `OCI_SODA_VERSION_SHA256` for `SHA256`, which is the corresponding value as it appears in the JSON collection metadata

- `OCI_SODA_VERSION_SEQUENTIAL` for `SEQUENTIAL`, which is the corresponding value as it appears in the JSON collection metadata

- `OCI_SODA_VERSION_NONE` for `NONE`, which is the corresponding value as it appears in the JSON collection metadata

See [Oracle Database Introduction to Simple Oracle Document Access (SODA)](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDI-GUID-BE42F8D3-B86B-43B4-B2A3-5760A4DF79FB) for more information about version generation methods for the collection metadata component Version Column Generation Method.

Attribute Data Type
`ub1`

#### OCI_ATTR_SODA_MODTIME_COL_NAME

Mode
READ

Description
Specifies the name of the column that stores the last-modified time stamp of the document.

Attribute Data Type
`oratext *`

#### OCI_ATTR_SODA_MODTIME_INDEX

Mode
READ

Description
Specifies the name of the index on the last-modified column.

Attribute Data Type
`oratext *`

#### OCI_ATTR_SODA_CRTIME_COL_NAME

Mode
READ

Description
Specifies the name of the column that stores the creation time stamp of the document.

Attribute Data Type
`oratext *`

#### OCI_ATTR_SODA_MTYPE_COL_NAME

Mode
READ

Description
Specifies the name of the column that stores the media type of the document. A media type column is needed if the collection is to be heterogeneous, that is, it can store documents other than JSON.

Attribute Data Type
`oratext *`

#### OCI_ATTR_SODA_READONLY

Mode
READ

Description
Specifies whether the collection is read-only.

Attribute Data Type
`boolean`

### A.17 SODA Output Options Handle Attributes

Lists and describes the OCI SODA Output Options handle attributes. This handle is used to return the number of documents processed by a bulk operation. Currently, it is returned only by bulk insert methods.

#### OCI_ATTR_SODA_DOC_COUNT

Mode
READ

Description
Number of documents processed successfully by the statement.

Attribute Data Type
`ub8 *`

### A.18 SODA Operation Options Handle Attributes

Lists and describes the OCI SODA Operation Options handle attributes.

Operation options handle is used to drive read and write SODA operations. The attributes that can be set on operation options handle represent the conditions of the operation. After the attributes are set, the operation options handle is passed to SODA functions perform the actual read or write operations such as finds, replaces, removes, and so on.

The attributes listed in this section can be set on the `OCISodaOperationOptions` handle using the standard OCIAttrSet methods. However, if you want to set an array of keys on the `OCISodaOperationOptions` handle, then you must use `OCISodaOperKeysSet()` method.

#### OCI_ATTR_SODA_KEY

Mode
READ/WRITE

Description
Key to be used for the operation.

**Note:**

If you use function `OCIAttrSet()` to set attribute `OCI_ATTR_SODA_KEY` on an operation-options handle, and you also use function `OCISodaOperKeysSet()` to set multiple keys on the same handle, then only the latest of the two settings takes effect. The effect of the first function invoked is overridden by the effect of the second.

Attribute Data Type
`oratext **/oratext *`

#### OCI_ATTR_SODA_VERSION

Mode
READ/WRITE

Description
Version to be used for the operation.

Attribute Data Type
`oratext **/oratext *`

#### OCI_ATTR_SODA_FILTER

Mode
READ/WRITE

Description
Filter to be used for the operation.

Attribute Data Type
`oratext **/oratext *`

#### OCI_ATTR_SODA_SKIP

Mode
READ/WRITE

Description
Number of document results to skip.

Attribute Data Type
`ub4 */ub4`

#### OCI_ATTR_SODA_LIMIT

Mode
READ/WRITE

Description
Number of documents to limit in the operation results.

Attribute Data Type
`ub4 */ub4`

#### OCI_ATTR_SODA_AS_OF_SCN

Mode
READ/WRITE

Description
Oracle Database release 19.11 introduces `OCI_ATTR_SODA_AS_OF_SCN` attribute. The System Change Number (SCN) can be used as the flashback parameter for the operation.

Attribute Data Type
`ub8 */ub8`

#### OCI_ATTR_SODA_AS_OF_TSTAMP

Mode
READ/WRITE

Description
Oracle Database release 19.11 introduces `OCI_ATTR_SODA_AS_OF_TSTAMP` attribute. The timestamp value can be used as the flashback parameter for the operation.

Attribute Data Type
`oratext **/oratext *`

#### OCI_ATTR_SODA_LOCK

Mode
READ/WRITE

<!-- -->

Description
Oracle Database release 19.11 introduces `OCI_ATTR_SODA_LOCK` attribute . When this attribute is set, the rows are fetched for updation. The lock is released with a subsequent commit or rollback.

<!-- -->

Attribute Data Type
boolean \*/boolean

#### OCI_ATTR_SODA_HINT

Mode
READ/WRITE

<!-- -->

Description
Oracle Database release 19.11 introduces `OCI_ATTR_SODA_HINT` attribute. If this value is set, then the value of that attribute is pasted into the hint section of the underlying SQL statements.

Oracle Database release 19.11 introduces `OCISodaInsertAndGetWithOpts`, `OCISodaBulkInsertAndGetWithOpts`, and `OCISodaSaveAndGetWithOpts` new variants of the existing functions in order for the inserts and saves to accept hints, These variants take the `OCISodaOperationOptions` handle, and thus allow the passing of hints (they ignore all the other attributes that can be set on this handle).

The string value for key "hint" uses the SQL hint syntax (that is, the hint text, without the enclosing SQL comment syntax /\*+...\*/). Use only hint MONITOR (turn on monitoring) or NO_MONITOR (turn off monitoring). You can use this to pass any SQL hints, but MONITOR and NO_MONITOR are the useful ones for SODA, and an inappropriate hint can cause the optimizer to produce a suboptimal query plan.

Attribute Data Type
oratext \*\*/oratext \*

**See Also:**

- [OCISodaSaveAndGet()](oci-SODA-functions-listed.md)
- [OCISodaBulkInsertAndGet()](oci-SODA-functions-listed.md)
- [OCISodaInsertAndGet()](oci-SODA-functions-listed.md)
- [Finding Documents in Collections with SODA for C](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDC-GUID-0CD8625C-61DF-4B82-A93E-A3BB6B379A5E)
- [Removing Documents from a Collection with SODA for C](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDC-GUID-F3C144A6-7F15-4ABC-AE0E-5C962C5A7AFE)
- [Replacing Documents in a Collection with SODA for C](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDC-GUID-25680AEE-1D25-4FF5-803D-7A500A9F2DF6)

### A.19 LOB Descriptor and LOB Locator Attributes

Lists and describes LOB locator attributes.

The following attributes are used for the parameter descriptor.

#### OCI_ATTR_LOBEMPTY

Mode
WRITE

Description
Sets the internal LOB locator to empty. The locator can then be used as a bind variable for an `INSERT` or `UPDATE` statement to initialize the LOB to empty. Once the LOB is empty, [OCILobWrite2()](lob-functions.md) or [OCILobWrite()](deprecated-oci-functions.md) (deprecated) can be called to populate the LOB with data. This attribute is only valid for internal LOBs (that is, `BLOB`, `CLOB`, `NCLOB`).

Applications should pass the address of a `ub4` that has a value of 0; for example, declare the following:

    ub4 lobEmpty = 0

Then they should pass the address: `&lobEmpty`.

Attribute Data Type
`ub4 *`

#### OCI_ATTR_LOB_REMOTE

Mode
READ

Description
Determines whether the LOB locator belongs to a local database table or a remote database table. The value `TRUE` indicates that the LOB locator is from a remote database table. The application must fetch the LOB descriptor from the database before using this attribute.

Only the server can set this value. If an application tries to set this attribute, then an `ORA-24315` error is raised.

Attribute Data Type
`boolean`

#### OCI_ATTR_LOB_TYPE

Mode
READ

Description
Gets the LOB type from the LOB descriptor.

Attribute Data Type
`ub2`

### A.20 Complex Object Attributes

Lists and describes complex object attributes.

The following attributes are used for complex objects.

**See Also:**

[Complex Object Retrieval](oci-object-relational-programming.md)

#### A.20.1 Complex Object Retrieval Handle Attributes

Lists and describes complex object retrieval handle attributes.

The following attributes are used for the complex object retrieval handle.

##### OCI_ATTR_COMPLEXOBJECT_LEVEL

Mode
WRITE

Description
The depth level for complex object retrieval.

Attribute Data Type
`ub4 *`

##### OCI_ATTR_COMPLEXOBJECT_COLL_OUTOFLINE

Mode
WRITE

Description
Whether to fetch collection attributes in an object type out-of-line.

Attribute Data Type
`ub1 *`

#### A.20.2 Complex Object Retrieval Descriptor Attributes

Lists and describes complex object retrieval descriptor attributes.

The following attributes are used for the complex object retrieval descriptor.

##### OCI_ATTR_COMPLEXOBJECTCOMP_TYPE

Mode
WRITE

Description
A type of `REF` to follow for complex object retrieval.

Attribute Data Type
`void *`

##### OCI_ATTR_COMPLEXOBJECTCOMP_TYPE_LEVEL

Mode
WRITE

Description
Depth level for the following `REF`s of type `OCI_ATTR_COMPLEXOBJECTCOMP_TYPE`.

Attribute Data Type
`ub4 *`

### A.21 Database Advanced Queuing Descriptor Attributes

Lists and describes Database Advanced Queuing descriptor attributes

The following attributes are used for the database advanced queuing descriptor.

**See Also:**

[Oracle Database Advanced Queuing User's Guide](../adque/aq-introduction.md)

#### A.21.1 OCIAQEnqOptions Descriptor Attributes

Lists and describes OCIAQEnqOptions descriptor attributes.

The following attributes are properties of the `OCIAQEnqOptions` descriptor.

##### OCI_ATTR_MSG_DELIVERY_MODE

Mode
WRITE

Description
The enqueue call can enqueue a persistent or buffered message into a queue, by setting the `OCI_ATTR_MSG_DELIVERY_MODE` attribute in the `OCIAQEnqOptions` descriptor to `OCI_MSG_PERSISTENT` or `OCI_MSG_BUFFERED`, respectively. The default value for this attribute is `OCI_MSG_PERSISTENT`.

Attribute Data Type
`ub2`

##### OCI_ATTR_RELATIVE_MSGID

Mode
READ/WRITE

Description
This feature is deprecated and may be removed in a future release.

Specifies the message identifier of the message that is referenced in the sequence deviation operation. This value is valid if and only if `OCI_ENQ_BEFORE` is specified in `OCI_ATTR_SEQUENCE_DIVISION`. This value is ignored if the sequence deviation is not specified.

Attribute Data Type
`OCIRaw *`

##### OCI_ATTR_SEQUENCE_DEVIATION

Mode
READ/WRITE

Description
This feature is deprecated for new applications, but it is retained for compatibility.

It specifies whether the message being enqueued should be dequeued before other messages in the queue.

Attribute Data Type
`ub4`

Valid Values
The only valid values are:

- `OCI_ENQ_BEFORE` - The message is enqueued ahead of the message specified by `OCI_ATTR_RELATIVE_MSGID`.

- `OCI_ENQ_TOP` - The message is enqueued ahead of any other messages.

##### OCI_ATTR_TRANSFORMATION

Mode
READ/WRITE

Description
The name of the transformation that must be applied before the message is enqueued into the database. The transformation must be created using `DBMS_TRANSFORM`.

Attribute Data Type
`oratext *`

##### OCI_ATTR_VISIBILITY

Mode
READ/WRITE

Description
Specifies the transactional behavior of the enqueue request.

Attribute Data Type
`ub4`

Valid Values
The only valid values are:

- `OCI_ENQ_ON_COMMIT` - The enqueue is part of the current transaction. The operation is complete when the transaction commits. This is the default case.

- `OCI_ENQ_IMMEDIATE` - The enqueue is not part of the current transaction. The operation constitutes a transaction of its own.

#### A.21.2 OCIAQDeqOptions Descriptor Attributes

Lists and describes OCIAQDeqOptions descriptor attributes.

The following attributes are properties of the `OCIAQDeqOptions` descriptor.

##### OCI_ATTR_CONSUMER_NAME

Mode
READ/WRITE

Description
Name of the consumer. Only those messages matching the consumer name are accessed. If a queue is not set up for multiple consumers, this field should be set to `null`.

Attribute Data Type
`oratext *`

##### OCI_ATTR_CORRELATION

Mode
READ/WRITE

Description
Specifies the correlation identifier of the message to be dequeued. Special pattern-matching characters, such as the percent sign (%) and the underscore (\_), can be used. If multiple messages satisfy the pattern, the order of dequeuing is undetermined.

Attribute Data Type
`oratext *`

##### OCI_ATTR_DEQ_MODE

Mode
READ/WRITE

Description
Specifies the locking behavior associated with the dequeue.

Attribute Data Type
`ub4`

Valid Values
The only valid values are:

- `OCI_DEQ_BROWSE` - Read the message without acquiring any lock on the message. This is equivalent to a `SELECT` statement.

- `OCI_DEQ_LOCKED` - Read and obtain a write lock on the message. The lock lasts for the duration of the transaction. This is equivalent to a `SELECT` `FOR` `UPDATE` statement.

- `OCI_DEQ_REMOVE` - Read the message and update or delete it. This is the default. The message can be retained in the queue table based on the retention properties.

- `OCI_DEQ_REMOVE_NODATA` - Confirm receipt of the message, but do not deliver the actual message content.

##### OCI_ATTR_DEQ_MSGID

Mode
READ/WRITE

Description
Specifies the message identifier of the message to be dequeued.

Attribute Data Type
`OCIRaw *`

##### OCI_ATTR_DEQCOND

Mode
READ/WRITE

Description
This attribute is a Boolean expression similar to the `WHERE` clause of a SQL query. This Boolean expression can include conditions on message properties, user data properties (object payloads only), and PL/SQL or SQL functions.

To specify dequeue conditions on a message payload (object payload), use attributes of the object type in clauses. You must prefix each attribute with` tab.user_data` as a qualifier to indicate the specific column of the queue table that stores the payload.

The attribute cannot exceed 4000 characters. If multiple messages satisfy the dequeue condition, then the order of dequeuing is indeterminate, and the sort order of the queue is not honored.

Attribute Data Type
`oratext *`

Example
    checkerr(errhp, OCIAttrSet(deqopt, OCI_DTYPE_AQDEQ_OPTIONS,
             (dvoid *)"tab.priority between 2 and 4" ,
             strlen("tab.priority between 2 and 4"),
             OCI_ATTR_DEQCOND, errhp));

##### OCI_ATTR_MSG_DELIVERY_MODE

Mode
WRITE

Description
You can specify the dequeue call to dequeue persistent, buffered, or both kinds of messages from a queue, by setting the `OCI_ATTR_MSG_DELIVERY_MODE `attribute in the `OCIAQDeqOptions` descriptor to `OCI_MSG_PERSISTENT`, `OCI_MSG_BUFFERED`, or `OCI_MSG_PERSISTENT_OR_BUFFERED`, respectively. The default value for this attribute is `OCI_MSG_PERSISTENT`.

Attribute Data Type
`ub2`

##### OCI_ATTR_NAVIGATION

Mode
READ/WRITE

Description
Specifies the position of the message that is retrieved. First, the position is determined. Second, the search criterion is applied. Finally, the message is retrieved.

Attribute Data Type
`ub4`

Valid Values
The only valid values are:

- `OCI_DEQ_FIRST_MSG` - Retrieves the first available message that matches the search criteria. This resets the position to the beginning of the queue.

- `OCI_DEQ_NEXT_MSG` - Retrieves the next available message that matches the search criteria. If the previous message belongs to a message group, AQ retrieves the next available message that matches the search criteria and belongs to the message group. This is the default.

- `OCI_DEQ_NEXT_TRANSACTION` - Skips the remainder of the current transaction group (if any) and retrieves the first message of the next transaction group. This option can only be used if message grouping is enabled for the current queue.

- `OCI_DEQ_FIRST_MSG_MULTI_GROUP` - Indicates that a call to `OCIAQDeqArray()` resets the position to the beginning of the queue and dequeue messages (possibly across different transaction groups) that are available and match the search criteria, until reaching the `iters` limit. To distinguish between transaction groups, a new message property, `OCI_ATTR_TRANSACTION_NO`, is defined. All messages belonging to the same transaction group have the same value for this message property.

- `OCI_DEQ_NEXT_MSG_MULTI_GROUP` - Indicates that a call to `OCIAQDeqArray()` dequeues the next set of messages (possibly across different transaction groups) that are available and match the search criteria, until reaching the `iters` limit. To distinguish between transaction groups, a new message property, `OCI_ATTR_TRANSACTION_NO`, is defined. All messages belonging to the same transaction group have the same value for this message property.

##### OCI_ATTR_TRANSFORMATION

Mode
READ/WRITE

Description
The name of the transformation that must be applied after the message is dequeued but before returning it to the dequeuing application. The transformation must be created using `DBMS_TRANSFORM`.

Attribute Data Type
`oratext *`

##### OCI_ATTR_VISIBILITY

Mode
READ/WRITE

Description
Specifies whether the new message is dequeued as part of the current transaction. The visibility parameter is ignored when using the `BROWSE` mode.

Attribute Data Type
`ub4`

Valid Values
The only valid values are:

- `OCI_DEQ_ON_COMMIT` - The dequeue is part of the current transaction. This is the default.

- `OCI_DEQ_IMMEDIATE` - The dequeued message is not part of the current transaction. It constitutes a transaction on its own.

##### OCI_ATTR_WAIT

Mode
READ/WRITE

Description
Specifies the wait time if no message is currently available that matches the search criteria. This parameter is ignored if messages in the same group are being dequeued.

Attribute Data Type
`ub4`

Valid Values
Any `ub4` value is valid, but the following predefined constants are provided:

- `OCI_DEQ_WAIT_FOREVER` - Wait forever. This is the default.

- `OCI_DEQ_NO_WAIT` - Do not wait.

**Note:**

If the `OCI_DEQ_NO_WAIT` option is used to poll a queue, then messages are not dequeued after polling an empty queue. Use the `OCI_DEQ_FIRST_MSG` option instead of the default `OCI_DEQ_NEXT_MSG` setting of `OCI_ATTR_NAVIGATION`. You can also use a nonzero wait setting (1 is suggested) of `OCI_ATTR_WAIT` for the dequeue.

#### A.21.3 OCIAQMsgProperties Descriptor Attributes

Lists and describes OCIAQMsgProperties descriptor attributes.

The following attributes are properties of the `OCIAQMsgProperties` descriptor.

##### OCI_ATTR_ATTEMPTS

Mode
`READ`

Description
Specifies the number of attempts that have been made to dequeue the message. This parameter cannot be set at enqueue time.

Attribute Data Type
`sb4`

Valid Values
Any `sb4` value is valid.

##### OCI_ATTR_CORRELATION

Mode
READ/WRITE

Description
Specifies the identification supplied by the producer for a message at enqueuing.

Attribute Data Type
`oratext *`

Valid Values
Any string up to 128 bytes is valid.

##### OCI_ATTR_DELAY

Mode
READ/WRITE

Description
Specifies the number of seconds to delay the enqueued message. The delay represents the number of seconds after which a message is available for dequeuing. Dequeuing by message ID (msgid) overrides the delay specification. A message enqueued with delay set is in the `WAITING` state; when the delay expires the messages goes to the `READY` state. `DELAY` processing requires the queue monitor to be started. Note that the delay is set by the producer who enqueues the message.

Attribute Data Type
`sb4`

Valid Values
Any sb4 value is valid, but the following predefined constant is available:

- OCI_MSG_NO_DELAY - Indicates that the message is available for immediate dequeuing.

##### OCI_ATTR_ENQ_TIME

Mode
READ

Description
Specifies the time that the message was enqueued. This value is determined by the system and cannot be set by the user.

Attribute Data Type
`OCIDate`

##### OCI_ATTR_EXCEPTION_QUEUE

Mode
READ/WRITE

Description
Specifies the name of the queue to which the message is moved if it cannot be processed successfully. Messages are moved in two cases: If the number of unsuccessful dequeue attempts has exceeded `max_retries`; or if the message has expired. All messages in the exception queue are in the `EXPIRED` state.

The default is the exception queue associated with the queue table. If the exception queue specified does not exist at the time of the move, the message is moved to the default exception queue associated with the queue table, and a warning is logged in the alert file. If the default exception queue is used, the parameter returns a `NULL` value at dequeue time.

This attribute must refer to a valid queue name.

Attribute Data Type
`oratext *`

##### OCI_ATTR_EXPIRATION

Mode
READ/WRITE

Description
Specifies the expiration of the message. It determines, in seconds, how long the message is available for dequeuing. This parameter is an offset from the delay. Expiration processing requires the queue monitor to be running.

While waiting for expiration, the message remains in the `READY` state. If the message is not dequeued before it expires, it is moved to the exception queue in the `EXPIRED` state.

Attribute Data Type
`sb4`

Valid Values
Any sb4 value is valid, but the following predefined constant is available:

- OCI_MSG_NO_EXPIRATION - The message never expires.

##### OCI_ATTR_MSG_DELIVERY_MODE

Mode
READ

Description
After a dequeue call, the OCI client can read the `OCI_ATTR_MSG_DELIVERY_MODE` attribute in the `OCIAQMsgProperties` descriptor to determine whether a persistent or buffered message was dequeued. The value of the attribute is `OCI_MSG_PERSISTENT` for persistent messages and `OCI_MSG_BUFFERED` for buffered messages.

Attribute Data Type
`ub2`

##### OCI_ATTR_MSG_STATE

Mode
READ

Description
Specifies the state of the message at the time of the dequeue. This parameter cannot be set at enqueue time.

Attribute Data Type
`ub4`

Valid Values
Only the following values are returned:

- `OCI_MSG_WAITING` - The message delay has not yet been reached.

- `OCI_MSG_READY` - The message is ready to be processed.

- `OCI_MSG_PROCESSED` - The message has been processed and is retained.

- `OCI_MSG_EXPIRED` - The message has been moved to the exception queue.

##### OCI_ATTR_ORIGINAL_MSGID

Mode
READ/WRITE

Description
The ID of the message in the last queue that generated this message. When a message is propagated from one queue to another, this attribute identifies the ID of the queue from which it was last propagated. When a message has been propagated through multiple queues, this attribute identifies the ID of the message in the last queue that generated this message, not the first queue.

Attribute Data Type
`OCIRaw *`

##### OCI_ATTR_PRIORITY

Mode
READ/WRITE

Description
Specifies the priority of the message. A smaller number indicates a higher priority. The priority can be any number, including negative numbers.

The default value is zero.

Attribute Data Type
`sb4`

##### OCI_ATTR_RECIPIENT_LIST

Mode
WRITE

Description
This parameter is only valid for queues that allow multiple consumers. The default recipients are the queue subscribers. This parameter is not returned to a consumer at dequeue time.

Attribute Data Type
`OCIAQAgent **`

##### OCI_ATTR_SENDER_ID

Mode
READ/WRITE

Description
Identifies the original sender of a message.

Attribute Data Type
`OCIAgent *`

##### OCI_ATTR_TRANSACTION_NO

Mode
READ

Description
For transaction-grouped queues, this identifies the transaction group of the message. This attribute is populated after a successful `OCIAQDeqArray()` call. All messages in a group have the same value for this attribute. This attribute cannot be used by the `OCIAQEnqArray()` call to set the transaction group for an enqueued message.

Attribute Data Type
`oratext *`

#### A.21.4 OCIAQAgent Descriptor Attributes

Lists and describes OCIAQAgent descriptor attributes.

The following attributes are properties of the `OCIAQAgent` descriptor.

##### OCI_ATTR_AGENT_ADDRESS

Mode
READ/WRITE

Description
Protocol-specific address of the recipient. If the protocol is 0 (default), the address is of the form \[`schema`.\]`queue`\[`@dblink`\].

Attribute Data Type
`oratext *`

Valid Values
Can be any string up to 128 bytes.

##### OCI_ATTR_AGENT_NAME

Mode
READ/WRITE

Description
Name of a producer or consumer of a message.

Attribute Data Type
`oratext *`

Valid Values
Can be any Oracle Database identifier, up to 30 bytes.

##### OCI_ATTR_AGENT_PROTOCOL

Mode
READ/WRITE

Description
Protocol to interpret the address and propagate the message. The default (and currently the only supported) value is 0.

Attribute Data Type
`ub1`

Valid Values
The only valid value is zero, which is also the default.

#### A.21.5 OCIServerDNs Descriptor Attributes

Lists and describes OCIServerDNs descriptor attributes.

The following attributes are properties of the `OCIServerDNs` descriptor.

##### OCI_ATTR_DN_COUNT

Mode
READ

Description
The number of database servers in the descriptor.

Attribute Data Type
`ub2`

##### OCI_ATTR_SERVER_DN

Mode
READ/WRITE

Description
For read mode, this attribute returns the list of Oracle Database distinguished names that are already inserted into the descriptor.

For write mode, this attribute takes the distinguished name of an Oracle Database.

Attribute Data Type
`oratext **/oratext *`

### A.22 Subscription Handle Attributes

Lists and describes subscription handle attributes.

The following attributes are used for the subscription handle.

**See Also:**

- [Publish-Subscribe Notification in OCI](notification-streams-advanced-queuing.md)

- [About Continuous Query Notification](notification-streams-advanced-queuing.md)

#### OCI_ATTR_SERVER_DNS

Mode
READ/WRITE

Description
The distinguished names of the Oracle database that the client is interested in for the registration.

Attribute Data Type
`OCIServerDNs *`

#### OCI_ATTR_SUBSCR_CALLBACK

Mode
READ/WRITE

Description
Subscription callback. If the attribute `OCI_ATTR_SUBSCR_RECPTPROTO` is set to `OCI_SUBSCR_PROTO_OCI` or is left not set, then this attribute must be set before the subscription handle can be passed into the registration call `OCISubscriptionRegister()`.

Attribute Data Type
`ub4 (void *, OCISubscription *, void *, ub4, void *, ub4)`

#### OCI_ATTR_SUBSCR_CQ_QOSFLAGS

Mode
WRITE

Description
Sets QOS (quality of service flags) specific to continuous query (CQ) notifications. For the possible values you can pass, see the section on using OCI subscription handle attributes for CQN in [Oracle Database Development Guide](../adfns/cqn.md).

Attribute Data Type
`ub4 *`

#### OCI_ATTR_SUBSCR_CTX

Mode
READ/WRITE

Description
Context that the client wants to get passed to the user callback denoted by `OCI_ATTR_SUBSCR_CALLBACK` when it gets invoked by the system. If the attribute `OCI_ATTR_SUBSCR_RECPTPROTO` is set to `OCI_SUBSCR_PROTO_OCI` or is left not set, then this attribute must be set before the subscription handle can be passed into the registration call `OCI Subscription Register()`.

Attribute Data Type
`void *`

#### OCI_ATTR_SUBSCR_HOSTADDR

Mode
READ/WRITE

Description
Before registering for notification using `OCISubscriptionRegister()`, specify the client IP (in either IPv4 or IPv6 format) of the listening endpoint of the OCI notification client to which the notification is sent. Enter either IPv4 addresses in dotted decimal format, for example, 192.0.2.34, or IPv6 addresses in hexadecimal format, for example, 2001:0db8:0000:0000:0217:f2ff:fe4b:4ced.

**See Also:**

[Oracle Database Net Services Administrator's Guide](../netag/understanding-communication-layers.md) for more information about the IPv6 format for IP addresses

Attribute Data Type
`text *`

Example
    /* Set notification client address*/
    text ipaddr[16] = "192.0.2.34";
    (void) OCIAttrSet((dvoid *) envhp, (ub4) OCI_HTYPE_ENV,
                      (dvoid *) ipaddr, (ub4) strlen(ipaddr),
                      (ub4) OCI_ATTR_SUBSCR_HOSTADDR, errhp);

#### OCI_ATTR_SUBSCR_IPADDR

Mode
READ/WRITE

Description
The client IP address (IPv4 or IPv6) on which an OCI client registered for notification listens, to receive notifications. For example, IPv4 address in dotted decimal format such as 192.1.2.34 or IPv6 address in hexadecimal format such as 2001:0db8:0000:0000:0217:f2ff:fe4b:4ced.

**See Also:**

[Oracle Database Net Services Administrator's Guide](../netag/understanding-communication-layers.md) for more information about the IPv6 format for IP addresses

Attribute Data Type
`oratext *`

#### OCI_ATTR_SUBSCR_NAME

Mode
READ/WRITE

Description
Subscription name. All subscriptions are identified by a subscription name. A subscription name consists of a sequence of bytes of specified length. The length in bytes of the name must be specified as it is not assumed that the name is `NULL`-terminated. This is important because the name could contain multibyte characters.

Clients can set the subscription name attribute of a subscription handle using an `OCIAttrSet()` call and by specifying a handle type of `OCI_HTYPE_SUBSCR` and an attribute type of `OCI_ATTR_SUBSCR_NAME`.

All of the subscription callbacks need a subscription handle with the `OCI_ATTR_SUBSCR_NAME` and `OCI_ATTR_SUBSCR_NAMESPACE` attributes set. If the attributes are not set, an error is returned. The subscription name that is set for the subscription handle must be consistent with its namespace.

Attribute Data Type
`oratext *`

#### OCI_ATTR_SUBSCR_NAMESPACE

Mode
READ/WRITE

Description
Namespace in which the subscription handle is used. The valid values for this attribute are `OCI_SUBSCR_NAMESPACE_AQ`, `OCI_SUBSCR_NAMESPACE_DBCHANGE`, and `OCI_SUBSCR_NAMESPACE_ANONYMOUS`.

The subscription name that is set for the subscription handle must be consistent with its namespace.

Attribute Data Type
`ub4 *`

#### OCI_ATTR_SUBSCR_NTFN_GROUPING_CLASS

Mode
READ/WRITE

Description
Notification grouping class. If set to 0 (the default) all other notification grouping attributes must be 0. It is implemented for time in the latest release and is the only current criterion for grouping. Can be set to `OCI_SUBSCR_NTFN_GROUPING_CLASS_TIME`.

**Note:**

`OCI_OBJECT` mode is required when using grouping notifications.

Attribute Data Type
`ub1 *`

#### OCI_ATTR_SUBSCR_NTFN_GROUPING_REPEAT_COUNT

Mode
READ/WRITE

Description
How many times to do the grouping. Notification repeat count. Positive integer. Can be set to `OCI_NTFN_GROUPING_FOREVER` to send grouping notifications forever.

Attribute Data Type
`sb4 *`

#### OCI_ATTR_SUBSCR_NTFN_GROUPING_START_TIME

Mode
READ/WRITE

Description
The time grouping starts. Set to a valid `TIMESTAMP WITH TIME ZONE`. The default is the current `TIMESTAMP WITH TIME ZONE`.

Attribute Data Type
`OCIDateTime */OCIDateTime **`

#### OCI_ATTR_SUBSCR_NTFN_GROUPING_TYPE

Mode
READ/WRITE

Description
The format of the grouping notification: whether a summary of all events in the group or just the last event in the group. Use `OCIAttrSet()` to set to one of the following notification grouping types: `OCI_SUBSCR_NTFN_TYPE_SUMMARY` or `OCI_SUBSCR_NTFN_TYPE_LAST`. Summary of notifications is the default. The other choice is the last notification.

Attribute Data Type
`ub1 *`

#### OCI_ATTR_SUBSCR_NTFN_GROUPING_VALUE

Mode
READ/WRITE

Description
Specifies the value for the grouping class. For time, this is the time-period of grouping notifications specified in seconds, that is, the time after which grouping notification is sent periodically until `OCI_ATTR_SUBSCR_NTFN_GROUPING_REPEAT_COUNT` is exhausted.

Attribute Data Type
`ub4 *`

#### OCI_ATTR_SUBSCR_PAYLOAD

Mode
READ/WRITE

Description
Buffer that corresponds to the payload that must be sent along with the notification. The length of the buffer can also be specified in the same set attribute call. This attribute must be set before a post can be performed on a subscription. For the current release, only an untyped (`ub1 *`) payload is supported.

Attribute Data Type
`ub1 *`

#### OCI_ATTR_SUBSCR_QOSFLAGS

Mode
READ/WRITE

Description
Quality of service levels of the server. The possible settings are:

- `OCI_SUBSCR_QOS_RELIABLE` - Reliable. If the database fails, it does not lose notification. Not supported for nonpersistent queues or buffered messaging.

- `OCI_SUBSCR_QOS_PURGE_ON_NTFN` - Once received, purge notification and remove subscription.

- `OCI_SUBSCR_QOS_PAYLOAD` - Payload notification.

Attribute Data Type
`ub4 *`

#### OCI_ATTR_SUBSCR_RECPT

Mode
READ/WRITE

Description
The name of the recipient of the notification when the attribute `OCI_ATTR_SUBSCR_RECPTPROTO` is set to `OCI_SUBSCR_PROTO_MAIL`, `OCI_SUBSCR_PROTO_HTTP`, or `OCI_SUBSCR_PROTO_SERVER`.

For `OCI_SUBSCR_PROTO_HTTP`, `OCI_ATTR_SUBSCR_RECPT` denotes the HTTP URL (for example, http://www.oracle.com:80) to which notification is sent. The validity of the HTTP URL is never checked by the database.

For `OCI_SUBSCR_PROTO_MAIL`, `OCI_ATTR_SUBSCR_RECPT` denotes the email address (for example, xyz@oracle.com) to which the notification is sent. The validity of the email address is never checked by the database system.

For `OCI_SUBSCR_PROTO_SERVER`, `OCI_ATTR_SUBSCR_RECPT` denotes the database procedure (for example: `schema.procedure`) that is invoked when there is a notification. The subscriber must have appropriate permissions on the procedure for it to be executed.

**See Also:**

[Notification Procedure](notification-streams-advanced-queuing.md) for information about procedure definition

Attribute Data Type
`oratext *`

#### OCI_ATTR_SUBSCR_RECPTPRES

Mode
READ/WRITE

Description
The presentation with which the client wants to receive the notification. The valid values for this are `OCI_SUBSCR_PRES_DEFAULT` and `OCI_SUBSCR_PRES_XML`.

If not set, this attribute defaults to `OCI_SUBSCR_PRES_DEFAULT`.

For event notification in XML presentation, set this attribute to `OCI_SUBSCR_PRES_XML`. XML presentation is limited to 2000 bytes. Otherwise, leave it unset or set it to `OCI_SUBSCR_PRES_DEFAULT`.

Attribute Data Type
`ub4`

#### OCI_ATTR_SUBSCR_RECPTPROTO

Mode
READ/WRITE

Description
The protocol with which the client wants to receive the notification. The valid values for this are:

- `OCI_SUBSCR_PROTO_OCI`

- `OCI_SUBSCR_PROTO_MAIL`

- `OCI_SUBSCR_PROTO_SERVER`

- `OCI_SUBSCR_PROTO_HTTP`

If an OCI client wants to receive the event notification, then you should set this attribute to `OCI_SUBSCR_PROTO_OCI`.

If you want an email to be sent on event notification, then set this attribute to `OCI_SUBSCR_PROTO_MAIL`. If you want a PL/SQL procedure to be invoked in the database on event notification, then set this attribute to `OCI_SUBSCR_PROTO_SERVER`. If you want an HTTP URL to be posted to on event notification, then set this attribute to `OCI_SUBSCR_PROTO_HTTP`.

If not set, this attribute defaults to `OCI_SUBSCR_PROTO_OCI`.

For `OCI_SUBSCR_PROTO_OCI`, the attributes `OCI_ATTR_SUBSCR_CALLBACK` and `OCI_ATTR_SUBSCR_CTX` must be set before the subscription handle can be passed into the registration call `OCISubscriptionRegister()`.

For `OCI_SUBSCR_PROTO_MAIL`, `OCI_SUBSCR_PROTO_SERVER`, and `OCI_SUBSCR_PROTO_HTTP`, the attribute `OCI_ATTR_SUBSCR_RECPT` must be set before the subscription handle can be passed into the registration call `OCISubscriptionRegister()`.

Attribute Data Type
`ub4 *`

#### OCI_ATTR_SUBSCR_TIMEOUT

Mode
READ/WRITE

Description
Registration timeout interval in seconds. If 0 or not specified, then the registration is active until the subscription is explicitly unregistered.

Attribute Data Type
`ub4 *`

#### A.22.1 Continuous Query Notification Attributes

Lists and describes continuous query notification attributes.

The following attributes are used for continuous query notification.

##### OCI_ATTR_CHNF_CHANGELAG

Mode
WRITE

Description
The number of transactions that the client is to lag in continuous query notifications.

Attribute Data Type
`ub4 *`

##### OCI_ATTR_CHNF_OPERATIONS

Mode
WRITE

Description
Used to filter notifications based on operation type.

**See Also:**

[About Continuous Query Notification](notification-streams-advanced-queuing.md) for details about the flag values

Attribute Data Type
`ub4 *`

##### OCI_ATTR_CHNF_ROWIDS

Mode
WRITE

Description
If `TRUE`, the continuous query notification message includes row-level details, such as operation type and `ROWID`. The default is `FALSE`.

Attribute Data Type
`boolean *`

##### OCI_ATTR_CHNF_TABLENAMES

Mode
READ

Description
Attributes provided to retrieve the list of table names that were registered. These attributes are available from the subscription handle after the query is executed.

Attribute Data Type
`OCIColl **`

#### A.22.2 Continuous Query Notification Descriptor Attributes

Lists and describes continuous query notification descriptor attributes.

The following attributes are used for the continuous query notification descriptor.

##### OCI_ATTR_CHDES_DBNAME

Mode
READ

Description
Name of the database.

Attribute Data Type
`oratext **`

##### OCI_ATTR_CHDES_NFTYPE

Mode
READ

Description
Flags describing the notification type.

**See Also:**

[About Continuous Query Notification](notification-streams-advanced-queuing.md) for the flag values

Attribute Data Type
`ub4 *`

##### OCI_ATTR_CHDES_ROW_OPFLAGS

Mode
READ

Description
Operation type: `INSERT`, `UPDATE`, `DELETE`, or `OTHER`.

Attribute Data Type
`ub4 *`

##### OCI_ATTR_CHDES_ROW_ROWID

Mode
READ

Description
String representation of a `ROWID`.

Attribute Data Type
`oratext **`

##### OCI_ATTR_CHDES_TABLE_CHANGES

Mode
READ

Description
A collection type describing operations on tables. Each element of the collection is a table continuous query descriptors (`OCITableChangeDesc *`) of type `OCI_DTYPE_TABLE_CHDES` that has the attributes that begin with `OCI_ATTR_CHDES_TABLE`. See the following entries.

Attribute Data Type
`OCIColl **`

##### OCI_ATTR_CHDES_TABLE_NAME

Mode
READ

Description
Schema and table name. `HR.EMPLOYEES`, for example.

Attribute Data Type
`oratext **`

##### OCI_ATTR_CHDES_TABLE_OPFLAGS

Mode
READ

Description
Flags describing the operations on the table.

Attribute Data Type
`ub4 *`

**See Also:**

[Oracle Database Development Guide](../adfns/cqn.md) for information about the flag values for the `OCI_DTYPETABLE_CHDES` continuous query notification descriptor

##### OCI_ATTR_CHDES_TABLE_ROW_CHANGES

Mode
READ

Description
An embedded collection describing the changes to the rows of the table. Each element of the collection is a row continuous query descriptor (`OCIRowChangeDesc *`) of type `OCI_DTYPE_ROW_CHDES` that has the attributes `OCI_ATTR_CHDES_ROW_OPFLAGS` and `OCI_ATTR_CHDES_ROW_ROWID`.

Attribute Data Type
`OCIColl **`

##### OCI_ATTR_CHDES_XID

Mode
READ

Description
The transaction ID of the message.

Attribute Data Type
`OCIRaw *`

**See Also:**

[Oracle Database Development Guide](../adfns/cqn.md) for more information.

#### A.22.3 Notification Descriptor Attributes

Lists and describes notification descriptor attributes.

The following are attributes of the descriptor `OCI_DTYPE_AQNFY`.

##### OCI_ATTR_AQ_NTFN_GROUPING_COUNT

Mode
READ

Description
For AQ namespace. Count of notifications received in the group.

Attribute Data Type
`ub4 *`

##### OCI_ATTR_AQ_NTFN_GROUPING\_ MSGID_ARRAY

Mode
READ

Description
For AQ namespace. The group: an OCI Collection of message IDs.

Attribute Data Type
`OCIColl **`

##### OCI_ATTR_CONSUMER_NAME

Mode
READ

Description
Consumer name of the notification.

Attribute Data Type
`oratext *`

##### OCI_ATTR_MSG_PROP

Mode
READ

Description
Message properties.

Attribute Data Type
`OCIAQMsgProperties **`

##### OCI_ATTR_NFY_FLAGS

Mode
READ

Description
0 = regular, 1 = timeout notification, 2 = grouping notification.

Attribute Data Type
`ub4 *`

##### OCI_ATTR_NFY_MSGID

Mode
READ

Description
Message ID.

Attribute Data Type
`OCIRaw *`

##### OCI_ATTR_QUEUE_NAME

Mode
READ

Description
The queue name of the notification.

Attribute Data Type
`oratext *`

#### A.22.4 Invalidated Query Attributes

Lists and describes invalidated query attributes.

This section describes `OCI_DTYPE_CQDES` attributes.

**See Also:**

[Oracle Database Development Guide](../adfns/cqn.md) for more information about the `OCI_DTYPE_CQDES` continuous query notification descriptor

##### OCI_ATTR_CQDES_OPERATION

Mode
READ

Description
The operation that occurred on the query. It can be one of two values: `OCI_EVENT_QUERYCHANGE` (query result set change) or `OCI_EVENT_DEREG` (query unregistered).

Attribute Data Type
`ub4 *`

##### OCI_ATTR_CQDES_QUERYID

Mode
READ

Description
Query ID of the query that was invalidated.

Attribute Data Type
`ub8 *`

##### OCI_ATTR_CQDES_TABLE_CHANGES

Mode
READ

Description
A collection of table continuous query descriptors describing DML or DDL operations on tables that caused the query result set change. Each element of the collection is of type `OCI_DTYPE_TABLE_CHDES`.

Attribute Data Type
`OCIColl *`

### A.23 Direct Path Loading Handle Attributes

Lists and describes direct path loading handle attributes.

The following attributes are used for the direct path loading handle.

**See Also:**

[Direct Path Loading Overview](direct-path-load-interface.md) and [Direct Path Loading of Object Types](direct-path-load-interface.md) for information about direct path loading and allocating the direct path handles

#### A.23.1 Direct Path Context Handle (OCIDirPathCtx) Attributes

Lists and describes direct path context handle (OCIDirPathCtx) attributes.

The following attributes are used for the direct path context handle.

##### OCI_ATTR_BUF_SIZE

Mode
READ/WRITE

Description
Sets the size of the stream transfer buffer. Default value is 64 KB.

Attribute Data Type
`ub4 */ub4 *`

##### OCI_ATTR_CHARSET_ID

Mode
READ/WRITE

Description
Default character set ID for the character data. Note that the character set ID can be overridden at the column level. If the character set ID is not specified at the column level or the table level, then the Global support environment setting is used.

Attribute Data Type
`ub2 */ub2 *`

##### OCI_ATTR_DATEFORMAT

Mode
READ/WRITE

Description
Default date format string for `SQLT_CHR` to `DTYDAT` conversions. Note that the date format string can be overridden at the column level. If date format string is not specified at the column level or the table level, then the Global Support environment setting is used.

Attribute Data Type
`oratext **/oratext *`

##### OCI_ATTR_DIRPATH_DCACHE_DISABLE

Mode
READ/WRITE

Description
Setting this attribute to 1 indicates that the date cache is to be disabled if exceeded. The default value is 0, which means that lookups in the cache continue on cache overflow.

**See Also:**

[About Using a Date Cache in Direct Path Loading of Dates in OCI](direct-path-load-interface.md) for a complete description of this attribute and of the four following attributes

Attribute Data Type
`ub1 */ub1 *`

##### OCI_ATTR_DIRPATH_DCACHE_HITS

Mode
READ

Description
Queries the number of date cache hits.

Attribute Data Type
`ub4 *`

##### OCI_ATTR_DIRPATH_DCACHE_MISSES

Mode
READ

Description
Queries the current number of date cache misses.

Attribute Data Type
`ub4 *`

##### OCI_ATTR_DIRPATH_DCACHE_NUM

Mode
READ

Description
Queries the current number of entries in a date cache.

Attribute Data Type
`ub4 *`

##### OCI_ATTR_DIRPATH_DCACHE_SIZE

Mode
READ/WRITE

Description
Sets the date cache size (in elements) for a table. To disable the date cache, set this to 0, which is the default value.

Attribute Data Type
`ub4 *`/`ub4 *`

##### OCI_ATTR_DIRPATH_DEF_EXP_CACHE_SIZE

#####

Mode
READ/WRITE

Description
Specifies the number of default expressions that are evaluated at a time. The default is 100. For default expressions that must be evaluated for every row, increasing this value may improve performance.

Valid values: `UB4`

Attribute Data Type
`ub4 */ub4 *`

Example
         ub4 default_cache = 200;

         OCIAttrSet ((void *)dpctx,
                          (ub4)OCI_HTYPE_DIRPATH_CTX,
                          (void *)&default_cache,
                          (ub4)0, (ub4)OCI_ATTR_DIRPATH_DEF_EXP_CACHE_SIZE, errhp);

##### OCI_ATTR_DIRPATH_DEFAULTS

Mode
Read/Write

Description
Specifies how the direct path API handles default expressions for columns that are not explicitly being loaded.

Valid values are:

- `OCI_DIRPATH_DEFAULTS_DEFAULT`

  Evaluate once, unless a sequence is involved, then evaluate every row.

  Error if an unsupported default value is seen. This is the default.

- `OCI_DIRPATH_DEFAULTS_EVALUATE_ONCE`

  Evaluate once, at the start of the load. Error if an unsupported default value is seen.

- `OCI_DIRPATH_DEFAULTS_EVALUATE_EVERY_ROW`

  Evaluate every row. Error if an unsupported default value is seen.

- `OCI_DIRPATH_DEFAULTS_IGNORE`

  Ignore all defaults, load NULLs.

- `OCI_DIRPATH_DEFAULTS_IGNORE_UNSUPPORTED_EVALUATE_ONCE`

  Ignore unsupported defaults, load NULLS, evaluate supported once.

- `OCI_DIRPATH_DEFAULTS_IGNORE_UNSUPPORTED_EVALUATE_EVERY_ROW`

  Ignore unsupported defaults, load NULLS, evaluate supported every row.

Attribute Data Type
`ub1 */ub1 *`

Example
         ub1 dirpath_handling = OCI_DIRPATH_DEFAULTS_EVALUATE_EVERY_ROW;

         OCIAttrSet ((void *)dpctx,
                          (ub4)OCI_HTYPE_DIRPATH_CTX,
                          (void *)&dirpath_handling,
                          (ub4)0, (ub4)OCI_ATTR_DIRPATH_DEFAULTS, errhp);

##### OCI_ATTR_DIRPATH_FLAGS

Mode
READ/WRITE

Description
Flags used to control behavior of the load.

`OCI_DIRPATH_FLAGS_VLDT` 0x01 – validate format for Oracle `NUMBER` and `DATE` data when the stream is parsed on the server. The default value is to not set this flag because it is an expensive operation. It can be used when you suspect that there is a problem with `OCIDirPath` generating invalid internal representation of dates and numbers.

Example
    ub4 dirpath_flags = OCI_ATTR_DIRPATH_FLAGS_VLDT;

    OCIAttrSet ((void *)dpctx,
                      (ub4)OCI_HTYPE_DIRPATH_CTX,
                     (void *)&dirpath_flags,
                     (ub4)0, (ub4)OCI_ATTR_DIRPATH_FLAGS, errhp);           

Attribute Data Type
`ub4 *`/`ub4 *`

##### OCI_ATTR_DIRPATH_INDEX_MAINT_METHOD

Mode
READ/WRITE

Description
Performs index row insertion on a per-row basis.

Valid value is:

`OCI_DIRPATH_INDEX_MAINT_SINGLE_ROW`

Attribute Data Type
`ub1 *`/`ub1 *`

##### OCI_ATTR_DIRPATH_MODE

Mode
READ/WRITE

Description
Mode of the direct path context:

- `OCI_DIRPATH_LOAD` - Load operation (default)

- `OCI_DIRPATH_CONVERT` - Convert-only operation

Attribute Data Type
`ub1 */ub1 *`

##### OCI_ATTR_DIRPATH_NO_INDEX_ERRORS

Mode
READ/WRITE

Description
When `OCI_ATTR_DIRPATH_NO_INDEX_ERRORS` is 1, indexes are not set as unusable at any time during the load. If any index errors are detected, the load is aborted. That is, no rows are loaded, and the indexes are left as is. The default is 0.

Attribute Data Type
ub1 \*/ub1 \*

##### OCI_ATTR_DIRPATH_NOLOG

Mode
READ/WRITE

Description
The `NOLOG` attribute of each segment determines whether image redo or invalidation redo is generated:

- 0 - Use the attribute of the segment being loaded.

- 1 - No logging. Overrides DDL statement, if necessary.

Attribute Data Type
`ub1 */ub1 *`

##### OCI_ATTR_DIRPATH_OBJ_CONSTR

Mode
READ/WRITE

Description
Indicates the object type of a substitutable object table:

    OraText *obj_type; /* stores an object type name */
    OCIAttrSet((void *)dpctx,
               (ub4)OCI_HTYPE_DIRPATH_CTX,
               (void *) obj_type,
               (ub4)strlen((const char *) obj_type),
               (ub4)OCI_ATTR_DIRPATH_OBJ_CONSTR, errhp);

Attribute Data Type
`oratext **/oratext *`

##### OCI_ATTR_DIRPATH_PARALLEL

Mode
READ/WRITE

Description
Setting this value to 1 allows multiple load sessions to load the same segment concurrently. The default is 0 (not parallel).

Attribute Data Type
`ub1 */ub1 *`

##### OCI_ATTR_DIRPATH_PGA_LIM

Mode
READ/WRITE

Description
The current partition loading memory limit. Once this limit is reached, some partition loading will be delayed to save memory. The value is in KB.

Attribute Data Type
`ub4 */ub4 *`

##### OCI_ATTR_DIRPATH_REJECT_ROWS_REPCH

Mode
READ/WRITE

Description
If set to 1, any rows with character conversions that use the replacement character will be rejected.

- 0 - Allow use of the replacement character in conversions.

- 1 - Reject rows if the replacement character was used during conversion.

Attribute Data Type
ub1 \*/ub1 \*

##### OCI_ATTR_DIRPATH_SKIPINDEX_METHOD

Mode
READ/WRITE

Description
Indicates how the handling of unusable indexes is performed.

Valid values are:

- `OCI_DIRPATH_INDEX_MAINT_SKIP_UNUSABLE` (skip unusable indexes)

- `OCI_DIRPATH_INDEX_MAINT_DONT_SKIP_UNUSABLE` (do not skip unusable indexes)

- `OCI_DIRPATH_INDEX_MAINT_SKIP_ALL` (skip all index maintenance)

Attribute Data Type
`ub1 *`/`ub1 *`

##### OCI_ATTR_DIRPATH_SPILL_PASSES

Mode
READ

Description
The number of passes required to load all partitions. If the direct path PGA limit is exceeded, this will likely be greater than one. Increasing the PGA limit, using the attribute `OCI_ATTR_DIRPATH_PGA_LIM`, can decrease the number of passes, but can also exceed available memory.

Attribute Data Type
`ub4 * `

##### OCI_ATTR_LIST_COLUMNS

Mode
READ

Description
Returns the handle to the parameter descriptor for the column list associated with the direct path context. The column list parameter descriptor can be retrieved after the number of columns is set with the `OCI_ATTR_NUM_COLS` attribute.

**See Also:**

"About Accessing Column Parameter Attributes"

Attribute Data Type
`OCIParam* *`

##### OCI_ATTR_NAME

Mode
READ/WRITE

Description
Name of the table to be loaded into.

Attribute Data Type
`oratext**/oratext *`

##### OCI_ATTR_NUM_COLS

Mode
READ/WRITE

Description
Number of columns being loaded in the table.

Attribute Data Type
`ub2 */ub2 *`

##### OCI_ATTR_NUM_ROWS

Mode
READ/WRITE

Description
Read: The number of rows loaded so far.

Write: The number of rows to be allocated for the direct path and the direct path function column arrays.

Attribute Data Type
`ub2 */ub2 *`

##### OCI_ATTR_SCHEMA_NAME

Mode
READ/WRITE

Description
Name of the schema where the table being loaded resides. If not specified, the schema defaults to that of the connected user.

Attribute Data Type
`oratext **/oratext *`

##### OCI_ATTR_SUB_NAME

Mode
READ/WRITE

Description
Name of the partition or subpartition to be loaded. If not specified, the entire table is loaded. The name must be a valid partition or subpartition name that belongs to the table.

Attribute Data Type
`oratext **/oratext *`

#### A.23.2 Direct Path Function Context Handle (OCIDirPathFuncCtx) Attributes

Lists and describes direct path function context handle (OCIDirPathFuncCtx) attributes.

For further explanations of these attributes, see [Direct Path Function Context and Attributes](direct-path-load-interface.md).

##### OCI_ATTR_DIRPATH_EXPR_TYPE

Mode
READ/WRITE

Description
Indicates the type of expression specified in `OCI_ATTR_NAME` in the function context of a nonscalar column.

Valid values are:

- `OCI_DIRPATH_EXPR_OBJ_CONSTR` (the object type name of a column object)

- `OCI_DIRPATH_EXPR_REF_TBLNAME` (table name of a reference object)

- `OCI_DIRPATH_EXPR_SQL` (a SQL string to derive the column value)

Attribute Data Type
`ub1 */ub1 *`

##### OCI_ATTR_LIST_COLUMNS

Mode
READ

Description
Returns the handle to the parameter descriptor for the column list associated with the direct path function context. The column list parameter descriptor can be retrieved after the number of columns (number of attributes or arguments associated with the nonscalar column) is set with the `OCI_ATTR_NUM_COLS` attribute.

**See Also:**

About Accessing Column Parameter Attributes

Attribute Data Type
`OCIParam** `

##### OCI_ATTR_NAME

Mode
READ/WRITE

Description
The object type name if the function context is describing a column object, a SQL function if the function context is describing a SQL string, or a reference table name if the function context is describing a `REF` column.

Attribute Data Type
`oratext **/oratext *`

##### OCI_ATTR_NUM_COLS

Mode
READ/WRITE

Description
The number of the object attributes to load if the column is a column object, or the number of arguments to process if the column is a SQL string or a REF column. This parameter must be set before the column list can be retrieved.

Attribute Data Type
`ub2 */ub2 *`

##### OCI_ATTR_NUM_ROWS

Mode
READ

Description
The number of rows loaded so far.

Attribute Data Type
`ub4 *`

#### A.23.3 Direct Path Function Column Array Handle (OCIDirPathColArray) Attributes

Lists and describes direct path function column array handle (OCIDirPathColArray) attributes.

The following attributes are used for the direct path function column array handle.

##### OCI_ATTR_COL_COUNT

Mode
READ

Description
Last column of the last row processed.

Attribute Data Type
`ub2 *`

##### OCI_ATTR_NUM_COLS

Mode
READ

Description
Column dimension of the column array.

Attribute Data Type
`ub2 *`

##### OCI_ATTR_NUM_ROWS

Mode
READ

Description
Row dimension of the column array.

Attribute Data Type
`ub4 *`

##### OCI_ATTR_ROW_COUNT

Mode
READ

Description
Number of rows successfully converted in the last call to `OCIDirPathColArrayToStream()`.

Attribute Data Type
`ub4 *`

#### A.23.4 Direct Path Stream Handle (OCIDirPathStream) Attributes

Lists and describes direct path stream handle (OCIDirPathStream) attributes.

The following attributes are used for the direct path stream handle.

##### OCI_ATTR_BUF_ADDR

Mode
READ

Description
Buffer address of the beginning of the stream data.

Attribute Data Type
`ub1 **`

##### OCI_ATTR_BUF_SIZE

Mode
READ

Description
Size of the stream data in bytes.

Attribute Data Type
`ub4 *`

##### OCI_ATTR_ROW_COUNT

Mode
READ

Description
Number of rows successfully loaded by the last `OCIDirPathLoadStream()` call.

Attribute Data Type
`ub4 *`

##### OCI_ATTR_STREAM_OFFSET

Mode
READ

Description
Offset into the stream buffer of the last processed row.

Attribute Data Type
`ub4 *`

#### A.23.5 Direct Path Column Parameter Attributes

Describes how direct path column parameter attributes are used.

The application specifies which columns are to be loaded, and the external format of the data by setting attributes on each column parameter descriptor. The column parameter descriptors are obtained as parameters of the column parameter list by `OCIParamGet()`. The column parameter list of the table is obtained from the `OCI_ATTR_LIST_COLUMNS` attribute of the direct path context. If a column is nonscalar, then its column parameter list is obtained from the `OCI_ATTR_LIST_COLUMNS` attribute of its direct path function context.

Note that all parameters are 1-based.

##### A.23.5.1 About Accessing Column Parameter Attributes

Lists and describes direct path column parameter attributes.

The following code example illustrates the use of the direct path column parameter attributes for scalar columns. Before the attributes are accessed, you must first set the number of columns to be loaded and get the column parameter list from the `OCI_ATTR_LIST_COLUMNS` attribute.

**See Also:**

[Direct Path Load Examples for Scalar Columns](direct-path-load-interface.md) for the data structures defined in the listings

    ...
      /* set number of columns to be loaded */
      OCI_CHECK(ctlp->errhp_ctl, OCI_HTYPE_ERROR, ociret, ctlp,
                OCIAttrSet((void *)dpctx, (ub4)OCI_HTYPE_DIRPATH_CTX,
                           (void *)&tblp->ncol_tbl,
                           (ub4)0, (ub4)OCI_ATTR_NUM_COLS, ctlp->errhp_ctl));

      /* get the column parameter list */
      OCI_CHECK(ctlp->errhp_ctl, OCI_HTYPE_ERROR, ociret, ctlp,
                OCIAttrGet((void *)dpctx, OCI_HTYPE_DIRPATH_CTX,
                           (void *)&ctlp->colLstDesc_ctl, (ub4 *)0,
                           OCI_ATTR_LIST_COLUMNS, ctlp->errhp_ctl));

Now you can set the parameter attributes.

      /* set the attributes of each column by getting a parameter handle on each
       * column, then setting attributes on the parameter handle for the column.
       * Note that positions within a column list descriptor are 1-based. */

       for (i = 0, pos = 1, colp = tblp->col_tbl, fldp = tblp->fld_tbl;
           i < tblp->ncol_tbl;
           i++, pos++, colp++, fldp++)
      {
        /* get parameter handle on the column */
        OCI_CHECK(ctlp->errhp_ctl, OCI_HTYPE_ERROR, ociret, ctlp,
                  OCIParamGet((const void  *)ctlp->colLstDesc_ctl,
                              (ub4)OCI_DTYPE_PARAM, ctlp->errhp_ctl,
                              (void  **)&colDesc, pos));

        colp->id_col = i;                  /* position in column array */

        /* set external attributes on the column */
        /* column name */
        OCI_CHECK(ctlp->errhp_ctl, OCI_HTYPE_ERROR, ociret, ctlp,
                  OCIAttrSet((void  *)colDesc, (ub4)OCI_DTYPE_PARAM,
                             (void  *)colp->name_col,
                             (ub4)strlen((const char *)colp->name_col),
                             (ub4)OCI_ATTR_NAME, ctlp->errhp_ctl));

        /* column type */
        OCI_CHECK(ctlp->errhp_ctl, OCI_HTYPE_ERROR, ociret, ctlp,
                  OCIAttrSet((void  *)colDesc, (ub4)OCI_DTYPE_PARAM,
                             (void  *)&colp->exttyp_col, (ub4)0,
                             (ub4)OCI_ATTR_DATA_TYPE, ctlp->errhp_ctl));

        /* max data size */
        OCI_CHECK(ctlp->errhp_ctl, OCI_HTYPE_ERROR, ociret, ctlp,
                  OCIAttrSet((void  *)colDesc, (ub4)OCI_DTYPE_PARAM,
                             (void  *)&fldp->maxlen_fld, (ub4)0,
                             (ub4)OCI_ATTR_DATA_SIZE, ctlp->errhp_ctl));

        if (colp->datemask_col)    /* set column (input field) date mask */
        {
          OCI_CHECK(ctlp->errhp_ctl, OCI_HTYPE_ERROR, ociret, ctlp,
                    OCIAttrSet((void  *)colDesc, (ub4)OCI_DTYPE_PARAM,
                             (void  *)colp->datemask_col,
                             (ub4)strlen((const char *)colp->datemask_col),
                              (ub4)OCI_ATTR_DATEFORMAT, ctlp->errhp_ctl));
        }
        if (colp->prec_col)
        {
          OCI_CHECK(ctlp->errhp_ctl, OCI_HTYPE_ERROR, ociret, ctlp,
                    OCIAttrSet((void  *)colDesc, (ub4)OCI_DTYPE_PARAM,
                             (void  *)&colp->prec_col, (ub4)0,
                             (ub4)OCI_ATTR_PRECISION, ctlp->errhp_ctl));
        }
        if (colp->scale_col)
        {
          OCI_CHECK(ctlp->errhp_ctl, OCI_HTYPE_ERROR, ociret, ctlp,
                    OCIAttrSet((void  *)colDesc, (ub4)OCI_DTYPE_PARAM,
                             (void  *)&colp->scale_col, (ub4)0,
                             (ub4)OCI_ATTR_SCALE, ctlp->errhp_ctl));
        }
        if (colp->csid_col)
        {
          OCI_CHECK(ctlp->errhp_ctl, OCI_HTYPE_ERROR, ociret, ctlp,
                    OCIAttrSet((void  *)colDesc, (ub4)OCI_DTYPE_PARAM,
                             (void  *)&colp->csid_col, (ub4)0,
                             (ub4)OCI_ATTR_CHARSET_ID, ctlp->errhp_ctl));
        }
        /* free the parameter handle to the column descriptor */
        OCI_CHECK((void  *)0, 0, ociret, ctlp,
                  OCIDescriptorFree((void  *)colDesc, OCI_DTYPE_PARAM));
      }
    ...

##### OCI_ATTR_CHARSET_ID

Mode
READ/WRITE

Description
Character set ID for character column. If not set, the character set ID defaults to the character set ID set in the direct path context.

Attribute Data Type
`ub2 */ub2 *`

##### OCI_ATTR_DATA_SIZE

Mode
READ/WRITE

Description
Maximum size in bytes of the external data for the column. This can affect conversion buffer sizes.

Attribute Data Type
`ub4 */ub4 *`

##### OCI_ATTR_DATA_TYPE

Mode
READ/WRITE

Description
Returns or sets the external data type of the column. Valid data types are:

- `SQLT_CHR`

- `SQLT_DATE`

- `SQLT_TIMESTAMP`

- `SQLT_TIMESTAMP_TZ`

- `SQLT_TIMESTAMP_LTZ`

- `SQLT_INTERVAL_YM`

- `SQLT_INTERVAL_DS`

- `SQLT_CLOB`

- `SQLT_BLOB`

- `SQLT_INT`

- `SQLT_UIN`

- `SQLT_FLT`

- `SQLT_PDN`

- `SQLT_BIN`

- `SQLT_NUM`

- `SQLT_NTY`

- `SQLT_REF`

- `SQLT_VST`

- `SQLT_VNU`

Attribute Data Type
`ub2 */ub2 *`

##### OCI_ATTR_DATEFORMAT

Mode
READ/WRITE

Description
Date conversion mask for the column. If not set, the date format defaults to the date conversion mask set in the direct path context.

Attribute Data Type
`oratext **/oratext *`

##### OCI_ATTR_DIRPATH_OID

Mode
READ/WRITE

Description
Indicates that the column to load into is an object table's object ID column.

Attribute Data Type
`ub1 */ub1 * `

##### OCI_ATTR_DIRPATH_SID

Mode
READ/WRITE

Description
Indicates that the column to load into is a nested table's `setid` column.

Attribute Data Type
`ub1 */ub1 *`

##### OCI_ATTR_NAME

Mode
READ/WRITE

Description
Returns or sets the name of the column that is being loaded. Initialize both the column name and the column name length to 0 before calling `OCIAttrGet()`.

Attribute Data Type
`oratext **/oratext *`

##### OCI_ATTR_PRECISION

Mode
READ/WRITE

Description
Returns or sets the precision.

Attribute Data Type
`ub1 */ub1 *` for explicit describes

`sb2 */sb2 *` for implicit describes

##### OCI_ATTR_SCALE

Mode
READ/WRITE

Description
Returns or sets the scale (number of digits to the right of the decimal point) for conversions from packed and zoned decimal input data types.

Attribute Data Type
`sb1 */sb1 *`

### A.24 Process Handle Attributes

Lists and describes process handle attributes.

The parameters for the shared system can be set and read using the `OCIAttrSet()` and `OCIAttrGet()` calls. The handle type to be used is the process handle `OCI_HTYPE_PROC`.

The `OCI_ATTR_MEMPOOL_APPNAME`, `OCI_ATTR_MEMPOOL_HOMENAME`, and `OCI_ATTR_MEMPOOL_INSTNAME` attributes specify the application, home, and instance names that can be used together to map the process to the right shared pool area. If these attributes are not provided, internal default values are used. The following are valid settings of the attributes for specific behaviors:

- Instance name, application name (unqualified): This allows only executables with a specific name to attach to the same shared subsystem. For example, this allows an OCI application named Office to connect to the same shared subsystem regardless of the directory Office resides in.

- Instance name, home name: This allows a set of executables in a specific home directory to attach to the same instance of the shared subsystem. For example, this allows all OCI applications residing in the ORACLE_HOME directory to use the same shared subsystem.

- Instance name, home name, application name (unqualified): This allows only a specific executable to attach to a shared subsystem. For example, this allows one application named Office in the ORACLE_HOME directory to attach to a given shared subsystem.

**See Also:**

OCI_ATTR_SHARED_HEAPALLOC

#### OCI_ATTR_MEMPOOL_APPNAME

Mode
READ/WRITE

Description
Executable name or fully qualified path name of the executable.

Attribute Data Type
`oratext *`

#### OCI_ATTR_MEMPOOL_HOMENAME

Mode
READ/WRITE

Description
Directory name where the executables that use the same shared subsystem instance are located.

Attribute Data Type
`oratext *`

#### OCI_ATTR_MEMPOOL_INSTNAME

Mode
READ/WRITE

Description
Any user-defined name to identify an instance of the shared subsystem.

Attribute Data Type
`oratext *`

#### OCI_ATTR_MEMPOOL_SIZE

Mode
READ/WRITE

Description
Size of the shared pool in bytes. This attribute is set as follows:

    ub4 plsz = 1000000;
    OCIAttrSet((void  *)0, (ub4) OCI_HTYPE_PROC,
               (void  *)&plsz, (ub4) 0, (ub4) OCI_ATTR_POOL_SIZE, 0);

Attribute Data Type
`ub4 *`

#### OCI_ATTR_PROC_MODE

Mode
READ

Description
Returns all the currently set process modes. The value read contains the OR'ed value of all the currently set OCI process modes. To determine if a specific mode is set, the value should be AND'ed with that mode. For example:

    ub4 mode;
    boolean is_shared;

    OCIAttrGet((void  *)0, (ub4)OCI_HTYPE_PROC,
               (void  *) &mode, (ub4 *) 0,
               (ub4)OCI_ATTR_PROC_MODE, 0);

    is_shared = mode & OCI_SHARED;

Attribute Data Type
`ub4 *`

### A.25 Event Handle Attributes

Lists and describes event handle attributes.

The `OCIEvent` handle encapsulates the attributes from the event payload. This handle is implicitly allocated before the event callback is called.

The event callback obtains the attributes of an event using `OCIAttrGet()` with the following attributes.

**See Also:**

[HA Event Notification](high-availability-in-oci.md)

#### OCI_ATTR_DBDOMAIN

Mode
READ

Description
When called with this attribute, `OCIAttrGet()` retrieves the name of the database domain that has been affected by this event. This is also a server handle attribute.

Attribute Data Type
`oratext **`

#### OCI_ATTR_DBNAME

Mode
READ

Description
When called with this attribute, `OCIAttrGet()` retrieves the name of the database that has been affected by this event. This is also a server handle attribute.

Attribute Data Type
`oratext **`

#### OCI_ATTR_EVENTTYPE

Mode
READ

Description
The type of event that occurred, `OCI_EVENTTYPE_HA`.

Attribute Data Type
`ub4 *`

#### OCI_ATTR_HA_SOURCE

Mode
READ

Description
If the event type is `OCI_EVENTTYPE_HA`, get the source of the event with this attribute. Valid values are:

- `OCI_HA_SOURCE_DATABASE`

- `OCI_HA_SOURCE_NODE`

- `OCI_HA_SOURCE_INSTANCE`

- `OCI_HA_SOURCE_SERVICE`

- `OCI_HA_SOURCE_SERVICE_MEMBER`

- `OCI_HA_SOURCE_ASM_INSTANCE`

- `OCI_HA_SOURCE_SERVICE_PRECONNECT`

Attribute Data Type
`ub4 *`

#### OCI_ATTR_HA_SRVFIRST

Mode
READ

Description
When called with this attribute, `OCIAttrGet()` retrieves the first server handle in the list of server handles affected by an Oracle Real Application Clusters (Oracle RAC) HA DOWN event.

Attribute Data Type
`OCIServer **`

#### OCI_ATTR_HA_SRVNEXT

Mode
READ

Description
When called with this attribute `OCIAttrGet()` retrieves the next server handle in the list of server handles affected by an Oracle RAC HA DOWN event.

Attribute Data Type
`OCIServer **`

#### OCI_ATTR_HA_STATUS

Mode
READ

Description
Valid value is `OCI_HA_STATUS_DOWN`. Only `DOWN` events are subscribed to currently.

Attribute Data Type
`ub4 *`

#### OCI_ATTR_HA_TIMESTAMP

Mode
READ

Description
The time that the HA event occurred.

Attribute Data Type
`OCIDateTime **`

#### OCI_ATTR_HOSTNAME

Mode
READ

Description
When called with this attribute, `OCIAttrGet()` retrieves the name of the host that has been affected by this event.

Attribute Data Type
`oratext **`

#### OCI_ATTR_INSTNAME

Mode
READ

Description
When called as an event handle attribute, `OCIAttrGet()` retrieves the name of the instance that has been affected by this event. This is also a server handle attribute. This attribute can also be used on service context to return the shard instance name for a given connection. This attribute can be used to find the shard instance name out of a shard instance descriptor that is filed by an `OCIShardInstancesGet()` call.

Attribute Data Type
`oratext **`

Example
The following example shows for a given connection (svchp) how to get the shard instance name.

    Oratext instanceName [OCI_INSTNAME_MAXLEN];
    ub4     instanceNameLen;
       OCIATTRGet(svchp,
                  OCI_HTYPE_SVCCTX,
                  instanceName,
                  (ub4 *) &instanceNameLen,
                  OCI_ATTR_INSTNAME,
                  errhp);

#### OCI_ATTR_INSTSTARTTIME

Mode
READ

Description
When called with this attribute, `OCIAttrGet()` retrieves the start time of the instance that has been affected by this event. This is also a server handle attribute.

Attribute Data Type
`OCIDateTime **`

#### OCI_ATTR_SERVICENAME

Mode
READ

Description
When called with this attribute, `OCIAttrGet()` retrieves the name of the service that has been affected by this event. The name length is `ub4 *`. This is also a server handle attribute.

Attribute Data Type
`oratext **`
