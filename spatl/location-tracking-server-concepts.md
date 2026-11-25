## 8 Location Tracking Server

The Oracle Spatial and Graph location tracking server enables you to define regions, track the movement of objects into or out of those regions, and receive notifications when certain movements occur.

For reference information about location tracking PL/SQL subprograms, see [SDO_TRKR Package (Location Tracking)](SDO_TRKR-reference.md).

- About the Location Tracking Server
  As location becomes an increasingly important aspect of our lives, and as location-sensing devices become ubiquitous, there is an increasing demand for applications to be able to monitor subscriber location data continuously. The monitoring of the location data may translate into alerts being generated in the system.
- Location Tracking Set
  The location tracking server tracks a set of moving objects against a known set of regions and generates notifications as required. In this framework, the set of objects and regions is referred to as a tracking set.
- Data Types for the Location Tracking Server
  The PL/SQL subprograms associated with location tracking have parameters of data types that are specific to the location tracking server.
- Data Structures for the Location Tracking Server
  The location tracking server requires the user to specify a tracking set name when the server is created. Based on this name, additional data structures are created.
- Workflow for the Location Tracking Server
  The typical location tracking workflow involves several operations, some required and others optional.

**Parent topic:** [Conceptual and Usage Information](spatial-concepts-usage.md)

### 8.1 About the Location Tracking Server

As location becomes an increasingly important aspect of our lives, and as location-sensing devices become ubiquitous, there is an increasing demand for applications to be able to monitor subscriber location data continuously. The monitoring of the location data may translate into alerts being generated in the system.

For example, a trucking company may want to monitor its network of 10,000 trucks as they move along their specified routes towards their destinations. They may want to track the movement of trucks within a specified range of the route and expect notifications to be generated to detect undesirable deviations the vehicles from their desired routes. Proactive location-based services (LBSs) generalize such applications that track locations of subscribers inside or outside a specified region for various purposes, such as location-based advertising and notifications about friends nearby.

The Oracle Spatial and Graph location tracking server provides:

- A simple framework for setting up a location tracking network within the database through a PL/SQL interface

- An API for continuous location monitoring of objects within a tracking network

- A queuing mechanism for incoming location updates and tracking requests and for outgoing relevant notifications, using Oracle Advanced Queuing

- Efficient, continuous location monitoring for thousands of relevant objects within the database

**Parent topic:** Location Tracking Server

### 8.2 Location Tracking Set

The location tracking server tracks a set of moving objects against a known set of regions and generates notifications as required. In this framework, the set of objects and regions is referred to as a tracking set.

In the database these are managed in a table with two columns:

    region_id  NUMBER,
    geometry   SDO_GEOMETRY

REGION_ID is the primary key for this table, and GEOMETRY is the geometry of the tracking region.

Several additional structures are created when you create a tracking set. You can create any number of tracking sets, and each tracking set can have thousands of regions. When a region is no longer of interest for tracking purposes, it should be deleted from the tracking regions table.

A set of objects to be tracked also needs to be created. Each object must specify an ID for the object and a region ID to specify the region in which this object is tracked. That is, each object can be tracked against one or more tracking regions. An object is created by inserting a tracker message, `TRACKER_MSG`, into a tracking queue.

A tracker message object specifies the `object_id`, `region_id`, and `operation`. The `operation` parameter has one of the following string values.

- `I`: A notification message is issued every time an object, defined by `object_id`, moves while inside the region, defined by` region_id`

- `O`: A notification message is issued every time an object, defined by `object_id`, moves while outside the region, defined by ` region_id`.

- `T`: A notification message is issued only when the object, defined by `object_id`, transitions from inside to outside or from outside to inside the region defined by ` region_id`.

- `D`: Disables the tracking of an object defined by `object_id` in the region defined by ` region_id`. To enable tracking of this object again, another tracking message must be sent.

