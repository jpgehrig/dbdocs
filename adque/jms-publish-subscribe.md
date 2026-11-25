The following topics describe the components of the Oracle Database Advanced Queuing (AQ) [Java Message Service](glossary.md) (JMS) operational interface that are specific to [publish/subscribe](glossary.md) operations. Components that are shared by point-to-point and publish/subscribe are described in [Oracle Java Message Service Shared Interfaces](jms-shared-interfaces.md).

- Creating a Connection with User Name/Password

- Creating a Connection with Default ConnectionFactory Parameters

- Creating a TopicConnection with User Name/Password

- Creating a TopicConnection with Open JDBC Connection

- Creating a TopicConnection with an Open OracleOCIConnectionPool

- Creating a Session

- Creating a TopicSession

- Creating a TopicPublisher

- Publishing Messages with Minimal Specification

- Publishing Messages Specifying Topic

- Publishing Messages Specifying Delivery Mode\_ Priority\_ and TimeToLive

- Publishing Messages Specifying a Recipient List

- Creating a DurableSubscriber for a JMS Topic Without Selector

- Creating a DurableSubscriber for a JMS Topic with Selector

- Creating a DurableSubscriber for an Oracle Object Type Topic Without Selector

- Creating a DurableSubscriber for an Oracle Object Type Topic with Selector

- Specifying Transformations for Topic Subscribers

- Creating a Remote Subscriber for JMS Messages

- Creating a Remote Subscriber for Oracle Object Type Messages

- Specifying Transformations for Remote Subscribers

- Unsubscribing a Durable Subscription for a Local Subscriber

- Unsubscribing a Durable Subscription for a Remote Subscriber

- Creating a TopicReceiver for a Topic of Standard JMS Type Messages

- Creating a TopicReceiver for a Topic of Oracle Object Type Messages

- Creating a TopicBrowser for Standard JMS Messages

- Creating a TopicBrowser for Standard JMS Messages\_ Locking Messages

- Creating a TopicBrowser for Oracle Object Type Messages

- Creating a TopicBrowser for Oracle Object Type Messages\_ Locking Messages

- Browsing Messages Using a TopicBrowser

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

### Creating a TopicConnection with User Name/Password

    public javax.jms.TopicConnection createTopicConnection(
                 java.lang.String username,
                 java.lang.String password)
          throws JMSException

This method creates a `TopicConnection` with the specified user name and password. It has the following parameters:

| Parameter  | Description                                             |
|:-----------|:--------------------------------------------------------|
| `username` | Name of the user connecting to the database for queuing |
| `password` | Password for creating the connection to the server      |

Example 14-1 Creating a TopicConnection with User Name/Password

    TopicConnectionFactory tc_fact = AQjmsFactory.getTopicConnectionFactory("sun123", "oratest", 5521, "thin");
    /* Create a TopicConnection using a username/password */
    TopicConnection tc_conn = tc_fact.createTopicConnection("jmsuser", "jmsuser");

### Creating a TopicConnection with Open JDBC Connection

    public static javax.jms.TopicConnection createTopicConnection(
                  java.sql.Connection jdbc_connection)
           throws JMSException

This method creates a `TopicConnection` with open JDBC connection. It has the following parameter:

| Parameter         | Description                       |
|:------------------|:----------------------------------|
| `jdbc_connection` | Valid open connection to database |

Example 14-2 Creating a TopicConnection with Open JDBC Connection

    Connection db_conn;   /*previously opened JDBC connection */
    TopicConnection tc_conn =
    AQjmsTopicConnectionFactory createTopicConnection(db_conn);

Example 14-3 Creating a TopicConnection with New JDBC Connection

    OracleDriver ora = new OracleDriver();
    TopicConnection tc_conn =
    AQjmsTopicConnectionFactory.createTopicConnection(ora.defaultConnection());

### Creating a TopicConnection with an Open OracleOCIConnectionPool

    public static javax.jms.TopicConnection createTopicConnection(
                  oracle.jdbc.pool.OracleOCIConnectionPool cpool)
           throws JMSException

This method creates a `TopicConnection` with an open `OracleOCIConnectionPool`. It is static and has the following parameter:

| Parameter | Description                                    |
|:----------|:-----------------------------------------------|
| `cpool`   | Valid open OCI connection pool to the database |

Example 14-4 Creating a TopicConnection with Open OracleOCIConnectionPool

    OracleOCIConnectionPool cpool; /* previously created OracleOCIConnectionPool */
    TopicConnection tc_conn =
    AQjmsTopicConnectionFactory.createTopicConnection(cpool);

### Creating a Session

    public javax.jms.Session createSession(boolean transacted,
                                                     int ack_mode)
                                              throws JMSException

This method creates a `Session` supporting both point-to-point and publish/subscribe operations. It is new and supports JMS version 1.1 specifications. It has the following parameters:

| Parameter    | Description                                                                                                                                                                                                                                          |
|:-------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `transacted` | If set to true, then the session is [transactional](glossary.md)                                                                                                                                                                                     |
| `ack_mode`   | Indicates whether the consumer or the client will acknowledge any messages it receives. It is ignored if the session is transactional. Legal values are `Session.AUTO_ACKNOWLEDGE`, `Session.CLIENT_ACKNOWLEDGE`, and `Session.DUPS_OK_ACKNOWLEDGE`. |

### Creating a TopicSession

    public javax.jms.TopicSession createTopicSession(boolean transacted,
                                                     int ack_mode)
                                              throws JMSException

This method creates a `TopicSession`. It has the following parameters:

| Parameter    | Description                                                                                                                                                                                                                                          |
|:-------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `transacted` | If set to true, then the session is [transactional](glossary.md)                                                                                                                                                                                     |
| `ack_mode`   | Indicates whether the consumer or the client will acknowledge any messages it receives. It is ignored if the session is transactional. Legal values are `Session.AUTO_ACKNOWLEDGE`, `Session.CLIENT_ACKNOWLEDGE`, and `Session.DUPS_OK_ACKNOWLEDGE`. |

Example 14-5 Creating a TopicSession

    TopicConnection tc_conn;
    TopicSession t_sess = tc_conn.createTopicSession(true,0);

### Creating a TopicPublisher

    public javax.jms.TopicPublisher createPublisher(javax.jms.Topic topic)
                                             throws JMSException

This method creates a `TopicPublisher`. It has the following parameter:

