Oracle Database Advanced Queuing (AQ) provides database-integrated message queuing functionality. Oracle Database AQ leverages the functions of Oracle Database so that messages can be stored persistently, propagated between queues on different computers and databases, and transmitted using Oracle Net Services and HTTP(S).

**Note:**

ODP.NET, Managed Driver and ODP.NET Core do not support the AQ .NET classes.

As Oracle Database AQ is implemented in database tables, all operational benefits of high availability, scalability, and reliability are also applicable to queue data. Oracle Database AQ supports standard database features such as recovery, restart, and security.

The following items discuss Oracle Database AQ concepts:

- Queues and Queue Tables

  Messages enqueued in a queue are stored in a queue table. A queue table must be created before creating a queue based on it. Use the `DBMS_AQADM` PL/SQL package or Oracle Developer Tools for Visual Studio to create and administer queue tables and queues.

  Queues are represented by `OracleAQQueue` objects.

- Single-Consumer and Multiple-Consumer Queues

  A single-consumer queue is created based on a single consumer queue table. Messages enqueued in a single-consumer queue can be dequeued by only a single consumer.

  A multiple-consumer queue is based on a multiple-consumer queue table. This queue supports queue subscribers and message recipients.

- Message Recipients

  A message producer can submit a list of recipients when enqueuing a message. This allows for a unique set of recipients for each message in the queue. The recipient list associated with the message overrides the subscriber list, if any, associated with the queue. The recipients need not be in the subscriber list. However, recipients can be selected from among the subscribers.The `Recipients` property of an `OracleAQMessage` can be used to specify the recipients to a specific message in terms of `OracleAQAgent` objects.

- Enqueue

  Messages are enqueued when producer applications push the messages into a queue. This is accomplished by calling the `Enqueue` method on an `OracleAQQueue` object. Multiple messages can be enqueued using the `EnqueueArray` method.

- Dequeue

  Messages are dequeued when consumer applications pull the messages from a queue. This is accomplished by calling the `Dequeue` method on an `OracleAQQueue` object. Multiple messages can be dequeued using the `DequeueArray` method.

- Listen

  Subscriber applications can use a `Listen` call to monitor multiple queues for subscriptions on different queues. This is a more scalable solution for cases where a subscriber application has subscribed to many queues and wishes to receive messages that arrive in any of the queues.This is accomplished by calling the `Listen` method of the `OracleAQQueue` class, passing the list of subscriptions in form of an array.

- Notification

  Subscriber applications can utilize the notification mechanism to get notifications about message availability in a queue. The applications can decide to skip or dequeue the message from the queue based on the information received.

  A subscriber application must register for event notification on the queues from which it wants to receive notifications. This is represented by the `MessageAvailable` event on `OracleAQQueue`. The event is triggered when messages matching the subscriptions arrive.

  Notifications can be registered as regular or grouping notifications. A time out value for these notifications can also be specified. Various notification options can be set using the `OracleAQQueue.Notification` property. Notifications set on an `OracleAQQueue` object gets cancelled automatically when the object gets disposed.

- Buffered Messaging

  In buffered messaging, messages reside in a shared memory area. This makes it faster than persistent messaging. The messages are written to disk only when the total memory consumption of buffered messages approaches the available shared memory limit. Buffered messaging is ideal for applications that do not require the reliability and transaction support of Oracle Database AQ persistent messaging.

  Buffered and persistent messages use the same single-consumer or multi-consumer queues, and the same administrative and operational interfaces. They are distinguished from each other by a delivery mode parameter. When an application enqueues a message to an Oracle Database AQ queue, it sets the delivery mode parameter as well.

  The delivery mode parameter can be set on `OracleAQMessage` by modifying the `DeliveryMode` property. Buffered messaging is supported in all queue tables created with compatibility 8.1 or higher.

**See Also:**

- "[OracleAQQueue Class](OracleAQQueueClass.md)"

- "[Recipients](AQMessageRecipients.md)"

- "[OracleAQAgent Class](OracleAQAgentClass.md)"

- "[Enqueue](AQQueueEnqueueOverloads.md)"

- "[EnqueueArray](AQQueueEnqueueArrayOverloads.md)"

- "[Dequeue](AQQueueDequeueOverloads.md)"

- "[DequeueArray](AQQueueDequeueArrayOverloads.md)"

- "[Listen](AQQueueListenOverloads001.md)"

- "[MessageAvailable Event](AQQueueMessageAvailableEvent.md)"

- "[Notification](AQQueueNotification.md)"

- "[DeliveryMode](AQMessageDeliveryMode.md)"

