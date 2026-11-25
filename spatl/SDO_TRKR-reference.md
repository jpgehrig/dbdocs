## 33  SDO_TRKR Package (Location Tracking)

The MDSYS.SDO_TRKR package contains subprograms for using the location tracking server.

To use these subprograms, you must understand the concepts and techniques described in [Location Tracking Server](location-tracking-server-concepts.md).

- SDO_TRKR.CREATE_TRACKING_SET
- SDO_TRKR.DROP_TRACKING_SET
- SDO_TRKR.GET_NOTIFICATION_MSG
- SDO_TRKR.SEND_LOCATION_MSGS
- SDO_TRKR.SEND_TRACKING_MSG
- SDO_TRKR.START_TRACKING_SET
- SDO_TRKR.STOP_TRACKING_SET

**Parent topic:** [Reference Information](spatial-reference-information.md)

### 33.1 SDO_TRKR.CREATE_TRACKING_SET

#### Format

    SDO_TRKR.CREATE_TRACKING_SET(
      tracking_set_name  IN VARCHAR2,
      num_trkr_queues    IN NUMBER(38) DEFAULT 4,
      num_loc_queues     IN NUMBER(38) DEFAULT 1);

#### Description

Creates a tracking set, specifically the tables and queues required for the location tracking server.

#### Parameters

tracking_set_name
Name of the tracking set.

num_trkr_queues
Number of queues to create to manage the tracking messages. The default value for this parameter is 4. For large numbers of regions in the tracking regions table, more tracker queues may improve performance. For every tracker queue created a scheduler job is also created, so the number of tracker queues should also be balanced with system resources.

num_loc_queues
Number of queues to create to manage the location messages. The default value for this parameter is 1. If a large number of objects are being tracked, more location queues may improve performance. For every location queue created a scheduler job is also created, so the number of location queues should also be balanced with system resources.

#### Usage Notes

This procedure creates the necessary tables and queues required for the location tracking server. This is the first step required for enabling the location tracking server

For conceptual and usage information about the location tracking server, see [Location Tracking Server](location-tracking-server-concepts.md).

#### Examples

The following example creates a tracking network named TRACKING_EXAMPLE with 8 tracking queues and 8 location queues.

    EXECUTE SDO_TRKR.CREATE_TRACKING_SET('TRACKING_EXAMPLE', 8, 8);

**Parent topic:** SDO_TRKR Package (Location Tracking)

### 33.2 SDO_TRKR.DROP_TRACKING_SET

#### Format

    SDO_TRKR.DROP_TRACKING_SET(
       tracking_set_name  IN VARCHAR2);

#### Description

Drops a tracking set. This removes the tables, queues, and jobs required for the location tracking server.

#### Parameters

tracking_set_name
Name of the tracking set.

#### Usage Notes

This procedure drops the tracking set that was created by a previous call to the SDO_TRKR.CREATE_TRACKING_SET procedure.

For conceptual and usage information about the location tracking server, see [Location Tracking Server](location-tracking-server-concepts.md).

#### Examples

The following example drops the previously created tracking set.

    EXECUTE SDO_TRKR.DROP_TRACKING_SET('TRACKING_EXAMPLE');

**Parent topic:** SDO_TRKR Package (Location Tracking)

### 33.3 SDO_TRKR.GET_NOTIFICATION_MSG

#### Format

    SDO_TRKR.GET_NOTIFICATION_MSG(
       tracking_set_name IN VARCHAR2,
       deq_wait          IN NUMBER(38) DEFAULT DBMS_AQ.NO_WAIT,
       message           OUT NOTIFICATION_MSG);

#### Description

Gets the next notification message from the tracking sets notification queue.

#### Parameters

tracking_set_name
Name of the tracking set. This parameter is used to build the name of the notification queue.

deq_set_wait
Number of seconds to wait for a message to arrive on the notification queue if no message matching the search criteria is not already on the queue. The DEFAULT for this parameter is DBMS_AQ.NO_WAIT, which means that the operation does not wait.

message
Output parameter of type NOTIFICATION_MSG. The next message from the notification queue, or null if the wait time expired.

#### Usage Notes

For conceptual and usage information about the location tracking server, see [Location Tracking Server](location-tracking-server-concepts.md).

#### Examples

The following example gets a notification message from the tracking sets notification queue and inserts the contents of the message into the tracking set auxiliary notification table. It will continue to get notification messages until it waits for 30 seconds with no messages arriving.

    ...
     LOOP
       SDO_TRKR.GET_NOTIFICATION_MSG(
         tracking_set_name => 'TRACKING_EXAMPLE',
         message => message,
         deq_wait =>30);
       IF (message IS NULL) THEN
         EXIT;
       END IF;
       INSERT INTO tracking_example_notifications (object_id, region_id,
                                                   time, x, y, state)
       VALUES (message.object_id,
               message.region_id,
               message.time,
               message.x,
               message.y,
               message.state);
     END LOOP;
    ...