| Parameter | Description                                                                     |
|:----------|:--------------------------------------------------------------------------------|
| `topic`   | Topic to publish to, or null if this is an unidentified [producer](glossary.md) |

### Publishing Messages with Minimal Specification

    public void publish(javax.jms.Message message)
                 throws JMSException

This method publishes a message with minimal specification. It has the following parameter:

| Parameter | Description     |
|:----------|:----------------|
| `message` | Message to send |

The `TopicPublisher` uses the default values for message `priority` (`1`) and `timeToLive` (`infinite`).

Example 14-6 Publishing Without Specifying Topic

    /* Publish without specifying topic */
    TopicConnectionFactory    tc_fact   = null;
    TopicConnection           t_conn    = null;
    TopicSession              jms_sess;
    TopicPublisher            publisher1;
    Topic                     shipped_orders;
    int                       myport = 5521;
    /* create connection and session */
    tc_fact = AQjmsFactory.getTopicConnectionFactory(
              "MYHOSTNAME",
              "MYSID",
               myport,
              "oci8");
    t_conn = tc_fact.createTopicConnection("jmstopic", "jmstopic");
    /* create TopicSession */
    jms_sess = t_conn.createTopicSession(true, Session.CLIENT_ACKNOWLEDGE);
    /* get shipped orders topic */
    shipped_orders = ((AQjmsSession )jms_sess).getTopic(
              "OE",
              "Shipped_Orders_Topic");
    publisher1 = jms_sess.createPublisher(shipped_orders);
    /* create TextMessage */
    TextMessage     jms_sess.createTextMessage();
    /* publish without specifying the topic */
    publisher1.publish(text_message);

Example 14-7 Publishing Specifying Correlation and Delay

    TopicConnectionFactory    tc_fact   = null;
    TopicConnection           t_conn    = null;
    TopicSession              jms_sess;
    TopicPublisher            publisher1;
    Topic                     shipped_orders;
    int                       myport = 5521;
    /* create connection and session */
    tc_fact = AQjmsFactory.getTopicConnectionFactory(
              "MYHOSTNAME",
              "MYSID",
               myport,
              "oci8");
    t_conn = tc_fact.createTopicConnection("jmstopic", "jmstopic");
    jms_sess = t_conn.createTopicSession(true, Session.CLIENT_ACKNOWLEDGE);
    shipped_orders = ((AQjmsSession )jms_sess).getTopic(
              "OE",
              "Shipped_Orders_Topic");
    publisher1 = jms_sess.createPublisher(shipped_orders);
    /* Create TextMessage */
    TextMessage     jms_sess.createTextMessage();
    /* Set correlation and delay */
    /* Set correlation */
    jms_sess.setJMSCorrelationID("FOO");
    /* Set delay of 30 seconds */
    jms_sess.setLongProperty("JMS_OracleDelay", 30);
    /* Publish  */
    publisher1.publish(text_message);

### Publishing Messages Specifying Topic

    public void publish(javax.jms.Topic topic, javax.jms.Message message)
                 throws JMSException

This method publishes a message specifying the topic. It has the following parameters:

| Parameter | Description         |
|:----------|:--------------------|
| `topic`   | Topic to publish to |
| `message` | Message to send     |

If the `TopicPublisher` has been created with a default topic, then the `topic` parameter may not be specified in the `publish()` call. If a topic is specified, then that value overrides the default in the `TopicPublisher`. If the `TopicPublisher` has been created without a default topic, then the topic must be specified with the `publish()` call.

Example 14-8 Publishing Specifying Topic

    /* Publish specifying topic */
    TopicConnectionFactory    tc_fact   = null;
    TopicConnection           t_conn    = null;
    TopicSession              jms_sess;
    TopicPublisher            publisher1;
    Topic                     shipped_orders;
    int                       myport = 5521;
    /* create connection and session */
    tc_fact = AQjmsFactory.getTopicConnectionFactory(
              'MYHOSTNAME', 'MYSID', myport, 'oci8');
    t_conn = tc_fact.createTopicConnection("jmstopic", "jmstopic");
    jms_sess = t_conn.createTopicSession(true, Session.CLIENT_ACKNOWLEDGE);
    /* create TopicPublisher */
    publisher1 = jms_sess.createPublisher(null);
    /* get topic object */
    shipped_orders = ((AQjmsSession )jms_sess).getTopic(
              'WS', 'Shipped_Orders_Topic');
    /* create text message */
    TextMessage     jms_sess.createTextMessage();
    /* publish specifying the topic */
    publisher1.publish(shipped_orders, text_message);

### Publishing Messages Specifying Delivery Mode, Priority, and TimeToLive

    public void publish(javax.jms.Topic topic,
                        javax.jms.Message message,
                        oracle.jms.AQjmsAgent[] recipient_list,
                        int deliveryMode,
                        int priority,
                        long timeToLive)
                 throws JMSException

This method publishes a message specifying delivery mode, priority and `TimeToLive`. It has the following parameters:

| Parameter        | Description                                                                                  |
|:-----------------|:---------------------------------------------------------------------------------------------|
| `topic`          | Topic to which to publish the message (overrides the default topic of the `MessageProducer`) |
| `message`        | Message to publish                                                                           |
| `recipient_list` | List of recipients to which the message is published. Recipients are of type `AQjmsAgent`.   |
| `deliveryMode`   | `PERSISTENT` or `NON_PERSISTENT` (only `PERSISTENT` is supported in this release)            |
| `priority`       | Priority for this message                                                                    |
| `timeToLive`     | Message lifetime in milliseconds (zero is unlimited)                                         |

Example 14-9 Publishing Specifying Priority and TimeToLive

    TopicConnectionFactory    tc_fact   = null;
    TopicConnection           t_conn    = null;
    TopicSession              jms_sess;
    TopicPublisher            publisher1;
    Topic                     shipped_orders;
    int                       myport = 5521;
    /* create connection and session */
    tc_fact = AQjmsFactory.getTopicConnectionFactory(
              "MYHOSTNAME", "MYSID", myport, "oci8");
    t_conn = tc_fact.createTopicConnection("jmstopic", "jmstopic");
    jms_sess = t_conn.createTopicSession(true, Session.CLIENT_ACKNOWLEDGE);
    shipped_orders = ((AQjmsSession )jms_sess).getTopic(
              "OE", "Shipped_Orders_Topic");
    publisher1 = jms_sess.createPublisher(shipped_orders);
    /* Create TextMessage */
    TextMessage     jms_sess.createTextMessage();
    /* Publish  message with priority 1 and time to live 200 seconds */
    publisher1.publish(text_message, DeliveryMode.PERSISTENT, 1, 200000);

