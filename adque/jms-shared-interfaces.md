The following topics describe the [Java Message Service](glossary.md) (JMS) operational interface (shared interfaces) to Oracle Database Advanced Queuing (AQ).

- Oracle Database Advanced Queuing JMS Operational Interface: Shared Interfaces

- Specifying JMS Message Properties

- Setting Default TimeToLive for All Messages Sent by a MessageProducer

- Setting Default Priority for All Messages Sent by a MessageProducer

- Creating an AQjms Agent

- Receiving a Message Synchronously

- Specifying the Navigation Mode for Receiving Messages

- Receiving a Message Asynchronously

- Getting Message ID

- Getting JMS Message Properties

- Closing and Shutting Down

- Troubleshooting

### Oracle Database Advanced Queuing JMS Operational Interface: Shared Interfaces

The following topics discuss Oracle Database Advanced Queuing shared interfaces for JMS operations.

- Starting a JMS Connection

- Getting a JMS Connection

- Committing All Operations in a Session

- Rolling Back All Operations in a Session

- Getting the JDBC Connection from a Session

- Getting the OracleOCIConnectionPool from a JMS Connection

- Creating a BytesMessage

- Creating a MapMessage

- Creating a StreamMessage

- Creating an ObjectMessage

- Creating a TextMessage

- Creating a JMS Message

- Creating an AdtMessage

- Setting a JMS Correlation Identifier

#### Starting a JMS Connection

    public void start()
              throws JMSException

`AQjmsConnection.start()` starts a [JMS connection](glossary.md) for receiving messages.

#### Getting a JMS Connection

    public oracle.jms.AQjmsConnection getJmsConnection()
                                                throws JMSException

`AQjmsSession.getJmsConnection()` gets a JMS connection from a session.

#### Committing All Operations in a Session

    public void commit()
               throws JMSException

`AQjmsSession.commit()` commits all JMS and SQL operations performed in a session.

#### Rolling Back All Operations in a Session

    public void rollback()
                  throws JMSException

`AQjmsSession.rollback()` terminates all JMS and SQL operations performed in a session.

#### Getting the JDBC Connection from a Session

    public java.sql.Connection getDBConnection()
                                        throws JMSException

`AQjmsSession.getDBConnection()` gets the underlying JDBC connection from a [JMS session](glossary.md). The JDBC connection can be used to perform SQL operations as part of the same transaction in which the JMS operations are accomplished.

Example 15-1 Getting Underlying JDBC Connection from JMS Session

    java.sql.Connection db_conn;
    QueueSession     jms_sess;
    db_conn = ((AQjmsSession)jms_sess).getDBConnection();

#### Getting the OracleOCIConnectionPool from a JMS Connection

    public oracle.jdbc.pool.OracleOCIConnectionPool getOCIConnectionPool()

`AQjmsConnection.getOCIConnectionPool()` gets the underlying `OracleOCIConnectionPool` from a JMS connection. The settings of the `OracleOCIConnectionPool` instance can be tuned by the user depending on the connection usage, for example, the number of sessions the user wants to create using the given connection. The user should not, however, close the `OracleOCIConnectionPool` instance being used by the JMS connection.

Example 15-2 Getting Underlying OracleOCIConnectionPool from JMS Connection

    oracle.jdbc.pool.OracleOCIConnectionPool cpool;
    QueueConnection jms_conn;
    cpool = ((AQjmsConnection)jms_conn).getOCIConnectionPool();

#### Creating a BytesMessage

    public javax.jms.BytesMessage createBytesMessage()
                                              throws JMSException

`AQjmsSession.createBytesMessage()` creates a bytes [message](glossary.md). It can be used only if the [queue table](glossary.md) that contains the destination [queue](glossary.md)/topic was created with the `SYS.AQ$_JMS_BYTES_MESSAGE` or `AQ$_JMS_MESSAGE` payload types.

#### Creating a MapMessage

    public javax.jms.MapMessage createMapMessage()
                                          throws JMSException

`AQjmsSession.createMapMessage()` creates a map message. It can be used only if the queue table that contains the destination queue/topic was created with the `SYS.AQ$_JMS_MAP_MESSAGE` or `AQ$_JMS_MESSAGE` payload types.

#### Creating a StreamMessage

    public javax.jms.StreamMessage createStreamMessage()
                                                throws JMSException

`AQjmsSession.createStreamMessage()` creates a stream message. It can be used only if the queue table that contains the destination queue/topic was created with the `SYS.AQ$_JMS_STREAM_MESSAGE` or `AQ$_JMS_MESSAGE` payload types.