**Parent topic:** SDO_TRKR Package (Location Tracking)

### 33.4 SDO_TRKR.SEND_LOCATION_MSGS

#### Format

    SDO_TRKR.SEND_LOCATION_MSGS(
       tracking_set_name IN VARCHAR2,
       location_msgs     IN LOCATION_MSG_ARR );

#### Description

Sends an array of new location information for objects that are being tracked in the tracking set.

#### Parameters

tracking_set_name
Name of the tracking set.

location_msgs
A message of type LOCATION_MSG_ARR.

queue_no
The specific location queue that should be used for this location message. It is recommended that you not specify this parameter, in which case the tracking server determine the best queue for managing this location message.

#### Usage Notes

This procedure adds a new location message for tracking purposes. Whenever a new location is obtained for an object that is being tracked, this procedure can be used to update the location of that object.

The `location_msgs` parameter is of type LOCATION_MSG_ARR, which is defined in [Data Types for the Location Tracking Server](location-tracking-server-concepts.md).

Each message includes a timestamp value, which is the time of the update and is maintained along with the location information.

For conceptual and usage information about the location tracking server, see [Location Tracking Server](location-tracking-server-concepts.md).

#### Examples

The following example adds a new location message. The message includes the object id (1), the current time, and the X and Y ordinates (2, 2) of the object's new location

    EXECUTE SDO_TRKR.SEND_LOCATION_MSGS('TRACKING_EXAMPLE',  LOCATION_MSG_ARR(location_msg(1, CURRENT_TIMESTAMP(), 2,2)));

**Parent topic:** SDO_TRKR Package (Location Tracking)

### 33.5 SDO_TRKR.SEND_TRACKING_MSG

#### Format

    SDO_TRKR.SEND_TRACKING_MSG(
       tracking_set_name  IN VARCHAR2,
       tracking_msg  IN TRACKER_MSG );

#### Description

Inserts a tracking message into a tracking queue. One TRACKER_MSG is required for each object that is tracked. If object 1 is being tracked in regions 1, 2, and 3, then three TRACKER_MSGs are required, one for each object ID/region ID pair.

#### Parameters

tracking_set_name
Name of the tracking set.

tracking_msg
Message of type TRACKER_MSG. This is used to create a relationship between objects that are being tracked and the region or regions in which they are being tracked.

#### Usage Notes

This procedure creates new row in the tracker table that tells the location tracker server what objects are being tracked within what regions.

The `tracking_ms` parameter is of type TRACKER_MSG, which is defined in [Data Types for the Location Tracking Server](location-tracking-server-concepts.md).

For conceptual and usage information about the location tracking server, see [Location Tracking Server](location-tracking-server-concepts.md).

#### Examples

The following example inserts a new tracking object with an ID of 4 to be tracked against a region with an ID of 8 in the tracking set named TRACKING_EXAMPLE. Notification messages are sent when the object is inside (`I`) the region. If `O` had been specified notifications would have been sent with the object was outside the region, and if `T` had been specified, notifications would only be sent when the object transitions into or out of the region.

    EXECUTE SDO_TRKR.SEND_TRACKING_MSG('TRACKING_EXAMPLE', TRACKER_MSG(4, 8, 'I'));

**Parent topic:** SDO_TRKR Package (Location Tracking)

### 33.6 SDO_TRKR.START_TRACKING_SET

#### Format

    SDO_TRKR.START_TRACKING_SET(
     tracking_set_name  IN VARCHAR2);

#### Description

Starts the queues for the location tracking server and starts jobs to monitor those queues.

#### Parameters

tracking_set_name
Name of the tracking set.

#### Usage Notes

This procedure starts the tracking set that has been previously created by a call to the SDO_TRKR.CREATE_TRACKING_SET procedure.

For conceptual and usage information about the location tracking server, see [Location Tracking Server](location-tracking-server-concepts.md).

#### Examples

The following example starts the tracking set that was previously created.

    EXECUTE SDO_TRKR.START_TRACKING_SET('TRACKING_EXAMPLE');

**Parent topic:** SDO_TRKR Package (Location Tracking)

### 33.7 SDO_TRKR.STOP_TRACKING_SET

#### Format

    SDO_TRKR.STOP_TRACKING_REGIONS(
     tracking_set_name  IN VARCHAR2 );

#### Description

Stops the queues for the location tracking server and stops the jobs that monitor those queues.

#### Parameters

traxking_set_name
Name of the tracking set.

#### Usage Notes

This procedure stops the tracking network that was previously started by a call to the SDO_TRKR.START_TRACKING_SET procedure.

For conceptual and usage information about the location tracking server, see [Location Tracking Server](location-tracking-server-concepts.md).

#### Examples

The following example stops the tracking set that was previously started.

    EXECUTE SDO_TRKR.STOP_TRACKING_REGIONS('TRACKING_EXAMPLE');

**Parent topic:** SDO_TRKR Package (Location Tracking)