After the objects are created and tracking regions configured, new location messages for the objects can be sent. As objects move in space, their locations change. Every time a new location message is sent, it is inserted into the location message queue, to be processed by the location tracking server. Location messages are processed and notification messages are generated as required. Applications can monitor the notification queue and process the notification messages whenever new notifications are generated.

The following additional grants are required for a user to run the location tracking server.

    GRANT aq_administrator_role, create job, manage scheduler to <USER>; grant execute on dbms_aq to <USER>;
    GRANT execute on dbms_aqadm to <USER>;
    GRANT execute on dbms_lock to  <USER>;
    GRANT execute on dbms_aqin to  <USER>;
    GRANT execute on dbms_aqjms to <USER>;

**Parent topic:** Location Tracking Server

### 8.3 Data Types for the Location Tracking Server

The PL/SQL subprograms associated with location tracking have parameters of data types that are specific to the location tracking server.

These subprograms are documented in the [SDO_TRKR Package (Location Tracking)](SDO_TRKR-reference.md). The specific data types have the following definitions:

- LOCATION_MSG

      (object_id INTEGER,
       time      TIMESTAMP,
       x         NUMBER,
       y         NUMBER)

- LOCATION_MSG_ARR

      VARRAY(1000) of location_msg

- LOCATION_MSG_PKD

      object(arr location_msg_arr)

- NOTIFICATION_MSG

      (object_id INTEGER,
       region_id INTEGER,
       time      TIMESTAMP,
       x         NUMBER,
       y         NUMBER,
       state     VARCHAR2(8))

- PROC_MSG

      (object_id  INTEGER,
       time       TIMESTAMP,
       x          NUMBER,
       y          NUMBER,
       region_id  INTEGER,
       alert_when VARCHAR2(2))

- PROC_MSG_ARR

      VARRAY(1000) of proc_msg

- PROC_MSG_PKD

      object(arr proc_msg_arr)

- TRACKER_MSG

      (object_id INTEGER,
       region_id INTEGER,
       operation VARCHAR2(2))

**Parent topic:** Location Tracking Server

### 8.4 Data Structures for the Location Tracking Server

The location tracking server requires the user to specify a tracking set name when the server is created. Based on this name, additional data structures are created.

- \<TS_NAME\>\_TRACKING_REGIONS (region_id NUMBER, geometry MDSYS.SDO_GEOMETRY) is a table containing the tracking region polygons defined in the tracking set \<TS_NAME\>. Users must insert the polygons into this table after the server is created. All of the polygons must be geodetic (using SRID 8307) and two dimensional. The table has a primary key defined on the REGION_ID column.

- \<TS_NAME\>\_TRACKER (object_id NUMBER, region_id NUMBER, queue_no NUMBER, alert_when VARCHAR2(2)) is a table whose entries map the relationship between an object and a region in which the object is tracked. The table has a primary key defined on the OBJECT_ID and REGION_ID columns. This table is managed using the TRACKER_MSG type; users should not update this table directly.

- \<TS_NAME\>\_TRACKER_QUEUES(num_loc_queues NUMBER, num_trkr_queues NUMBER) is a table that holds queue information needed by the server. The server populates and maintains this table; users should never modify this table.

- \<TS_NAME\>\_TRACKER_LOG (message_level VARCHAR2(1), message VARCHAR2(512), ts TIMESTAMP WITH TIMEZONE) is a table containing log messages generated by the server. Message level ‘I’ indicates an informational message, and message level ‘E’ indicates an error message. This table is not dropped when the tracking set is dropped. However, if a tracking set of the same name is then created, this table is truncated and reused by the new tracking set.

- \<TS_NAME\>\_NOTIFICATIONS (object_id NUMBER, region_id NUMBER, time TIMESTAMP, x NUMBER, y NUMBER, state VARCHAR2(8)) is an auxiliary table provided to users to store messages from the notifications queue. The layout of columns in this table match that of the NOTIFICATION_MSG type. The X and Y columns are the coordinate that prompted the notification for object_id in region_id at the time. The STATE column shows if the point INSIDE or OUTSIDE the region. For tracking types INSIDE and OUTSIDE this value never changes. For tracking type TRANSITION this column is the state of the object at the time it generated the notification.

