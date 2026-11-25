Oracle Data Provider for .NET provides a notification framework that supports Continuous Query Notification, enabling applications to receive client-side notifications when there is a change in a query result set, schema objects, or the state of the database, even if no Oracle Data Provider for .NET database connection exists. Using Continuous Query Notification, an application can maintain the validity of the client-side cache (for example, the ADO.NET `DataSet`) easily. Continuous Query Notification was previously known as Database Change Notification.

**Note:**

Continuous Query Notification is not supported in a .NET stored procedure.

Using the notification framework, applications can specify a query result set as a registered query for notification request on the database, and create this notification registration to maintain the validity of the query result set. When there is a change on the database that could affect the client-side cache's query results, the notification framework notifies the application.

**Note:**

The content of a change notification is referred to as an invalidation message. It indicates that the query result set is now invalid and provides information about the changes.

Based on the information provided by the invalidation message, the application can then act accordingly. For example, the application might need to refresh its own copy of the data for the registered query that is stored locally in the application.

**Note:**

If a registered object is dropped from the database and a new one is created with the same name in the same schema, re-registration is required to receive notifications for the newly created object.

**See Also:**

Firewalls, such as Windows Firewall, may be set up to block TCP network ports, which blocks incoming database notifications. Ensure the firewall is configured so that database applications can use the designated port for Continuous Query Notification.

Beginning with Oracle Database 11g and ODP.NET 11g (11.1), Continuous Query Notification queries can be query-based (default) or object-based. The query-based registrations allow ODP.NET to notify applications when the selected rows have changed in the database. The object-based registrations allow ODP.NET to notify applications for any changes that occur in the table(s) containing the selected rows.

Query-based registrations have two modes: guaranteed mode and best-effort mode. In guaranteed mode, any continuous query notification ensures that a change occurred to something contained in the queried result set. However, if a query is complex, then it cannot be registered in guaranteed mode. Best-effort mode is used in such cases.

Best-effort mode simplifies the query for query-based registration. No notifications are lost from the simplification. However, the simplification may cause false positives, as the simpler version's query result could change when the original query result would not.There still remain some restrictions on which queries can have best-effort mode query-based registrations. In such cases, developers can use object-based registrations, which can register most query types. Object-based registrations generate notifications when the query object changes, even if the actual query result does not. This also means that object-based registrations are more prone to false positives than query-based registrations. Developers should be aware of the relative strengths and weaknesses of each continuous query notification option and choose the one that best suits their requirements.

If a large number of rows are modified at once, consuming significant shared pool resources, the application will not receive any change notifications with specific row information that had undergone changes. Rather, it will receive a notification with `OracleNotificationEventArgs.Info` property set to `OracleNotificationInfo.Error`.

This section contains the following topics:

- Continuous Query Notification Classes

- Supported Operations

- Requirements of Notification Registration

- Using Continuous Query Notification

- Best Practice Guidelines and Performance Considerations

**See Also:**

- "[Configuring a Port to Listen for Database Notifications](InstallConfiguringPort.md)"

- [Oracle Database Platform Guide for Microsoft Windows](../ntqrf/postinstallation-configuration-tasks-on-windows.md) for details on configuring the Windows Firewall

- [Oracle Database Development Guide](../adfns/cqn.md) for more information on Continuous Query Notification

### Continuous Query Notification Classes

The following classes are associated with Continuous Query Notification Support:

- `OracleDependency`

  Represents a dependency between an application and an Oracle database based on the database events which the application is interested in. It contains information about the dependency and provides the mechanism to notify the application when specified database events occurs. The `OracleDependency` class is also responsible for creating the notification listener to listen for database notifications. There is only one database notification listener for each application domain. This notification listener terminates when the application process terminates.

  The dependency between the application and the database is not established when the `OracleDependency` object is created. The dependency is established when the command that is associated with this `OracleDependency` object is executed. That command execution creates a continuous query notification registration in the database.

  When a change has occurred in the database, the `HasChanges` property of the `OracleDependency` object is set to true. Furthermore, if an event handler was registered with the `OnChange` event of the `OracleDependency` object, the registered event handler function will be invoked.

- `OracleNotificationRequest`

  Represents a notification request to be registered in the database. It contains information about the request and the properties of the notification.

