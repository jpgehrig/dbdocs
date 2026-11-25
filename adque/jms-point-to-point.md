The following topics describe the components of the Oracle Database Advanced Queuing (AQ) [Java Message Service](glossary.md) (JMS) operational interface that are specific to point-to-point operations. Components that are shared by point-to-point and publish/subscribe are described in [Oracle Java Message Service Shared Interfaces](jms-shared-interfaces.md).

- Creating a Connection with User Name/Password

- Creating a Connection with Default ConnectionFactory Parameters

- Creating a QueueConnection with User Name/Password

- Creating a QueueConnection with an Open JDBC Connection

- Creating a QueueConnection with Default ConnectionFactory Parameters

- Creating a QueueConnection with an Open OracleOCIConnectionPool

- Creating a Session

- Creating a QueueSession

- Creating a QueueSender

- Sending Messages Using a QueueSender with Default Send Options

- Sending Messages Using a QueueSender by Specifying Send Options

- Creating a QueueBrowser for Standard JMS Type Messages

- Creating a QueueBrowser for Standard JMS Type Messages\_ Locking Messages

- Creating a QueueBrowser for Oracle Object Type Messages

- Creating a QueueBrowser for Oracle Object Type Messages\_ Locking Messages

- Creating a QueueReceiver for Standard JMS Type Messages

- Creating a QueueReceiver for Oracle Object Type Messages

### Creating a Connection with User Name/Password

    public javax.jms.Connection createConnection(
                 java.lang.String username,
                 java.lang.String password)
          throws JMSException

This method creates a connection supporting both point-to-point and publish/subscribe operations with the specified user name and password. This method is new and supports JMS version 1.1 specifications. It has the following parameters:

| Parameter  | Description                                             |
|:-----------|:--------------------------------------------------------|
| `username` | Name of the user connecting to the database for queuing |
| `password` | Password for creating the connection to the server      |

### Creating a Connection with Default ConnectionFactory Parameters

    public javax.jms.Connection createConnection()
          throws JMSException

This method creates a connection supporting both point-to-point and publish/subscribe operations with default [ConnectionFactory](glossary.md) parameters. This method is new and supports JMS version 1.1 specifications. If the `ConnectionFactory` properties do not contain a default user name and password, then it throws a JMSException.

### Creating a QueueConnection with User Name/Password

    public javax.jms.QueueConnection createQueueConnection(
                 java.lang.String username,
                 java.lang.String password)
          throws JMSException

This method creates a [queue](glossary.md) connection with the specified user name and password. It has the following parameters:

| Parameter  | Description                                             |
|:-----------|:--------------------------------------------------------|
| `username` | Name of the user connecting to the database for queuing |
| `password` | Password for creating the connection to the server      |

Example 13-1 Creating a QueueConnection with User Name/Password

    QueueConnectionFactory qc_fact = AQjmsFactory.getQueueConnectionFactory(
       "sun123", "oratest", 5521, "thin");
    QueueConnection qc_conn = qc_fact.createQueueConnection("jmsuser", "jmsuser");

### Creating a QueueConnection with an Open JDBC Connection

    public static javax.jms.QueueConnection createQueueConnection(
       java.sql.Connection jdbc_connection)
       throws JMSException

This method creates a queue connection with an open JDBC connection. It is static and has the following parameter:

| Parameter         | Description                           |
|:------------------|:--------------------------------------|
| `jdbc_connection` | Valid open connection to the database |

The method in Example 13-2 can be used if the user wants to use an existing JDBC connection (say from a connection pool) for JMS operations. In this case JMS does not open a new connection, but instead uses the supplied JDBC connection to create the JMS `QueueConnection` object.

The method in Example 13-3 is the only way to create a JMS `QueueConnection` when using JMS from a Java stored procedures inside the database (JDBC Server driver)

Example 13-2 Creating a QueueConnection with an Open JDBC Connection

    Connection db_conn;     /* previously opened JDBC connection */
    QueueConnection qc_conn = AQjmsQueueConnectionFactory.createQueueConnection(
               db_conn);