#### Creating an ObjectMessage

    public javax.jms.ObjectMessage createObjectMessage(java.io.Serializable object)
                                                throws JMSException

`AQjmsSession.createObjectMessage()` creates an object message. It can be used only if the queue table that contains the destination queue/topic was created with the `SYS.AQ$_JMS_OBJECT_MESSAGE` or `AQ$_JMS_MESSAGE` payload types.

#### Creating a TextMessage

    public javax.jms.TextMessage createTextMessage()
                                            throws JMSException

`AQjmsSession.createTextMessage()` creates a text message. It can be used only if the queue table that contains the destination queue/topic was created with the `SYS.AQ$_JMS_TEXT_MESSAGE` or `AQ$_JMS_MESSAGE` payload types.

#### Creating a JMS Message

    public javax.jms.Message createMessage()
                                    throws JMSException

`AQjmsSession.createMessage()` creates a [JMS message](glossary.md). You can use the `AQ$_JMS_MESSAGE` construct message to construct messages of different types. The message type must be one of the following:

- `DBMS_AQ.JMS_TEXT_MESSAGE`

- `DBMS_AQ.JMS_OBJECT_MESSAGE`

- `DBMS_AQ.JMS_MAP_MESSAGE`

- `DBMS_AQ.JMS_BYTES_MESSAGE`

- `DBMS_AQ.JMS_STREAM_MESSAGE`

You can also use this ADT to create a header-only JMS message.

#### Creating an AdtMessage

    public oracle.jms.AdtMessage createAdtMessage()
                                           throws JMSException

`AQjmsSession.createAdtMessage()` creates an `AdtMessage`. It can be used only if the queue table that contains the queue/topic was created with an Oracle ADT payload type. An `AdtMessage` must be populated with an object that implements the `CustomDatum` interface. This object must be the Java mapping of the SQL ADT defined as the payload for the queue/topic. Java classes corresponding to SQL ADT types can be generated using the Jpublisher tool.

#### Setting a JMS Correlation Identifier

    public void setJMSCorrelationID(java.lang.String correlationID)
                             throws JMSException

`AQjmsMessage.setJMSCorrelationID()` specifies the message correlation identifier.

### Specifying JMS Message Properties

Property names starting with JMS are provider-specific. User-defined properties cannot start with JMS.

The following provider properties can be set by clients using text, stream, object, bytes or map messages:

- `JMSXAppID (string)`

- `JMSXGroupID (string)`

- `JMSXGroupSeq (int)`

- `JMS_OracleExcpQ (string) `

  This message property specifies the [exception queue](glossary.md).

- `JMS_OracleDelay (int)`

  This message property specifies the message delay in seconds.

The following properties can be set on `AdtMessage`

- `JMS_OracleExcpQ (String)`

  This message property specifies the exception queue as "`schema``.queue_name`"

- `JMS_OracleDelay (int)`

  This message property specifies the message delay in seconds.

This section contains these topics:

- Setting a Boolean Message Property

- Setting a String Message Property

- Setting an Integer Message Property

- Setting a Double Message Property

- Setting a Float Message Property

- Setting a Byte Message Property

- Setting a Long Message Property

- Setting a Short Message Property

- Getting an Object Message Property

#### Setting a Boolean Message Property

    public void setBooleanProperty(java.lang.String name,
                                   boolean value)
                            throws JMSException

`AQjmsMessage.setBooleanProperty()` specifies a message property as Boolean. It has the following parameters:

| Parameter | Description                                  |
|:----------|:---------------------------------------------|
| `name`    | Name of the Boolean property                 |
| `value`   | Boolean property value to set in the message |

#### Setting a String Message Property

    public void setStringProperty(java.lang.String name,
                                  java.lang.String value)
                           throws JMSException

`AQjmsMessage.setStringProperty()` specifies a message property as string. It has the following parameters:

| Parameter | Description                                 |
|:----------|:--------------------------------------------|
| `name`    | Name of the string property                 |
| `value`   | String property value to set in the message |

#### Setting an Integer Message Property

    public void setIntProperty(java.lang.String name,
                               int value)
                        throws JMSException

`AQjmsMessage.setIntProperty()` specifies a message property as integer. It has the following parameters:

| Parameter | Description                                  |
|:----------|:---------------------------------------------|
| `name`    | Name of the integer property                 |
| `value`   | Integer property value to set in the message |

#### Setting a Double Message Property

    public void setDoubleProperty(java.lang.String name,
                                  double value)
                           throws JMSException