- `OracleNotificationEventArgs`

  Represents the [invalidation message](glossary.md) generated for a notification when a specified database event occurs and contains details about that database event.

  **See Also:**

  - "[OracleDependency Class](OracleDependencyClass.md)"

  - "[OracleNotificationRequest Class](OracleNotificationRequestClass.md)"

  - "[OracleNotificationEventArgs Class](OracleNotificationEventArgsClass.md)"

### Supported Operations

The ODP.NET notification framework in conjunction with Continuous Query Notification supports the following activities:

- Creating a notification registration by:

  - Creating an `OracleDependency` instance and binding it to an `OracleCommand` instance.

- Grouping multiple notification requests into one registration by:

  - Using the `OracleDependency.AddCommandDependency` method.

  - Setting the `OracleCommand.Notification` request using the same `OracleNotificationRequest` instance.

- Registering for Continuous Query Notification by:

  - Executing the `OracleCommand`. If either the notification property is null or `NotificationAutoEnlist` is false, the notification will not be made.

- Removing notification registration by:

  - Using the `OracleDependency.RemoveRegistration` method.

  - Setting the `Timeout` property in the `OracleNotificationRequest` instance before the registration is created.

  - Setting the `IsNotifiedOnce` property to `true` in the `OracleNotificationRequest` instance before the registration is created. The registration is removed once a database notification is sent.

- Ensuring Change Notification Persistence by:

  - Specifying whether or not the invalidation message is queued persistently in the database before delivery. If an invalidation message is to be stored persistently in the database, then the change notification is guaranteed to be sent. If an invalidation message is stored in an in-memory queue, the change notification can be received faster, however, it could be lost upon database shutdown or crashes.

- Retrieving notification information including:

  - The changed object name.

  - The schema name of the changed object.

  - Database events that cause the notification, such as insert, delete, and so on.

  - The `RowID` of the modified object row.

    In Oracle SQL, the `ROWIDTOCHAR(ROWID)` and `ROWIDTONCHAR(ROWID)` functions convert a `ROWID` value to `VARCHAR2` and `NVARCHAR` data types, respectively. If these functions are used within a SQL statement, `ROWID`s are not returned in the `OracleNotificationEventArgs` object that is passed to the continuous query notification callback.

- Defining the listener port number.

  By default, the static `OracleDependency.Port` property is set to `-1`. This indicates that the ODP.NET listens on a port that is randomly picked when ODP.NET registers a continuous query notification request for the first time during the execution of an application.

  ODP.NET creates only one listener that listens on one port within an application domain. Once ODP.NET starts the listener, the port number cannot be changed; Changes to the static `OracleDependency.Port` property will generate an error if a listener has already been created.

**See Also:**

- "[OracleCommand Class](OracleCommandClass.md)"

- "[Notification](CommandNotification.md)"

- "[NotificationAutoEnlist](CommandNotificationAutoEnlist.md)"

- "[OracleDependency Class](OracleDependencyClass.md)"

- "[OracleNotificationEventArgs Class](OracleNotificationEventArgsClass.md)"

### Requirements of Notification Registration

The connected user must have the `CHANGE` `NOTIFICATION` privilege to create a notification registration.

This SQL statement grants the `CHANGE` `NOTIFICATION` privilege:

    grant change notification to user name

This SQL statement revokes the `CHANGE` `NOTIFICATION` privilege:

    revoke change notification from user name

### Using Continuous Query Notification

This section describes what the application should do, and the flow of the process, when an application uses Continuous Query Notification to receive notifications for any changes in the registered query result set.

#### Application Steps

The application should do the following:

1.  Create an `OracleDependency` instance.

2.  Assign an event handler to the `OracleDependency.OnChange` event property if the application wishes to have an event handler invoked when database changes are detected. Otherwise, the application can choose to poll on the `HasChanges` property of the `OracleDependency` object. This event handler is invoked when the change notification is received.

3.  Set the port number for the listener to listen on. The application can specify the port number for one notification listener to listen on. If the application does not specify a port number, a random one is used by the listener.

4.  Bind the `OracleDependency` instance to an `OracleCommand` instance that contains the actual query to be executed. Internally, the Continuous Query Notification request (an `OracleNotificationRequest` instance) is created and assigned to the `OracleCommand.Notification` property.

#### Flow of Notification Process

1.  When the command associated with the notification request is executed, the notification registration is created in the database. The command execution must return a result set, or contain one or more `REF` cursors for a PL/SQL stored procedure.

2.  ODP.NET starts the application listener on the first successful notification registration.

