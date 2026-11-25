This chapter describes high availability (HA) features in OCI.

This chapter includes the following topics:

- Runtime Connection Load Balancing

- HA Event Notification

- Transparent Application Failover in OCI

- OCI and Transaction Guard

- OCI and Application Continuity

### 12.1 Runtime Connection Load Balancing

Runtime connection load balancing routes work requests to sessions in a session pool that best serve the work.

It occurs when an application selects a session from an existing session pool and thus is a very frequent activity. For session pools that support services at one instance only, the first available session in the pool is adequate. When the pool supports services that span multiple instances, there is a need to distribute the work requests across instances so that the instances that are providing better service or have greater capacity get more requests.

Applications must connect to an Oracle RAC instance to enable runtime connection load balancing. Furthermore, these applications must:

- Initialize the OCI Environment in `OCI_EVENTS` mode

- Connect to a service that has runtime connection load balancing enabled (use the `DBMS_SERVICE.MODIFY_SERVICE` procedure to set `GOAL` and `CLB_GOAL` as appropriate)

- Link with a thread library

**See Also:**

- [Oracle Real Application Clusters Administration and Deployment Guide](../racad/workload-management-with-dynamic-database-services.md) for information about load balancing advisory

- [Oracle Database Development Guide](../adfns/connection_strategies.md) for information about enabling and disabling runtime connection load balancing for the supported interfaces, and receiving load balancing advisory FAN events

### 12.2 HA Event Notification

Use HA event notification to provide a best-effort programmatic signal to the client if there is a database failure for high availability clients connected to an Oracle RAC database.

Suppose that a user employs a web browser to log in to an application server that accesses a back-end database server. Failure of the database instance can result in a wait that can be up to minutes in duration before the failure is known to the user. The ability to quickly detect failures of server instances, communicate this to the client, close connections, and clean up idle connections in connection pools is provided by HA event notification.

For high availability clients connected to an Oracle RAC database, you can use HA event notification to provide a best-effort programmatic signal to the client if there is a database failure. Client applications can register a callback on the environment handle to signal interest in this information. When a significant failure event occurs that applies to a connection made by this client, the callback is invoked, with information concerning the event (the event payload) and a list of connections (server handles) that were disconnected because of the failure.

