This event is notified when a message is available in the queue for `NotificationConsumers`.

### Declaration

    // C#
    public event OracleAQMessageAvailableEventHandler MessageAvailable;

### Event Data

The event handler receives an `OracleAQMessageAvailableEventArgs` object.

### Exceptions

`InvalidOperationException` - The connection is not open.

### Remarks

Asynchronous notification is supported in all queue tables created with a database compatibility level of 8.1 or higher.

In order to receive the notification about message availability, the client must create an `OracleAQMessageAvailableEventHandler` delegate to listen to this event. The delegate should be added to this event only after setting the [NotificationConsumers](AQQueueNotificationConsumers.md) and [Notification](AQQueueNotification.md) properties.

The notification registration takes place after the first delegate is added to the event. The notification is unregistered when the last delegate is removed from the event. Notifications set on an `OracleAQQueue` object get cancelled automatically when the object gets disposed.

Oracle Data Provider for .NET opens a port to listen for notifications. HA events, load balancing, and continuous query notification features also share the same port. This port can be configured centrally by setting the database notification port in an application or Web configuration file. The following example code specifies a port number of 1200:

    <configuration>
      <oracle.dataaccess.client>
        <settings>
          <add name="DbNotificationPort" value="1200"/>
        </settings>
      </oracle.dataaccess.client>
    </configuration>

If the configuration file does not exist or the db notification port is not specified, then ODP.NET uses a valid and random port number. The configuration file may also request for a random port number by specifying a db notification port value of -1.

The notification listener, which runs in the same application domain as ODP.NET, uses the specified port number to listen to notifications from the database. A notification listener gets created when the application registers with `OracleAQQueue.MessageAvailable` event. One notification listener can listen to all notification types. Only one notification listener is created for each application domain.

### Example

The following example demonstrates application notification. The first part of the example performs the requisite database setup for the database user, `SCOTT`. The second part of the example demonstrates how an application is notified when a message is available in the queue.

    -- Part I: Database setup required for this demo

    ------------------------------------------------------------------
    -- SQL to grant appropriate privilege to database user, SCOTT
    ------------------------------------------------------------------
    SQL> ALTER USER SCOTT ACCOUNT UNLOCK IDENTIFIED BY Pwd4Sct;
    User altered.
    SQL> GRANT ALL ON DBMS_AQADM TO scott;

    ------------------------------------------------------------------
    -- PLSQL to create queue-table and queue and start queue for SCOTT
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
    -- PLSQL to stop queue and drop queue & queue-table from SCOTT
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

    //Part II: Demonstrates application notification
    //C#
    using System;
    using System.Text;
    using Oracle.DataAccess.Client;
    using Oracle.DataAccess.Types;

    namespace ODPSample
    {
      /// <summary>
      /// Demonstrates how the application can be notified when a message is
      /// available in a queue.
      /// </summary>
      class Notification
      {
        static bool isNotified = false;

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

            // Set message type for the queue
            queue.MessageType = OracleAQMessageType.Raw;

            // Add the event handler to handle the notification. The
            // MsgReceived method will be invoked when a message is enqueued
            queue.MessageAvailable +=
              new OracleAQMessageAvailableEventHandler(Notification.MsgReceived);

            Console.WriteLine("Notification registered...");

            // Begin txn for enqueue
            OracleTransaction txn = con.BeginTransaction();

            Console.WriteLine("Now enqueuing message...");

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
            Console.WriteLine();

            // Enqueue txn commit
            txn.Commit();

            // Loop while waiting for notification
            while (isNotified == false)
            {
              System.Threading.Thread.Sleep(2000);
            }
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

        static void MsgReceived(object src, OracleAQMessageAvailableEventArgs arg)
        {
          try
          {
            Console.WriteLine("Notification Received...");
            Console.WriteLine("QueueName : {0}", arg.QueueName);
            Console.WriteLine("Notification Type : {0}", arg.NotificationType);

            //following type-cast to "byte[]" is required only for .NET 1.x
            byte[] notifiedMsgId = (byte[]) arg.MessageId[0];
            Console.WriteLine("MessageId of Notified Message : "
              + ByteArrayToString(notifiedMsgId));
            isNotified = true;
          }
          catch (Exception e)
          {
            Console.WriteLine("Error: {0}", e.Message);
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

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQQueue Class](OracleAQQueueClass.md)

- [OracleAQQueue Members](AQQueueMembers.md)
