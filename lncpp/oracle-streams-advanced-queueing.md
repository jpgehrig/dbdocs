This chapter describes the OCCI implementation of Oracle Database Advanced Queuing (AQ) for messages.

This chapter contains these topics:

- Overview of Oracle Database Advanced Queuing

- About AQ Implementation in OCCI

- About Creating Messages

- Enqueuing Messages

- Dequeuing Messages

- Listening for Messages

- About Registering for Notification

- About Message Format Transformation

**See Also:**

- [Oracle Database Advanced Queuing User's Guide](../adque/aq-introduction.md) for basic concepts of Advanced Queuing

- [OCCI Application Programming Interface](occi-application-programing-interface.md)

### 10.1 Overview of Oracle Database Advanced Queuing

Oracle Streams is a new information sharing feature that provides replication, message queuing, data warehouse loading, and event notification. It is also the foundation behind Oracle Database Advanced Queuing (AQ).

Advanced Queuing is the integrated message queuing feature that exposes message queuing capabilities of Oracle Database AQ enables applications to:

- Perform message queuing operations similar to SQL operations from the Oracle database

- Communicate asynchronously through messages in AQ queues

- Integrate with database for unprecedented levels of operational simplicity, reliability, and security to message queuing

- Audit and track messages

- Supports both synchronous and asynchronous modes of communication

The advantages of using AQ in OCCI applications include:

- Create applications that communicate with each other in a consistent, reliable, secure, and autonomous manner

- Store messages in database tables, bringing the reliability and recoverability of the database to your messaging infrastructure

- Retain messages in the database automatically for auditing and business intelligence

- Create applications that leverage messaging without having to deal with a different security, data type, or operational mode

- Leverage transactional characteristics of the database

Since traditional messaging solutions have single subscriber queues, a queue must be created for each pair of applications that communicate with each other. The publish/subscribe protocol of the AQ makes it easy to add additional applications (subscribers) to a conversation between multiple applications.

### 10.2 About AQ Implementation in OCCI

OCCI AQ is a set of interfaces that allows messaging clients to access the Advanced Queuing feature of Oracle for enterprise messaging applications. Currently, OCCI AQ supports only the operational interfaces and not the administrative interface, but administrative operations can be accessed through embedded PL/SQL calls.

**See Also:**

Package [`DBMS_AQADM`](../arpls/DBMS_AQADM.md) in [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_AQADM.md) for administrative operations in AQ support through PL/SQL

The AQ feature can be used with other interfaces available through OCCI for sending, receiving, publishing, and subscribing in a message-enabled database. Synchronous and asynchronous message consumption is available based on a message selection rule.

Enqueuing refers to sending a message to a queue and dequeuing refers to receiving one. A client application can create a message, set the desired properties on it and enqueue it by storing the message in the queue, a table in the database. When dequeuing a message, an application can either dequeue it synchronously by calling receive methods on the queue, or asynchronously by waiting for a notification from the database.

The AQ feature is implemented through the following abstractions:

- Message

- Agent

- Producer

- Consumer

- Listener

- Subscription

#### 10.2.1 Message

A message is the basic unit of information being inserted into and retrieved from a queue. A message consists of control information and payload data. The control information represents message properties used by AQ to manage messages. The payload data is the information stored in the queue and is transparent to AQ.

**See Also:**

[Message Class](message-class.md) documentation in [OCCI Application Programming Interface](occi-application-programing-interface.md)

#### 10.2.2 Agent

An `Agent` represents and identifies a user of the queue, either producer or consumer of the message, either an end-user or an application. An `Agent` is identified by a name, an address and a protocol. The name can be either assigned by the application, or be the application itself. The address is determined in terms of the communication protocol. If the protocol is `0` (default), the address is of the form`[schema.]queuename[@dblink]`, a database link.

`Agent`s on the same queue must have a unique combination of name, address, and protocol. Example 10-1 demonstrates an instantiation of a new `Agent` object in a client program.

**See Also:**

[Agent Class](agent-class.md) documentation in [OCCI Application Programming Interface](occi-application-programing-interface.md)

Example 10-1 Creating an Agent

    Agent agt(env, "Billing_app", "billqueue", 0);

#### 10.2.3 Producer

A client uses a `Producer` object to enqueue `Message`s into a queue. It is also used to specify various enqueue options.

**See Also:**

[Producer Class](producer-class.md) documentation in [OCCI Application Programming Interface](occi-application-programing-interface.md)

#### 10.2.4 Consumer

A client uses a `Consumer` object to dequeue `Message`s that have been delivered to a queue. It also specifies various dequeuing options.

Before a consumer can receive messages,

**See Also:**

[Consumer Class](consumer-class.md) documentation in [OCCI Application Programming Interface](occi-application-programing-interface.md)

Example 10-2 Setting the Agent on the Consumer

    Consumer cons(conn);
    ...
    cons.setAgent(ag);
    cons.receive();

#### 10.2.5 Listener

A `Listener` listens for `Message`s for registered `Agent`s at specified queues.

**See Also:**

[Listener Class](listener-class.md) documentation in [OCCI Application Programming Interface](occi-application-programing-interface.md)

#### 10.2.6 Subscription

A `Subscription` encapsulates the information and operations necessary for registering a subscriber for notifications.

### 10.3 About Creating Messages

As mentioned previously, a `Message` is a basic unit of information that contains both the properties of the message and its content, or payload. Each message is enqueued by the `Producer` and dequeued by the `Consumer` objects.

This section includes the following topics:

- About Message Payloads

- Message Properties

#### 10.3.1 About Message Payloads

OCCI supports three types of message payloads:

- RAW

- AnyData

- Using User-defined Types as Payloads

##### 10.3.1.1 RAW

`RAW` payloads are mapped as objects of the [Bytes Class](bytes-class.md) in OCCI.

##### 10.3.1.2 AnyData

The `AnyData` type models self-descriptive data encapsulation; it contains both the type information and the actual data value. Data values of most SQL types can be converted to `AnyData`, and then be converted to the original data type. `AnyData` also supports user-defined data types. The advantage of using `AnyData` payloads is that it ensures both type preservation after an enqueue and dequeue process, and that it allows the user to use a single queue for all types used in the application. Example 10-3 demonstrates how to create an `AnyData `message. Example 10-4 shows how to retrieve the original data type from the message.

Example 10-3 Creating an AnyData Message with a String Payload

    AnyData any(conn);
    any.setFromString("item1");
    Message mes(env);
    mes.setAnyData(any);

Example 10-4 Determining the Type of the Payload in an AnyData Message

    TypeCode tc = any.getType();

##### 10.3.1.3 Using User-defined Types as Payloads

OCCI supports enqueuing and dequeuing of user-defined types as payloads. Example 10-5 demonstrates how to create a payload with a user-defined `Employee` object.

Example 10-5 Creating an User-defined Payload

    // Assuming type Employee ( name varchar2(25),
    //                          deptid number(10),
    //                          manager varchar2(25) )
    Employee *emp = new Employee();
    emp.setName("Scott");
    emp.setDeptid(10);
    emp.setManager("James");
    Message mes(env);
    mes.setObject(emp);

#### 10.3.2 Message Properties

Aside from payloads, the user can specify several additional message properties, such as:

- Correlation

- Sender

- Delay and Expiration

- Recipients

- Priority and Ordering

##### 10.3.2.1 Correlation

Applications can specify a correlation identifier of the message during the enqueuing process, as demonstrated in Example 10-6. This identifier can then be used by the dequeuing application.

Example 10-6 Specifying the Correlation identifier

    mes.setCorrelationId("enq_corr_di");

##### 10.3.2.2 Sender

Applications can specify the sender of the message, as demonstrated in Example 10-7. The sender identifier can then be used by the receiver of the message.

Example 10-7 Specifying the Sender identifier

    mes.setSenderId(agt);

##### 10.3.2.3 Delay and Expiration

Time settings control the delay and expiration times of the message in seconds, as demonstrated in Example 10-8.

Example 10-8 Specifying the Delay and Expiration times of the message

    mes.setDelay(10);
    mes.setExpirationTime(60);

##### 10.3.2.4 Recipients

The agents for whom the message is intended can be specified during message encoding, as demonstrated in Example 10-9. This ensures that only the specified recipients can access the message.

Example 10-9 Specifying message recipients

    vector<Agent> agt_list;
    for (i=0; i<num_recipients; i++)
       agt_list.push_back(Agent(name, address, protocol));
    mes.setRecipientList(agt_list);

##### 10.3.2.5 Priority and Ordering

By assigning a priority level to a message, the sender can control the order in which the messages are dequeued by the receiver. Example 10-10 demonstrates how to set the priority of a message.

Example 10-10 Specifying the Priority of a Message

    mes.setPriority(3);

### 10.4 Enqueuing Messages

Messages are enqueued by the Producer. The [Producer Class](producer-class.md) is also used to specify enqueue options. A `Producer` object can be created on a valid connection where enqueuing is performed, as illustrated in Example 10-11.

The transactional behavior of the enqueue operation can be defined based on application requirements. The application can make the effect of the enqueue operation visible externally either immediately after it is completed, as in Example 10-11, or only after the enclosing transaction has been committed.

To enqueue the message, use the `send()` method, as demonstrated in Example 10-11. A client may retain the `Message` object after it is sent, modify it, and send it again.

Example 10-11 Creating a Producer, Setting Visibility, and Enqueuing the Message

    Producer prod(conn);
    ...
    prod.setVisibility(Producer::ENQ_IMMEDIATE);
    ...
    Message mes(env);
    ...
    mes.setBytes(obj);            // obj represents the content of the message
    prod.send(mes, queueName);    // queueName is the name of the queue

### 10.5 Dequeuing Messages

Messages delivered to a queue are dequeued by the `Consumer`. The [Consumer Class](consumer-class.md) is also used to specify dequeue options. A `Consumer` object can be created on a valid connection to the database where a queue exists, as demonstrated in Example 10-12.

In applications that support multiple consumers in the same queue, the name of the consumer has to be specified as a registered subscriber to the queue, as shown in Example 10-12.

To dequeue the message, use the `receive()` method, as demonstrated in Example 10-12. The `typeName` and `schemaName` parameters of the `receive()` method specify the type of payload and the schema of the payload type.

When the queue payload type is either RAW or AnyData, `schemaName` and `typeName` are optional, but you must specify these parameters explicitly when working with user-defined payloads. This is illustrated in Example 10-13.

Example 10-12 Creating a Consumer, Naming the Consumer, and Receiving a Message

    Consumer cons(conn);
    ...
    // Name must be registered with the queue through administrative interface
    cons.setConsumerName("BillApp");
    cons.setQueueName(queueName);
    ...
    Message mes = cons.receive(Message::OBJECT, "BILL_TYPE", "BILL_PROCESSOR");
    ...
    // obj is is assigned the content of the message
    obj = mes.getObject();

Example 10-13 Receiving a Message

    //receiving a RAW message
    Message mes = cons.receive(Message::RAW);
    ...
    //receiving an ANYDATA message
    Message mes = cons.receive(Message::ANYDATA);
    ...

This section includes the following topic: About Dequeuing Options.

#### 10.5.1 About Dequeuing Options

The dequeuing application can specify several dequeuing options before it begins to receive messages. These include:

- Correlation

- Mode

- Navigation

##### 10.5.1.1 Correlation

The message can be dequeued based on the value of its correlation identifier using the `setCorrelationId()` method, as shown in Example 10-14.

##### 10.5.1.2 Mode

Based on application requirements, the user can choose to only browse through messages in the queue, remove the messages from the queue, or lock messages using the `setDequeueMode()` method, as shown in Example 10-14.

##### 10.5.1.3 Navigation

Messages enqueued in a single transaction can be viewed as a single group by implementing the `setPositionOfMessage()` method, as shown in Example 10-14.

Example 10-14 Specifying dequeuing options

    cons.setCorrelationId(corrId);
    ...
    cons.setDequeueMode(deqMode);
    ...
    cons.setPositionOfMessage(Consumer::DEQ_NEXT_TRANSACTION);

### 10.6 Listening for Messages

The Listener listens for messages on queues on behalf of its registered clients. The [Listener Class](listener-class.md) implements the `listen()` method, which is a blocking call that returns when a queue has a message for a registered agent, or throws an error when the time out period expires. Example 10-15 illustrates the listening protocol.

Example 10-15 Listening for messages

    Listener listener(conn);

    vector<Agent> agtList;
    for( int i=0; i<num_agents; i++)
       agtList.push_back( Agent( name, address, protocol);

    listener.setAgentList(agtList);
    listener.setTimeOutForListen(10);

    Agent agt(env);

    try{
       agt = listener.listen();
    }
    catch{
       cout<<e.getMessage()<<endl;
    }

### 10.7 About Registering for Notification

The [Subscription Class](subscription-class.md) implements the publish-subscribe notification feature. It allows an OCCI AQ application to receive client notifications directly, register an e-mail address to which notifications can be sent, register an HTTP URL to which notifications can be posted, or register a PL/SQL procedure to be invoked on a notification. Registered clients are notified asynchronously when events are triggered or on an explicit AQ enqueue. Clients do not have to be connected to a database.

An OCCI application can do all of the following:

- Register interest in notification in the AQ namespace, and be notified when an enqueue occurs.

- Register interest in subscriptions to database events, and receive notifications when these events are triggered.

- Manage registrations, such as disable registrations temporarily, or dropping registrations entirely.

- Post (or send) notifications to registered clients.

This section includes the following topics:

- Publish-Subscribe Notifications

- About Message Format Transformation

#### 10.7.1 Publish-Subscribe Notifications

Notifications can work in several ways. They can be:

- received directly by the OCCI application

- sent to a pre-specified e-mail address

- sent to a pre-defined HTTP URL

- invoke a pre-specified database PL/SQL procedure

Registered clients are notified asynchronously when events are triggered, or on an explicit AQ enqueue. Clients do not have to be connected to a database for notifications to work. Registration can be accomplished either as:

- How to Use Direct Registration

- Using Open Registration

##### 10.7.1.1 How to Use Direct Registration

You can register directly with the database. This is relatively simple, and the registration takes effect immediately. Example 10-16 outlines the required steps to successfully register for direct event notification. It is assumed that the appropriate event trigger or queue is in existence, and that the initialization parameter `COMPATIBLE` is set to `8.1` or higher.

Example 10-16 How to Register for Notifications; Direct Registration

1.  Create the environment in `Environment::EVENTS` mode.

2.  Create the `Subscription` object.

3.  Set these `Subscription` attributes.

    The `namespace` can be set to these options:

    - To receive notifications from AQ queues, `namespace` must be set to `Subscription::NS_AQ`. The subscription name is then either of the form `SCHEMA.QUEUE` when registering on a single consumer queue, or `SCHEMA.QUEUE:``CONSUMER_NAME` when registering on a multiconsumer queue.

    - To receive notifications from other applications that use `conn->postToSubscription()` method, `namespace` must be set to `Subscription::NS_ANONYMOUS`

    The `protocol` can be set to these options:

    - If an OCCI client must receive an event notification, this attribute should be set to `Subscription::PROTO_CBK`. You also must set the notification callback and the subscription context before registering the `Subscription`. The notification callback is called when the event occurs.

    - For an e-mail notification, set the protocol to `Subscription::PROTO_MAIL`. You must set the recipient name before subscribing to avoid an application error.

    - For an HTTP URL notification, set the protocol to `Subscription::HTTP`. You must set the recipient name before subscribing to avoid an application error.

    - To invoke PL/SQL procedures in the database on event notification, set protocol to `Subscription::PROTO_SERVER`. You must set the recipient name before subscribing to avoid an application error.

4.  Register the subscriptions using `connection->registerSubscriptions()`.

##### 10.7.1.2 Using Open Registration

You can also register through an intermediate LDAP that sends the registration request to the database. This is used when the client cannot have a direct database connection; for example, the client wants to register for an open event while the database is down. This approach is also used when a client wants to register for the same event(s) in multiple databases, concurrently.

Example 10-17 outlines the LDAP open registration using the Oracle Enterprise Security Manager (OESM). Open registration has these prerequisites:

- The client must be an enterprise user

  - In each enterprise domain, create an enterprise role `ENTERPRISE_AQ_USER_ROLE`

  - For each database in the enterprise domain, add a global role `GLOBAL_AQ_USER_ROLE` to enterprise the role `ENTERPRISE_AQ_USER_ROLE`.

  - For each enterprise domain, add an enterprise role `ENTERPRISE_AQ_USER_ROLE` to the privilege group `cn=OracleDBAQUsers` under `cn=oraclecontext` in the administrative context

  - For each enterprise user that is authorized to register for events in the database, grant enterprise the role `ENTERPRISE_AQ_USER_ROLE`

- The compatibility of the database must be 9.0 or higher

- `LDAP_REGISTRATION_ENABLED` must be set to `TRUE` (default is `FALSE`):

      ALTER SYSTEM SET LDAP_REGISTRATION_ENABLED=TRUE

- `LDAP_REG_SYNC_INTERVAL` must be set to the `time_interval` (in seconds) to refresh registrations from LDAP (default is `0`, do not refresh):

      ALTER SYSTEM SET LDAP_REG_SYNC_INTERVAL = time_interval

To force a database refresh of LDAP registration information immediately, issue this command:

    ALTER SYSTEM REFRESH LDAP_REGISTRATION

Open registration takes effect when the database accesses LDAP to pick up new registrations. The frequency of pick-ups is determined by the value of `REG_SYNC_INTERVAL`.

Clients can temporarily disable subscriptions, re-enable them, or permanently unregister from future notifications.

Example 10-17 How to Use Open Registration with LDAP

1.  Create the environment in `Environment::EVENTS|Environment::USE_LDAP` mode.

2.  Set the `Environment` object for accessing LDAP:

    - The host and port on which the LDAP server is residing and listening

    - The authentication method; only simple username and password authentication is currently supported

    - The username (distinguished name) and password for authentication with the LDAP server

    - The administrative context for Oracle in the LDAP server

3.  Create the `Subscription` object.

4.  Set the distinguished names of the databases in which the client wants to receive notifications on the `Subscription` object.

5.  Set these `Subscription` attributes.

    The `namespace` can be set to these options:

    - To receive notifications from AQ queues, `namespace` must be set to `Subscription::NS_AQ`. The subscription name is then either of the form `SCHEMA.QUEUE` when registering on a single consumer queue, or `SCHEMA.QUEUE:``CONSUMER_NAME` when registering on a multiconsumer queue.

    - To receive notifications from other applications that use `conn->postToSubscription()` method, `namespace` must be set to `Subscription::NS_ANONYMOUS`

    The `protocol` can be set to these options:

    - If an OCCI client must receive an event notification, this attribute should be set to `Subscription::PROTO_CBK`. You also must set the notification callback and the subscription context before registering the `Subscription`. The notification callback is called when the event occurs.

    - For an e-mail notification, set the protocol to `Subscription::PROTO_MAIL`. You must then set the recipient name to the e-mail address to which the notifications must be sent.

    - For an HTTP URL notification, set the protocol to `Subscription::HTTP`. You must set the recipient name to the URL to which the notification must be posted.

    - To invoke PL/SQL procedures in the database on event notification, set protocol to `Subscription::PROTO_SERVER`. You must set the recipient name to the database procedure invoked on notification.

6.  Register the subscription: `environment->registerSubscriptions()`.

#### 10.7.2 About Notification Callback

The client must register a notification callback. This callback is invoked only when there is some activity on the registered subscription. In the Database AQ namespace, this happens when a message of interest is enqueued.

The callback must return `0`, and it must have the following specification:

    typedef unsigned int (*callbackfn) (Subscription &sub, NotifyResult *nr);

where:

- The `sub` parameter is the `Subscription` object which was used when the callback was registered.

- The `nr` parameter is the `NotifyResult` object holding the notification info.

Ensure that the subscription object used to register for notifications is not destroyed until it explicitly unregisters the subscription.

The user can retrieve the payload, message, message id, queue name and consumer name from the `NotifyResult` object, depending on the source of notification. These results are summarized in Table 10-1. Only a bytes payload is currently supported, and you must explicitly dequeue messages from persistent queues in the AQ namespace. If notifications come from non-persistent queues, messages are available to the callback directly; only `RAW` payloads are supported. If notifications come from persistent queues, the message has to be explicitly dequeued; all payload types are supported.

Table 10-1 Notification Result Attributes; ANONYMOUS and AQ Namespace

| Notification Result Attribute | ANONYMOUS Namespace | AQ Namespace, Persistent Queue | AQ Namespace, Non-Persistent Queue |
|:------------------------------|:--------------------|:-------------------------------|:-----------------------------------|
| payload                       | valid               | invalid                        | invalid                            |
| message                       | invalid             | invalid                        | valid                              |
| messageID                     | invalid             | valid                          | valid                              |
| consumer name                 | invalid             | valid                          | valid                              |
| queue name                    | invalid             | valid                          | valid                              |

### 10.8 About Message Format Transformation

Applications often use data in different formats, and this requires a type transformation. A transformation is implemented as a SQL function that takes the source data type as input and returns an object of the target data type.Transformations can be applied when message are enqueued, dequeued, or when they are propagated to a remote subscriber.

**See Also:**

The following chapters of the [Oracle Database Advanced Queuing User's Guide](../adque/index.md) for information of format transformation:

- [Oracle Streams AQ Administrative Interface](../adque/aq-messaging-gateway-views.md)

- [Oracle Streams AQ Administrative Interface: Views](../adque/aq-introduction.md)

- [Oracle Streams AQ Operational Interface: Basic Operations](../adque/aq-operations-using-pl-sql.md)