3.  When a change related to the registration occurs in the database, the application is notified through the event delegate assigned to the `OracleDependency.OnChange` event property, or the application can poll the `OracleDependency.HasChanges` property.

The following example demonstrates the continuous query notification feature.

    // Database Setup
    // NOTE: unless the following SQL command is executed,
    // ORA-29972 will be obtained from running this sample
    /*
    grant change notification to scott;
    */
    using System;
    using System.Threading;
    using System.Data;
    using Oracle.DataAccess.Client;
    using Oracle.DataAccess.Types;

    //This sample shows the continuous query notification feature in ODP.NET.
    //Application specifies to get a notification when emp table is updated.
    //When emp table is updated, the application will get a notification
    //through an event handler.
    namespace NotificationSample
    {
      public class MyNotificationSample
      {
        public static bool IsNotified = false;

        public static void Main(string[] args)
        {
          //To Run this sample, make sure that the change notification privilege
          //is granted to scott.
          string constr = "User Id=scott;Password=tiger;Data Source=oracle";
          OracleConnection con = null;
          OracleDependency dep = null;

          try
          {
            con = new OracleConnection(constr);
            OracleCommand    cmd = new OracleCommand("select * from emp", con);
            con.Open();

            // Set the port number for the listener to listen for the notification
            // request
            OracleDependency.Port = 1005;

            // Create an OracleDependency instance and bind it to an OracleCommand
            // instance.
            // When an OracleDependency instance is bound to an OracleCommand
            // instance, an OracleNotificationRequest is created and is set in the
            // OracleCommand's Notification property. This indicates subsequent
            // execution of command will register the notification.
            // By default, the notification request is using the Database Change
            // Notification.
            dep = new OracleDependency(cmd);

            // Add the event handler to handle the notification. The
            // OnMyNotification method will be invoked when a notification message
            // is received from the database
            dep.OnChange +=
              new OnChangeEventHandler(MyNotificationSample.OnMyNotificaton);

            // The notification registration is created and the query result sets
            // associated with the command can be invalidated when there is a
            // change.  When the first notification registration occurs, the
            // notification listener is started and the listener port number
            // will be 1005.
            cmd.ExecuteNonQuery();

            // Updating emp table so that a notification can be received when
            // the emp table is updated.
            // Start a transaction to update emp table
            OracleTransaction txn = con.BeginTransaction();
            // Create a new command which will update emp table
            string updateCmdText =
              "update emp set sal = sal + 10 where empno = 7782";
            OracleCommand updateCmd = new OracleCommand(updateCmdText, con);
            // Update the emp table
            updateCmd.ExecuteNonQuery();
            //When the transaction is committed, a notification will be sent from
            //the database
            txn.Commit();
          }
          catch (Exception e)
          {
            Console.WriteLine(e.Message);
          }

          con.Close();
          // Loop while waiting for notification
          while(MyNotificationSample.IsNotified == false)
          {
            Thread.Sleep(100);
          }
        }

        public static void OnMyNotificaton(object src,
          OracleNotificationEventArgs arg)
        {
          Console.WriteLine("Notification Received");
          DataTable changeDetails = arg.Details;
          Console.WriteLine("Data has changed in {0}",
            changeDetails.Rows[0]["ResourceName"]);
          MyNotificationSample.IsNotified = true;
        }
      }
    }

### Best Practice Guidelines and Performance Considerations

This section provides guidelines for working with Continuous Query Notification and the ODP.NET notification framework, and discusses the performance impacts.Every change notification registration consumes database memory, storage or network resources, or some combination thereof. The resource consumption further depends on the volume and size of the [invalidation message](glossary.md). In order to scale well with a large number of mid-tier clients, Oracle recommends that the client implement these best practices:

- Few and mostly read-only tables

  There should be few registered objects, and these should be mostly read-only, with very infrequent invalidations. If an object is extremely volatile, then a large number of invalidation notifications are sent, potentially requiring a lot of space (in memory or on disk) in the invalidation queue. This is also true if a large number of objects are registered.

- Few rows updated for each table

  Transactions should update (or insert or delete) only a small number of rows within the registered tables. Depending on database resources, a whole table could be invalidated if too many rows are updated within a single transaction, for a given table.

  This policy helps to contain the size of a single invalidation message, and reduces disk storage for the invalidation queue.

**See Also:**

[Oracle Database Development Guide](../adfns/cqn.md) for further information on Continuous Query Notification