Example 13-3 Creating a QueueConnection from a Java Procedure Inside Database

    OracleDriver ora = new OracleDriver();
    QueueConnection qc_conn = AQjmsQueueConnectionFactory.createQueueConnection(ora.defaultConnection());

### Creating a QueueConnection with Default ConnectionFactory Parameters

    public javax.jms.QueueConnection createQueueConnection()
          throws JMSException

This method creates a queue connection with default [ConnectionFactory](glossary.md) parameters. If the queue connection factory properties do not contain a default user name and password, then it throws a JMSException.

### Creating a QueueConnection with an Open OracleOCIConnectionPool

    public static javax.jms.QueueConnection createQueueConnection(
              oracle.jdbc.pool.OracleOCIConnectionPool cpool)
       throws JMSException

This method creates a queue connection with an open `OracleOCIConnectionPool`. It is static and has the following parameter:

| Parameter | Description                                    |
|:----------|:-----------------------------------------------|
| `cpool`   | Valid open OCI connection pool to the database |

The method in Example 13-4 can be used if the user wants to use an existing `OracleOCIConnectionPool` instance for JMS operations. In this case JMS does not open an new `OracleOCIConnectionPool` instance, but instead uses the supplied `OracleOCIConnectionPool` instance to create the JMS QueueConnection object.

Example 13-4 Creating a QueueConnection with an Open OracleOCIConnectionPool

    OracleOCIConnectionPool cpool; /* previously created OracleOCIConnectionPool */
    QueueConnection qc_conn = AQjmsQueueConnectionFactory.createQueueConnection(cpool);

### Creating a Session

    public javax.jms.Session createSession(boolean transacted,
                                                     int ack_mode)
                                              throws JMSException

This method creates a `Session`, which supports both point-to-point and publish/subscribe operations. This method is new and supports JMS version 1.1 specifications. Transactional and [nontransactional](glossary.md) sessions are supported. It has the following parameters:

| Parameter    | Description                                                                                                                                                                                                                                          |
|:-------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `transacted` | If set to true, then the session is [transactional](glossary.md)                                                                                                                                                                                     |
| `ack_mode`   | Indicates whether the consumer or the client will acknowledge any messages it receives. It is ignored if the session is transactional. Legal values are `Session.AUTO_ACKNOWLEDGE`, `Session.CLIENT_ACKNOWLEDGE`, and `Session.DUPS_OK_ACKNOWLEDGE`. |

### Creating a QueueSession

    public javax.jms.QueueSession createQueueSession(
       boolean transacted, int ack_mode)
            throws JMSException

This method creates a `QueueSession`. Transactional and nontransactional sessions are supported. It has the following parameters:

| Parameter    | Description                                                                                                                                                                                                                                          |
|:-------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `transacted` | If set to true, then the session is [transactional](glossary.md)                                                                                                                                                                                     |
| `ack_mode`   | Indicates whether the consumer or the client will acknowledge any messages it receives. It is ignored if the session is transactional. Legal values are `Session.AUTO_ACKNOWLEDGE`, `Session.CLIENT_ACKNOWLEDGE`, and `Session.DUPS_OK_ACKNOWLEDGE`. |

Example 13-5 Creating a Transactional QueueSession

    QueueConnection qc_conn;
    QueueSession  q_sess = qc_conn.createQueueSession(true, 0);

### Creating a QueueSender

    public javax.jms.QueueSender createSender(javax.jms.Queue queue)
                                       throws JMSException

This method creates a `QueueSender`. If a sender is created without a default queue, then the destination queue must be specified on every [send](glossary.md) operation. It has the following parameter:

| Parameter | Description               |
|:----------|:--------------------------|
| `queue`   | Name of destination queue |

### Sending Messages Using a QueueSender with Default Send Options

    public void send(javax.jms.Queue queue,
                     javax.jms.Message message)
              throws JMSException

This method sends a [message](glossary.md) using a `QueueSender` with default send options. This operation uses default values for message `priority` (`1`) and `timeToLive` (`infinite`). It has the following parameters:

| Parameter | Description                   |
|:----------|:------------------------------|
| `queue`   | Queue to send this message to |
| `message` | Message to send               |

If the `QueueSender` has been created with a default queue, then the queue parameter may not necessarily be supplied in the `send()` call. If a queue is specified in the `send()` operation, then this value overrides the default queue of the `QueueSender`.

If the `QueueSender` has been created without a default queue, then the queue parameter must be specified in every `send()` call.

Example 13-6 Creating a Sender to Send Messages to Any Queue

    /* Create a sender to send messages to any queue */
    QueueSession  jms_sess;
    QueueSender  sender1;
    TextMessage  message;
    sender1 = jms_sess.createSender(null);
    sender1.send(queue, message);

Example 13-7 Creating a Sender to Send Messages to a Specific Queue

    /* Create a sender to send messages to a specific queue */
    QueueSession jms_sess;
    QueueSender sender2;
    Queue   billed_orders_que;
    TextMessage  message;
    sender2 = jms_sess.createSender(billed_orders_que);
    sender2.send(queue, message);

### Sending Messages Using a QueueSender by Specifying Send Options

    public void send(javax.jms.Queue queue,
                     javax.jms.Message message,
                     int deliveryMode,
                     int priority,
                     long timeToLive)
              throws JMSException

This method sends messages using a `QueueSender` by specifying send options. It has the following parameters:

| Parameter      | Description                                          |
|:---------------|:-----------------------------------------------------|
| `queue`        | Queue to send this message to                        |
| `message`      | Message to send                                      |
| `deliveryMode` | Delivery mode to use                                 |
| `priority`     | Priority for this message                            |
| `timeToLive`   | Message lifetime in milliseconds (zero is unlimited) |

If the `QueueSender` has been created with a default queue, then the queue parameter may not necessarily be supplied in the `send()` call. If a queue is specified in the `send()` operation, then this value overrides the default queue of the `QueueSender`.

If the `QueueSender` has been created without a default queue, then the queue parameter must be specified in every `send()` call.

Example 13-8 Sending Messages Using a QueueSender by Specifying Send Options 1

    /* Create a sender to send messages to any queue */
    /* Send a message to new_orders_que with priority 2 and timetoLive 100000
       milliseconds */
    QueueSession  jms_sess;
    QueueSender  sender1;
    TextMessage mesg;
    Queue   new_orders_que
    sender1 = jms_sess.createSender(null);
    sender1.send(new_orders_que, mesg, DeliveryMode.PERSISTENT, 2, 100000);

Example 13-9 Sending Messages Using a QueueSender by Specifying Send Options 2

    /* Create a sender to send messages to a specific queue */
    /* Send a message with priority 1 and timetoLive 400000 milliseconds */
    QueueSession jms_sess;
    QueueSender sender2;
    Queue   billed_orders_que;
    TextMessage mesg;
    sender2 = jms_sess.createSender(billed_orders_que);
    sender2.send(mesg, DeliveryMode.PERSISTENT, 1, 400000);

### Creating a QueueBrowser for Standard JMS Type Messages

    public javax.jms.QueueBrowser createBrowser(javax.jms.Queue queue,
                                                java.lang.String messageSelector)
                                         throws JMSException

This method creates a `QueueBrowser` for queues with text, stream, objects, bytes or MapMessage message bodies. It has the following parameters:

| Parameter         | Description                                                                           |
|:------------------|:--------------------------------------------------------------------------------------|
| `queue`           | Queue to access                                                                       |
| `messageSelector` | Only messages with properties matching the `messageSelector` expression are delivered |

Use methods in `java.util.Enumeration` to go through list of messages.

**See Also:**

"[MessageSelector](jms-introduction.md)"

Example 13-10 Creating a QueueBrowser Without a Selector

    /* Create a browser without a selector */
    QueueSession    jms_session;
    QueueBrowser    browser;
    Queue           queue;
    browser = jms_session.createBrowser(queue);

