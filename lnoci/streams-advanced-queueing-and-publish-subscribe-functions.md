Lists and describes the Database Advanced Queuing and publish-subscribe functions.

Table 26-3 lists the Database Advanced Queuing and publish-subscribe functions that are described in this section. Use functions that end in "2" for all new applications.

**See Also:**

[Table B-1](oci-demo-programs.md) for Database Advanced Queuing programs

Table 26-3 Advanced Queuing and Publish-Subscribe Functions

| Function                    | Purpose                                                                                                        |
|:----------------------------|:---------------------------------------------------------------------------------------------------------------|
| OCIAQDeq()                  | Performs an Advanced Queuing dequeue operation                                                                 |
| OCIAQDeqArray()             | Dequeue an array of messages                                                                                   |
| OCIAQEnq()                  | Performs an Advanced Queuing enqueue operation                                                                 |
| OCIAQEnqArray()             | Enqueue an array of messages                                                                                   |
| OCIAQListen2()              | Listen on one or more queues on behalf of a list of agents. Supports buffered messaging and persistent queues. |
| OCISubscriptionDisable()    | Disable a subscription registration to turn off notifications                                                  |
| OCISubscriptionEnable()     | Enable notifications on a subscription                                                                         |
| OCISubscriptionPost()       | Post to a subscription to receive notifications                                                                |
| OCISubscriptionRegister()   | Register a subscription                                                                                        |
| OCISubscriptionUnRegister() | Unregister a subscription                                                                                      |

### 26.4.1 OCIAQDeq()

#### Purpose

Performs a dequeue operation using Database Advanced Queuing with OCI.

#### Syntax

    sword OCIAQDeq ( OCISvcCtx            *svch,
                     OCIError             *errh,
                     OraText              *queue_name,
                     OCIAQDeqOptions      *dequeue_options,
                     OCIAQMsgProperties   *message_properties,
                     OCIType              *payload_tdo,
                     void                **payload,
                     void                **payload_ind,
                     OCIRaw              **msgid,
                     ub4                   flags );

#### Parameters

svch (IN)
OCI service context.

errh (IN)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

queue_name (IN)
The target queue for the dequeue operation.

dequeue_options (IN)
The options for the dequeue operation; stored in an `OCIAQDeqOptions` descriptor, with OCI type constant `OCI_DTYPE_AQDEQ_OPTIONS`.

`OCI_DTYPE_AQDEQ_OPTIONS` has the additional attribute `OCI_ATTR_MSG_DELIVERY_MODE` (introduced in Oracle Database 10g Release 2) with the following values:

- `OCI_MSG_PERSISTENT` (default)

- `OCI_MSG_BUFFERED`

- `OCI_MSG_PERSISTENT_OR_BUFFERED`

message_properties (OUT)
The message properties for the message; the properties are stored in an `OCIAQMsgProperties` descriptor, with OCI type constant `OCI_DTYPE_AQMSG_PROPERTIES`, which can have the following values:

- `OCI_AQ_PERSISTENT` (default)

- `OCI_AQ_BUFFERED`

payload_tdo (IN)
The TDO (type descriptor object) of an object type. For a raw queue, this parameter should point to the TDO of `SYS.RAW`.

payload (IN/OUT)
A pointer to a pointer to a program variable buffer that is an instance of an object type. For a raw queue, this parameter should point to an instance of `OCIRaw`.

Memory for the payload is dynamically allocated in the object cache. The application can optionally call `OCIObjectFree()` to deallocate the payload instance when it is no longer needed. If the pointer to the program variable buffer (`*payload`) is passed as `NULL`, the buffer is implicitly allocated in the cache.

The application may choose to pass `NULL` for `payload` the first time `OCIAQDeq()` is called, and let the OCI allocate the memory for the payload. It can then use a pointer to that previously allocated memory in subsequent calls to `OCIAQDeq()`.

To obtain a TDO for the payload, use `OCITypeByName()`, or `OCITypeByRef()`.

The OCI provides functions that allow the user to set attributes of the payload, such as its text. For information about setting these attributes, see "[Manipulating Object Attributes](oci-object-relational-programming.md)".

payload_ind (IN/OUT)
A pointer to a pointer to the program variable buffer containing the parallel indicator structure for the object type.

The memory allocation rules for `payload_ind` are the same as those for `payload`.

msgid (OUT)
The message ID.

