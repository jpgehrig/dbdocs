Oracle Database Advanced Queuing can deliver nonpersistent messages asynchronously to subscribers. These messages can be event-driven and do not persist beyond the failure of the system (or instance). The messages are stored in a system-created queue table. Oracle Database Advanced Queuing supports persistent and nonpersistent messages with a common [API](glossary.md).

Nonpersistent queues, which can be either single-consumer or multiconsumer, provide a mechanism for notification to all currently connected users. Subscribers can be added to multiconsumer nonpersistent queues, and nonpersistent queues can be destinations for propagation.

You use the enqueue interface to enqueue messages into a nonpersistent queue in the usual way. You can enqueue RAW and Oracle object type messages into a nonpersistent queue. OCI notifications are used to deliver such messages to users that are currently registered for notification.

The following topics describe nonpersistent queues, which are deprecated in Oracle Database Advanced Queuing 10g Release 2 (10.2). Oracle recommends that you use buffered messaging instead.

**See Also:**

"[Buffered Messaging](aq-introduction.md)"

Topics:

- Creating Nonpersistent Queues

- Managing Nonpersistent Queues

- Compatibility of Nonpersistent Queues

- Nonpersistent Queue Notification

- Restrictions on Nonpersistent Queues

### Creating Nonpersistent Queues

    DBMS_AQADM.CREATE_NP_QUEUE (
       queue_name              IN        VARCHAR2,
       multiple_consumers      IN        BOOLEAN  DEFAULT FALSE,
       comment                 IN        VARCHAR2 DEFAULT NULL);

This procedure creates a [nonpersistent](glossary.md) queue.

Only local recipients are supported for nonpersistent queues. The queue can be either single-consumer or multiconsumer. All queue names must be unique within a schema. The queues are created in an 8.1-compatible system-created queue table (`AQ$_MEM_SC` or `AQ$_MEM_MC`) in the same schema as that specified by the queue name. If the queue name does not specify a schema name, then the queue is created in the login user's schema.

**Note:**

Names of nonpersistent queues must not be longer than 24 characters. If you attempt to create a nonpersistent queue with a longer name, error ORA-24019 results.

### Managing Nonpersistent Queues

Once a queue is created with `CREATE_NP_QUEUE`, it can be enabled by calling `START_QUEUE`. By default, the queue is created with both enqueue and dequeue disabled.

You can enqueue RAW and Oracle object type messages into a nonpersistent queue. You cannot dequeue from a nonpersistent queue. The only way to retrieve a message from a nonpersistent queue is by using the [Oracle Call Interface](glossary.md) (OCI) notification mechanism. You cannot invoke the `listen` call on a nonpersistent queue.

A nonpersistent queue can be dropped only by its owner.

### Compatibility of Nonpersistent Queues

For 8.1-style or higher queues, the `compatible` parameter of `init.ora` and the `compatible` parameter of the [queue table](glossary.md) should be set to 8.1 or higher to use nonpersistent queues.

### Nonpersistent Queue Notification

For nonpersistent queues, the message is delivered as part of the notification. Table A-1 shows the actions performed for [nonpersistent](glossary.md) queues for different notification mechanisms when RAW presentation is specified. Table A-2 shows the actions performed when XML presentation is specified.

Table A-1 Actions Performed for Nonpersistent Queues When RAW Presentation Specified

| Queue Payload Type | OCI Callback                                       | E-mail        | PL/SQL Callback                                       |
|:-------------------|:---------------------------------------------------|:--------------|:------------------------------------------------------|
| RAW                | OCI callback receives the RAW data in the payload. | Not supported | PL/SQL callback receives the RAW data in the payload. |
| Oracle object type | Not supported                                      | Not supported | Not supported                                         |

Table A-2 Actions Performed for Nonpersistent Queues When XML Presentation Specified

| Queue Payload Type | OCI Callback                                       | E-mail                                                                                 | PL/SQL Callback                                       |
|:-------------------|:---------------------------------------------------|:---------------------------------------------------------------------------------------|:------------------------------------------------------|
| RAW                | OCI callback receives the XML data in the payload. | XML data is formatted as a SOAP message and e-mailed to the registered e-mail address. | PL/SQL callback receives the XML data in the payload. |
| Oracle object type | OCI callback receives the XML data in the payload. | XML data is formatted as a SOAP message and e-mailed to the registered e-mail address. | PL/SQL callback receives the XML data in the payload. |

### Restrictions on Nonpersistent Queues

You can create nonpersistent queues of `RAW` and Oracle object type.You are limited to sending messages only to subscribers and explicitly specified recipients who are local. Propagation is not supported from nonpersistent queues. When retrieving messages, you cannot use the dequeue call, but must instead employ the asynchronous notification mechanism, registering for the notification by mean of `OCISubscriptionRegister`.

The `visibility` attribute of `enqueue_options` must be set to `IMMEDIATE` for nonpersistent messages.

**See Also:**

"[Enqueue Options](aq-operations-using-pl-sql.md)"