### Publishing Messages Specifying a Recipient List

    public void publish(javax.jms.Message message,
                        oracle.jms.AQjmsAgent[] recipient_list)
                 throws JMSException

This method publishes a message specifying a [recipient](glossary.md) list overriding topic subscribers. It has the following parameters:

| Parameter        | Description                                                                                |
|:-----------------|:-------------------------------------------------------------------------------------------|
| `message`        | Message to publish                                                                         |
| `recipient_list` | List of recipients to which the message is published. Recipients are of type `AQjmsAgent`. |

Example 14-10 Publishing Specifying a Recipient List Overriding Topic Subscribers

    /* Publish specifying priority and timeToLive */
    TopicConnectionFactory    tc_fact   = null;
    TopicConnection           t_conn    = null;
    TopicSession              jms_sess;
    TopicPublisher            publisher1;
    Topic                     shipped_orders;
    int                       myport = 5521;
    AQjmsAgent[]              recipList;
    /* create connection and session */
    tc_fact = AQjmsFactory.getTopicConnectionFactory(
              "MYHOSTNAME", "MYSID", myport, "oci8");
    t_conn = tc_fact.createTopicConnection("jmstopic", "jmstopic");
    jms_sess = t_conn.createTopicSession(true, Session.CLIENT_ACKNOWLEDGE);
    shipped_orders = ((AQjmsSession )jms_sess).getTopic(
              "OE", "Shipped_Orders_Topic");
    publisher1 = jms_sess.createPublisher(shipped_orders);
    /* create TextMessage */
    TextMessage     jms_sess.createTextMessage();
    /* create two receivers */
    recipList = new AQjmsAgent[2];
    recipList[0] = new AQjmsAgent(
              "ES", "ES.shipped_orders_topic", AQAgent.DEFAULT_AGENT_PROTOCOL);
    recipList[1] = new AQjmsAgent(
              "WS", "WS.shipped_orders_topic", AQAgent.DEFAULT_AGENT_PROTOCOL);
    /* publish  message specifying a recipient list */
    publisher1.publish(text_message, recipList);

### Creating a DurableSubscriber for a JMS Topic Without Selector

    public javax.jms.TopicSubscriber createDurableSubscriber(
                 javax.jms.Topic topic,
                 java.lang.String subs_name)
          throws JMSException

This method creates a DurableSubscriber for a [JMS topic](glossary.md) without selector. It has the following parameters:

| Parameter   | Description                             |
|:------------|:----------------------------------------|
| `topic`     | Non-temporary topic to subscribe to     |
| `subs_name` | Name used to identify this subscription |

#### Exclusive Access to Topics

`CreateDurableSubscriber()` and `Unsubscribe()` both require exclusive access to their target topics. If there are pending JMS `send()`, `publish()`, or `receive()` operations on the same topic when these calls are applied, then exception ORA - 4020 is raised. There are two solutions to the problem:

- Limit calls to `createDurableSubscriber()` and `Unsubscribe()` to the setup or cleanup phase when there are no other JMS operations pending on the topic. That makes sure that the required resources are not held by other JMS operational calls.

- Call `TopicSession.commit` before calling `createDurableSubscriber()` or `Unsubscribe()`.

Example 14-11 Creating a Durable Subscriber for a JMS Topic Without Selector

    TopicConnectionFactory    tc_fact   = null;
    TopicConnection           t_conn    = null;
    TopicSession              jms_sess;
    TopicSubscriber           subscriber1;
    Topic                     shipped_orders;
    int                       myport = 5521;
    AQjmsAgent[]              recipList;
    /* create connection and session */
    tc_fact = AQjmsFactory.getTopicConnectionFactory(
              "MYHOSTNAME",
              "MYSID",
               myport,
              "oci8");
    t_conn = tc_fact.createTopicConnection("jmstopic", "jmstopic");
    jms_sess = t_conn.createTopicSession(true, Session.CLIENT_ACKNOWLEDGE);
    shipped_orders = ((AQjmsSession )jms_sess).getTopic(
              "OE",
              "Shipped_Orders_Topic");
    /* create a durable subscriber on the shipped_orders topic*/
    subscriber1 = jms_sess.createDurableSubscriber(
              shipped_orders,
             'WesternShipping');

### Creating a DurableSubscriber for a JMS Topic with Selector

    public javax.jms.TopicSubscriber createDurableSubscriber(
                 javax.jms.Topic topic,
                 java.lang.String subs_name,
                 java.lang.String messageSelector,
                 boolean noLocal)
          throws JMSException

This method creates a durable subscriber for a JMS topic with selector. It has the following parameters:

| Parameter         | Description                                                                                                                                                                                      |
|:------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `topic`           | Non-temporary topic to subscribe to                                                                                                                                                              |
| `subs_name`       | Name used to identify this subscription                                                                                                                                                          |
| `messageSelector` | Only messages with properties matching the `messageSelector` expression are delivered. A value of null or an empty string indicates that there is no `messageSelector` for the message consumer. |
| `noLocal`         | If set to true, then it inhibits the delivery of messages published by its own connection                                                                                                        |

A client can change an existing durable subscription by creating a durable TopicSubscriber with the same name and a different `messageSelector`. An unsubscribe call is needed to end the subscription to the topic.

**See Also:**

- "Exclusive Access to Topics"

- "[MessageSelector](jms-introduction.md)"

Example 14-12 Creating a Durable Subscriber for a JMS Topic With Selector

    TopicConnectionFactory    tc_fact   = null;
    TopicConnection           t_conn    = null;
    TopicSession              jms_sess;
    TopicSubscriber           subscriber1;
    Topic                     shipped_orders;
    int                       myport = 5521;
    AQjmsAgent[]              recipList;
    /* create connection and session */
    tc_fact = AQjmsFactory.getTopicConnectionFactory(
              "MYHOSTNAME", "MYSID", myport, "oci8");
    t_conn = tc_fact.createTopicConnection("jmstopic", "jmstopic");
    jms_sess = t_conn.createTopicSession(true, Session.CLIENT_ACKNOWLEDGE);
    shipped_orders = ((AQjmsSession )jms_sess).getTopic(
              "OE", "Shipped_Orders_Topic");
    /* create a subscriber */
    /* with condition on JMSPriority and user property 'Region' */
    subscriber1 = jms_sess.createDurableSubscriber(
              shipped_orders, 'WesternShipping',
             "JMSPriority > 2 and Region like 'Western%'", false);