flags (IN)
Not currently used; pass as `OCI_DEFAULT`.

#### Comments

Users must have the `AQ_USER_ROLE` or privileges to execute the `DBMS_AQ` package to use this call. The OCI environment must be initialized in object mode (using `OCIEnvCreate()`, `OCIEnvNlsCreate()`), or `OCIInitialize()` (deprecated) to use this call.

**Related Topics**

- [OCIObjectFree()](oci-pin-unpin-and-free-functions.md)
- [OCITypeByName()](oci-type-information-accessor-functions.md)
- [OCITypeByRef()](oci-type-information-accessor-functions.md)
- OCIAQEnq()
- OCIAQListen2()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

**See Also:**

- [OCI and Database Advanced Queuing](notification-streams-advanced-queuing.md)

- [Oracle Database Advanced Queuing User's Guide](../adque/aq-introduction.md)

### 26.4.2 OCIAQDeqArray()

Dequeues an array of messages from a queue.

#### Purpose

All messages in the array are dequeued with the same option and have the same queue table payload column TDO.

#### Syntax

    sword OCIAQDeqArray ( OCISvcCtx            *svchp,
                          OCIError             *errhp,
                          OraText              *queue_name,
                          OCIAQDeqOptions      *deqopt,
                          ub4                  *iters,
                          OCIAQMsgProperties  **msgprop,
                          OCIType              *payload_tdo,
                          void                **payload,
                          void                **payload_ind,
                          OCIRaw              **msgid,
                          void                 *ctxp,
                          OCICallbackAQDeq     (cbfp)
                                              (
                                              void          *ctxp,
                                              void         **payload,
                                              void         **payload_ind
                                              ),
                          ub4                   flags );

#### Parameters

svchp (IN)
OCI service context (unchanged from `OCIAQDeq()`).

errhp (IN)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error (unchanged from `OCIAQDeq()`).

queue_name (IN)
The name of the queue from which messages are dequeued (unchanged from `OCIAQDeq()`

deqopt (IN)
A pointer to an `OCIAQDeqOptions` descriptor (unchanged from `OCIAQDeq()`).

`OCI_DTYPE_AQDEQ_OPTIONS` OCI type constant has the additional attribute `OCI_ATTR_MSG_DELIVERY_MODE` (introduced in Oracle Database 10g Release 2) with the following values:

- `OCI_MSG_PERSISTENT` (default)

- `OCI_MSG_BUFFERED`

- `OCI_MSG_PERSISTENT_OR_BUFFERED`

iters (IN/OUT)
On input, the number of messages to dequeue. On output, the number of messages successfully dequeued.

msgprop (OUT)
An array of pointers to `OCIAQMsgProperties` descriptors, of OCI type constant `OCI_DTYPE_AQMSG_PROPERTIES`, which can have the following values:

- `OCI_AQ_PERSISTENT` (default)

- `OCI_AQ_BUFFERED`

payload_tdo (OUT)
A pointer to the TDO of the queue table's payload column.

payload (OUT)
An array of pointers to dequeued messages.

payload_ind (OUT)
An array of pointers to indicators.

msgid (OUT)
An array of pointers to the message ID of the dequeued messages.

ctxp (IN)
The context that is passed to the callback function.

cbfp (IN)
The callback that can be registered to provide a buffer pointer into which the dequeued message is placed. If `NULL`, then messages are dequeued into buffers pointed to by `payload`.

flags (IN)
Not currently used; pass as `OCI_DEFAULT`.

#### Comments

Users must have the `AQ_USER_ROLE` or privileges to execute the `DBMS_AQ` package to use this call. The OCI environment must be initialized in object mode (using `OCIEnvCreate()`, `OCIEnvNlsCreate()`), or `OCIInitialize()` (deprecated) to use this call.

A nonzero wait time, as specified in the `OCIAQDeqOptions`, is recognized only when there are no messages in the queue. If the queue contains messages that are eligible for dequeuing, then the `OCIAQDeqArray()` function dequeues up to `iters` messages and returns immediately.

This function is not supported in nonblocking mode.

**Related Topics**

- OCIAQDeq()
- OCIAQEnqArray()
- OCIAQListen2()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

**See Also:**

- [OCI and Database Advanced Queuing](notification-streams-advanced-queuing.md)

- [Oracle Database Advanced Queuing User's Guide](../adque/aq-introduction.md)

### 26.4.3 OCIAQEnq()

Performs an enqueue operation using Database Advanced Queuing.

#### Purpose

Performs an enqueue operation using Database Advanced Queuing.

#### Syntax

    sword OCIAQEnq ( OCISvcCtx            *svch,
                     OCIError             *errh,
                     OraText              *queue_name,
                     OCIAQEnqOptions      *enqueue_options,
                     OCIAQMsgProperties   *message_properties,
                     OCIType              *payload_tdo,
                     void                **payload,
                     void                **payload_ind,
                     OCIRaw              **msgid,
                     ub4                   flags );

#### Parameters

svch (IN)
OCI service context.

errh (IN)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

queue_name (IN)
The target queue for the enqueue operation.

enqueue_options (IN)
The options for the enqueue operation; stored in an `OCIAQEnqOptions` descriptor.

message_properties (IN)
The message properties for the message. The properties are stored in an `OCIAQMsgProperties` descriptor, of OCI type constant `OCI_DTYPE_AQMSG_PROPERTIES`, introduced in Oracle Database 10g Release 2.

Descriptor `OCI_DTYPE_AQMSG_PROPERTIES` has the attribute `OCI_ATTR_MSG_DELIVERY_MODE`, which has the following values:

- `OCI_MSG_PERSISTENT` (default)

- `OCI_MSG_BUFFERED`

payload_tdo (IN)
The TDO (type descriptor object) of an object type. For a raw queue, this parameter should point to the TDO of `SYS.RAW`.

payload (IN)
A pointer to a pointer to an instance of an object type. For a raw queue, this parameter should point to an instance of `OCIRaw`.

OCI provides functions that allow the user to set attributes of the payload, such as its text.

**See Also:**

[Manipulating Object Attributes](oci-object-relational-programming.md) for information about setting these attributes

payload_ind (IN)
A pointer to a pointer to the program variable buffer containing the parallel indicator structure for the object type.

msgid (OUT)
The message ID.

flags (IN)
Not currently used; pass as `OCI_DEFAULT`.

#### Comments

Users must have the `AQ_USER_ROLE` or privileges to execute the `DBMS_AQ` package to use this call.

The OCI environment must be initialized in object mode (using `OCIEnvCreate()`, `OCIEnvNlsCreate()`), or `OCIInitialize()` (deprecated) to use this call.

**See Also:**

- [OCI and Database Advanced Queuing](notification-streams-advanced-queuing.md) for more information about OCI and Advanced Queuing

- [Oracle Database Advanced Queuing User's Guide](../adque/aq-introduction.md)

To obtain a TDO for the payload, use `OCITypeByName()`, or `OCITypeByRef()`.

**Related Topics**

- [OCITypeByName()](oci-type-information-accessor-functions.md)
- [OCITypeByRef()](oci-type-information-accessor-functions.md)
- OCIAQDeq()
- OCIAQListen2()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.4.4 OCIAQEnqArray()

Enqueues an array of messages to a queue.

#### Purpose

The array of messages is enqueued with the same options and has the same payload column TDO.

#### Syntax

    sword OCIAQEnqArray ( OCISvcCtx               *svchp,
                          OCIError                *errhp,
                          OraText                 *queue_name,
                          OCIAQEnqOptions         *enqopt,
                          ub4                     *iters,
                          OCIAQMsgProperties     **msgprop,
                          OCIType                 *payload_tdo,
                          void                   **payload,
                          void                   **payload_ind,
                          OCIRaw                 **msgid,
                          void                    *ctxp,
                          OCICallbackAQEnq        (cbfp)
                                                 (
                                                 void         *ctxp,
                                                 void        **payload,
                                                 void        **payload_ind
                                                 ),
                          ub4                     flags );

#### Parameters

svchp (IN)
The service context (unchanged from `OCIAQEnq()`).

errhp (IN/OUT)
The error handle (unchanged from `OCIAQEnq()`).

queue_name (IN)
The name of the queue in which messages are enqueued (unchanged from `OCIAQEnq()`).

enqopt (IN)
A pointer to an `OCIAQEnqOptions` descriptor (unchanged from `OCIAQEnq()`).

iters (IN/OUT)
On input, the number of messages to enqueue. On output, the number of messages successfully enqueued.

msgprop (IN)
An array of pointers to `OCIAQMsgProperties` descriptors, of OCI type constant `OCI_DTYPE_AQMSG_PROPERTIES`, introduced in Oracle Database 10g Release 2.

`OCI_DTYPE_AQMSG_PROPERTIES` has the attribute `OCI_ATTR_MSG_DELIVERY_MODE`, which has the following values:

- `OCI_MSG_PERSISTENT` (default)

- `OCI_MSG_BUFFERED`

payload_tdo (IN)
A pointer to the TDO of the queue table's payload column.

payload (IN)
An array of pointers to messages to be enqueued.

payload_ind (IN)
An array of pointers to indicators, or a `NULL` pointer if indicator variables are not used.

msgid (OUT)
An array of pointers to the message ID of the enqueued messages, or a `NULL` pointer if no message IDs are returned.

ctxp (IN)
The context that is passed to the registered callback function.

cbfp (IN)
A callback that can be registered to provide messages dynamically. If `NULL`, then all messages must be materialized before calling `OCIAQEnqArray()`.

flags (IN)
Not currently used; pass as `OCI_DEFAULT`.

#### Comments

This function is not supported in nonblocking mode.

**Related Topics**

- OCIAQEnq()
- OCIAQDeqArray()
- OCIAQListen2()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.4.5 OCIAQListen2()

Listens on one or more queues on behalf of a list of agents.

#### Purpose

Supports buffered messaging and persistent queues. Introduced in Oracle Database 10g Release 2.

#### Syntax

    sword OCIAQListen2 (OCISvcCtx          *svchp,
                        OCIError           *errhp,
                        OCIAQAgent        **agent_list,
                        ub4                 num_agents,
                        OCIAQListenOpts    *lopts,
                        OCIAQAgent        **agent,
                        OCIAQLisMsgProps   *lmops,
                        ub4                 flags);

#### Parameters

svchpp (IN/OUT)
The service context handle.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

agent_list (IN)
List of agents for which to monitor messages.

num_agents (IN)
Number of agents in the agent list.

lopts (IN)
Type constant `OCI_DTYPE_AQLIS_OPTIONS` has the following attributes:

- `OCI_ATTR_WAIT` - Maximum wait time, in seconds, for the listen call

- `OCI_ATTR_MSG_DELIVERY_MODE` - Has one of these values:

  - `OCI_MSG_PERSISTENT`

  - `OCI_MSG_BUFFERED`

  - `OCI_MSG_PERSISTENT_OR_BUFFERED`

agent (OUT)
Agent for which there is a message. `OCIAgent` is an OCI descriptor.

lmops (OUT)
`OCI_DTYPE_AQLIS_MSG_PROPERTIES` (listen message properties) has one attribute, `OCI_ATTR_MSG_DELIVERY_MODE`, which has the following values:

- `OCI_MSG_PERSISTENT`

- `OCI_MSG_BUFFERED`

flags (IN)
Not currently used; pass as `OCI_DEFAULT`.

#### Comments

This is a blocking call that returns when there is a message ready for consumption for an agent in the list. If there are no messages found when the wait time expires, an error is returned.

**Related Topics**

- OCIAQEnq()
- OCIAQDeq()
- [OCISvcCtxToLda()](miscellaneous-functions.md)
- OCISubscriptionEnable()
- OCISubscriptionPost()
- OCISubscriptionRegister()
- OCISubscriptionUnRegister()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.4.6 OCISubscriptionDisable()

Disables a subscription registration that turns off all notifications.

#### Purpose

Disables a subscription registration that turns off all notifications.

#### Syntax

    ub4 OCISubscriptionDisable ( OCISubscription   *subscrhp,
                                 OCIError          *errhp
                                 ub4                mode );

#### Parameters

subscrhp (IN)
A subscription handle with the `OCI_ATTR_SUBSCR_NAME` and `OCI_ATTR_SUBSCR_NAMESPACE` attributes set.

**See Also:**

[Subscription Handle Attributes](handle-and-descriptor-attributes.md)

errhp (OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

mode (IN)
Call-specific mode. The only valid value is `OCI_DEFAULT`. `OCI_DEFAULT` executes the default call that discards all notifications on this subscription until the subscription is enabled.

#### Comments

This call is used to temporarily turn off notifications. This is useful when the application is running a critical section of the code and should not be interrupted.

The user need not be connected or authenticated to perform this operation. A registration must have been performed to the subscription specified by the subscription handle before this call is made.

All notifications after an `OCISubscriptionDisable()` are discarded by the system until an `OCISubscriptionEnable()` is performed.

**Related Topics**

- OCIAQListen2()
- OCISubscriptionEnable()
- OCISubscriptionPost()
- OCISubscriptionRegister()
- OCISubscriptionUnRegister()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.4.7 OCISubscriptionEnable()

Enables a subscription registration that has been disabled.

#### Purpose

This turns on all notifications.

#### Syntax

    ub4 OCISubscriptionEnable ( OCISubscription   *subscrhp,
                                OCIError          *errhp
                                ub4                mode );

#### Parameters

subscrhp (IN)
A subscription handle with the `OCI_ATTR_SUBSCR_NAME` and `OCI_ATTR_SUBSCR_NAMESPACE` attributes set.

**See Also:**

[Subscription Handle Attributes](handle-and-descriptor-attributes.md)

errhp (OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

mode (IN)
Call-specific mode. The only valid value is OCI_DEFAULT. This value executes the default call that buffers all notifications on this subscription until a subsequent enable is performed.

#### Comments

This call is used to turn on notifications after a subscription registration has been disabled.

The user need not be connected or authenticated to perform this operation. A registration must have been done for the specified subscription before this call is made.

**Related Topics**

- OCIAQListen2()
- [OCISvcCtxToLda()](miscellaneous-functions.md)
- OCISubscriptionRegister()
- OCISubscriptionUnRegister()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.4.8 OCISubscriptionPost()

Posts to a subscription that allows all clients who are registered for the subscription to get notifications.

#### Purpose

Posts to a subscription that allows all clients who are registered for the subscription to get notifications.

#### Syntax

    ub4 OCISubscriptionPost ( OCISvcCtx          *svchp,
                              OCISubscription   **subscrhpp,
                              ub2                 count,
                              OCIError           *errhp
                              ub4                 mode );

#### Parameters

svchp (IN)
An OCI service context (after release 7). This service context should have a valid authenticated user handle.

subscrhpp (IN)
An array of subscription handles. Each element of this array should be a subscription handle with the `OCI_ATTR_SUBSCR_NAME` and `OCI_ATTR_SUBSCR_NAMESPACE` attributes set.

**See Also:**

[Subscription Handle Attributes](handle-and-descriptor-attributes.md)

The `OCI_ATTR_SUBSCR_PAYLOAD` attribute must be set for each subscription handle before this call. If it is not set, the payload is assumed to be `NULL` and no payload is delivered when the notification is received by the clients that have registered interest. Note that the caller must preserve the payload until the post is done, as the `OCIAttrSet()` call keeps track of the reference to the payload but does not copy the contents.

count (IN)
The number of elements in the subscription handle array.

errhp (OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

mode (IN)
Call-specific mode. The only valid value is OCI_DEFAULT. This value executes the default call.

#### Comments

Posting to a subscription involves identifying the subscription name and the payload if desired. If no payload is associated, the payload length can be set to 0.

This call provides a best-effort guarantee. A notification goes to registered clients at most once.

This call is primarily used for nonpersistent notification and is useful for several system events. If the application needs more rigid guarantees, it can use the Advanced Queuing functionality by enqueuing to the queue.

**Related Topics**

- OCIAQListen2()
- [OCISvcCtxToLda()](miscellaneous-functions.md)
- OCISubscriptionEnable()
- OCISubscriptionRegister()
- OCISubscriptionUnRegister()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.4.9 OCISubscriptionRegister()

Registers a callback for message notification.

#### Purpose

Registers a callback for message notification.

#### Syntax

    ub4 OCISubscriptionRegister ( OCISvcCtx          *svchp,
                                  OCISubscription   **subscrhpp,
                                  ub2                 count,
                                  OCIError           *errhp
                                  ub4                 mode );

#### Parameters

svchp (IN)
An OCI service context (after release 7). This service context should have a valid authenticated user handle.

subscrhpp (IN)
An array of subscription handles. Each element of this array should be a subscription handle with all of the following attributes set:

- `OCI_ATTR_SUBSCR_NAME`

- `OCI_ATTR_SUBSCR_NAMESPACE`

- `OCI_ATTR_SUBSCR_RECPTPROTO`

Otherwise, an error is returned.

One of the following attributes must also be set:

- `OCI_ATTR_SUBSCR_CALLBACK`

- `OCI_ATTR_SUBSCR_CTX`

- `OCI_ATTR_SUBSCR_RECPT`

**See Also:**

[Subscription Handle Attributes](handle-and-descriptor-attributes.md) for information about the handle attributes

When a notification is received for the registration denoted by `subscrhpp[i]`, either the user-defined callback function (`OCI_ATTR_SUBSCR_CALLBACK`) set for `subscrhpp[i]` is invoked with the context (`OCI_ATTR_SUBSCR_CTX`) set for `subscrhpp[i]`, or an email is sent to (`OCI_ATTR_SUBSCR_RECPT`) set for `subscrhpp[i]`, or the PL/SQL procedure (`OCI_ATTR_SUBSCR_RECPT`) set for `subscrhpp[i]` is invoked in the database, provided the subscriber of `subscrhpp[i]` has the appropriate permissions on the procedure.

count (IN)
The number of elements in the subscription handle array.

errhp (OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

mode (IN)
Call-specific mode. Valid values are:

- `OCI_DEFAULT` - Use when there is only one server DN in the server DN descriptor. The registration request is sent to the database. If a database connection is not available, the registration request is detoured to the LDAP server.

- `OCI_REG_LDAPONLY` - The registration request is sent directly to the LDAP server. Use this mode when there are multiple server DNs in the server DN descriptor, or you are certain that a database connection is not available.

Whenever a new client process comes up, or an old one goes down and comes back up, it must register for all subscriptions of interest. If the client stays up and the server first goes down and then comes back up, the client continues to receive notifications for registrations that are DISCONNECTED. However, the client does not receive notifications for CONNECTED registrations, as they are lost after the server goes down and comes back up.

#### Comments

This call is invoked for registration to a subscription that identifies the subscription name of interest and the associated callback to be invoked. Interest in several subscriptions can be registered simultaneously.

This interface is only valid for the asynchronous mode of message delivery. In this mode, a subscriber issues a registration call that specifies a callback. When messages are received that match the subscription criteria, the callback is invoked. The callback may then issue an explicit `message_receive` (dequeue) to retrieve the message.

The user must specify a subscription handle at registration time with the namespace attribute set to `OCI_SUBSCR_NAMESPACE_AQ`.

The subscription name is the string `SCHEMA.QUEUE`if the registration is for a single consumer queue and `SCHEMA.QUEUE:CONSUMER_NAME` if the registration is for a multiconsumer queue. The string should be in uppercase.

Each namespace has its own privilege model. If the user performing the registration is not entitled to register in the namespace for the specified subscription, an error is returned.

**Related Topics**

- OCIAQListen2()
- [OCISvcCtxToLda()](miscellaneous-functions.md)
- OCISubscriptionEnable()
- OCISubscriptionPost()
- OCISubscriptionUnRegister()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.4.10 OCISubscriptionUnRegister()

Unregisters a subscription that turns off notifications.

#### Purpose

Unregisters a subscription that turns off notifications.

#### Syntax

    ub4 OCISubscriptionUnRegister ( OCISvcCtx         *svchp,
                                    OCISubscription   *subscrhp,
                                    OCIError          *errhp
                                    ub4                mode );

#### Parameters

svchp (IN)
An OCI service context (after release 7). This service context should have a valid authenticated user handle.

subscrhp (IN)
A subscription handle with the `OCI_ATTR_SUBSCR_NAME` and `OCI_ATTR_SUBSCR_NAMESPACE` attributes set.

**See Also:**

[Subscription Handle Attributes](handle-and-descriptor-attributes.md)

errhp (OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

mode (IN)
Call-specific mode. Valid values are:

- `OCI_DEFAULT` - Use when there is only one server DN in the server DN descriptor. The registration request is sent to the database. If a database connection is not available, the registration request is detoured to the LDAP server.

- `OCI_REG_LDAPONLY` - The registration request is sent directly to the LDAP server. Use this mode when there are multiple server DNs in the server DN descriptor, or you are certain that a database connection is not available.

#### Comments

Unregistering a subscription ensures that the user does not receive notifications regarding the specified subscription in the future. If the user wants to resume notification, then the only option is to reregister for the subscription.

All notifications that would otherwise have been delivered are not delivered after a subsequent registration is performed because the user is no longer in the list of interested clients.

**Related Topics**

- OCIAQListen2()
- [OCISvcCtxToLda()](miscellaneous-functions.md)
- OCISubscriptionEnable()
- OCISubscriptionPost()
- OCISubscriptionRegister()
- [OCIErrorGet()](miscellaneous-functions.md)