`AQjmsMessage.setDoubleProperty()` specifies a message property as double. It has the following parameters:

| Parameter | Description                                 |
|:----------|:--------------------------------------------|
| `name`    | Name of the double property                 |
| `value`   | Double property value to set in the message |

#### Setting a Float Message Property

    public void setFloatProperty(java.lang.String name,
                                 float value)
                          throws JMSException

`AQjmsMessage.setFloatProperty()` specifies a message property as float. It has the following parameters:

| Parameter | Description                                |
|:----------|:-------------------------------------------|
| `name`    | Name of the float property                 |
| `value`   | Float property value to set in the message |

#### Setting a Byte Message Property

    public void setByteProperty(java.lang.String name,
                                byte value)
                         throws JMSException

`AQjmsMessage.setByteProperty()` specifies a message property as byte. It has the following parameters:

| Parameter | Description                               |
|:----------|:------------------------------------------|
| `name`    | Name of the byte property                 |
| `value`   | Byte property value to set in the message |

#### Setting a Long Message Property

    public void setLongProperty(java.lang.String name,
                                long value)
                         throws JMSException

`AQjmsMessage.setLongProperty()` specifies a message property as long. It has the following parameters:

| Parameter | Description                               |
|:----------|:------------------------------------------|
| `name`    | Name of the long property                 |
| `value`   | Long property value to set in the message |

#### Setting a Short Message Property

    public void setShortProperty(java.lang.String name,
                                 short value)
                          throws JMSException

`AQjmsMessage.setShortProperty()` specifies a message property as short. It has the following parameters:

| Parameter | Description                                |
|:----------|:-------------------------------------------|
| `name`    | Name of the short property                 |
| `value`   | Short property value to set in the message |

#### Setting an Object Message Property

    public void setObjectProperty(java.lang.String name,
                                  java.lang.Object value)
                           throws JMSException

`AQjmsMessage.setObjectProperty()` specifies a message property as object. Only objectified primitive values are supported: Boolean, byte, short, integer, long, float, double and string. It has the following parameters:

| Parameter | Description                                      |
|:----------|:-------------------------------------------------|
| `name`    | Name of the Java object property                 |
| `value`   | Java object property value to set in the message |

### Setting Default TimeToLive for All Messages Sent by a MessageProducer

    public void setTimeToLive(long timeToLive)
                       throws JMSException

This method sets the default `TimeToLive` for all messages sent by a `MessageProducer`. It is calculated after message delay has taken effect. This method has the following parameter:

| Parameter    | Description                                              |
|:-------------|:---------------------------------------------------------|
| `timeToLive` | Message time to live in milliseconds (zero is unlimited) |

Example 15-3 Setting Default TimeToLive for All Messages Sent by a MessageProducer

    /* Set default timeToLive value to 100000 milliseconds for all messages sent by the QueueSender*/
    QueueSender sender;
    sender.setTimeToLive(100000);

### Setting Default Priority for All Messages Sent by a MessageProducer

    public void setPriority(int priority)
                     throws JMSException

This method sets the default `Priority` for all messages sent by a `MessageProducer`. It has the following parameter:

| Parameter  | Description                                                   |
|:-----------|:--------------------------------------------------------------|
| `priority` | Message priority for this message producer. The default is 4. |

Priority values can be any integer. A smaller number indicates higher priority. If a priority value is explicitly specified during a `send()` operation, then it overrides the default value set by this method.

Example 15-4 Setting Default Priority Value for All Messages Sent by QueueSender

    /* Set default priority value to 2 for all messages sent by the QueueSender*/
    QueueSender sender;
    sender.setPriority(2);

Example 15-5 Setting Default Priority Value for All Messages Sent by TopicPublisher

    /* Set default priority value to 2 for all messages sent by the TopicPublisher*/
    TopicPublisher publisher;
    publisher.setPriority(1);