For example, consider a client application that has two connections to instance A and two connections to instance B of the same database. If instance A goes down, a notification of the event is sent to the client, which then disconnects the two connections to instance B and invokes the registered callback. Note that if another instance C of the same database goes down, the client is not notified (because it does not affect any of the client's connections).

The HA event notification mechanism improves the response time of the application in the presence of failure. Before the mechanism was introduced in Oracle Database 10g Release 2 (10.2), a failure would result in the connection being broken only after the TCP timeout interval expired, which could take minutes. With HA event notification, the standalone, connection pool, and session pool connections are automatically broken and cleaned up by OCI, and the application callback is invoked within seconds of the failure event. If any of these server handles are TAF-enabled, failover is also automatically engaged by OCI.

In the current release, this functionality depends on Oracle Notification Service (ONS). It requires Oracle Clusterware to be installed and configured on the database server for the clients to receive the HA notifications through ONS. All clusterware installations (for example, Oracle Data Guard) should have the same ONS port. There is no client configuration required for ONS.

**Note:**

The client transparently gets the ONS server information from the database to which it connects. The application administrator can augment or override that information using the deployment configuration file `oraaccess.xml`.

Applications must connect to an Oracle RAC instance to enable HA event notification. Furthermore, these applications must:

- Initialize the OCI Environment in `OCI_EVENTS` mode

- Connect to a service that has notifications enabled (use the `DBMS_SERVICE.MODIFY_SERVICE` procedure to set `AQ_HA_NOTIFICATIONS` to `TRUE`)

- Link with a thread library

Then these applications can register a callback that is invoked whenever an HA event occurs.

This section includes the following topics:

- OCIEvent Handle

- OCI Failover for Connection and Session Pools

- OCI Failover for Independent Connections

- Event Callback

- Custom Pooling: Tagged Server Handles

- About Determining Transparent Application Failover (TAF) Capabilities

**See Also:**

[About Client-Side Deployment Parameters Specified in oraaccess.xml](build-and-configure-oci-applications.md) for more information about `oraaccess.xml` and details about the parameters under `<events>`, `<fan>` and `<ons>`

#### 12.2.1 OCIEvent Handle

The `OCIEvent` handle encapsulates the attributes from the event payload.

OCI implicitly allocates this handle before calling the event callback, which can obtain the read-only attributes of the event by calling `OCIAttrGet()`. Memory associated with these attributes is only valid for the duration of the event callback.

**See Also:**

- [Event Handle Attributes](handle-and-descriptor-attributes.md)

- [OCIAttrGet()](handle-and-descriptor-functions.md)

#### 12.2.2 OCI Failover for Connection and Session Pools

A connection pool in an instance of Oracle RAC consists of a pool of connections connected to different instances of Oracle RAC.

Upon receiving the node failure notification, all the connections connected to that particular instance should be cleaned up. For the connections that are in use, OCI must close the connections: transparent application failover (TAF) occurs immediately, and those connections are reestablished. The connections that are idle and in the free list of the pool must be purged, so that a bad connection is never returned to the user from the pool.

To accommodate custom connection pools, OCI provides a callback function that can be registered on the environment handle. If registered, this callback is invoked when an HA event occurs. Session pools are treated the same way as connection pools. Note that server handles from OCI connection pools or session pools are not passed to the callback. Hence in some cases, the callback could be called with an empty list of connections.

#### 12.2.3 OCI Failover for Independent Connections

No special handling is required for independent connections; all such connections that are connected to failed instances are immediately disconnected.

For idle connections, TAF is engaged to reestablish the connection when the connection is used on a subsequent OCI call. Connections that are in use at the time of the failure event are broken out immediately, so that TAF can begin. Note that this applies for the "in-use" connections of connection and session pools also.

#### 12.2.4 Event Callback

Shows the signature of the event callback of type `OCIEventCallback`.

The event callback, of type `OCIEventCallback`, has the following signature:

    void evtcallback_fn (void      *evtctx,
                         OCIEvent  *eventhp );

In this signature `evtctx` is the client context, and `OCIEvent` is an event handle that is opaque to the OCI library. The other input argument is `eventhp`, the event handle (the attributes associated with an event).

If registered, this function is called once for each event. For Oracle RAC HA events, this callback is invoked after the affected connections have been disconnected. The following environment handle attributes are used to register an event callback and context, respectively:

- `OCI_ATTR_EVTCBK` is of data type `OCIEventCallback` `*`. It is read-only.

- `OCI_ATTR_EVTCTX` is of data type `void` `*`. It is also read-only.

<!-- -->

    text *myctx = "dummy context"; /* dummy context passed to callback fn */
    ...
    /* OCI_ATTR_EVTCBK and OCI_ATTR_EVTCTX are read-only. */
    OCIAttrSet(envhp, (ub4) OCI_HTYPE_ENV, (void *) evtcallback_fn,
               (ub4) 0, (ub4) OCI_ATTR_EVTCBK, errhp);
    OCIAttrSet(envhp, (ub4) OCI_HTYPE_ENV, (void *) myctx,
               (ub4) 0, (ub4) OCI_ATTR_EVTCTX, errhp);
    ...

Within the OCI event callback, the list of affected server handles is encapsulated in the `OCIEvent` handle. For Oracle RAC HA DOWN events, client applications can iterate over a list of server handles that are affected by the event by using `OCIAttrGet()` with attribute types `OCI_ATTR_HA_SRVFIRST` and `OCI_ATTR_HA_SRVNEXT`:

    OCIAttrGet(eventhp, OCI_HTYPE_EVENT, (void *)&srvhp, (ub4 *)0,
               OCI_ATTR_HA_SRVFIRST, errhp);
    /* or, */
    OCIAttrGet(eventhp, OCI_HTYPE_EVENT, (void *)&srvhp, (ub4 *)0,
               OCI_ATTR_HA_SRVNEXT, errhp);

When called with attribute `OCI_ATTR_HA_SRVFIRST`, this function retrieves the first server handle in the list of server handles affected. When called with attribute `OCI_ATTR_HA_SRVNEXT`, this function retrieves the next server handle in the list. This function returns `OCI_NO_DATA` and `srvhp` is a `NULL` pointer, when there are no more server handles to return.

`srvhp` is an output pointer to a server handle whose connection has been closed because of an HA event. `errhp` is an error handle to populate. The application returns an `OCI_NO_DATA` error when there are no more affected server handles to retrieve.

When retrieving the list of server handles that have been affected by an HA event, be aware that the connection has already been closed and many server handle attributes are no longer valid. Instead, use the user memory segment of the server handle to store any per-connection attributes required by the event notification callback. This memory remains valid until the server handle is freed.

**See Also:**

[OCIAttrGet()](handle-and-descriptor-functions.md)

#### 12.2.5 Custom Pooling: Tagged Server Handles

Using custom pools, you can retrieve the server handle’s tag information so appropriate cleanup can be performed.

The following features apply to custom pools:

- You can tag a server handle with its parent connection object if it is created on behalf of a custom pool. Use the "user memory" parameters of `OCIHandleAlloc()` to request that the server handle be allocated with a user memory segment. A pointer to the "user memory" segment is returned by `OCIHandleAlloc()`.

- When an HA event occurs and an affected server handle has been retrieved, there is a means to retrieve the server handle's tag information so appropriate cleanup can be performed. The attribute `OCI_ATTR_USER_MEMORY` is used to retrieve a pointer to a handle's user memory segment. `OCI_ATTR_USER_MEMORY` is valid for all user-allocated handles. If the handle was allocated with extra memory, this attribute returns a pointer to the user memory. A `NULL` pointer is returned for those handles not allocated with extra memory. This attribute is read-only and is of data type `void*`.

**Note:**

You are free to define the precise contents of the server handle's user memory segment to facilitate cleanup activities from within the HA event callback (or for other purposes if needed) because OCI does not write or read from this memory in any way. The user memory segment is freed with the `OCIHandleFree()` call on the server handle.

Example 12-1 shows an example of event notification.

Example 12-1 Event Notification

    sword retval;
    OCIServer *srvhp;
    struct myctx {
       void *parentConn_myctx;
       uword numval_myctx;
    };
    typedef struct myctx myctx;
    myctx  *myctxp;
    /* Allocate a server handle with user memory - pre 10.2 functionality */
    if (retval = OCIHandleAlloc(envhp, (void **)&srvhp, OCI_HTYPE_SERVER,
                                (size_t)sizeof(myctx), (void **)&myctxp)
    /* handle error */
    myctxp->parentConn_myctx = <parent connection reference>;

    /* In an event callback function, retrieve the pointer to the user memory */
    evtcallback_fn(void *evtctx, OCIEvent *eventhp)
    {
      myctx *ctxp = (myctx *)evtctx;
      OCIServer *srvhp;
      OCIError *errhp;
      sb4       retcode;
      retcode = OCIAttrGet(eventhp, OCI_HTYPE_SERVER, &srvhp, (ub4 *)0,
                           OCI_ATTR_HA_SRVFIRST, errhp);
      while (!retcode) /* OCIAttrGet will return OCI_NO_DATA if no more srvhp */
      {
         OCIAttrGet((void *)srvhp, OCI_HTYPE_SERVER, (void *)&ctxp,
                    (ub4)0, (ub4)OCI_ATTR_USER_MEMORY, errhp);
               /* Remove the server handle from the parent connection object */
         retcode = OCIAttrGet(eventhp, OCI_HTYPE_SERVER, &srvhp, (ub4 *)0,
                              OCI_ATTR_HA_SRVNEXT, errhp);
    ...
      }
    ...
    }

**See Also:**

- [OCIHandleAlloc()](handle-and-descriptor-functions.md)

- [OCIHandleFree()](handle-and-descriptor-functions.md)

#### 12.2.6 About Determining Transparent Application Failover (TAF) Capabilities

You can have the application adjust its behavior if a connection is or is not TAF-enabled.

Use `OCIAttrGet()` as follows to determine if a server handle is TAF-enabled:

    boolean taf_capable;
    ...
    OCIAttrGet(srvhp, (ub4) OCI_HTYPE_SERVER, (void *) &taf_capable,
               (ub4) sizeof(taf_capable), (ub4)OCI_ATTR_TAF_ENABLED, errhp);
    ...

In this example, `taf_capable` is a Boolean variable, which this call sets to `TRUE` if the server handle is TAF-enabled, and `FALSE` if not; `srvhp` is an input target server handle; `OCI_ATTR_TAF_ENABLED` is an attribute that is a pointer to a Boolean variable and is read-only; `errhp` is an input error handle.

### 12.3 Transparent Application Failover in OCI

Transparent application failover (TAF) is a client-side feature designed to minimize disruptions to end-user applications that occur when database connectivity fails because of instance or network failure.

TAF can be implemented on a variety of system configurations including Oracle Real Application Clusters (Oracle RAC) and Oracle Data Guard physical standby databases. TAF can also be used after restarting a single instance system (for example, when repairs are made).

TAF can be configured to restore database sessions and optionally, to replay open queries. Starting with Oracle Database 10g Release 2 (10.2) all statements that an application attempts to use after a failure attempt failover. That is, an attempt to execute or fetch against other statements engages TAF recovery just as for the failure-time statement. Subsequent statements may now succeed (whereas in the past they failed), or the application may receive errors corresponding to an attempted TAF recovery (such as `ORA-25401`).

**Note:**

Oracle recommends for applications to register a callback, so when failover happens, the callback can be used to restore the session to the desired state.

**Note:**

TAF is not supported for remote database links or for DML statements.

This section contains the following topics:

- About Configuring Transparent Application Failover

- Transparent Application Failover Callbacks in OCI

- Transparent Application Failover Callback Structure and Parameters

- Failover Callback Structure and Parameters

- Failover Callback Registration

- Failover Callback Example

- Handling OCI_FO_ERROR

- TAF Support for IAM Based Token Authentication in OCI

#### 12.3.1 About Configuring Transparent Application Failover

TAF can be configured on both the client side and the server side. If both are configured, server-side settings take precedence.

Configure TAF on the client side by including the `FAILOVER_MODE` parameter in the `CONNECT_DATA` portion of a connect descriptor.

Configure TAF on the server side by modifying the target service with the `DBMS_SERVICE.MODIFY_SERVICE` packaged procedure.

An initial attempt at failover may not always succeed. OCI provides a mechanism for retrying failover after an unsuccessful attempt.

**See Also:**

- [Oracle Database Net Services Reference](../netrf/local-naming-parameters-in-tns-ora-file.md) for more information about client-side configuration of TAF (Connect Data Section)

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_SERVICE.md) for more information about the server-side configuration of TAF (DBMS_SERVICE)

#### 12.3.2 Transparent Application Failover Callbacks in OCI

Because of the delay that can occur during failover, the application developer may want to inform the user that failover is in progress, and request that the user wait for notification that failover is complete.

Additionally, the session on the initial instance may have received some `ALTER` `SESSION` commands. These `ALTER` `SESSION` commands are not automatically replayed on the second instance. Consequently, the developer may want to replay them on the second instance. `OCIAttrSet()` calls that affect the session must also be reexecuted.

To accommodate these requirements, the application developer can register a failover callback function. If failover occurs, the callback function is invoked several times while reestablishing the user's session.

The first call to the callback function occurs when the database first detects an instance connection loss. This callback is intended to allow the application to inform the user of an upcoming delay. If failover is successful, a second call to the callback function occurs when the connection is reestablished and usable.

Once the connection has been reestablished, the client may want to replay `ALTER` `SESSION` commands and inform the user that failover has happened. If failover is unsuccessful, then the callback is called to inform the application that failover cannot occur. Additionally, the callback is called each time a user handle besides the primary handle is reauthenticated on the new connection. Because each user handle represents a server-side session, the client may want to replay `ALTER` `SESSION` commands for that session.

**See Also:**

- [OCIAttrSet()](handle-and-descriptor-functions.md)

- Handling OCI_FO_ERROR for more information about this scenario

#### 12.3.3 Transparent Application Failover Callback Structure and Parameters

Describes the TAF Callback structure and parameters.

The basic structure of a Transparent Application Failover (TAF) callback function is as follows:

    sb4  TAFcbk_fn(OCISvcCtx *svchp,
                   OCIEnv    *envhp,
                   void      *fo_ctx,
                   ub4        fo_type,
                   ub4        fo_event);

svchp
The service context handle.

envhp
The OCI environment handle.

fo_ctx
The client context. This is a pointer to memory specified by the client. In this area the client can keep any necessary state or context.

fo_type
The failover type. This lets the callback know what type of failover the client has requested. The usual values are as follows:

- `OCI_FO_SESSION` indicates that the user has requested only session failover.

- `OCI_FO_SELECT` indicates that the user has requested select failover as well.

fo_event
The failover event indicates the current status of the failover.

- `OCI_FO_BEGIN` indicates that failover has detected a lost connection and failover is starting.

- `OCI_FO_END` indicates successful completion of failover.

- `OCI_FO_ABORT` indicates that failover was unsuccessful, and there is no option of retrying.

- `OCI_FO_ERROR` also indicates that failover was unsuccessful, but it gives the application the opportunity to handle the error and retry failover.

- `OCI_FO_REAUTH` indicates that you have multiple authentication handles and failover has occurred after the original authentication. It indicates that a user handle has been reauthenticated. To determine which one, the application checks the `OCI_ATTR_SESSION` attribute of the service context handle `svchp`.

- `OCI_FO_BEGIN_EXPIREDTOKEN` indicates that this failover event should be used by the applications to provide the renewed token and the private key.

If Application Continuity is configured, the TAF callback is called with `OCI_FO_END` after successfully re-connecting, re-authenicating, and determining the status of the inflight transaction.

Upon completion of the TAF callback, OCI returns an error if an open transaction is present and Application Continuity for OCI is enabled.

#### 12.3.4 Failover Callback Structure and Parameters

Shows and describes the basic structure of a user-defined application failover callback function.

The basic structure of a user-defined application failover callback function is as follows:

    sb4 appfocallback_fn ( void       * svchp,
                           void       * envhp,
                           void       * fo_ctx,
                           ub4        fo_type,
                           ub4        fo_event );

An example is provided in "Failover Callback Example" on page 9‐31 for the following parameters:

svchp
The first parameter, `svchp`, is the service context handle. It is of type `void *`.

envhp
The second parameter, `envhp`, is the OCI environment handle. It is of type `void *`.

fo_ctx
The third parameter, `fo_ctx`, is a client context. It is a pointer to memory specified by the client. In this area the client can keep any necessary state or context. It is passed as a `void *`.

fo_type
The fourth parameter, `fo_type`, is the failover type. This lets the callback know what type of failover the client has requested. The usual values are as follows:

- `OCI_FO_SESSION` indicates that the user has requested only session failover.

- `OCI_FO_SELECT` indicates that the user has requested select failover as well.

fo_event
The last parameter is the failover event. This indicates to the callback why it is being called. It has several possible values:

- `OCI_FO_BEGIN` indicates that failover has detected a lost connection and failover is starting.

- `OCI_FO_END` indicates successful completion of failover.

- `OCI_FO_ABORT` indicates that failover was unsuccessful, and there is no option of retrying.

- `OCI_FO_ERROR` also indicates that failover was unsuccessful, but it gives the application the opportunity to handle the error and retry failover.

- `OCI_FO_REAUTH` indicates that you have multiple authentication handles and failover has occurred after the original authentication. It indicates that a user handle has been reauthenticated. To determine which one, the application checks the `OCI_ATTR_SESSION` attribute of the service context handle (which is the first parameter).

- `OCI_FO_BEGIN_EXPIREDTOKEN` indicates that this failover event should be used by the application to provide the renewed token and the private key.

#### 12.3.5 Failover Callback Registration

For the failover callback to be used, it must be registered on the server context handle. This registration is done by creating a callback definition structure and setting the `OCI_ATTR_FOCBK` attribute of the server handle to this structure.

The callback definition structure must be of type `OCIFocbkStruct`. It has two fields: `callback_function`, which contains the address of the function to call, and `fo_ctx`, which contains the address of the client context.

**See Also:**

Example 12-3 for an example of callback registration

#### 12.3.6 Failover Callback Example

Shows several failover callback examples.

This section shows an example of a simple user-defined callback function definition (see Example 12-2), failover callback registration (see Example 12-3), and failover callback unregistration (see Example 12-4).

Example 12-2 User-Defined Failover Callback Function Definition

    sb4  callback_fn(svchp, envhp, fo_ctx, fo_type, fo_event)
    void * svchp;
    void * envhp;
    void *fo_ctx;
    ub4 fo_type;
    ub4 fo_event;
    {
    switch (fo_event)
       {
       case OCI_FO_BEGIN:
       {
         printf(" Failing Over ... Please stand by \n");
         printf(" Failover type was found to be %s \n",
                         ((fo_type==OCI_FO_SESSION) ? "SESSION"
                         :(fo_type==OCI_FO_SELECT) ? "SELECT"
                         : "UNKNOWN!"));
         printf(" Failover Context is :%s\n",
                        (fo_ctx?(char *)fo_ctx:"NULL POINTER!"));
         break;
       }
       case OCI_FO_ABORT:
       {
         printf(" Failover stopped. Failover will not occur.\n");
         break;
       }
       case    OCI_FO_END:
       {
           printf(" Failover ended ...resuming services\n");
         break;
       }
       case OCI_FO_REAUTH:
       {
           printf(" Failed over user. Resuming services\n");
         break;
       }
       default:
       {
         printf("Bad Failover Event: %d.\n",  fo_event);
         break;
       }
       }
       return 0;
    }

Example 12-3 Failover Callback Registration

    int register_callback(srvh, errh)
    void *srvh; /* the server handle */
    OCIError *errh; /* the error handle */
    {
      OCIFocbkStruct failover;                 /*  failover callback structure */
      /* allocate memory for context */
      if (!(failover.fo_ctx = (void *)malloc(strlen("my context.")+1)))
         return(1);
      /* initialize the context. */
      strcpy((char *)failover.fo_ctx, "my context.");
      failover.callback_function = &callback_fn;
      /* do the registration */
      if (OCIAttrSet(srvh, (ub4) OCI_HTYPE_SERVER,
                    (void *) &failover, (ub4) 0,
                    (ub4) OCI_ATTR_FOCBK, errh)  != OCI_SUCCESS)
         return(2);
      /* successful conclusion */
      return (0);
    }

Example 12-4 Failover Callback Unregistration

    OCIFocbkStruct failover;   /*  failover callback structure */
    sword status;

      /* set the failover context to null */
      failover.fo_ctx = NULL;
      /* set the failover callback to null */
      failover.callback_function = NULL;
      /* unregister the callback */
      status = OCIAttrSet(srvhp, (ub4) OCI_HTYPE_SERVER,
                          (void *) &failover, (ub4) 0,
                          (ub4) OCI_ATTR_FOCBK, errhp);

#### 12.3.7 Handling OCI_FO_ERROR

A failover attempt is not always successful. If the attempt fails, the callback function receives a value of `OCI_FO_ABORT` or `OCI_FO_ERROR` in the `fo_event` parameter.

A value of `OCI_FO_ABORT` indicates that failover was unsuccessful, and no further failover attempts are possible. `OCI_FO_ERROR`, however, provides the callback function with the opportunity to handle the error. For example, the callback may choose to wait a specified period of time and then indicate to the OCI library that it must reattempt failover.

**Note:**

This functionality is only available to applications linked with the 8.0.5 or later OCI libraries running against any Oracle Database server.

Failover does not work if a LOB column is part of the select list.

Consider the timeline of events presented in Table 12-1.

Table 12-1 Time and Event

| Time | Event                                                                |
|:-----|:---------------------------------------------------------------------|
| T0   | Database fails (failure lasts until T5).                             |
| T1   | Failover is triggered by user activity.                              |
| T2   | User attempts to reconnect; attempt fails.                           |
| T3   | Failover callback is invoked with `OCI_FO_ERROR`.                    |
| T4   | Failover callback enters a predetermined sleep period.               |
| T5   | Database comes back up again.                                        |
| T6   | Failover callback triggers a new failover attempt; it is successful. |
| T7   | User successfully reconnects.                                        |

The callback function triggers the new failover attempt by returning a value of `OCI_FO_RETRY` from the function.

Example 12-5 shows a callback function that you can use to implement the failover strategy similar to the scenario described earlier. In this case, the failover callback enters a loop in which it sleeps and then reattempts failover until it is successful:

Example 12-5 Callback Function That Implements a Failover Strategy

    /*--------------------------------------------------------------------*/
    /* the user-defined failover callback  */
    /*--------------------------------------------------------------------*/
    sb4  callback_fn(svchp, envhp, fo_ctx, fo_type, fo_event )
    void * svchp;
    void * envhp;
    void *fo_ctx;
    ub4 fo_type;
    ub4 fo_event;
    {
       OCIError *errhp;
       OCIHandleAlloc(envhp, (void **)&errhp, (ub4) OCI_HTYPE_ERROR,
                  (size_t) 0, (void **) 0);
       switch (fo_event)
       {
       case OCI_FO_BEGIN:
       {
         printf(" Failing Over ... Please stand by \n");
         printf(" Failover type was found to be %s \n",
                ((fo_type==OCI_FO_NONE) ? "NONE"
                 :(fo_type==OCI_FO_SESSION) ? "SESSION"
                 :(fo_type==OCI_FO_SELECT) ? "SELECT"
                 :(fo_type==OCI_FO_TXNAL) ? "TRANSACTION"
                 : "UNKNOWN!"));
         printf(" Failover Context is :%s\n",
                (fo_ctx?(char *)fo_ctx:"NULL POINTER!"));
         break;
       }
       case OCI_FO_ABORT:
       {
         printf(" Failover aborted. Failover will not occur.\n");
         break;
       }
       case    OCI_FO_END:
       {
           printf("\n Failover ended ...resuming services\n");
         break;
       }
       case OCI_FO_REAUTH:
       {
           printf(" Failed over user. Resuming services\n");
         break;
       }
       case OCI_FO_ERROR:
       {
         /* all invocations of this can only generate one line. The newline
          * will be put at fo_end time.
          */
         printf(" Failover error gotten. Sleeping...");
         sleep(3);
         printf("Retrying. ");
         return (OCI_FO_RETRY);
         break;
       }
       default:
       {
         printf("Bad Failover Event: %d.\n",  fo_event);
         break;
       }
       }
       return 0;
    }

#### 12.3.8 TAF Support for IAM Based Token Authentication in OCI

This section covers TAF support for token-based authentication in OCI.

**See Also:**

- [Identity and Access Management (IAM) Token-Based Authentication](introduction.md)

##### 12.3.8.1 Providing the DB Token Programmatically

If the cached token expires, the latest token and key must be specified in the failover callback as attributes on the connection passed to the callback. These are cached by OCI after the failover is complete.

A new fail over event `OCI_FO_BEGIN_EXPIREDTOKEN` is introduced. The TAF callback is invoked to renew the expired token.

Example 12-6 TAF Callback Function to Accommodate Token-Based Authentication

    sb4 callback_fn(dvoid *svchp, dvoid *envhp, dvoid *fo_ctx, ub4 fo_type, ub4 fo_\
    event)
    {
      if (fo_event == OCI_FO_BEGIN_EXPIREDTOKEN)
      {
        /* Set new token attributes */
        OCISession *usrhp=NULL;
        OCIError *ehp=NULL;
        OCIHandleAlloc ((dvoid *)envhp, (dvoid **)&ehp,
                        OCI_HTYPE_ERROR, 0, (dvoid *)0);
        OCIAttrGet((dvoid *)svchp, (ub4)OCI_HTYPE_SVCCTX,
                   (dvoid *)&usrhp, (ub4 *)0, (ub4)OCI_ATTR_SESSION, ehp);
        if (usrhp)
        {
          getToken(token, &tokenLen, privateKey, &privateKeyLen);
          OCIAttrSet((dvoid *) usrhp, (ub4) OCI_HTYPE_SESSION,
                     (dvoid *) token, (ub4) tokenLen,
                     OCI_ATTR_TOKEN, ehp);
          OCIAttrSet((dvoid *) usrhp, (ub4) OCI_HTYPE_SESSION,
                     (dvoid *) privateKey, (ub4) privateKeyLen,
                     OCI_ATTR_IAM_PRIVKEY, ehp);
        }
        OCIHandleFree((dvoid *) ehp, OCI_HTYPE_ERROR);
      }
    }

Example 12-7 Get Token

    void getToken(char *token[], sb4 *tokenLen, char *privateKey[], char *tokenLoc)
    {
      token_file_loc = 'tokenFile.txt';
      private_key_file_loc = 'privateKey.pem';
      fp = fopen(token_file_loc, "r");
      if (fp != NULL) {
        size_t newLen = fread(token, sizeof(char), MAXBUFLEN, fp);
        token[newLen++] = '\0';
      }
      *tokenLen = newLen;
      fclose(fp);
      fp = fopen(private_key_file_loc, "r");
      if (fp != NULL)
      {
        while ((rlen = getline(&line, &len, fp)) != -1 && line != NULL)
        {
          /* skip lines containing PEM delimiters */
          if ( strstr( line, "--BEGIN ") != NULL) {
            start = TRUE;
            continue;
          }
          else if ( strstr( line, "--END ") != NULL) {
            start = FALSE;
          break;
          }
          if (!start)
            continue;
          /* remove the \n */
          line[strlen((const char *)line) - 1] = '\0';
          strcat((char *)privateKey, line);
          pvreadLen += strlen((const char *)line);
      }
      *privateKeyLen = pvreadLen;
      return;
    }

##### 12.3.8.2 Providing the DB Token in a File

The location of the token file must be specified in the connect string when establishing the initial session and the post-failover session.

**Note:**

The token is always read from the file and not cached

The application administrator must keep the token location up-to-date with the latest token.

### 12.4 OCI and Transaction Guard

Transaction Guard introduces the concept of at-most-once transaction execution in case of a planned or unplanned outage to help prevent an application upon failover from submitting a duplicate submission of an original submission.

When an application opens a connection to the database using this service, the logical transaction ID (LTXID) is generated at authentication and stored in the session handle. This is a globally unique ID that identifies the database transaction from the application perspective. When there is an outage, an application using Transaction Guard can retrieve the LTXID from the previous failed session's handle and use it to determine the outcome of the transaction that was active prior to the session failure. If the LTXID is determined to be unused, then the application can replay an uncommitted transaction by first blocking the original submission using the retrieved LTXID. If the LTXID is determined to be used, then the transaction is committed and the result is returned to the application.

Transaction Guard is a developer API supported for JDBC Type 4 (Oracle Thin), OCI, OCCI, and Oracle Data Provider for .NET (ODP.NET) drivers. For OCI, when an application is written to support Transaction Guard, upon an outage, the OCI client driver acquires and retrieves the LTXID from the previous failed session's handle by calling `OCI_ATTR_GET()` using the `OCI_ATTR_LTXID` session handle attribute.

This section includes the following topic: Developing Applications that Use Transaction Guard.

**See Also:**

[Oracle Database Development Guide](../adfns/transaction-guard.md) for information in the chapter about using Transaction Guard in for an overview of Transaction Guard, supported transaction types, transaction types that are not supported, and database configuration information for using Transaction Guard.

#### 12.4.1 Developing Applications that Use Transaction Guard

This section describes developing OCI user applications that use Transaction Guard.

See the chapter about using Transaction Guard in [Oracle Database Development Guide](../adfns/transaction-guard.md) for more detailed information about developing applications using Transaction Guard.

For the third-party or user application to use Transaction Guard in order to be able to fail over a session for OCI, it must include several major steps:

1.  Verify if Transparent Application Failover (TAF) is enabled for the connection. Do not attempt to explicitly use Transaction Guard on a TAF-enabled connection, as TAF will automatically check the `LTXID`.
2.  On receipt of an error, determine whether the error is a recoverable error - `OCI_ATTR_ERROR_IS_RECOVERABLE` on `OCI_ERROR` handle. If the error is recoverable, then continue to Step 3.
    **Note:**

    Do not attempt to use the LTXID to check transaction outcome if the connection has not suffered a recoverable error.
3.  Retrieve the LTXID associated with the failed session by using OCI_ATTR_GET() to get the OCI_ATTR_LTXID from the user session handle.
4.  Reconnect to the database.
    **Note:**

    The new session will have a new LTXID, but you will not need it when checking the status of the original session.
5.  Invoke the `DBMS_APP_CONT.GET_LTXID_OUTCOME` PL/SQL procedure with the LTXID obtained from the `OCI_ATTR_GET()` call. The original LTXID of the failed-over session is marked as forced if that LTXID has not been used. The return state tells the driver if the last transaction was `COMMITTED (TRUE/FALSE)` and `USER_CALL_COMPLETED (TRUE/FALSE)`.
6.  The application can replay an uncommitted transaction or return the result to the user. If the replay itself incurs an outage, then the LTXID for the replaying session is used for the `DBMS_APP_CONT.GET_LTXID_OUTCOME` procedure.

See the following sections for Transaction Guard usage and examples:

- Typical Transaction Guard Usage

- Transaction Guard Examples

##### 12.4.1.1 Typical Transaction Guard Usage

Shows typical usage of Transaction Guard using pseudocode.

The following pseudocode shows a typical usage of Transaction Guard:

1.  Receive a FAN down event (or recoverable error)

2.  FAN aborts the dead session

3.  Call `OCIAttrGet()` using the `OCI_ATTR_TAF_ENABLED` attribute on the server handle. If the value is `TRUE`, stop. If the value is `FALSE`, proceed to the next step.

4.  If it is a recoverable error, for OCI (`OCI_ATTR_ERROR_IS_RECOVERABLE` on `OCI_ERROR` handle):

    1.  Get the last LTXID from the dead session by calling `OCIAttrGet()` using the `OCI_ATTR_LTXID` session handle attribute to retrieve the LTXID associated with the session's handle

    2.  Obtain a new session

    3.  Call `DBMS_APP_CONT.GET_LTXID_OUTCOME` with the last LTXID to get the return state

5.  If the return state is:

    1.  `COMMITTED` and `USER_CALL_COMPLETED`

        Then return the result.

    2.  `ELSEIF COMMITTED` and `NOT USER_CALL_COMPLETED`

        Then return the result with a warning (with details, such as out binds or row count was not returned).

    3.  `ELSEIF NOT COMMITTED`

        Resubmit the transaction or series of calls or both, or return error to user.

**See Also:**

[OCIAttrGet()](handle-and-descriptor-functions.md)

##### 12.4.1.2 Transaction Guard Examples

Shows a Transaction Guard demo program.

Example 12-8 is an OCI Transaction Guard demo program (`cdemotg.c`) that demonstrates:

- Use of the attribute `OCI_ATTR_ERROR_IS_RECOVERABLE`. When an error occurs, the program checks if the error is recoverable.

- Use of the packaged procedure `DBMS_APP_CONT.GET_LTXID_OUTCOME`. If the error is recoverable, the program calls `DBMS_APP_CONT.GET_LTXID_OUTCOME` to determine the status of the active transaction.

If the transaction has not committed, the program re-executes the failed transaction.

**Note:**

This program does not modify the session state such as NLS parameters, and so forth. Programs that do so may need to reexecute such commands after obtaining a new session from the pool following the error.

Example 12-8 Transaction Guard Demo Program

    */

    #ifndef OCISP_ORACLE
    # include <cdemosp.h>
    #endif

    /* Maximum Number of threads  */
    #define MAXTHREAD 1
    static ub4 sessMin = 1;
    static ub4 sessMax = 9;
    static ub4 sessIncr = 2;

    static OCIError   *errhp;
    static OCIEnv     *envhp;
    static OCISPool   *poolhp=(OCISPool *) 0;
    static int employeeNum[MAXTHREAD];

    static OraText *poolName;
    static ub4 poolNameLen;
    static CONST OraText *database = (text *)"ltxid_service";
    static CONST OraText *appusername =(text *)"scott";
    static CONST OraText *apppassword =(text *)"tiger";

    static CONST char getLtxid[]=
      ("BEGIN DBMS_APP_CONT.GET_LTXID_OUTCOME ("
       ":ltxid,:committed,:callComplete); END;");

    static CONST char insertst1[] =
      ("INSERT INTO EMP(ENAME, EMPNO) values ('NAME1', 1000)");

    static void checkerr (OCIError *errhp, sword status);
    static void threadFunction (dvoid *arg);

    int main(void)
    {
      int i = 0;
      sword lstat;
      int timeout =1;
      OCIEnvCreate (&envhp, OCI_THREADED, (dvoid *)0,  NULL,
                    NULL, NULL, 0, (dvoid *)0);

      (void) OCIHandleAlloc((dvoid *) envhp, (dvoid **) &errhp, OCI_HTYPE_ERROR,
                            (size_t) 0, (dvoid **) 0);

      (void) OCIHandleAlloc((dvoid *) envhp, (dvoid **) &poolhp, OCI_HTYPE_SPOOL,
                            (size_t) 0, (dvoid **) 0);

      /* Create the session pool */
      checkerr(errhp, OCIAttrSet((dvoid *) poolhp,
               (ub4) OCI_HTYPE_SPOOL, (dvoid *) &timeout, (ub4)0,
               OCI_ATTR_SPOOL_TIMEOUT, errhp));

      if (lstat = OCISessionPoolCreate(envhp, errhp,poolhp, (OraText **)&poolName,
                  (ub4 *)&poolNameLen, database,
                  (ub4)strlen((const char *)database),
                  sessMin, sessMax, sessIncr,
                  (OraText *)appusername,
                  (ub4)strlen((const char *)appusername),
                  (OraText *)apppassword,
                  (ub4)strlen((const char *)apppassword),
                  OCI_SPC_STMTCACHE|OCI_SPC_HOMOGENEOUS))
      {
        checkerr(errhp,lstat);
      }

      printf("Session Pool Created \n");

      /* Multiple threads using the session pool */
      {
        OCIThreadId *thrid[MAXTHREAD];
        OCIThreadHandle *thrhp[MAXTHREAD];

        OCIThreadProcessInit ();
        checkerr (errhp, OCIThreadInit (envhp, errhp));
        for (i = 0; i < MAXTHREAD; ++i)
        {
          checkerr (errhp, OCIThreadIdInit (envhp, errhp, &thrid[i]));
          checkerr (errhp, OCIThreadHndInit (envhp, errhp, &thrhp[i]));
        }
        for (i = 0; i < MAXTHREAD; ++i)
        {
          employeeNum[i]=i;
          /* Inserting into EMP table */
          checkerr (errhp, OCIThreadCreate (envhp, errhp, threadFunction,
                    (dvoid *) &employeeNum[i], thrid[i], thrhp[i]));
        }
        for (i = 0; i < MAXTHREAD; ++i)
        {
          checkerr (errhp, OCIThreadJoin (envhp, errhp, thrhp[i]));
          checkerr (errhp, OCIThreadClose (envhp, errhp, thrhp[i]));
          checkerr (errhp, OCIThreadIdDestroy (envhp, errhp, &(thrid[i])));
          checkerr (errhp, OCIThreadHndDestroy (envhp, errhp, &(thrhp[i])));
        }
        checkerr (errhp, OCIThreadTerm (envhp, errhp));
      } /* ALL THE THREADS ARE COMPLETE */
      lstat =  OCISessionPoolDestroy(poolhp, errhp, OCI_DEFAULT);

      printf("Session Pool Destroyed \n");

      if (lstat != OCI_SUCCESS)
        checkerr(errhp, lstat);

      checkerr(errhp, OCIHandleFree((dvoid *)poolhp, OCI_HTYPE_SPOOL));

      checkerr(errhp, OCIHandleFree((dvoid *)errhp, OCI_HTYPE_ERROR));
      return 0;

    } /* end of main () */

    /* Inserts records into EMP table */
    static void threadFunction (dvoid *arg)
    {
      int empno = *(int *)arg;
      OCISvcCtx *svchp = (OCISvcCtx *) 0;
      OCISvcCtx *svchp2 = (OCISvcCtx *) 0;
      OCISession *embUsrhp = (OCISession *)0;
      OCIBind *bnd1p, *bnd2p, *bnd3p;

      OCIStmt *stmthp = (OCIStmt *)0;
      OCIStmt *getLtxidStm = (OCIStmt *)0;
      OCIError  *errhp2 = (OCIError *) 0;
      OCIAuthInfo *authp = (OCIAuthInfo *)0;
      sword lstat;
      text name[10];

      boolean callCompl, committed, isRecoverable;
      ub1 *myLtxid;
      ub4  myLtxidLen;

      ub4 numAttempts = 0;

      (void) OCIHandleAlloc((dvoid *) envhp, (dvoid **) &errhp2, OCI_HTYPE_ERROR,
                         (size_t) 0, (dvoid **) 0);

      lstat =  OCIHandleAlloc((dvoid *) envhp,
                              (dvoid **)&authp, (ub4) OCI_HTYPE_AUTHINFO,
                              (size_t) 0, (dvoid **) 0);
      if (lstat)
        checkerr(errhp2, lstat);

      checkerr(errhp2, OCIAttrSet((dvoid *) authp,(ub4) OCI_HTYPE_AUTHINFO,
               (dvoid *) appusername, (ub4) strlen((char *)appusername),
               (ub4) OCI_ATTR_USERNAME, errhp2));

      checkerr(errhp2,OCIAttrSet((dvoid *) authp,(ub4) OCI_HTYPE_AUTHINFO,
               (dvoid *) apppassword, (ub4) strlen((char *)apppassword),
               (ub4) OCI_ATTR_PASSWORD, errhp2));

    restart:
      if  (lstat = OCISessionGet(envhp, errhp2, &svchp, authp,
                   (OraText *)poolName, (ub4)strlen((char *)poolName), NULL,
                   0, NULL, NULL, NULL, OCI_SESSGET_SPOOL))
      {
        checkerr(errhp2,lstat);
      }

      /* save the ltxid from the session in case we need to call
       *  get_ltxid_outcome to determine the transaction status.
       */
      checkerr(errhp2, OCIAttrGet(svchp, OCI_HTYPE_SVCCTX,
                                  (dvoid *)&embUsrhp, (ub4 *)0,
                                  (ub4)OCI_ATTR_SESSION, errhp2));
      checkerr(errhp2, OCIAttrGet(embUsrhp, OCI_HTYPE_SESSION,
                                  (dvoid *)&myLtxid, (ub4 *)&myLtxidLen,
                                  (ub4)OCI_ATTR_LTXID, errhp2));


      /* */
      checkerr(errhp2, OCIStmtPrepare2(svchp, &stmthp, errhp2,
                                       (CONST OraText *)insertst1,
                                       (ub4)sizeof(insertst1),
                                       (const oratext *)0, (ub4)0,
                                       OCI_NTV_SYNTAX, OCI_DEFAULT));

      if (!numAttempts)
      {
        char input[1];

        printf("Kill SCOTT's session now. Press ENTER when complete\n");
        gets(input);
      }
      lstat = OCIStmtExecute (svchp, stmthp, errhp2, (ub4)1, (ub4)0,
                              (OCISnapshot *)0, (OCISnapshot *)0,
                              OCI_DEFAULT );
      if (lstat == OCI_ERROR)
      {
        checkerr(errhp2, OCIAttrGet(errhp2, OCI_HTYPE_ERROR,
                                    (dvoid *)&isRecoverable, (ub4 *)0,
                                    (ub4)OCI_ATTR_ERROR_IS_RECOVERABLE, errhp2));
        if (isRecoverable)
        {

          printf("Recoverable error occurred; checking transaction status.\n");
          /* get another session to use for the get_ltxid_outcome call */
          if  (lstat = OCISessionGet(envhp, errhp2, &svchp2, authp,
                                     (OraText *)poolName,
                                     (ub4)strlen((char *)poolName), NULL,
                                     0, NULL, NULL, NULL, OCI_SESSGET_SPOOL))
          {
            checkerr(errhp2,lstat);
          }

          checkerr(errhp2,OCIStmtPrepare2(svchp2,&getLtxidStm, errhp2,
                                          (CONST OraText *)getLtxid,
                                          (ub4)sizeof(getLtxid),
                                          (const oratext *)0, (ub4)0,
                                          OCI_NTV_SYNTAX, OCI_DEFAULT));
          checkerr(errhp, OCIBindByPos(getLtxidStm, &bnd1p, errhp, 1,
                                       (dvoid *) myLtxid, (sword)myLtxidLen,
                                       SQLT_BIN, (dvoid *)0,
                                       (ub2 *) 0, (ub2 *) 0, (ub4) 0, (ub4 *) 0,
                                       OCI_DEFAULT));
          checkerr(errhp, OCIBindByPos(getLtxidStm, &bnd2p, errhp, 2,
                                       (dvoid *) &committed,
                                       (sword)sizeof(committed),
                                       SQLT_BOL, (dvoid *)0,
                                       (ub2 *) 0, (ub2 *) 0, (ub4) 0, (ub4 *) 0,
                                       OCI_DEFAULT));
          checkerr(errhp, OCIBindByPos(getLtxidStm, &bnd3p, errhp, 3,
                                       (dvoid *) &callCompl,
                                       (sword)sizeof(callCompl),
                                       SQLT_BOL, (dvoid *)0,
                                       (ub2 *) 0, (ub2 *) 0, (ub4) 0, (ub4 *) 0,
                                       OCI_DEFAULT));

          checkerr(errhp2,OCIStmtExecute(svchp2, getLtxidStm, errhp2,
                                         (ub4)1, (ub4)0,
                                         (OCISnapshot *)0, (OCISnapshot *)0,
                                         OCI_DEFAULT ));
          checkerr(errhp2, OCISessionRelease(svchp2, errhp2,
                                             NULL, 0, OCI_DEFAULT));
          if (committed && callCompl)
            printf("Insert successfully commited \n");
          else if (!committed)
          {
            printf("Transaction did not commit; re-executing last transaction\n");
            numAttempts++;

            /* As there was an outage, do not return this session to the pool */
            checkerr(errhp2,
                     OCISessionRelease(svchp, errhp2,
                                       NULL, 0, OCI_SESSRLS_DROPSESS));
            svchp = (OCISvcCtx *)0;
            goto restart;
          }
        }
      }
      else
      {
        checkerr(errhp2, OCITransCommit(svchp,errhp2,(ub4)0));
        printf("Transaction committed successfully\n");
      }
      if (stmthp)
        checkerr(errhp2, OCIStmtRelease((dvoid *) stmthp, errhp2,
                                        (void *)0, 0, OCI_DEFAULT));
      if (getLtxidStm)
        checkerr(errhp2, OCIStmtRelease((dvoid *) getLtxidStm, errhp2,
                                        (void *)0, 0, OCI_DEFAULT));

      if (svchp)
        checkerr(errhp2, OCISessionRelease(svchp, errhp2, NULL, 0, OCI_DEFAULT));
      OCIHandleFree((dvoid *)authp, OCI_HTYPE_AUTHINFO);
      OCIHandleFree((dvoid *)errhp2, OCI_HTYPE_ERROR);

    } /* end of threadFunction (dvoid *) */

    /* This function prints the error */
    void checkerr(errhp, status)
    OCIError *errhp;
    sword status;
    {
      text errbuf[512];
      sb4 errcode = 0;

      switch (status)
      {
      case OCI_SUCCESS:
        break;
      case OCI_SUCCESS_WITH_INFO:
        (void) printf("Error - OCI_SUCCESS_WITH_INFO\n");
        break;
      case OCI_NEED_DATA:
        (void) printf("Error - OCI_NEED_DATA\n");
        break;
      case OCI_NO_DATA:
        (void) printf("Error - OCI_NODATA\n");
        break;
      case OCI_ERROR:
        (void) OCIErrorGet((dvoid *)errhp, (ub4) 1, (text *) NULL, &errcode,
                           errbuf, (ub4) sizeof(errbuf), OCI_HTYPE_ERROR);
        (void) printf("Error - %.*s\n", 512, errbuf);
        break;
      case OCI_INVALID_HANDLE:
        (void) printf("Error - OCI_INVALID_HANDLE\n");
        break;
      case OCI_STILL_EXECUTING:
        (void) printf("Error - OCI_STILL_EXECUTE\n");
        break;
      case OCI_CONTINUE:
        (void) printf("Error - OCI_CONTINUE\n");
        break;
      default:
        break;
      }
    }

### 12.5 OCI and Application Continuity

Application Continuity (AC) gives High Availability (HA) during planned and unplanned outages. OCI support for AC was introduced with Oracle Database 12c Release 2 (12.2).

AC masks hardware, software, network, storage errors, and timeouts in a HA environment running either Oracle RAC, Oracle RAC One, or Active Data Guard for instance or site failover. AC provides support for SQL\*Plus, Tuxedo, WebLogic Server, and JDBC Type 4 (Oracle Thin), OCI, and Oracle Data Provider for .NET (ODP.NET) drivers.

With planned outages for applications that use the OCI session pool, the OCI session pool detects when a connection has been affected by a `PLANNED DOWN` event and terminates the connection when it is returned to the pool. In planned outages for applications that do not use the OCI session pool, an OCI application detects when a connection has been impacted by a planned shutdown event. In either case, OCI implicitly determines when DML replay is safe and applications see fewer errors following a shutdown event.

With unplanned outages, OCI uses Transaction Guard, which enables an OCI application to reliably determine the outcome of a transaction by recovering an in-flight transaction after a recoverable error occurs. This support means the completion of application requests during outages incurs only a minor delay while restoring database connectivity and session state. AC only attempts to replay an in-flight transaction if it can determine the transaction did not commit during original execution.

For AC support for OCI, Oracle recommends you use an OCI session pool or Tuxedo.

This section includes the following topics:

- About Added Support for Application Continuity

- What Happens Following a Recoverable Error

- Criteria for Successful Replay

- What Factors Disable Application Continuity in OCI

- Failed Replay

- When Is Application Continuity Most Effective

**See Also:**

- [Oracle Real Application Clusters Administration and Deployment Guide](../racad/workload-management-with-dynamic-database-services.md) for information about creating services for Application Continuity and Transaction Guard.

#### 12.5.1 About Added Support for Application Continuity

Oracle Database release 18c, version 18.1 adds more support for Application Continuity.

Beginning with Oracle Database release 18c, version 18.1, the following support is added for Application Continuity:

- Support is added for OCI dynamic binds and defines for numeric, character, and date/time types. This means the following OCI APIs are extended to support Application Continuity: `OCIBindDynamic()` and `OCIDefineDynamic()`.

- Support is added for binding and defining objects. This means the following OCI APIs are extended to support Application Continuity: `OCIBindObject()`, `OCIDefineObject()`, and `OCITypeByName()`.

- During execution of LOB calls, Application Continuity now supports the handling of connection failure by restarting LOB calls that were interrupted by an outage.

- OCI now supports the new Application Continuity `FAILOVER_TYPE` of `AUTO`, which only attempts to fail over if the session state is known to be restorable at the explicit request boundary.

#### 12.5.2 What Happens Following a Recoverable Error

Following a recoverable error, database sessions fail over from one database instance to another database instance.

The new instance may be part of the same Oracle RAC cluster, or an Oracle Data Guard standby database that has been brought up as a primary database following a site failure. After transparent application failover (TAF) successfully reconnects and reauthenticates, Application Continuity in OCI replays the call history associated with the failed session, including all SQL and PL/SQL statements. Replay operates on a single session and does not attempt to synchronize the re-submission activity with any other database session. Replay is successful only if the client-visible results of transaction replay are identical to the original submission.

#### 12.5.3 Criteria for Successful Replay

Successful driver replay requires that the client-visible effects of a post-failover transaction be identical to the initial submission.

This success is indicated by the following criteria:

- Return codes and error message text must be identical.

- Result sets must be identical. The define data must be identical and the rows must be returned in the same order.

- The rows processed count must be identical. For example, a post-failover update statement must update the same number of rows as the original update statement.

- Session state for the new connection matches session state from the original connection.

See [Oracle Real Application Clusters Administration and Deployment Guide](../racad/ensuring-application-continuity.md) for information about these criteria.

##### Stability of Mutable Data and Application Continuity

When values change from one execution to the next for a mutable object, its data is considered to be mutable and is thus guaranteed to be non-replayable. Sequences are an example of this mutable data.

To improve the success rate for DML replay, it is necessary to replay DML involving mutable data with the values used at initial submission. If the original values are not kept and if different values for these mutable objects are returned to the client, replay is rejected because the client sees different results.

Support for keeping mutable object values is currently provided for `SYSDATE`, `SYSTIMESTAMP`, `SYS_GUID`, and `sequence``.NEXTVAL`.

**See Also:**

[Oracle Real Application Clusters Administration and Deployment Guide](../racad/ensuring-application-continuity.md) for more information about mutable objects and Application Continuity.

#### 12.5.4 What Factors Disable Application Continuity in OCI

Lists the factors that implicitly disables Application Continuity in OCI until the start of the next application request.

The following situations implicitly disables Application Continuity in OCI until the start of the next application request:

- The server detects a condition that is not consistent with replay. For example, for `SESSION_STATE_CONSISTENCY=DYNAMIC` if a PL/SQL anonymous block has an embedded top level `COMMIT` statement (autonomous transactions are not considered top level), the driver implicitly disables Application Continuity in OCI.

- The application calls an OCI function that is not supported by Application Continuity in OCI.

The application can explicitly disable Application Continuity in OCI by calling `OCIRequestDisableReplay()`.

#### 12.5.5 Failed Replay

What causes replay to fail.

When Application Continuity in OCI replays a transaction, the following situations will cause replay to fail:

- Encountering a `COMMIT` statement at replay time

- Replay results are not consistent with the initial submission of the transaction

- Presence of a recoverable error during replay if the internal replay retries limit is exceeded

- Applications that use `OCIStmtPrepare()` return the following error: `Error - ORA-25412: transaction replay disabled by call to OCIStmtPrepare`. Use the `OCIStmtPrepare2()` call to support the use of Application Continuity in an HA infrastructure.

Application Continuity returns an error if it cannot successfully replay a failed transaction. Additional diagnostic information will be logged in the client-side trace file to indicate the reason for the replay failure.

#### 12.5.6 When Is Application Continuity Most Effective

What determines the effectiveness of Application Continuity in OCI.

Application Continuity in OCI is most effective under the following conditions:

- The database service specifies the `COMMIT_OUTCOME` attribute and transparent application failover (TAF) is configured.

- An application is able to mark the beginning and end of an application request, either explicitly (calling `OCIRequestBegin()` and `OCIRequestEnd()`) or implicitly through use of an OCI session pool.

- An application request contains at most one database transaction that is committed at the end of the request.

- If the application executes PL/SQL or Java in the server, that PL/SQL or Java:
  - Does not have embedded `COMMIT` statements

  - Does not set any state (for example, package variables) that is expected to persist after the PL/SQL or Java completes.

- The TAF callback does not leave an open database transaction.

This section includes the following topics:

- When Application Continuity in OCI Can Fail Over

- Application Continuity in OCI Does Not Support These Constructs

- Possible Side Effects of Application Continuity

##### 12.5.6.1 When Application Continuity in OCI Can Fail Over

Describes with which functions when Application Continuity in OCI can fail over if an outage occurs.

Application Continuity in OCI can fail over if an outage occurs during one of the following functions:

- `OCILobAppend()`

- `OCILobArrayRead()`

- `OCILobArrayWrite()`

- `OCILobAssign()`

- `OCILobCharSetForm()`

- `OCILobClose()`

- `OCILobCopy2()`

- `OCILobCreateTemporary()`

- `OCILobDisableBuffering()`

- `OCILobEnableBuffering()`

- `OCILobFileClose()`

- `OCILobFileCloseAll()`

- `OCILobFileGetName()`

- `OCILobFileIsOpen()`

- `OCILobFileOpen()`

- `OCILobFileSetName()`

- `OCILobFlushBuffer()`

- `OCILobFreeTemporary()`

- `OCILobGetChunkSize()`

- `OCILobGetLength()`

- `OCILobGetLength2()`

- `OCILobGetStorageLimit()`

- `OCILobIsEqual()`

- `OCILobIsOpen()`

- `OCILobIsTemporary()`

- `OCILobLoadFromFile()`

- `OCILobLoadFromFile2()`

- `OCILobLocatorAssign()`

- `OCILobLocatorIsInit()`

- `OCILobOpen()`

- `OCILobRead()`

- `OCILobRead2()`

- `OCILobTrim()`

- `OCILobTrim2()`

- `OCILobWriteAppend()`

- `OCILobWriteAppend2()`

- `OCILobWrite()`

- `OCILobWrite2()`

- `OCIPing()`

- `OCIStmtExecute()`

- `OCIStmtFetch()`

- `OCIStmtFetch2()`

- `OCISessionEnd()`

- `OCITransCommit()`

- `OCITransRollback()`

##### 12.5.6.2 Application Continuity in OCI Does Not Support These Constructs

What constructs are not supported by Application Continuity in OCI.

Application Continuity in OCI does not support the following constructs:

- XA Transactions

- PL/SQL blocks with embedded `COMMIT` statements

- AQ Dequeue in dequeue immediate mode (deqopt.visibility)

- Streaming binds or defines of descriptor-based types such as objects or lob locators

- Function `OCIStmtPrepare()`

- Registered OCI callbacks of type `OCI_CBTYPE_ENTRY` that do not return `OCI_CONTINUE`

- `COMMIT NOWAIT` statement

- DCL commands

##### 12.5.6.3 Possible Side Effects of Application Continuity

Application Continuity in OCI replays the original PL/SQL and SQL statements following a recoverable error once a session is rebuilt and the database state is restored. The replay leaves side-effects that are seen twice, which may or may not be desirable.

It is important that applications understand these side-effects and decide whether duplicate execution is acceptable. If it is not acceptable, then the application must take action to accommodate or mitigate the effects of replay. For example, by calling `OCIRequestDisableReplay()`.

**See Also:**

[Oracle Real Application Clusters Administration and Deployment Guide](../racad/ensuring-application-continuity.md) for more information about examples of actions that create side effects.