- [Oracle Database Advanced Queuing User's Guide](../adque/aq-introduction.md)

### Using ODP.NET for Advanced Queuing

.NET applications can use ODP.NET to access all the operational features of AQ such as Enqueuing, Dequeuing, Listen, and Notification.

Table 3-27 maps the AQ features to their corresponding ODP.NET implementation.

Table 3-27 Mapping AQ Features with their ODP.NET Implementation

| Functionality                   | ODP.NET Implementation                                                                                                                                                |
|:--------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Create a Message                | Create an `OracleAQMessage` object                                                                                                                                    |
| Enqueue a single message        | Specify the message as `OracleAQMessage`, queue as `OracleAQQueue` and enqueue options on `OracleAQQueue`, call `OracleAQQueue.`[Enqueue](AQQueueEnqueueOverloads.md) |
| Enqueue multiple messages       | Specify the messages as an `OracleAQMessage` array in `OracleAQQueue.`[EnqueueArray](AQQueueEnqueueArrayOverloads.md)                                                 |
| Dequeue a single message        | Specify dequeue options on `OracleAQQueue` and call `OracleAQQueue.`[Dequeue](AQQueueDequeueOverloads.md)                                                             |
| Dequeue multiple messages       | Call `OracleAQQueue.`[DequeueArray](AQQueueDequeueArrayOverloads.md)                                                                                                  |
| Listen for messages on Queue(s) | Call `OracleAQQueue.`[Listen](AQQueueListenOverloads001.md).To listen on multiple queues use static [Listen](AQQueueListenOverloads.md) method of `OracleAQQueue`     |
| Message Notifications           | Use `OracleAQQueue.`[MessageAvailable Event](AQQueueMessageAvailableEvent.md) along with the `NotificationConsumers` property                                         |

**Note:**

AQ samples are provided in the `ORACLE_BASE``\``ORACLE_HOME``\ODP.NET\Samples` directory in ODAC installations done using Oracle Universal Installer.

#### Enqueuing and Dequeuing Example

The following example demonstrates enqueuing and dequeuing messages using a single consumer queue. The first part of the example performs the requisite database setup for the database user, `SCOTT`. The second part of the example demonstrates enqueuing and dequeuing messages.

    -- Part I: Database setup required for this demo

    ------------------------------------------------------------------
    -- SQL to grant appropriate privilege to database user, SCOTT
    ------------------------------------------------------------------
    SQL> ALTER USER SCOTT ACCOUNT UNLOCK IDENTIFIED BY Pwd4Sct;
    User altered.
    SQL> GRANT ALL ON DBMS_AQADM TO scott;

    ------------------------------------------------------------------
    -- PL/SQL to create queue-table and queue and start queue for SCOTT
    ------------------------------------------------------------------
    BEGIN
      DBMS_AQADM.CREATE_QUEUE_TABLE(
        queue_table=>'scott.test_q_tab',
        queue_payload_type=>'RAW',
        multiple_consumers=>FALSE);

      DBMS_AQADM.CREATE_QUEUE(
        queue_name=>'scott.test_q',
        queue_table=>'scott.test_q_tab');

      DBMS_AQADM.START_QUEUE(queue_name=>'scott.test_q');
    END;
    /

    ------------------------------------------------------------------
    -- PL/SQL to stop queue and drop queue & queue-table from SCOTT
    ------------------------------------------------------------------
    BEGIN
      DBMS_AQADM.STOP_QUEUE('scott.test_q');

      DBMS_AQADM.DROP_QUEUE(
        queue_name => 'scott.test_q',
        auto_commit => TRUE);

      DBMS_AQADM.DROP_QUEUE_TABLE(
        queue_table => 'scott.test_q_tab',
        force => FALSE,
        auto_commit => TRUE);
    END;
    /
    -- End of Part I, database setup.

    //Part II: Enqueuing and dequeuing messages
    //C#
    using System;
    using System.Text;
    using Oracle.DataAccess.Client;
    using Oracle.DataAccess.Types;

    namespace ODPSample
    {
      /// <summary>
      /// Demonstrates Enqueuing and Dequeuing raw message
      /// using a single consumer queue
      /// </summary>
      class EnqueueDequeue
      {
        static void Main(string[] args)
        {
          // Create connection
          string constr = "user id=scott;password=Pwd4Sct;data source=oracle";
          OracleConnection con = new OracleConnection(constr);

          // Create queue
          OracleAQQueue queue = new OracleAQQueue("scott.test_q", con);

          try
          {
            // Open connection
            con.Open();

            // Begin txn for enqueue
            OracleTransaction txn = con.BeginTransaction();

            // Set message type for the queue
            queue.MessageType = OracleAQMessageType.Raw;

            // Prepare message and RAW payload
            OracleAQMessage enqMsg = new OracleAQMessage();
            byte[] bytePayload = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
            enqMsg.Payload = bytePayload;

            // Prepare to Enqueue
            queue.EnqueueOptions.Visibility = OracleAQVisibilityMode.OnCommit;

            // Enqueue message
            queue.Enqueue(enqMsg);

            Console.WriteLine("Enqueued Message Payload      : "
              + ByteArrayToString(enqMsg.Payload as byte[]));
            Console.WriteLine("MessageId of Enqueued Message : "
              + ByteArrayToString(enqMsg.MessageId));

            // Enqueue txn commit
            txn.Commit();

            // Begin txn for Dequeue
            txn = con.BeginTransaction();

            // Prepare to Dequeue
            queue.DequeueOptions.Visibility = OracleAQVisibilityMode.OnCommit;
            queue.DequeueOptions.Wait = 10;

            // Dequeue message
            OracleAQMessage deqMsg = queue.Dequeue();

            Console.WriteLine("Dequeued Message Payload      : "
              + ByteArrayToString(deqMsg.Payload as byte[]));
            Console.WriteLine("MessageId of Dequeued Message : "
              + ByteArrayToString(deqMsg.MessageId));

            // Dequeue txn commit
            txn.Commit();
          }
          catch (Exception e)
          {
            Console.WriteLine("Error: {0}", e.Message);
          }
          finally
          {
            // Close/Dispose objects
            queue.Dispose();
            con.Close();
            con.Dispose();
          }
        }

        // Function to convert byte[] to string
        static private string ByteArrayToString(byte[] byteArray)
        {
          StringBuilder sb = new StringBuilder();
          for (int n = 0; n < byteArray.Length; n++)
          {
            sb.Append((int.Parse(byteArray[n].ToString())).ToString("X"));
          }
          return sb.ToString();
        }
      }
    }