### Creating an AQjms Agent

    public void createAQAgent(java.lang.String agent_name,
                              boolean enable_http,
                       throws JMSException

This method creates an `AQjmsAgent`. It has the following parameters:

| Parameter     | Description                                                          |
|:--------------|:---------------------------------------------------------------------|
| `agent_name`  | Name of the AQ agent                                                 |
| `enable_http` | If set to true, then this agent is allowed to access AQ through HTTP |

### Receiving a Message Synchronously

You can receive a message synchronously by specifying Timeout or without waiting. You can also receive a message using a transformation:

- Using a Message Consumer by Specifying Timeout

- Using a Message Consumer Without Waiting

- Receiving Messages from a Destination Using a Transformation

#### Using a Message Consumer by Specifying Timeout

    public javax.jms.Message receive(long timeout)
                              throws JMSException

This method receives a message using a message [consumer](glossary.md) by specifying timeout.

| Parameter | Description                   |
|:----------|:------------------------------|
| `timeout` | Timeout value in milliseconds |

Example 15-6 Using a Message Consumer by Specifying Timeout

    TopicConnectionFactory    tc_fact   = null;
    TopicConnection           t_conn    = null;
    TopicSession              t_sess    = null;
    TopicSession              jms_sess;
    Topic                     shipped_orders;
    int                       myport = 5521;

    /* create connection and session */
    tc_fact = AQjmsFactory.getTopicConnectionFactory(
       "MYHOSTNAME", "MYSID", myport, "oci8");
    t_conn = tc_fact.createTopicConnection("jmstopic", "jmstopic");
    jms_sess = t_conn.createTopicSession(true, Session.CLIENT_ACKNOWLEDGE);
    shipped_orders = ((AQjmsSession )jms_sess).getTopic(
       "WS", "Shipped_Orders_Topic");

    /* create a subscriber, specifying the correct CustomDatumFactory  and
    selector */
    subscriber1 = jms_sess.createDurableSubscriber(
       shipped_orders, 'WesternShipping',
       " priority > 1 and tab.user_data.region like 'WESTERN %'",
       false, AQjmsAgent.getFactory());
    /* receive, blocking for 30 seconds if there were no messages */
    Message = subscriber.receive(30000);

Example 15-7 JMS: Blocking Until a Message Arrives

    public BolOrder get_new_order1(QueueSession jms_session)
     {
       Queue            queue;
       QueueReceiver    qrec;
       ObjectMessage    obj_message;
       BolCustomer      customer;
       BolOrder         new_order = null;
       String           state;

       try
       {
       /* get a handle to the new_orders queue */
        queue = ((AQjmsSession) jms_session).getQueue("OE", "OE_neworders_que");
        qrec = jms_session.createReceiver(queue);

        /* wait for a message to show up in the queue */
        obj_message = (ObjectMessage)qrec.receive();
        new_order = (BolOrder)obj_message.getObject();
        customer = new_order.getCustomer();
        state    = customer.getState();
        System.out.println("Order:  for customer " + customer.getName());
       }
      catch (JMSException ex)
       {
         System.out.println("Exception: " + ex);
       }
       return new_order;
     }

#### Using a Message Consumer Without Waiting

    public javax.jms.Message receiveNoWait()
                                    throws JMSException

This method receives a message using a message consumer without waiting.

Example 15-8 JMS: Nonblocking Messages

    public BolOrder poll_new_order3(QueueSession jms_session)
     {
       Queue            queue;
       QueueReceiver    qrec;
       ObjectMessage    obj_message;
       BolCustomer      customer;
       BolOrder         new_order = null;
       String           state;

       try
       {
        /* get a handle to the new_orders queue */
        queue = ((AQjmsSession) jms_session).getQueue("OE", "OE_neworders_que");
        qrec = jms_session.createReceiver(queue);

        /* check for a message to show in the queue */
        obj_message = (ObjectMessage)qrec.receiveNoWait();
        new_order = (BolOrder)obj_message.getObject();
        customer = new_order.getCustomer();
        state    = customer.getState();

        System.out.println("Order:  for customer " + customer.getName());
       }
       catch (JMSException ex)
       {
         System.out.println("Exception: " + ex);
       }
       return new_order;
     }

#### Receiving Messages from a Destination Using a Transformation

A transformation can be applied when receiving a message from a queue or topic. The transformation is applied to the message before returning it to JMS application.

The transformation can be specified using the `setTransformation()` interface of the `AQjmsQueueReceiver`, `AQjmsTopicSubscriber` or `AQjmsTopicReceiver`.

Example 15-9 JMS: Receiving Messages from a Destination Using a Transformation

Assume that the Western Shipping application retrieves messages from the OE_bookedorders_topic. It specifies the transformation `OE2WS` to retrieve the message as the Oracle object type `WS_order`. Assume that the WSOrder Java class has been generated by Jpublisher to map to the Oracle object `WS.WS_order`:

    public AQjmsAdtMessage retrieve_bookedorders(TopicSession jms_session)
      AQjmsTopicReceiver  receiver;
      Topic               topic;
      Message             msg = null;

      try
      {
        /* get a handle to the OE_bookedorders_topic */
        topic = ((AQjmsSession)jms_session).getTopic("OE", "OE_bookedorders_topic");

        /* Create a receiver for WShip */
        receiver = ((AQjmsSession)jms_session).createTopicReceiver(
           topic, "WShip, null, WSOrder.getFactory());

        /* set the transformation in the publisher */
        receiver.setTransformation("OE2WS");
        msg = receiver.receive(10);
      }
      catch (JMSException ex)
      {
         System.out.println("Exception :", ex);
      }
           return (AQjmsAdtMessage)msg;
    }

### Specifying the Navigation Mode for Receiving Messages

    public void setNavigationMode(int mode)
                           throws JMSException

This method specifies the navigation mode for receiving messages. It has the following parameter:

| Parameter | Description                      |
|:----------|:---------------------------------|
| `mode`    | New value of the navigation mode |

Example 15-10 Specifying Navigation Mode for Receiving Messages

    TopicConnectionFactory    tc_fact   = null;
    TopicConnection           t_conn    = null;
    TopicSession              t_sess    = null;
    TopicSession              jms_sess;
    Topic                     shipped_orders;
    int                       myport = 5521;

    /* create connection and session */
    tc_fact = AQjmsFactory.getTopicConnectionFactory(
       "MYHOSTNAME", "MYSID", myport, "oci8");
    t_conn = tc_fact.createTopicConnection("jmstopic", "jmstopic");
    jms_sess = t_conn.createTopicSession(true, Session.CLIENT_ACKNOWLEDGE);
    shipped_orders = ((AQjmsSession )jms_sess).getTopic("WS", "Shipped_Orders_Topic");

    /* create a subscriber, specifying the correct CustomDatumFactory and selector */
    subscriber1 = jms_sess.createDurableSubscriber(
       shipped_orders, 'WesternShipping',
       "priority > 1 and tab.user_data.region like 'WESTERN %'", false,
       AQjmsAgent.getFactory());
    subscriber1.setNavigationMode(AQjmsConstants.NAVIGATION_FIRST_MESSAGE);

    /* get message for the subscriber, returning immediately if there was nomessage */
    Message = subscriber.receive();

### Receiving a Message Asynchronously

You can receive a message asynchronously two ways:

- Specifying a Message Listener at the Message Consumer

- Specifying a Message Listener at the Session

#### Specifying a Message Listener at the Message Consumer

    public void setMessageListener(javax.jms.MessageListener myListener)
                            throws JMSException

This method specifies a message listener at the message consumer. It has the following parameter:

| Parameter    | Description                        |
|:-------------|:-----------------------------------|
| `myListener` | Sets the consumer message listener |

Example 15-11 Specifying Message Listener at Message Consumer

    TopicConnectionFactory    tc_fact   = null;
    TopicConnection           t_conn    = null;
    TopicSession              t_sess    = null;
    TopicSession              jms_sess;
    Topic                     shipped_orders;
    int                       myport = 5521;
    MessageListener           mLis = null;

    /* create connection and session */
    tc_fact = AQjmsFactory.getTopicConnectionFactory(
       "MYHOSTNAME", "MYSID", myport, "oci8");
    t_conn = tc_fact.createTopicConnection("jmstopic", "jmstopic");
    jms_sess = t_conn.createTopicSession(true, Session.CLIENT_ACKNOWLEDGE);
    shipped_orders = ((AQjmsSession )jms_sess).getTopic(
        "WS", "Shipped_Orders_Topic");

    /* create a subscriber, specifying the correct CustomDatumFactory and selector */
    subscriber1 = jms_sess.createDurableSubscriber(
       shipped_orders, 'WesternShipping',
       "priority > 1 and tab.user_data.region like 'WESTERN %'",
       false, AQjmsAgent.getFactory());
    mLis = new myListener(jms_sess, "foo");

    /* get message for the subscriber, returning immediately if there was nomessage */
    subscriber.setMessageListener(mLis);
    The definition of the myListener class
    import oracle.AQ.*;
    import oracle.jms.*;
    import javax.jms.*;
    import java.lang.*;
    import java.util.*;
    public class myListener implements MessageListener
    {
       TopicSession   mySess;
       String         myName;
       /* constructor */
       myListener(TopicSession t_sess, String t_name)
       {
          mySess = t_sess;
          myName = t_name;
       }
       public onMessage(Message m)
       {
          System.out.println("Retrieved message with correlation: " ||
    m.getJMSCorrelationID());
          try{
            /* commit the dequeue */
            mySession.commit();
          } catch (java.sql.SQLException e)
          {System.out.println("SQL Exception on commit"); }
       }
    }

#### Specifying a Message Listener at the Session

    public void setMessageListener(javax.jms.MessageListener listener)
                            throws JMSException

This method specifies a message listener at the session.

| Parameter  | Description                                     |
|:-----------|:------------------------------------------------|
| `listener` | Message listener to associate with this session |

### Getting Message ID

This section contains these topics:

- Getting the Correlation Identifier

- Getting the Message Identifier

#### Getting the Correlation Identifier

    public java.lang.String getJMSCorrelationID()
              throws JMSException

`AQjmsMessage.getJMSCorrelationID()` gets the correlation identifier of a message.

#### Getting the Message Identifier

    public byte[] getJMSCorrelationIDAsBytes()
              throws JMSException

`AQjmsMessage.getJMSMessageID()` gets the message identifier of a message as bytes or a string.

### Getting JMS Message Properties

This section contains these topics:

- Getting a Boolean Message Property

- Getting a String Message Property

- Getting an Integer Message Property

- Getting a Double Message Property

- Getting a Float Message Property

- Getting a Byte Message Property

- Getting a Long Message Property

- Getting a Short Message Property

- Getting an Object Message Property

#### Getting a Boolean Message Property

    public boolean getBooleanProperty(java.lang.String name)
              throws JMSException

`AQjmsMessage.getBooleanProperty()` gets a message property as Boolean. It has the following parameter:

| Parameter | Description                  |
|:----------|:-----------------------------|
| `name`    | Name of the Boolean property |

#### Getting a String Message Property

    public java.lang.String getStringProperty(java.lang.String name)
              throws JMSException

`AQjmsMessage.getStringProperty()` gets a message property as string. It has the following parameter:

| Parameter | Description                 |
|:----------|:----------------------------|
| `name`    | Name of the string property |

#### Getting an Integer Message Property

    public int getIntProperty(java.lang.String name)
              throws JMSException

`AQjmsMessage.getIntProperty()` gets a message property as integer. It has the following parameter:

| Parameter | Description                  |
|:----------|:-----------------------------|
| `name`    | Name of the integer property |

#### Getting a Double Message Property

    public double getDoubleProperty(java.lang.String name)
                             throws JMSException

`AQjmsMessage.getDoubleProperty()` gets a message property as double. It has the following parameter:

| Parameter | Description                 |
|:----------|:----------------------------|
| `name`    | Name of the double property |

#### Getting a Float Message Property

    public float getFloatProperty(java.lang.String name)
              throws JMSException

`AQjmsMessage.getFloatProperty()` gets a message property as float. It has the following parameter:

| Parameter | Description                |
|:----------|:---------------------------|
| `name`    | Name of the float property |

#### Getting a Byte Message Property

    public byte getByteProperty(java.lang.String name)
              throws JMSException

`AQjmsMessage.getByteProperty()` gets a message property as byte. It has the following parameter:

| Parameter | Description               |
|:----------|:--------------------------|
| `name`    | Name of the byte property |

#### Getting a Long Message Property

    public long getLongProperty(java.lang.String name)
              throws JMSException

`AQjmsMessage.getLongProperty()` gets a message property as long. It has the following parameter:

| Parameter | Description               |
|:----------|:--------------------------|
| `name`    | Name of the long property |

#### Getting a Short Message Property

    public short getShortProperty(java.lang.String name)
                           throws JMSException

AQjmsMessage.getShortProperty() gets a message property as short. It has the following parameter:

| Parameter | Description                |
|:----------|:---------------------------|
| `name`    | Name of the short property |

#### Getting an Object Message Property

    public java.lang.Object getObjectProperty(java.lang.String name)
                                       throws JMSException

`AQjmsMessage.getObjectProperty()` gets a message property as object. It has the following parameter:

| Parameter | Description                 |
|:----------|:----------------------------|
| `name`    | Name of the object property |

Example 15-12 Getting Message Property as an Object

    TextMessage message;
    message.getObjectProperty("empid", new Integer(1000);

### Closing and Shutting Down

This section contains these topics:

- Closing a MessageProducer

- Closing a Message Consumer

- Stopping a JMS Connection

- Closing a JMS Session

- Closing a JMS Connection

#### Closing a MessageProducer

    public void close()
               throws JMSException

`AQjmsProducer.close()` closes a `MessageProducer`.

#### Closing a Message Consumer

    public void close()
               throws JMSException

`AQjmsConsumer.close()` closes a message consumer.

#### Stopping a JMS Connection

    public void stop()
              throws JMSException

`AQjmsConnection.stop()` stops a JMS connection.

#### Closing a JMS Session

    public void close()
               throws JMSException

`AQjmsSession.close()` closes a JMS session.

#### Closing a JMS Connection

    public void close()
              throws JMSException

`AQjmsConnection.close()` closes a JMS connection and releases all resources allocated on behalf of the connection. Because the JMS provider typically allocates significant resources outside the JVM on behalf of a connection, clients should close them when they are not needed. Relying on garbage collection to eventually reclaim these resources may not be timely enough.

### Troubleshooting

This section contains these topics:

- Getting a JMS Error Code

- Getting a JMS Error Number

- Getting an Exception Linked to a JMS Exception

- Printing the Stack Trace for a JMS Exception

- Setting an Exception Listener

- Getting an Exception Listener

#### Getting a JMS Error Code

    public java.lang.String getErrorCode()

`AQjmsException.getErrorCode()` gets the error code for a JMS exception.

#### Getting a JMS Error Number

    public int getErrorNumber()

`AQjmsException.getErrorNumber()` gets the error number for a JMS exception.

**Note:**

This method will be deprecated in a future release. Use `getErrorCode()` instead.

#### Getting an Exception Linked to a JMS Exception

    public java.lang.String getLinkString()

`AQjmsException.getLinkString()` gets the exception linked to a JMS exception. In general, this contains the SQL exception raised by the database.

#### Printing the Stack Trace for a JMS Exception

    public void printStackTrace(java.io.PrintStream s)

`AQjmsException.printStackTrace()` prints the stack trace for a JMS exception.

#### Setting an Exception Listener

    public void setExceptionListener(javax.jms.ExceptionListener listener)
                              throws JMSException

`AQjmsConnection.setExceptionListener()` specifies an exception listener for a connection. It has the following parameter:

| Parameter  | Description        |
|:-----------|:-------------------|
| `listener` | Exception listener |

If an exception listener has been registered, then it is informed of any serious problem detected for a connection. This is accomplished by calling the listener `onException()` method, passing it a JMS exception describing the problem. This allows a JMS client to be notified of a problem asynchronously. Some connections only consume messages, so they have no other way to learn the connection has failed.

Example 15-13 Specifying Exception Listener for Connection

    //register an exception listener
    Connection jms_connection;
    jms_connection.setExceptionListener(
        new ExceptionListener() {
            public void onException (JMSException jmsException) {
                System.out.println("JMS-EXCEPTION: " + jmsException.toString());
            }
        };
      );

#### Getting an Exception Listener

    public javax.jms.ExceptionListener getExceptionListener()
                                                     throws JMSException

`AQjmsConnection.getExceptionListener()` gets the exception listener for the connection.

Example 15-14 demonstrates how to use `ExceptionListener` with `MessageListener`. Ensure that the following conditions are met:

- The user `jmsuser` with password `jmsuser` is created in the database, with appropriate privileges.

- The queue `demoQueue` is created and started.

This example demonstrates how to make the MessageListener asynchronously receive the messages, where the exception listener recreates the JMS objects in case there is a connection restart.

Example 15-14 Using ExceptionListener with MessageListener

    import java.util.Enumeration;
    import java.util.Properties;

    import javax.jms.Connection;
    import javax.jms.JMSException;
    import javax.jms.Message;
    import javax.jms.MessageConsumer;
    import javax.jms.MessageProducer;
    import javax.jms.Queue;
    import javax.jms.QueueBrowser;
    import javax.jms.Session;
    import javax.jms.TextMessage;

    import oracle.jms.AQjmsConnectionFactory;
    import oracle.jms.AQjmsFactory;
    import oracle.jms.AQjmsSession;

    public class JMSDemo {

      static String queueName = "demoQueue";

      static String queueOwner = "jmsuser";

      static String queueOwnerPassword = "jmsuser";

      static Connection connection = null;

      static int numberOfMessages = 25000;

      static int messageCount = 0;

      static String jdbcURL = "";

      public static void main(String args[]) {
        try {
          jdbcURL = System.getProperty("JDBC_URL");

          if (jdbcURL == null)
            System.out
                .println("The system property JDBC_URL has not been set, " +
                        "usage:java -DJDBC_URL=xxx filename ");
          else {
            JMSDemo demo = new JMSDemo();
            demo.performJmsOperations();
          }
        } catch (Exception exception) {
          System.out.println("Exception : " + exception);
          exception.printStackTrace();
        } finally {
          try {
            if (connection != null)
              connection.close();
          } catch (Exception exc) {
            exc.printStackTrace();
          }
        }
        System.out.println("\nEnd of Demo aqjmsdemo11.");
      }

      public void performJmsOperations() {
        try {
          connection = getConnection(jdbcURL);
          Session session = connection.createSession(false,
              Session.AUTO_ACKNOWLEDGE);
          Queue queue = session.createQueue(queueName);

          // remove the messages from the Queue
          drainQueue(queueName, queueOwner, jdbcURL, true);

          // set the exception listener on the Connection
          connection.setExceptionListener(new DemoExceptionListener());

          MessageProducer producer = session.createProducer(queue);
          TextMessage textMessage = null;

          System.out.println("Sending " + numberOfMessages + " messages to queue "
              + queueName);
          for (int i = 0; i < numberOfMessages; i++) {
            textMessage = session.createTextMessage();
            textMessage.setText("Sample message text");
            producer.send(textMessage);
          }

          MessageConsumer consumer = session.createConsumer(queue);
          System.out.println("Setting the message listener ...");
          consumer.setMessageListener(new DemoMessageListener());
          connection.start();

          // Introduce a long wait to allow the listener to receive all the messages
          while (messageCount < numberOfMessages) {
            try {
              Thread.sleep(5000);
            } catch (InterruptedException interruptedException) {
            }
          }
        } catch (JMSException jmsException) {
          jmsException.printStackTrace();
        }
      }

      // Sample message listener
      static class DemoMessageListener implements javax.jms.MessageListener {

        public void onMessage(Message message) {
          try {
            System.out.println("Message listener received message with JMSMessageID "
                    + message.getJMSMessageID());
            messageCount++;
          } catch (JMSException jmsException) {
            System.out.println("JMSException " + jmsException.getMessage());
          }
        }
      }

      // sample exception listener
      static class DemoExceptionListener implements javax.jms.ExceptionListener {

        public void onException(JMSException jmsException) {
          try {
            // As a first step close the connection
            if (connection != null)
              connection.close();
          } catch (JMSException exception) {}

          try {
            System.out.println("Re-create the necessary JMS objects ...");
            connection = getConnection(jdbcURL);
            connection.start();
            Session session = connection.createSession(false,
                Session.AUTO_ACKNOWLEDGE);
            Queue queue = session.createQueue(queueName);
            MessageConsumer consumer = session.createConsumer(queue);
            consumer.setMessageListener(new DemoMessageListener());
          } catch (JMSException newJmsException) {
            newJmsException.printStackTrace();
          }
        }
      }

      // Utility method to get a connection
      static Connection getConnection(String jdbcUrl) throws JMSException {
        Properties prop = new Properties();
        prop.put("user", queueOwner);
        prop.put("password", queueOwnerPassword);

        AQjmsConnectionFactory fact = (AQjmsConnectionFactory) AQjmsFactory
            .getConnectionFactory(jdbcUrl, prop);
        Connection conn = fact.createConnection();
        return conn;
      }

      // Utility method to remove the messages from the queue
      static void drainQueue(String queueName, String queueOwner, String jdbcUrl,
          boolean debugInfo) {
        Connection connection = null;
        Session session = null;
        long timeout = 10000;
        int count = 0;
        Message message = null;
        try {
          connection = getConnection(jdbcUrl);
          connection.start();
          session = connection.createSession(false, Session.AUTO_ACKNOWLEDGE);
          Queue queue = ((AQjmsSession) session).getQueue(queueOwner, queueName);

          MessageConsumer messageConsumer = session.createConsumer(queue);
          QueueBrowser browser = session.createBrowser(queue);
          Enumeration enumeration = browser.getEnumeration();

          if (enumeration.hasMoreElements()) {
            while ((message = messageConsumer.receive(timeout)) != null) {
              if (debugInfo) {
                count++;
              }
            }
          }
          messageConsumer.close();
          if (debugInfo) {
            System.out.println("Removed " + count + " messages from the queue : "
                + queueName);
          }
        } catch (JMSException jmsException) {
          jmsException.printStackTrace();
        } finally {
          try {
            if (session != null)
              session.close();

            if (connection != null)
              connection.close();
          } catch (Exception exception) {

          }
        }
      }

    }

Example 15-15 Getting the Exception Listener for the Connection

    //Get the exception listener
    Connection jms_connection;
    ExceptionListener el = jms_connection.getExceptionListener();
