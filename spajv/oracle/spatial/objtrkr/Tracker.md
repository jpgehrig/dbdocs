Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- Prev Class
- [Next Class](Tracker.Callback.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

oracle.spatial.objtrkr

## Class Tracker

- java.lang.Object

- - oracle.spatial.objtrkr.Tracker

<!-- -->

-

  ------------------------------------------------------------------------



      public class Tracker
      extends java.lang.Object

  Provides an interface to a database location tracking set. Refer to Oracle's documentation for details of how a tracking set works.
  ## Typical usage:

  Set optional parameters using the available methods, and optionally create and start the tracking set on the server (if not already done). Once setup is finished, call the `begin()` method. After begin() is called, you can set or delete tracking regions on the server, subscribe to notifications using `setNotification(long, long, NotificationType)`, and start sending locations and receiving and processing notifications.
  To connect to an existing, running tracking set named "fleet" owned by user "john", and send a location update that objectId 21 is at (x1, y1) and object 27 is at (x2, y2):


       Tracker tracker = new Tracker("john", "fleet", oracleDataSource).begin();
       tracker.location(21, x1, y1);
       tracker.location(27, x1, y1);
       tracker.sendLocations();



  To use "fleet" if it exists, or create and/or start it if necessary (with 3 tracking queues and 2 location queues), with the capability of setting callbacks on regions:


       Tracker tracker = new Tracker("john", "fleet", oracleDataSource);
       tracker.setNumTrackingQueues(3);         // Value used only if fleet needs to be created
       tracker.setNumLocationQueues(2);         // Value used only if fleet needs to be created
       tracker.allowRegionCallbacks(true);
       tracker.startTrackingSet(true);          // Start if not already started; create if it doesn't already exist
       tracker.begin();



  After begin() is called, location messages can be sent to the server and notifications can be received and processed.

  List of permissions that may be needed by the database user of the tracking set: connect, resource, aq_administrator_role, create job, manage scheduler, dbms_aq, dbms_aqadm, dbms_lock, dbms_aqin, dbms_aqjms

  You can use the following SQL command to check the number of messages in the queues on the server:
  `Select a.queue_table, b.* from dba_queues a, v$aq b where b.ready > 0 and a.qid = b.qid;`

  ## Concurrency:

  Each Tracker object has a single session and must be single-threaded. Use the `newSession()` method to create duplicate Tracker objects with separate sessions; each such duplicate can be used by a different thread. You can create dedicated workers using the createWorkerThread call, which returns a new Thread with its own session.
  The group of Trackers and workers created via newSession() and `createWorker()` share common location and notification queues with the original Tracker, and a common set of callbacks. Efficiency is generally improved by the ability to batch multiple messages to and from the database, and the ability of multiple threads to process incoming notifications.

  If you instead use **new** to create multiple Trackers for the same database tracking set, then location messages from separate Trackers can not be batched together. Notifications fetched from the database by one Tracker will not be available to other Trackers. Callbacks, if used, are set separately for each of the **new**'d Trackers, and so a notification will be processed according to whichever Tracker receives it. Subject to these limitations, multiple Tracker objects are supported, and are useful for applications running on multiple computers creating location messages.

  Database processing is concurrent, and it is possible for location messages to be processed in a different order than what they were sent in. For similar reasons, location messages sent immediately after a setNotification() subscription may be processed before the setNotification() is completed on the server. While these variations occur for all notification types, the effects are most dramatic for TRANSITION notifications. A sequence of locations like "out1 out2 out3 in4 in5 in6" you would expect to generate two TRANSITION notifications "out1 in4", can instead (if the locations are sent very close together) generate potentially up to six notifications, "out1 in4 out2 in5 out3 in6". If order is important, you must resolve these using the timestamp field of the messages.

  ## Example code


         static volatile boolean stopWork = false;
         static void example(OracleDataSource oracleDataSource) throws SQLException, JMSException, InterruptedException {

           // Connect to database and start a tracking set named "sample", creating it if necessary
           Tracker sample = new Tracker("sdobug", "sample", oracleDataSource)
                 .stopDrop()                // For this example, delete & re-create queues to make sure no old data from previous run
                 .startTrackingSet(true)       // Create and start the tracking set
                 .begin();                     // Must call begin before communicating with database

           Tracker.debugLevel(3);              // Request debugging information

           // Set up a tracking region with id 77
           JGeometry geom = new JGeometry(2003, SRID, new int[] {1,1003,1}, new double[] {11,2, 20,2, 20,14, 11,14, 11,2});
           sample.setTrackingRegion(77, geom);
           // Track whenever object 1 enters or leaves region 77
           sample.setNotification(1, 77, Tracker.NotificationType.TRANSITION);

           // Start a location worker to send locations and a notification worker to fetch notifications from server
           Thread workerL = sample.createWorkerThread(WorkerType.LOCATION_WORKER, () -> stopWork);
           workerL.start();
           Thread workerN = sample.createWorkerThread(WorkerType.NOTIFICATION_WORKER, () -> stopWork);
           workerN.start();

           // Setup processing for incoming notification
           sample.setCallback(msg -> System.out.println("Object "+msg.getObjectId()
                     +" ("+msg.getX()+", "+msg.getY()
                     +") is "+msg.getState()+" region "+msg.getRegionId()));

           // Send a location
           sample.location(1,   1.10,  1.20, new Timestamp(69,  7, 20, 20, 39, 33, 0));
           sample.location(1,   2,     3,    new Timestamp(69,  7, 20, 59, 18,  0, 0));
           sample.location(1,  15,    10,    new Timestamp(69, 11, 19,  5, 32,  0, 0));
           // (sendLocations() call not needed because we have a LOCATION_WORKER running)

           // Expect to see two notifications, (1.10, 1.20) OUTSIDE and (15, 10) INSIDE

           // Wait 20 seconds, and then tell the workers to quit
           Thread.sleep(20000);

           stopWork = true;
           workerL.interrupt();
           workerL.join();
           workerN.interrupt();
           workerN.join();

           // Done, close the java object (but leave the database tracking set intact)
           sample.close();

         }



  Since:
  18.1

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type   | Class and Description                                                                                                                                 |
    |---------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static interface ` | [`Tracker.Callback`](Tracker.Callback.md)`<`[`T`](Tracker.Callback.md)`>`<br>Equivalent to consumer lambda, but allows SQLException and JMSException. |
    | `static class `     | [`Tracker.NotificationType`](Tracker.NotificationType.md)<br>The type of notifications that can be subscribed to                                      |
    | `static class `     | [`Tracker.WorkerType`](Tracker.WorkerType.md)<br>Types of worker threads that can be created                                                          |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                     |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `Tracker``(java.lang.String owner, java.lang.String name, OracleDataSource ods)`<br>Create a Tracker for accessing the tracking set owner.name on the database. |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                | Method and Description                                                                                                                                                                                                       |
    |--------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `Tracker`                                        | `allowObjectCallbacks``(boolean allowed)`<br>Whether or not per-object callbacks will be used in this Tracker.                                                                                                               |
    | `Tracker`                                        | `allowRegionCallbacks``(boolean allowed)`<br>Whether or not per-region callbacks will be used in this Tracker.                                                                                                               |
    | `Tracker`                                        | `begin``()`<br>Marks the end of setup.                                                                                                                                                                                       |
    | `void`                                           | `close``()`<br>Close the connection to the database and release the client resources and database connections.                                                                                                               |
    | `Tracker`                                        | `createTrackingSet``()`<br>Create the tracker on the database.                                                                                                                                                               |
    | `java.lang.Thread`                               | `createWorkerThread``(`[`Tracker.WorkerType`](Tracker.WorkerType.md)` workerType, java.util.function.BooleanSupplier exitFlag)`<br>Create a new session of this tracker usable as a worker thread.                           |
    | `static void`                                    | `debugLevel``(int level)`<br>Set level of debug output (overriding any system value).                                                                                                                                        |
    | `static void`                                    | `debugOutput``(java.io.PrintStream ps)`<br>Copy debugging output to the given print stream, in addition to its normal output location.                                                                                       |
    | `Tracker`                                        | `deleteObjectSubscription``(long objectId, java.lang.Long regionId)`<br>Delete notifications for a tracked object.                                                                                                           |
    | `Tracker`                                        | `deleteTrackingRegion``(long regionId, boolean deleteNotifications)`<br>Delete a tracking region.                                                                                                                            |
    | `int`                                            | `fetchNotifications``(long waitMs)`<br>Fetch notification(s) from the database, waiting at most the specified time for the first one to arrive.                                                                              |
    | `void`                                           | `finalize``()`                                                                                                                                                                                                               |
    | `java.lang.String`                               | `getName``()`                                                                                                                                                                                                                |
    | `NotificationMsg`                                | `getNotification``()`<br>Return one notification, blocking if there are no outstanding                                                                                                                                       |
    | `NotificationMsg`                                | `getNotification``(long waitMs)`<br>Return one notification, waiting up to the specified time if there are no outstanding.                                                                                                   |
    | `int`                                            | `getNotificationQueueSize``()`<br>The number of notifications without callbacks to store before discarding the oldest                                                                                                        |
    | `java.util.List<NotificationMsg>`                | `getNotifications``(long waitMs)`<br>Return all available notifications.                                                                                                                                                     |
    | `int`                                            | `getNumLocationQueues``()`<br>If a tracking set of this name appears on the server, then this will return the number of location queues it has.                                                                              |
    | `int`                                            | `getNumTrackingQueues``()`<br>If a tracking set of this name appears on the server, then this will return the number of tracking queues it has.                                                                              |
    | `java.lang.String`                               | `getOwner``()`<br>Return the database schema of this tracker.                                                                                                                                                                |
    | `java.util.Map<java.lang.String,java.lang.Long>` | `getStatistics``()`<br>Return statistics.                                                                                                                                                                                    |
    | `void`                                           | `location``(long objId, double x, double y)`<br>Same as calling `location(objId, x, y, new Timestamp(System.currentTimeMillis())`.                                                                                           |
    | `void`                                           | `location``(long objId, double x, double y, java.sql.Timestamp timestamp)`<br>Queues a location message to be sent to the server.                                                                                            |
    | `Tracker`                                        | `newSession``()`<br>Create a duplicate of this tracker with its own session (each thread needs its own session).                                                                                                             |
    | `void`                                           | `sendLocations``()`<br>Send any queued locations to the server.                                                                                                                                                              |
    | `void`                                           | `setCallback``(`[`Tracker.Callback`](Tracker.Callback.md)`<NotificationMsg> callback)`<br>Set a callback for all notifications that are not otherwise covered by a region or object callback.                                |
    | `Tracker`                                        | `setNotification``(long objId, long regionId, `[`Tracker.NotificationType`](Tracker.NotificationType.md)` type)`<br>Subscribe to notifications about a particular object/region pair                                         |
    | `Tracker`                                        | `setNotification``(TrackerMsg msg)`<br>Add a single subscription to the database                                                                                                                                             |
    | `void`                                           | `setNotificationQueueSize``(int maxSize)`<br>The number of notifications without callbacks to store before discarding the oldest                                                                                             |
    | `Tracker`                                        | `setNotifications``(java.util.List<TrackerMsg> subscriptionList)`<br>Set multiple subscriptions on the server.                                                                                                               |
    | `void`                                           | `setNumLocationQueues``(int numLocationQueues)`<br>Set the number of location queues we should use when creating a new tracking set on the database.                                                                         |
    | `void`                                           | `setNumTrackingQueues``(int numTrackingQueues)`<br>Set the number of tracking queues we should use when creating a new tracking set on the database.                                                                         |
    | `void`                                           | `setObjectCallback``(long objectId, `[`Tracker.Callback`](Tracker.Callback.md)`<NotificationMsg> callback)`<br>When a notification occurs for the given objectId, forward the notification to the specified callback method. |
    | `void`                                           | `setRegionCallback``(long regionId, `[`Tracker.Callback`](Tracker.Callback.md)`<NotificationMsg> callback)`<br>When a notification occurs for the given regionId, forward the notification to the specified callback method. |
    | `Tracker`                                        | `setTrackingRegion``(long regionId, `[`JGeometry`](../geometry/JGeometry.md)` geom)`<br>Set a tracking region on the server.                                                                                                 |
    | `Tracker`                                        | `startTrackingSet``(boolean createIfNecessary)`<br>Connect to an existing tracking set on the database; optionally create if it doesn't already exist.                                                                       |
    | `Tracker`                                        | `stopDrop``()`<br>Stop (if running) and drop the tracker on the database, cleaning up all database resources.                                                                                                                |
    | `Tracker`                                        | `stopTrackingSet``()`<br>Stop the tracker on the database.                                                                                                                                                                   |
    | `boolean`                                        | `trackingsetExists``()`<br>Indicates whether a tracking set of the given name has been created on the server, whether by us or from a previously existing tracker.                                                           |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### Tracker

          public Tracker(java.lang.String owner,
                         java.lang.String name,
                         OracleDataSource ods)
                  throws java.sql.SQLException,
                         JMSException

      Create a Tracker for accessing the tracking set owner.name on the database. After setting up options, call begin() to activate.
      This object must only be used by a single thread. use `Tracker(Tracker)` to duplicate this for use in a separate thread.

      Parameters:
      `owner` - the owner (schema) of the queue

      `name` - the name of this tracker

      `ods` - Oracle data source

      Throws:
      `java.sql.SQLException` - for problems communicating with the database

      `JMSException` - from database

  <!-- -->

  - ### Method Detail

    - #### newSession

          public Tracker newSession()
                             throws JMSException,
                                    java.sql.SQLException

      Create a duplicate of this tracker with its own session (each thread needs its own session). All other data (including callback settings, location and notification queues) is shared. Note that callbacks may be processed by any thread or worker requesting notifications.
      The alternative of creating a separate tracker with `new Tracker(...)` will result in separate queues and callbacks on the client side and may reduce efficiency.

      Returns:
      new Duplicate tracker suitable for use in a separate thread

      Throws:
      `JMSException` - on database error

      `java.sql.SQLException` - on database error

    <!-- -->

    - #### createWorkerThread

          public java.lang.Thread createWorkerThread(Tracker.WorkerType workerType,
                                                     java.util.function.BooleanSupplier exitFlag)
                                              throws JMSException,
                                                     java.sql.SQLException

      Create a new session of this tracker usable as a worker thread. All other data (including callback settings, location and notification queues) is shared. Note that callbacks may be processed by any thread requesting notifications.
      Caller is responsible for calling Thread.start() on the returned object.

      To terminate thread, arrange for exitFlag to return true and interrupt the thread.

      Parameters:
      `workerType` - the type of worker to create

      `exitFlag` - worker will run until this lambda returns true (typically refers to a volatile boolean)

      Returns:
      new Duplicate tracker suitable for use in a separate thread

      Throws:
      `JMSException` - on database error

      `java.sql.SQLException` - on database error

    <!-- -->

    - #### setNumLocationQueues

          public void setNumLocationQueues(int numLocationQueues)

      Set the number of location queues we should use when creating a new tracking set on the database. Does not affect an existing tracking set.
      Parameters:
      `numLocationQueues` - the number of queues to create

    <!-- -->

    - #### setNumTrackingQueues

          public void setNumTrackingQueues(int numTrackingQueues)

      Set the number of tracking queues we should use when creating a new tracking set on the database. Does not affect an existing tracking set.
      Parameters:
      `numTrackingQueues` - the number of queues to create

    <!-- -->

    - #### allowRegionCallbacks

          public Tracker allowRegionCallbacks(boolean allowed)

      Whether or not per-region callbacks will be used in this Tracker. There is some minimal overhead
      Parameters:
      `allowed` - set true to allow per-region callbacks to be set

      Returns:
      this Tracker

    <!-- -->

    - #### setNotificationQueueSize

          public void setNotificationQueueSize(int maxSize)

      The number of notifications without callbacks to store before discarding the oldest
      Parameters:
      `maxSize` - maximum number of unprocessed notifications to store; older ones will be dropped to make room for new.

    <!-- -->

    - #### allowObjectCallbacks

          public Tracker allowObjectCallbacks(boolean allowed)

      Whether or not per-object callbacks will be used in this Tracker. There is some minimal overhead.
      Parameters:
      `allowed` - true to allow per-object callbacks to be set

      Returns:
      this Tracker

    <!-- -->

    - #### debugOutput

          public static void debugOutput(java.io.PrintStream ps)

      Copy debugging output to the given print stream, in addition to its normal output location. Logging level must also be set. This setting is global for all Tracker objects.
      Example usage


           Tracker.debugOutput(Sysetm.err);
           Tracker.debugLevel(3);



      Parameters:
      `ps` - the print stream to log to

    <!-- -->

    - #### debugLevel

          public static void debugLevel(int level)

      Set level of debug output (overriding any system value). Recommend setting this before creating Tracker objects. This setting is global for all Tracker objects.
      Parameters:
      `level` - Zero (most detailed) through 9 (fatal errors only). Three is a good starting point.

    <!-- -->

    - #### stopTrackingSet

          public Tracker stopTrackingSet()
                                  throws java.sql.SQLException

      Stop the tracker on the database.
      Returns:
      this Tracker

      Throws:
      `java.sql.SQLException` - from database operation

    <!-- -->

    - #### startTrackingSet

          public Tracker startTrackingSet(boolean createIfNecessary)
                                   throws java.sql.SQLException,
                                          JMSException

      Connect to an existing tracking set on the database; optionally create if it doesn't already exist. Then start it on the database if not already started.
      Parameters:
      `createIfNecessary` - if true and tracking set doesn't exist on database, create one

      Returns:
      this Tracker

      Throws:
      `java.sql.SQLException` - from database operation

      `JMSException` - from database operation

    <!-- -->

    - #### begin

          public Tracker begin()
                        throws java.sql.SQLException,
                               JMSException

      Marks the end of setup. After this call, can send locations, receive notifications, set tracking regions and subscribe to notifications, and create new sessions and workers.
      Returns:
      this Tracker

      Throws:
      `java.sql.SQLException` - from database operation

      `JMSException` - from database operation

    <!-- -->

    - #### stopDrop

          public Tracker stopDrop()
                           throws java.sql.SQLException

      Stop (if running) and drop the tracker on the database, cleaning up all database resources. Should not be followed by any operation other than close().
      Returns:
      this Tracker

      Throws:
      `java.sql.SQLException` - from database operation

    <!-- -->

    - #### createTrackingSet

          public Tracker createTrackingSet()
                                    throws java.sql.SQLException

      Create the tracker on the database. Does not issue a `startTrackingSet(boolean)`. It is an error if the tracker already exists.
      Returns:
      this Tracker

      Throws:
      `java.sql.SQLException` - from database operation

    <!-- -->

    - #### setTrackingRegion

          public Tracker setTrackingRegion(long regionId,
                                           JGeometry geom)
                                    throws java.sql.SQLException,
                                           JMSException

      Set a tracking region on the server.
      Parameters:
      `regionId` - an integer identifying the region

      `geom` - the corresponding geometry (polygon or multipolygon)

      Returns:
      this tracker

      Throws:
      `java.sql.SQLException` - on database error

      `JMSException` - on database error

    <!-- -->

    - #### deleteTrackingRegion

          public Tracker deleteTrackingRegion(long regionId,
                                              boolean deleteNotifications)
                                       throws java.sql.SQLException,
                                              JMSException

      Delete a tracking region. Tracker must be started before any region or location operations.
      Parameters:
      `regionId` - the ID of the region to remove

      `deleteNotifications` - if true, subscriptions matching the regionId are also deleted

      Returns:
      this Tracker

      Throws:
      `java.sql.SQLException` - on database error

      `JMSException` - on database error

    <!-- -->

    - #### deleteObjectSubscription

          public Tracker deleteObjectSubscription(long objectId,
                                                  java.lang.Long regionId)
                                           throws java.sql.SQLException,
                                                  JMSException

      Delete notifications for a tracked object. Tracker must be started before any region or location operations.
      Parameters:
      `objectId` - the ID of the object to no longer track

      `regionId` - the ID of a particular region, or null for all regions

      Returns:
      this Tracker

      Throws:
      `java.sql.SQLException` - on database error

      `JMSException` - on database error

    <!-- -->

    - #### location

          public void location(long objId,
                               double x,
                               double y,
                               java.sql.Timestamp timestamp)
                        throws java.sql.SQLException,
                               JMSException

      Queues a location message to be sent to the server. You must separately send the queued messages, either by calling sendLocations() from this Tracker or any of its duplicate sessions, or by creating a worker thread, `createWorkerThread(WorkerType.LOCATION_WORKER, flag).start()`.
      Parameters:
      `objId` - the object's ID

      `x` - the x-value of the location

      `y` - the y-value of the location

      `timestamp` - the timestamp of this location message

      Throws:
      `java.sql.SQLException` - from database

      `JMSException` - from database

    <!-- -->

    - #### location

          public void location(long objId,
                               double x,
                               double y)
                        throws java.sql.SQLException,
                               JMSException

      Same as calling `location(objId, x, y, new Timestamp(System.currentTimeMillis())`. See description there.
      Parameters:
      `objId` - the object's ID

      `x` - the x-value of the location

      `y` - the y-value of the location

      Throws:
      `java.sql.SQLException` - from database

      `JMSException` - from database

    <!-- -->

    - #### sendLocations

          public void sendLocations()
                             throws JMSException,
                                    java.sql.SQLException

      Send any queued locations to the server. Necessary if there is no LOCATION worker thread processing the queue.
      Throws:
      `JMSException` - from database operation

      `java.sql.SQLException` - from database operation

    <!-- -->

    - #### setNotification

          public Tracker setNotification(long objId,
                                         long regionId,
                                         Tracker.NotificationType type)
                                  throws java.sql.SQLException,
                                         JMSException

      Subscribe to notifications about a particular object/region pair
      Parameters:
      `objId` - an integer identifying the object to be notified about

      `regionId` - an integer identifying the region

      `type` - INSIDE/OUTSIDE/TRANSITION

      Returns:
      this tracker

      Throws:
      `java.sql.SQLException` - on database error

      `JMSException` - on database error

    <!-- -->

    - #### setNotification

          public Tracker setNotification(TrackerMsg msg)
                                  throws java.sql.SQLException,
                                         JMSException

      Add a single subscription to the database
      Parameters:
      `msg` - the subscription

      Returns:
      this tracker

      Throws:
      `java.sql.SQLException` - on database error

      `JMSException` - on database error

    <!-- -->

    - #### setNotifications

          public Tracker setNotifications(java.util.List<TrackerMsg> subscriptionList)
                                   throws java.sql.SQLException,
                                          JMSException

      Set multiple subscriptions on the server.
      Parameters:
      `subscriptionList` - the list of subscriptions

      Returns:
      this tracker

      Throws:
      `java.sql.SQLException` - on database error

      `JMSException` - on database error

    <!-- -->

    - #### setRegionCallback

          public void setRegionCallback(long regionId,
                                        Tracker.Callback<NotificationMsg> callback)

      When a notification occurs for the given regionId, forward the notification to the specified callback method.
      You must also do `setNotification(objectId, regionId, NotificationType)` for every (object, region) combination you want the server to notify you of.

      This method is thread-safe and may be called before or after begin (but after allowRegionCallbacks)

      Parameters:
      `regionId` - the region we are interested in

      `callback` - the method to call when we have a notification for regionId, or null to delete any existing callback for regionId

    <!-- -->

    - #### setObjectCallback

          public void setObjectCallback(long objectId,
                                        Tracker.Callback<NotificationMsg> callback)

      When a notification occurs for the given objectId, forward the notification to the specified callback method.
      You must also do `setNotification(objectId, regionId, NotificationType)` for every (region, object) combination you want the server to notify you of.

      This method is thread-safe and may be called before or after begin (but after allowObjectCallbacks)

      Parameters:
      `objectId` - the object we are interested in

      `callback` - the method to call when we have a notification for objectId, or null to remove any existing callback for objectId

    <!-- -->

    - #### setCallback

          public void setCallback(Tracker.Callback<NotificationMsg> callback)

      Set a callback for all notifications that are not otherwise covered by a region or object callback.
      If this is set, no notifications will be returned by `getNotification()` or `getNotifications(long)`. Those calls are still useful for pulling notifications from the server and processing them if you are not using a NOTIFICATION worker.

      This method is thread-safe and may be called at any time.

      Parameters:
      `callback` - the callback to execute, or null to remove an existing callback

    <!-- -->

    - #### getNotifications

          public java.util.List<NotificationMsg> getNotifications(long waitMs)
                                                           throws JMSException,
                                                                  java.sql.SQLException

      Return all available notifications. If none are available, waits up to msWait for one to arrive. Arriving notifications are shared between duplicate sessions of this Tracker.
      Arriving notifications that match callbacks will be processed via those callbacks during this call and not returned.

      Parameters:
      `waitMs` - number of milliseconds to wait if none currently available: -1 means no wait, zero means infinite wait

      Returns:
      List of the received notifications (empty list if timed out waiting)

      Throws:
      `java.sql.SQLException` - propagated from database

      `JMSException` - propagated from database

    <!-- -->

    - #### getNotification

          public NotificationMsg getNotification(long waitMs)
                                          throws JMSException,
                                                 java.sql.SQLException

      Return one notification, waiting up to the specified time if there are no outstanding.
      Arriving notifications that match callbacks will be processed via those callbacks during this call and not returned. If all notifications match a callback, then this method will process notifications until the specified timeout. If you are using callbacks, consider using fetchNotifications() instead.

      Parameters:
      `waitMs` - length of time to wait (-1 = don't wait, 0 = wait forever)

      Returns:
      the notification, or null if none is available before the specified wait time

      Throws:
      `JMSException` - from database operation

      `java.sql.SQLException` - from database operation

    <!-- -->

    - #### getNotification

          public NotificationMsg getNotification()
                                          throws JMSException,
                                                 java.sql.SQLException

      Return one notification, blocking if there are no outstanding
      Arriving notifications that match callbacks will be processed via those callbacks during this call and not returned. If all notifications match a callback, then this method will process notifications forever. If you are using callbacks, consider using fetchNotifications() instead.

      Returns:
      the notification

      Throws:
      `JMSException` - from database operation

      `java.sql.SQLException` - from database operation

    <!-- -->

    - #### fetchNotifications

          public int fetchNotifications(long waitMs)
                                 throws JMSException,
                                        java.sql.SQLException

      Fetch notification(s) from the database, waiting at most the specified time for the first one to arrive. Callback processing is done; notifications without callbacks are queued for calls to getNotification() to return (either in this session or a different session).
      fetchNotificaitons processes all notifications that have arrived (or arrive while it is processing) regardless of how long that takes, as long as the additional notifications are available without waiting.

      Parameters:
      `waitMs` - length of time to wait (-1 = don't wait, 0 = wait forever)

      Returns:
      the number of messages fetched

      Throws:
      `JMSException` - from database operation

      `java.sql.SQLException` - from database operation

    <!-- -->

    - #### close

          public void close()
                     throws JMSException,
                            java.sql.SQLException

      Close the connection to the database and release the client resources and database connections. The tracking set on the server is not stopped nor dropped.
      No further method calls can be made to this object after close(). Close() must be called on each Tracker object, since each has its own connection to the database.

      Throws:
      `JMSException` - on database error

      `java.sql.SQLException` - on database error

    <!-- -->

    - #### finalize

          public void finalize()
                        throws java.lang.Throwable

      Overrides:
      `finalize` in class `java.lang.Object`

      Throws:
      `java.lang.Throwable`

    <!-- -->

    - #### getStatistics

          public java.util.Map<java.lang.String,java.lang.Long> getStatistics()

      Return statistics. Note that some statistics are not synchronized and may be inaccurate in a multi-threaded environment.
      The values reported and the labels given may change without notice. These are intended as a human-readable debugging aid.

      **List of statistics collected**

      |                                               |                                                                                                          |
      |-----------------------------------------------|----------------------------------------------------------------------------------------------------------|
      | maxQueuedLocations                            | The high-water mark of locations waiting transmission to server                                          |
      | notificationQueue current size                | Current number of notifications waiting for the user to read (excludes anything that matches a callback) |
      | notificationQueue maxQueueSizeSeen            | High-water mark of the notification queue                                                                |
      | notificationQueue numBatchLargerThanSizeLimit | Number of times a single insertion with more than sizeLimit notifications was attempted                  |
      | notificationQueue numQueued                   | Number of notifications inserted into the queue                                                          |
      | notificationQueue numRemoved                  | Number of notifications retrieved by the user                                                            |
      | notificationQueue numSurplus                  | Number of notifications discarded due to reaching sizeLimit                                              |
      | notificationQueue sizeLimit                   | Maximum number of notifications stored before discarding oldest                                          |
      | numGeneralCallbacks (approx)                  | Number of notifications that went through the general callback instead of being queued                   |
      | numLocations                                  | Number of location calls made                                                                            |
      | numMaxBatches                                 | Locations are batched to server, up to a maximum size; this is the number of maximum-sized batches sent  |
      | numObjectCallbacks (approx)                   | Number of notifications that matched an objectId callback                                                |
      | numObjectRegionCallbacks (approx)             | Number of notifications that matched both an objectId and regionId callback                              |
      | numRegionCallbacks (approx)                   | Number of notifications that matched a regionId callback                                                 |
      | unsentLocations                               | Locations not yet sent to the server                                                                     |

      Returns:
      a map of statistics.

    <!-- -->

    - #### getOwner

          public java.lang.String getOwner()

      Return the database schema of this tracker.
      Returns:
      the schema

    <!-- -->

    - #### getName

          public java.lang.String getName()

      Returns:
      the name of the tracking set

    <!-- -->

    - #### trackingsetExists

          public boolean trackingsetExists()

      Indicates whether a tracking set of the given name has been created on the server, whether by us or from a previously existing tracker.
      Returns:
      cached value indicating whether tracking set of this name existed on the server at last check

    <!-- -->

    - #### getNotificationQueueSize

          public int getNotificationQueueSize()

      The number of notifications without callbacks to store before discarding the oldest
      Returns:
      max size of the incoming notification queue.

    <!-- -->

    - #### getNumLocationQueues

          public int getNumLocationQueues()

      If a tracking set of this name appears on the server, then this will return the number of location queues it has. Otherwise, returns the number of location queues we would create.
      Returns:
      num of location queues, at least one.

    <!-- -->

    - #### getNumTrackingQueues

          public int getNumTrackingQueues()

      If a tracking set of this name appears on the server, then this will return the number of tracking queues it has. Otherwise, returns the number of tracking queues we would create.
      Returns:
      num of tracking queues, at least one.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- Prev Class
- [Next Class](Tracker.Callback.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