### Creating a DurableSubscriber for an Oracle Object Type Topic Without Selector

    public javax.jms.TopicSubscriber createDurableSubscriber(
                 javax.jms.Topic topic,
                 java.lang.String subs_name,
                 java.lang.Object payload_factory)
          throws JMSException

This method creates a durable subscriber for an Oracle [object type](glossary.md) topic without selector. It has the following parameters:

| Parameter         | Description                                                                             |
|:------------------|:----------------------------------------------------------------------------------------|
| `topic`           | Non-temporary topic to subscribe to                                                     |
| `subs_name`       | Name used to identify this subscription                                                 |
| `payload_factory` | `CustomDatumFactory` or `ORADataFactory` for the Java class that maps to the Oracle ADT |

**Note:**

- `CustomDatum` support will be deprecated in a future release. Use `ORADataFactory` payload factories instead.

- Sharded queues do not support object type messages.

**See Also:**

"Exclusive Access to Topics"

Example 14-13 Creating a Durable Subscriber for an Oracle Object Type Topic Without Selector

    /* Subscribe to an ADT queue */
    TopicConnectionFactory    tc_fact   = null;
    TopicConnection           t_conn    = null;
    TopicSession              t_sess    = null;
    TopicSession              jms_sess;
    TopicSubscriber           subscriber1;
    Topic                     shipped_orders;
    int                       my[port = 5521;
    AQjmsAgent[]              recipList;
    /* the java mapping of the oracle object type created by J Publisher */
    ADTMessage                message;
    /* create connection and session */
    tc_fact = AQjmsFactory.getTopicConnectionFactory(
              "MYHOSTNAME", "MYSID", myport, "oci8");
    t_conn = tc_fact.createTopicConnection("jmstopic", "jmstopic");
    jms_sess = t_conn.createTopicSession(true, Session.CLIENT_ACKNOWLEDGE);
    shipped_orders = ((AQjmsSession )jms_sess).getTopic(
              "OE", "Shipped_Orders_Topic");
    /* create a subscriber, specifying the correct CustomDatumFactory */
    subscriber1 = jms_sess.createDurableSubscriber(
              shipped_orders, 'WesternShipping', AQjmsAgent.getFactory());

### Creating a DurableSubscriber for an Oracle Object Type Topic with Selector

    public javax.jms.TopicSubscriber createDurableSubscriber(
                 javax.jms.Topic topic,
                 java.lang.String subs_name,
                 java.lang.String messageSelector,
                 boolean noLocal,
                 java.lang.Object payload_factory)
          throws JMSException

This method creates a durable subscriber for an Oracle object type topic with selector. It has the following parameters:

| Parameter         | Description                                                                                                                                                                                      |
|:------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `topic`           | Non-temporary topic to subscribe to                                                                                                                                                              |
| `subs_name`       | Name used to identify this subscription                                                                                                                                                          |
| `messageSelector` | Only messages with properties matching the `messageSelector` expression are delivered. A value of null or an empty string indicates that there is no `messageSelector` for the message consumer. |
| `noLocal`         | If set to true, then it inhibits the delivery of messages published by its own connection                                                                                                        |
| `payload_factory` | `CustomDatumFactory` or `ORADataFactory` for the Java class that maps to the Oracle ADT                                                                                                          |

**Note:**

- `CustomDatum` support will be deprecated in a future release. Use `ORADataFactory` payload factories instead.

- Sharded queues do not support object yype messages.

**See Also:**

"Exclusive Access to Topics"

Example 14-14 Creating a Durable Subscriber for an Oracle Object Type Topic With Selector

    TopicConnectionFactory    tc_fact   = null;
    TopicConnection           t_conn    = null;
    TopicSession              jms_sess;
    TopicSubscriber           subscriber1;
    Topic                     shipped_orders;
    int                       myport = 5521;
    AQjmsAgent[]              recipList;
    /* the java mapping of the oracle object type created by J Publisher */
    ADTMessage                message;
    /* create connection and session */
    tc_fact = AQjmsFactory.getTopicConnectionFactory(
              "MYHOSTNAME", "MYSID", myport, "oci8");
    t_conn = tc_fact.createTopicConnection("jmstopic", "jmstopic");
    jms_sess = t_conn.createTopicSession(true, Session.CLIENT_ACKNOWLEDGE);
    shipped_orders = ((AQjmsSession )jms_sess).getTopic(
              "OE", "Shipped_Orders_Topic");
    /* create a subscriber, specifying correct CustomDatumFactory and selector */
    subscriber1 = jms_sess.createDurableSubscriber(
              shipped_orders, "WesternShipping",
             "priority > 1 and tab.user_data.region like 'WESTERN %'", false,
              ADTMessage.getFactory());

### Specifying Transformations for Topic Subscribers

A transformation can be supplied when sending/publishing a message to a queue/topic. The transformation is applied before putting the message into the queue/topic.

The application can specify a transformation using the `setTransformation` interface in the `AQjmsQueueSender` and `AQjmsTopicPublisher` interfaces.

A transformation can also be specified when creating topic subscribers using the `CreateDurableSubscriber()` call. The transformation is applied to the retrieved message before returning it to the subscriber. If the subscriber specified in the `CreateDurableSubscriber()` call already exists, then its transformation is set to the specified transformation.

Example 14-15 Sending Messages to a Destination Using a Transformation

Suppose that the orders that are processed by the order entry application should be published to `WS_bookedorders_topic`. The transformation OE2WS (defined in the previous section) is supplied so that the messages are inserted into the topic in the correct format.

    public void ship_bookedorders(
       TopicSession jms_session,
        AQjmsADTMessage adt_message)
    {
        TopicPublisher  publisher;
        Topic           topic;

        try
        {
          /* get a handle to the WS_bookedorders_topic */
              topic = ((AQjmsSession)jms_session).getTopic("WS", "WS_bookedorders_topic");
          publisher = jms_session.createPublisher(topic);

          /* set the transformation in the publisher */
          ((AQjmsTopicPublisher)publisher).setTransformation("OE2WS");
          publisher.publish(topic, adt_message);
            }
            catch (JMSException ex)
            {
               System.out.println("Exception :" ex);
        }
    }

Example 14-16 Specifying Transformations for Topic Subscribers

The Western Shipping application subscribes to the OE_bookedorders_topic with the transformation `OE2WS`. This transformation is applied to the messages and the returned message is of Oracle object type `WS.WS_orders`.

Suppose that the WSOrder java class has been generated by Jpublisher to map to the Oracle object `WS.WS_order`:

    public AQjmsAdtMessage retrieve_bookedorders(TopicSession jms_session)
    {
        TopicSubscriber     subscriber;
        Topic               topic;
        AQjmsAdtMessage     msg = null;

        try
        {
          /* get a handle to the OE_bookedorders_topic */
          topic = ((AQjmsSession)jms_session).getTopic("OE", "OE_bookedorders_topic");

          /* create a subscriber with the transformation OE2WS */
          subs = ((AQjmsSession)jms_session).createDurableSubscriber(
             topic, 'WShip', null, false, WSOrder.getFactory(), "OE2WS");
          msg = subscriber.receive(10);
        }
        catch (JMSException ex)
        {
            System.out.println("Exception :" ex);
        }
        return (AQjmsAdtMessage)msg;
    }

### Creating a Remote Subscriber for JMS Messages

    public void createRemoteSubscriber(javax.jms.Topic topic,
                                       oracle.jms.AQjmsAgent remote_subscriber,
                                       java.lang.String messageSelector)
                                throws JMSException

This method creates a remote subscriber for topics of JMS messages. It has the following parameters:

| Parameter           | Description                                                                                                                                                                                      |
|:--------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `topic`             | Topic to subscribe to                                                                                                                                                                            |
| `remote_subscriber` | `AQjmsAgent` that refers to the remote subscriber                                                                                                                                                |
| `messageSelector`   | Only messages with properties matching the `messageSelector` expression are delivered. A value of null or an empty string indicates that there is no `messageSelector` for the message consumer. |

Oracle Database Advanced Queuing allows topics to have remote subscribers, for example, subscribers at other topics in the same or different database. In order to use remote subscribers, you must set up [propagation](glossary.md) between the local and remote topic.

Remote subscribers can be a specific consumer at the remote topic or all subscribers at the remote topic. A remote subscriber is defined using the `AQjmsAgent` structure. An `AQjmsAgent` consists of a name and address. The name refers to the `consumer_name` at the remote topic. The address refers to the remote topic. Its syntax is `schema.topic_name[@dblink]`.

To publish messages to a particular consumer at the remote topic, the `subscription_name` of the recipient at the remote topic must be specified in the name field of `AQjmsAgent`, and the remote topic must be specified in the address field. To publish messages to all subscribers of the remote topic, the name field of `AQjmsAgent` must be set to null.

**Note:**

Sharded queues do not support remote subscribers.

**See Also:**

"[MessageSelector](jms-introduction.md)"

Example 14-17 Creating a Remote Subscriber for Topics of JMS Messages

    TopicConnectionFactory    tc_fact   = null;
    TopicConnection           t_conn    = null;
    TopicSession              t_sess    = null;
    TopicSession              jms_sess;
    TopicSubscriber           subscriber1;
    Topic                     shipped_orders;
    int                       my[port = 5521;
    AQjmsAgent                remoteAgent;
    /* create connection and session */
    tc_fact = AQjmsFactory.getTopicConnectionFactory(
              "MYHOSTNAME", "MYSID", myport, "oci8");
    t_conn = tc_fact.createTopicConnection("jmstopic", "jmstopic");
    jms_sess = t_conn.createTopicSession(true, Session.CLIENT_ACKNOWLEDGE);
    shipped_orders = ((AQjmsSession )jms_sess).getTopic(
              "OE", "Shipped_Orders_Topic");
    remoteAgent = new AQjmsAgent("WesternRegion", "WS.shipped_orders_topic", null);
    /* create a remote subscriber (selector is null )*/
    subscriber1 = ((AQjmsSession)jms_sess).createRemoteSubscriber(
              shipped_orders, remoteAgent, null);

### Creating a Remote Subscriber for Oracle Object Type Messages

    public void createRemoteSubscriber(javax.jms.Topic topic,
                                       oracle.jms.AQjmsAgent remote_subscriber,
                                       java.lang.String messageSelector,
                                       java.lang.Object payload_factory)
                                throws JMSException

This method creates a remote subscriber for topics of Oracle object type messages. It has the following parameters:

| Parameter           | Description                                                                                                                                                                                      |
|:--------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `topic`             | Topic to subscribe to                                                                                                                                                                            |
| `remote_subscriber` | `AQjmsAgent` that refers to the remote subscriber                                                                                                                                                |
| `messageSelector`   | Only messages with properties matching the `messageSelector` expression are delivered. A value of null or an empty string indicates that there is no `messageSelector` for the message consumer. |
| `payload_factory`   | `CustomDatumFactory` or `ORADataFactory` for the Java class that maps to the Oracle ADT                                                                                                          |

**Note:**

- `CustomDatum` support will be deprecated in a future release. Use `ORADataFactory` payload factories instead.

- Sharded queues do not support remote subscribers or object type messages.

Oracle Database Advanced Queuing allows topics to have remote subscribers, for example, subscribers at other topics in the same or different database. In order to use remote subscribers, you must set up [propagation](glossary.md) between the local and remote topic.

Remote subscribers can be a specific consumer at the remote topic or all subscribers at the remote topic. A remote subscriber is defined using the `AQjmsAgent` structure. An `AQjmsAgent` consists of a name and address. The name refers to the `consumer_name` at the remote topic. The address refers to the remote topic. Its syntax is `schema.topic_name[@dblink]`.

To publish messages to a particular consumer at the remote topic, the `subscription_name` of the recipient at the remote topic must be specified in the name field of `AQjmsAgent`, and the remote topic must be specified in the address field. To publish messages to all subscribers of the remote topic, the name field of `AQjmsAgent` must be set to null.

**Note:**

AQ does not support the use of multiple dblink to the same destination. As a workaround, use a single database link for each destination.

**See Also:**

"[MessageSelector](jms-introduction.md)"

Example 14-18 Creating a Remote Subscriber for Topics of Oracle Object Type Messages

    TopicConnectionFactory    tc_fact   = null;
    TopicConnection           t_conn    = null;
    TopicSession              t_sess    = null;
    TopicSession              jms_sess;
    TopicSubscriber           subscriber1;
    Topic                     shipped_orders;
    int                       my[port = 5521;
    AQjmsAgent                remoteAgent;
    ADTMessage                message;
    /* create connection and session */
    tc_fact = AQjmsFactory.getTopicConnectionFactory(
              "MYHOSTNAME", "MYSID", myport, "oci8");
    t_conn = tc_fact.createTopicConnection("jmstopic", "jmstopic");
    /* create TopicSession */
    jms_sess = t_conn.createTopicSession(true, Session.CLIENT_ACKNOWLEDGE);
    /* get the Shipped order topic */
    shipped_orders = ((AQjmsSession )jms_sess).getTopic(
              "OE", "Shipped_Orders_Topic");
    /* create a remote agent */
    remoteAgent = new AQjmsAgent("WesternRegion", "WS.shipped_orders_topic", null);
    /* create a remote subscriber  with null selector*/
    subscriber1 = ((AQjmsSession)jms_sess).createRemoteSubscriber(
              shipped_orders, remoteAgent, null, message.getFactory);

### Specifying Transformations for Remote Subscribers

Oracle Database Advanced Queuing allows a remote subscriber, that is a subscriber at another database, to subscribe to a topic.

Transformations can be specified when creating remote subscribers using the `createRemoteSubscriber()` call. This enables propagation of messages between topics of different formats. When a message published at a topic meets the criterion of a remote subscriber, Oracle Database Advanced Queuing automatically propagates the message to the queue/topic at the remote database specified for the remote subscriber. If a transformation is also specified, then Oracle Database Advanced Queuing applies the transformation to the message before propagating it to the queue/topic at the remote database.

**Note:**

Sharded queues do not support remote subscribers.

Example 14-19 Specifying Transformations for Remote Subscribers

A remote subscriber is created at the OE.OE_bookedorders_topic so that messages are automatically propagated to the WS.WS_bookedorders_topic. The transformation OE2WS is specified when creating the remote subscriber so that the messages reaching the WS_bookedorders_topic have the correct format.

Suppose that the WSOrder java class has been generated by Jpublisher to map to the Oracle object `WS.WS_order`

    public void create_remote_sub(TopicSession jms_session)
    {
       AQjmsAgent          subscriber;
       Topic               topic;

       try
       {
         /* get a handle to the OE_bookedorders_topic */
         topic = ((AQjmsSession)jms_session).getTopic("OE", "OE_bookedorders_topic");
         subscriber = new AQjmsAgent("WShip", "WS.WS_bookedorders_topic");

         ((AQjmsSession )jms_session).createRemoteSubscriber(
            topic, subscriber, null, WSOrder.getFactory(),"OE2WS");
       }
       catch (JMSException ex)
       {
         System.out.println("Exception :" ex);
       }
    }

### Unsubscribing a Durable Subscription for a Local Subscriber

    public void unsubscribe(javax.jms.Topic topic,
                            java.lang.String subs_name)
                     throws JMSException

This method unsubscribes a durable subscription for a local subscriber. It has the following parameters:

| Parameter   | Description                             |
|:------------|:----------------------------------------|
| `topic`     | Non-temporary topic to unsubscribe      |
| `subs_name` | Name used to identify this subscription |

**See Also:**

"Exclusive Access to Topics"

Example 14-20 Unsubscribing a Durable Subscription for a Local Subscriber

    TopicConnectionFactory    tc_fact   = null;
    TopicConnection           t_conn    = null;
    TopicSession              jms_sess;
    TopicSubscriber           subscriber1;
    Topic                     shipped_orders;
    int                       myport = 5521;
    AQjmsAgent[]              recipList;
    /* create connection and session */
    tc_fact = AQjmsFactory.getTopicConnectionFactory(
              "MYHOSTNAME", "MYSID", myport, "oci8");
    t_conn = tc_fact.createTopicConnection("jmstopic", "jmstopic");
    jms_sess = t_conn.createTopicSession(true, Session.CLIENT_ACKNOWLEDGE);
    shipped_orders = ((AQjmsSession )jms_sess).getTopic(
              "OE", "Shipped_Orders_Topic");
    /* unsusbcribe "WesternShipping" from shipped_orders */
    jms_sess.unsubscribe(shipped_orders, "WesternShipping");

### Unsubscribing a Durable Subscription for a Remote Subscriber

    public void unsubscribe(javax.jms.Topic topic,
                            oracle.jms.AQjmsAgent remote_subscriber)
                     throws JMSException

This method unsubscribes a durable subscription for a remote subscriber. It has the following parameters:

| Parameter           | Description                                                                                              |
|:--------------------|:---------------------------------------------------------------------------------------------------------|
| `topic`             | Non-temporary topic to unsubscribe                                                                       |
| `remote_subscriber` | `AQjmsAgent` that refers to the remote subscriber. The address field of the `AQjmsAgent` cannot be null. |

**Note:**

Sharded queues do not support remote subscribers.

**See Also:**

"Exclusive Access to Topics"

Example 14-21 Unsubscribing a Durable Subscription for a Remote Subscriber

    TopicConnectionFactory    tc_fact   = null;
    TopicConnection           t_conn    = null;
    TopicSession              t_sess    = null;
    TopicSession              jms_sess;
    Topic                     shipped_orders;
    int                       myport = 5521;
    AQjmsAgent                remoteAgent;
    /* create connection and session */
    tc_fact = AQjmsFactory.getTopicConnectionFactory(
              "MYHOSTNAME", "MYSID", myport, "oci8");
    t_conn = tc_fact.createTopicConnection("jmstopic", "jmstopic");
    jms_sess = t_conn.createTopicSession(true, Session.CLIENT_ACKNOWLEDGE);
    shipped_orders = ((AQjmsSession )jms_sess).getTopic(
              "OE", "Shipped_Orders_Topic");
    remoteAgent = new AQjmsAgent("WS", "WS.Shipped_Orders_Topic", null);
    /* unsubscribe the remote agent from shipped_orders */
    ((AQjmsSession)jms_sess).unsubscribe(shipped_orders, remoteAgent);

### Creating a TopicReceiver for a Topic of Standard JMS Type Messages

    public oracle.jms.AQjmsTopicReceiver createTopicReceiver(
                  javax.jms.Topic topic,
                  java.lang.String receiver_name,
                  java.lang.String messageSelector)
           throws JMSException

This method creates a `TopicReceiver` for a topic of standard JMS type messages. It has the following parameters:

| Parameter         | Description                                                                                                                                                                                      |
|:------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `topic`           | Topic to access                                                                                                                                                                                  |
| `receiver_name`   | Name of message receiver                                                                                                                                                                         |
| `messageSelector` | Only messages with properties matching the `messageSelector` expression are delivered. A value of null or an empty string indicates that there is no `messageSelector` for the message consumer. |

Oracle Database Advanced Queuing allows messages to be sent to specified recipients. These receivers may or may not be subscribers of the topic. If the receiver is not a subscriber to the topic, then it receives only those messages that are explicitly addressed to it. This method must be used order to create a `TopicReceiver` object for consumers that are not durable subscribers.

**See Also:**

"[MessageSelector](jms-introduction.md)"

Example 14-22 Creating a TopicReceiver for Standard JMS Type Messages

    TopicConnectionFactory    tc_fact   = null;
    TopicConnection           t_conn    = null;
    TopicSession              t_sess    = ull;
    TopicSession              jms_sess;
    Topic                     shipped_orders;
    int                       myport = 5521;
    TopicReceiver             receiver;
    /* create connection and session */
    tc_fact = AQjmsFactory.getTopicConnectionFactory(
              "MYHOSTNAME", "MYSID", myport, "oci8");
    t_conn = tc_fact.createTopicConnection("jmstopic", "jmstopic");
    jms_sess = t_conn.createTopicSession(true, Session.CLIENT_ACKNOWLEDGE);
    shipped_orders = ((AQjmsSession )jms_sess).getTopic(
              "WS", "Shipped_Orders_Topic");
    receiver = ((AQjmsSession)jms_sess).createTopicReceiver(
              shipped_orders, "WesternRegion", null);

### Creating a TopicReceiver for a Topic of Oracle Object Type Messages

    public oracle.jms.AQjmsTopicReceiver createTopicReceiver(
                  javax.jms.Topic topic,
                  java.lang.String receiver_name,
                  java.lang.String messageSelector,
                  java.lang.Object payload_factory)
           throws JMSException

This method creates a `TopicReceiver` for a topic of Oracle object type messages with selector. It has the following parameters:

| Parameter         | Description                                                                                                                                                                                      |
|:------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `topic`           | Topic to access                                                                                                                                                                                  |
| `receiver_name`   | Name of message receiver                                                                                                                                                                         |
| `messageSelector` | Only messages with properties matching the `messageSelector` expression are delivered. A value of null or an empty string indicates that there is no `messageSelector` for the message consumer. |
| `payload_factory` | `CustomDatumFactory` or `ORADataFactory` for the Java class that maps to the Oracle ADT                                                                                                          |

**Note:**

- `CustomDatum` support will be deprecated in a future release. Use `ORADataFactory` payload factories instead.

- Sharded queues do not support object type messages.

Oracle Database Advanced Queuing allows messages to be sent to all subscribers of a topic or to specified recipients. These receivers may or may not be subscribers of the topic. If the receiver is not a subscriber to the topic, then it receives only those messages that are explicitly addressed to it. This method must be used order to create a `TopicReceiver` object for consumers that are not durable subscribers.

**See Also:**

"[MessageSelector](jms-introduction.md)"

Example 14-23 Creating a TopicReceiver for Oracle Object Type Messages

    TopicConnectionFactory    tc_fact   = null;
    TopicConnection           t_conn    = null;
    TopicSession              t_sess    = null;
    TopicSession              jms_sess;
    Topic                     shipped_orders;
    int                       myport = 5521;
    TopicReceiver             receiver;
    /* create connection and session */
    tc_fact = AQjmsFactory.getTopicConnectionFactory(
              "MYHOSTNAME", "MYSID", myport, "oci8");
    t_conn = tc_fact.createTopicConnection("jmstopic", "jmstopic");
    jms_sess = t_conn.createTopicSession(true, Session.CLIENT_ACKNOWLEDGE);
    shipped_orders = ((AQjmsSession )jms_sess).getTopic(
              "WS", "Shipped_Orders_Topic");
    receiver = ((AQjmsSession)jms_sess).createTopicReceiver(
              shipped_orders, "WesternRegion", null);

### Creating a TopicBrowser for Standard JMS Messages

    public oracle.jms.TopicBrowser createBrowser(javax.jms.Topic topic,
                                                 java.lang.String cons_name,
                                                 java.lang.String messageSelector)
                                          throws JMSException

This method creates a `TopicBrowser` for topics with `TextMessage`, `StreamMessage`, `ObjectMessage`, `BytesMessage`, or `MapMessage` message bodies. It has the following parameters:

| Parameter         | Description                                                                                                                                                                                      |
|:------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `topic`           | Topic to access                                                                                                                                                                                  |
| `cons_name`       | Name of the durable subscriber or consumer                                                                                                                                                       |
| `messageSelector` | Only messages with properties matching the `messageSelector` expression are delivered. A value of null or an empty string indicates that there is no `messageSelector` for the message consumer. |
| `payload_factory` | `CustomDatumFactory` or `ORADataFactory` for the Java class that maps to the Oracle ADT                                                                                                          |

**See Also:**

"[MessageSelector](jms-introduction.md)"

Example 14-24 Creating a TopicBrowser Without a Selector

    /* Create a browser without a selector */
    TopicSession    jms_session;
    TopicBrowser    browser;
    Topic           topic;
    browser = ((AQjmsSession) jms_session).createBrowser(topic, "SUBS1");

Example 14-25 Creating a TopicBrowser With a Specified Selector

    /* Create a browser for topics with a specified selector */
    TopicSession    jms_session;
    TopicBrowser    browser;
    Topic           topic;
    /* create a Browser to look at messages with correlationID = RUSH  */
    browser = ((AQjmsSession) jms_session).createBrowser(
              topic, "SUBS1", "JMSCorrelationID = 'RUSH'");

### Creating a TopicBrowser for Standard JMS Messages, Locking Messages

    public oracle.jms.TopicBrowser createBrowser(javax.jms.Topic topic,
                                                 java.lang.String cons_name,
                                                 java.lang.String messageSelector,
                                                 boolean locked)
                                          throws JMSException

This method creates a `TopicBrowser` for topics with text, stream, objects, bytes or map messages, locking messages while browsing. It has the following parameters:

| Parameter         | Description                                                                                                                                                                                      |
|:------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `topic`           | Topic to access                                                                                                                                                                                  |
| `cons_name`       | Name of the durable subscriber or consumer                                                                                                                                                       |
| `messageSelector` | Only messages with properties matching the `messageSelector` expression are delivered. A value of null or an empty string indicates that there is no `messageSelector` for the message consumer. |
| `locked`          | If set to true, then messages are locked as they are browsed (similar to a SELECT for UPDATE)                                                                                                    |

Example 14-26 Creating a TopicBrowser Without a Selector, Locking Messages While Browsing

    /* Create a browser without a selector */
    TopicSession    jms_session;
    TopicBrowser    browser;
    Topic           topic;
    browser = ((AQjmsSession) jms_session).createBrowser(
              topic, "SUBS1", true);

Example 14-27 Creating a TopicBrowser With a Specified Selector, Locking Messages

    /* Create a browser for topics with a specified selector */
    TopicSession    jms_session;
    TopicBrowser    browser;
    Topic           topic;
    /* create a Browser to look at messages with correlationID = RUSH in
    lock mode */
    browser = ((AQjmsSession) jms_session).createBrowser(
              topic, "SUBS1", "JMSCorrelationID = 'RUSH'", true);

### Creating a TopicBrowser for Oracle Object Type Messages

    public oracle.jms.TopicBrowser createBrowser(javax.jms.Topic topic,
                                                 java.lang.String cons_name,
                                                 java.lang.String messageSelector,
                                                 java.lang.Object payload_factory)
                                          throws JMSException

This method creates a `TopicBrowser` for topics of Oracle object type messages. It has the following parameters:

| Parameter         | Description                                                                                                                                                                                      |
|:------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `topic`           | Topic to access                                                                                                                                                                                  |
| `cons_name`       | Name of the durable subscriber or consumer                                                                                                                                                       |
| `messageSelector` | Only messages with properties matching the `messageSelector` expression are delivered. A value of null or an empty string indicates that there is no `messageSelector` for the message consumer. |
| `payload_factory` | `CustomDatumFactory` or `ORADataFactory` for the Java class that maps to the Oracle ADT                                                                                                          |

**Note:**

- `CustomDatum` support will be deprecated in a future release. Use `ORADataFactory` payload factories instead.

- Sharded queues do not support object type messages.

The `CustomDatumFactory` for a particular Java class that maps to the SQL object type payload can be obtained using the `getFactory` static method. Assume the topic` test_topic` has payload of type `SCOTT.EMPLOYEE` and the Java class that is generated by Jpublisher for this Oracle object type is called `Employee`. The Employee class implements the `CustomDatum` interface. The `CustomDatumFactory` for this class can be obtained by using the `Employee.getFactory()` method.

**See Also:**

"[MessageSelector](jms-introduction.md)"

Example 14-28 Creating a TopicBrowser for AdtMessage Messages

    /* Create a browser for a Topic with AdtMessage messages of type EMPLOYEE*/
    TopicSession jms_session
    TopicBrowser browser;
    Topic        test_topic;
    browser = ((AQjmsSession) jms_session).createBrowser(
              test_topic, "SUBS1", Employee.getFactory());

### Creating a TopicBrowser for Oracle Object Type Messages, Locking Messages

    public oracle.jms.TopicBrowser createBrowser(javax.jms.Topic topic,
                                                 java.lang.String cons_name,
                                                 java.lang.String messageSelector,
                                                 java.lang.Object payload_factory,
                                                 boolean locked)
                                          throws JMSException

This method creates a `TopicBrowser` for topics of Oracle object type messages, locking messages while browsing. It has the following parameters:

| Parameter         | Description                                                                                                                                                                                      |
|:------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `topic`           | Topic to access                                                                                                                                                                                  |
| `cons_name`       | Name of the durable subscriber or consumer                                                                                                                                                       |
| `messageSelector` | Only messages with properties matching the `messageSelector` expression are delivered. A value of null or an empty string indicates that there is no `messageSelector` for the message consumer. |
| `payload_factory` | `CustomDatumFactory` or `ORADataFactory` for the Java class that maps to the Oracle ADT                                                                                                          |
| `locked`          | If set to true, then messages are locked as they are browsed (similar to a SELECT for UPDATE)                                                                                                    |

**Note:**

- `CustomDatum` support will be deprecated in a future release. Use `ORADataFactory` payload factories instead.

- Sharded queues do not support object type messages.

**See Also:**

"[MessageSelector](jms-introduction.md)"

Example 14-29 Creating a TopicBrowser for AdtMessage Messages, Locking Messages

    /* Create a browser for a Topic with AdtMessage messages of type EMPLOYEE* in
    lock mode/
    TopicSession jms_session
    TopicBrowser browser;
    Topic        test_topic;
    browser = ((AQjmsSession) jms_session).createBrowser(
              test_topic, "SUBS1", Employee.getFactory(), true);

### Browsing Messages Using a TopicBrowser

    public void purgeSeen()
                   throws JMSException

This method browses messages using a `TopicBrowser`. Use methods in `java.util.Enumeration` to go through the list of messages. Use the method `purgeSeen` in `TopicBrowser` to purge messages that have been seen during the current browse.

Example 14-30 Creating a TopicBrowser with a Specified Selector

    /* Create a browser for topics with a specified selector */
    public void browse_rush_orders(TopicSession jms_session)
    TopicBrowser    browser;
    Topic           topic;
    ObjectMessage   obj_message
    BolOrder        new_order;
    Enumeration     messages;
    /* get a handle to the new_orders topic */
    topic = ((AQjmsSession) jms_session).getTopic("OE", "OE_bookedorders_topic");
    /* create a Browser to look at RUSH orders */
    browser = ((AQjmsSession) jms_session).createBrowser(
              topic, "SUBS1", "JMSCorrelationID = 'RUSH'");
    /* Browse through the messages */
    for (messages = browser.elements() ; message.hasMoreElements() ;)
    {obj_message = (ObjectMessage)message.nextElement();}
    /* Purge messages seen during this browse */
    browser.purgeSeen()