- \<TS_NAME\>\_TRAJECTORY is an auxiliary table not currently used by the location tracking server.

In addition to these tables, the location tracking server also creates a set of Advanced Queuing (AQ) objects for managing the location, tracking and notification messages. All of the queues have a prefix of \<TS_NAME\>, for example. \<TS_NAME\>\_TRACKER_Q_1 and \<TS_NAME\>\_LOCATION_Q_1.

**Parent topic:** Location Tracking Server

### 8.5 Workflow for the Location Tracking Server

The typical location tracking workflow involves several operations, some required and others optional.

The typical workflow contains several steps:

1.  Create a tracking set.

2.  Optionally, show the tracking set tables that were created.

3.  Start the tracking set.

4.  Optionally, show the queues used by the tracking set.

5.  Optionally, show the Scheduler jobs used by the tracking set.

6.  Insert polygons for various regions.

7.  Create object-region pairs to be tracked.

8.  Optionally, show the object-region pairs in the tracking set.

9.  Send location messages.

10. Optionally, show the location messages that have been sent.

11. Dequeue the notification messages into the notifications table.

12. Optionally, disable the tracking server's object-region pairs.

13. Stop the tracking set.

14. Drop the tracking set.

The following is a simple example of the location tracking server workflow.

Example 8-1 Location Tracking Server Workflow

    -- Create a tracking set named sample with one tracker/process
    -- queue pair and one location queue.
    EXEC sdo_trkr.create_tracking_set('sample', 1, 1);

    -- Optional: Show the tracking sets tables that were created
    SELECT table_name
    FROM user_tables
    WHERE table_name LIKE ‘SAMPLE%’
    ORDER BY table_name;

    TABLE_NAME
    ----------------------
    SAMPLE_LOCATION_QT_1    - AQ queue table for location queue
    SAMPLE_NOTIFICATIONS    - Auxiliary table to store notification messages
    SAMPLE_NOTIFICATION_QT  - AQ queue table for the notification queue
    SAMPLE_PROC_QT_1        - AQ queue table for the process queue
    SAMPLE_TRACKER          - Table, will contain object-region tracking pairs
    SAMPLE_TRACKER_LOG      - Table, contains log messages from the server
    SAMPLE_TRACKER_QT_1     - AQ queue table for the tracker queue
    SAMPLE_TRACKER_QUEUES   - Table, contains tracking sets queue metadata
    SAMPLE_TRACKING_REGIONS - Table, will contain the regions geometry
    SAMPLE_TRAJECTORY       - Table, currently unused

    -- Start the tracking set
    EXEC sdo_trkr.start_tracking_set(‘sample’);

    -- Optional: Show the queues used by the tracking set
    SELECT name
    FROM user_queues
    WHERE name LIKE 'SAMPLE%'
    ORDER BY name;

    NAME
    ---------------------
    SAMPLE_LOCATION_Q_1
    SAMPLE_NOTIFICATION_Q
    SAMPLE_PROC_Q_1
    SAMPLE_TRACKER_Q_1

    -- Optional: Show the scheduler jobs used by the tracking set
    SELECT job_name, state
    FROM user_scheduler_jobs
    WHERE job_name LIKE 'SAMPLE%'
    ORDER BY job_name;

    JOB_NAME        STATE
    --------------------------
    SAMPLE_LOC_JOB_1   RUNNING
    SAMPLE_TRKR_JOB_1  RUNNING

    -- Insert a polygon for region 1. This polygon must be geodetic (using SRID 8307)
    -- and two dimensional. The region may also be a multi-polygon.
    INSERT INTO SAMPLE_TRACKING_REGIONS VALUES (1,
      MDSYS.SDO_GEOMETRY(2003, 8307, null,
        sdo_elem_info_array(1, 1003, 1),
        sdo_ordinate_array(0,0, 5,0, 5,5, 0,5, 0,0)));
    -- Create two objects, object 1 and 2 that are tracked in region 1.
    -- Object 1 sends notification messages when it is inside region 1.
    -- Object 2 sends notification messages when it is outside region 1.
    EXEC sdo_trkr.send_tracking_msg(
      'SAMPLE', mdsys.tracker_msg(1, 1, 'I'));
    EXEC sdo_trkr.send_tracking_msg(
      'SAMPLE', mdsys.tracker_msg(2, 1, 'O'));
    -- Optional: Show the object-region pairs used in the tracking set
    SELECT object_id, region_id, alert_when  FROM sample_tracker;

    OBJECT_ID  REGION_ID  ALERT_WHEN
    ---------- ---------- -----------
         1           1        I
         2           1        O

    -- Send 2 location messages.
    –- Object 1 moves to (1, 1).
    –- Object 2 moves to (8, 8).
    EXEC sdo_trkr.send_location_msgs('SAMPLE',
      mdsys.location_msg_arr(
        mdsys.location_msg(1, '01-AUG-16 01.01.46.000000 PM', 1, 1),
        mdsys.location_msg(2, '01-AUG-16 01.02.46.000000 PM', 8, 8)));

    -- Optional: Show that 2 notification message were generated
    SELECT a.name, b.ready
    FROM user_queues a, v$aq b
    WHERE a.name='SAMPLE_NOTIFICATION_Q' AND a.qid=b.qid
    ORDER BY a.name;

    NAME                   READY
    ---------------------- ------
    SAMPLE_NOTIFICATION_Q    2

    -- Dequeue the notification messages into the notifications table
    DECLARE
      message       mdsys.notification_msg;
    BEGIN
      LOOP
        sdo_trkr.get_notification_msg(
          tracking_set_name => 'SAMPLE',
          message => message,
          deq_wait =>2); -- wait at most 2 seconds for a message

        IF (message IS NULL) THEN
          EXIT;
        END IF;

        INSERT INTO sample_notifications (
                      object_id, region_id, time, x, y, state)
          (SELECT message.object_id, message.region_id,
                  message.time, message.x, message.y, message.state);
      END LOOP;
    END;
    -- Query the object id, region id, (x, y) coordinate and the objects
    -- relationship to the region sorted by the time that was sent with
    -- the objects location message.
    SELECT object_id, region_id, x, y, state
    FROM sample_notifications
    ORDER BY time;
    OBJECT_ID  REGION_ID    X   Y   STATE
    ---------- ---------- --- --- -------
      1       1         1   1   INSIDE
      2       1         8   8   OUTSIDE
    -- Optional: Disable the tracking server's object-region pairs
    EXEC sdo_trkr.send_tracking_msg('SAMPLE',
      mdsys.tracker_msg(1, 1, 'D'));
    EXEC sdo_trkr.send_tracking_msg('SAMPLE',
      mdsys.tracker_msg(2, 1, 'D'));
    -- Stop the tracking set. This stops the tracking sets
    -- queues and its scheduler jobs. Running stop_tracking_set
    -- does not delete the tables and queues used by the tracking
    -- server so start_tracking_set can be rerun and all of the
    -- object and region data is still available.
    -- This must be done before dropping a tracking set
    EXEC sdo_trkr.stop_tracking_set('sample');

    -- Drop the tracking set. This completely deletes the tracking
    -- sets queues and tables. Once completed all traces of the tracking
    -- set are removed except for the log table which is left intact for
    -- debugging purposes. If another tracking set of the same name is
    -- created the log table is truncated.
    EXEC sdo_trkr.drop_tracking_set('sample');

**Parent topic:** Location Tracking Server