Example 13-11 Creating a QueueBrowser With a Specified Selector

    /* Create a browser for queues with a specified selector */
    QueueSession    jms_session;
    QueueBrowser    browser;
    Queue           queue;
    /* create a Browser to look at messages with correlationID = RUSH  */
    browser = jms_session.createBrowser(queue, "JMSCorrelationID = 'RUSH'");

### Creating a QueueBrowser for Standard JMS Type Messages, Locking Messages

    public javax.jms.QueueBrowser createBrowser(javax.jms.Queue queue,
                                                java.lang.String messageSelector,
                                                boolean locked)
                                         throws JMSException

This method creates a `QueueBrowser` for queues with TextMessage, StreamMessage, ObjectMessage, BytesMessage, or MapMessage message bodies, locking messages while browsing. Locked messages cannot be removed by other consumers until the browsing session ends the transaction. It has the following parameters:

| Parameter         | Description                                                                                   |
|:------------------|:----------------------------------------------------------------------------------------------|
| `queue`           | Queue to access                                                                               |
| `messageSelector` | Only messages with properties matching the `messageSelector` expression are delivered         |
| `locked`          | If set to true, then messages are locked as they are browsed (similar to a SELECT for UPDATE) |

Example 13-12 Creating a QueueBrowser Without a Selector, Locking Messages

    /* Create a browser without a selector */
    QueueSession    jms_session;
    QueueBrowser    browser;
    Queue           queue;
    browser = jms_session.createBrowser(queue, null, true);

Example 13-13 Creating a QueueBrowser With a Specified Selector, Locking Messages

    /* Create a browser for queues with a specified selector */
    QueueSession    jms_session;
    QueueBrowser    browser;
    Queue           queue;
    /* create a Browser to look at messages with
    correlationID = RUSH in lock mode */
    browser = jms_session.createBrowser(queue, "JMSCorrelationID = 'RUSH'", true);

### Creating a QueueBrowser for Oracle Object Type Messages

    public javax.jms.QueueBrowser createBrowser(javax.jms.Queue queue,
                                                java.lang.String messageSelector,
                                                java.lang.Object payload_factory)
                                         throws JMSException

This method creates a `QueueBrowser` for queues of Oracle [object type](glossary.md) messages. It has the following parameters:

| Parameter         | Description                                                                             |
|:------------------|:----------------------------------------------------------------------------------------|
| `queue`           | Queue to access                                                                         |
| `messageSelector` | Only messages with properties matching the `messageSelector` expression are delivered   |
| payload_factory   | `CustomDatumFactory` or `ORADataFactory` for the java class that maps to the Oracle ADT |

The `CustomDatumFactory` for a particular java class that maps to the SQL object payload can be obtained using the `getFactory` static method.

**Note:**

`CustomDatum` support will be deprecated in a future release. Use `ORADataFactory` payload factories instead.

Assume the queue `test_queue` has payload of type `SCOTT.EMPLOYEE` and the java class that is generated by Jpublisher for this Oracle object type is called Employee. The Employee class implements the `CustomDatum` interface. The `CustomDatumFactory` for this class can be obtained by using the `Employee.getFactory()` method.

**Note:**

Sharded queues do not support Object Type messages

**See Also:**

"[MessageSelector](jms-introduction.md)"

Example 13-14 Creating a QueueBrowser for ADTMessages

    /* Create a browser for a Queue with AdtMessage messages of type EMPLOYEE*/
    QueueSession jms_session
    QueueBrowser browser;
    Queue        test_queue;
    browser = ((AQjmsSession)jms_session).createBrowser(test_queue,
                                                       "corrid='EXPRESS'",
                                                        Employee.getFactory());

### Creating a QueueBrowser for Oracle Object Type Messages, Locking Messages

    public javax.jms.QueueBrowser createBrowser(javax.jms.Queue queue,
                                                java.lang.String messageSelector,
                                                java.lang.Object payload_factory,
                                                boolean locked)
                                         throws JMSException

This method creates a `QueueBrowser` for queues of Oracle object type messages, locking messages while browsing. It has the following parameters:

| Parameter         | Description                                                                                   |
|:------------------|:----------------------------------------------------------------------------------------------|
| `queue`           | Queue to access                                                                               |
| `messageSelector` | Only messages with properties matching the `messageSelector` expression are delivered         |
| payload_factory   | `CustomDatumFactory` or `ORADataFactory` for the java class that maps to the Oracle ADT       |
| `locked`          | If set to true, then messages are locked as they are browsed (similar to a SELECT for UPDATE) |

**Note:**

`CustomDatum` support will be deprecated in a future release. Use `ORADataFactory` payload factories instead.

**Note:**

Sharded queues do not support Object Type messages

Example 13-15 Creating a QueueBrowser for AdtMessages, Locking Messages

    /* Create a browser for a Queue with AdtMessage messagess of type EMPLOYEE* in lock mode/
    QueueSession jms_session
    QueueBrowser browser;
    Queue        test_queue;
    browser = ((AQjmsSession)jms_session).createBrowser(test_queue,
                                                        null,
                                                        Employee.getFactory(),
                                                        true);

### Creating a QueueReceiver for Standard JMS Type Messages

    public javax.jms.QueueReceiver createReceiver(javax.jms.Queue queue,
                                                  java.lang.String messageSelector)
                                           throws JMSException

This method creates a `QueueReceiver` for queues of standard JMS type messages. It has the following parameters:

| Parameter         | Description                                                                           |
|:------------------|:--------------------------------------------------------------------------------------|
| `queue`           | Queue to access                                                                       |
| `messageSelector` | Only messages with properties matching the `messageSelector` expression are delivered |

**See Also:**

"[MessageSelector](jms-introduction.md)"

Example 13-16 Creating a QueueReceiver Without a Selector

    /* Create a receiver without a selector */
    QueueSession    jms_session
    QueueReceiver   receiver;
    Queue           queue;
    receiver = jms_session.createReceiver(queue);

Example 13-17 Creating a QueueReceiver With a Specified Selector

    /* Create a receiver for queues with a specified selector */
    QueueSession    jms_session;
    QueueReceiver   receiver;
    Queue           queue;
    /* create Receiver to receive messages with correlationID starting with EXP  */
    browser = jms_session.createReceiver(queue, "JMSCorrelationID LIKE 'EXP%'");

### Creating a QueueReceiver for Oracle Object Type Messages

    public javax.jms.QueueReceiver createReceiver(javax.jms.Queue queue,
                                                  java.lang.String messageSelector,
                                                  java.lang.Object payload_factory)
                                           throws JMSException

This method creates a `QueueReceiver` for queues of Oracle object type messages. It has the following parameters:

| Parameter         | Description                                                                             |
|:------------------|:----------------------------------------------------------------------------------------|
| `queue`           | Queue to access                                                                         |
| `messageSelector` | Only messages with properties matching the `messageSelector` expression are delivered   |
| payload_factory   | `CustomDatumFactory` or `ORADataFactory` for the java class that maps to the Oracle ADT |

The `CustomDatumFactory` for a particular java class that maps to the SQL object type payload can be obtained using the `getFactory` static method.

**Note:**

`CustomDatum` support will be deprecated in a future release. Use `ORADataFactory` payload factories instead.

Assume the queue `test_queue` has payload of type `SCOTT.EMPLOYEE` and the java class that is generated by Jpublisher for this Oracle object type is called Employee. The Employee class implements the `CustomDatum` interface. The `ORADataFactory` for this class can be obtained by using the Employee.getFactory() method.

**Note:**

Sharded queues do not support Object Type messages

**See Also:**

"[MessageSelector](jms-introduction.md)"

Example 13-18 Creating a QueueReceiver for AdtMessage Messages

    /* Create a receiver for a Queue with AdtMessage messages of type EMPLOYEE*/
    QueueSession jms_session
    QueueReceiver receiver;
    Queue        test_queue;
    browser = ((AQjmsSession)jms_session).createReceiver(
                     test_queue,
                    "JMSCorrelationID = 'MANAGER',
                     Employee.getFactory());
