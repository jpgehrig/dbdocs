Certain applications may be interested in knowing what Workspace Manager operations are being performed and may want to take some actions based on that. Several types of Workspace Manager operations can be captured as events.

Workspace Manager provides a framework for communicating these events asynchronously to the interested applications. The applications can then take some actions based on the event. Some scenarios in which events can be used include the following:

- An application wants to be notified whenever a workspace is merged to LIVE so that it can refresh its data.

- Workspace data needs to be archived whenever a new savepoint is created.

The Workspace Manager event framework is built on the Oracle Advanced Queuing (AQ) capability. Messaging features provided by AQ, such as asynchronous notification, persistence, propagation, access control, history, and rule-based subscription, can be used for Workspace Manager events.

Workspace Manager creates a multiconsumer queue where events are enqueued. The relevant information about the event, such as the type of event, the user and workspace that triggered the event, and the name of the versioned table, is initialized in the event payload and enqueued. Applications can subscribe to these events, optionally specifying a rule for their subscriptions. Only the events that satisfy the rule will be applicable to the subscriber. Subscribers can get event notification in variety of ways, such as listening for the events in the queue, registering a callback for notification, or explicitly dequeuing events from the queue.

Because events are communicated asynchronously to the other applications, the performance of the workspace operation generating the event is not affected.

**Note:**

To use Workspace Manager events in an application, you must understand the relevant AQ concepts and techniques described in [Oracle Database Advanced Queuing User's Guide](../adque/aq-introduction.md).

This chapter contains the following major sections:

- List of Workspace Manager Events
  The following table lists the Workspace Manager events and when each occurs.
- Event Parameters
  When an event occurs, information is stored in parameters that are bundled into an object type called `WMSYS.WM$EVENT_TYPE` and enqueued into the event queue. A subscriber can dequeue the event object on receiving notification.
- ALLOW_CAPTURE_EVENTS System Parameter
  The Workspace Manager system parameter `ALLOW_CAPTURE_EVENTS` can be used to capture events.
- AQ Operations and Workspace Manager Events
  This section describes Advanced Queuing objects and techniques relevant to developers of applications that work with captured Workspace Manager events.

**Parent topic:** [Conceptual and Usage Information](workspace-manager-concepts-usage.md)

### 2.1 List of Workspace Manager Events

The following table lists the Workspace Manager events and when each occurs.

Table 2-1 Workspace Manager Events

| Event                      | Occurs                                                                                                                                                                                                   |
|:---------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| TABLE_MERGE_W_REMOVE_DATA  | When [MergeTable](DBMS_WM-reference.md) is invoked with `remove_data` set to `TRUE`.                                                                                                                     |
| TABLE_MERGE_WO_REMOVE_DATA | When [MergeTable](DBMS_WM-reference.md) is invoked with `remove_data` set to `FALSE`.                                                                                                                    |
| TABLE_REFRESH              | When [RefreshTable](DBMS_WM-reference.md) is invoked.                                                                                                                                                    |
| TABLE_ROLLBACK             | When [RollbackTable](DBMS_WM-reference.md) is invoked.                                                                                                                                                   |
| WORKSPACE_COMPRESS         | When [CompressWorkspace](DBMS_WM-reference.md) or [CompressWorkspaceTree](DBMS_WM-reference.md) is invoked.                                                                                              |
| WORKSPACE_CREATE           | When [CreateWorkspace](DBMS_WM-reference.md) is invoked.                                                                                                                                                 |
| WORKSPACE_MERGE_W_REMOVE   | When [MergeWorkspace](DBMS_WM-reference.md) is invoked with `remove_workspace` set to `TRUE`.                                                                                                            |
| WORKSPACE_MERGE_WO_REMOVE  | When [MergeWorkspace](DBMS_WM-reference.md) is invoked with `remove_workspace` set to `FALSE`.                                                                                                           |
| WORKSPACE_REFRESH          | When [RefreshWorkspace](DBMS_WM-reference.md) is invoked.                                                                                                                                                |
| WORKSPACE_REMOVE           | When [RemoveWorkspace](DBMS_WM-reference.md) or [RemoveWorkspaceTree](DBMS_WM-reference.md) is invoked.                                                                                                  |
| WORKSPACE_ROLLBACK         | When [RollbackWorkspace](DBMS_WM-reference.md) is invoked.                                                                                                                                               |
| WORKSPACE_VERSION          | When a new version is created in the workspace as a result of the creation of an explicit or implicit savepoint. (Savepoints are described in [Using Savepoints](introduction-to-workspace-manager.md).) |

**Parent topic:** Workspace Manager Events

### 2.2 Event Parameters

When an event occurs, information is stored in parameters that are bundled into an object type called `WMSYS.WM$EVENT_TYPE` and enqueued into the event queue. A subscriber can dequeue the event object on receiving notification.

The following table describes the Workspace Manager event parameters.

Table 2-2 Workspace Manager Event Parameters

| Event Parameter       | Data Type                                                              | Description                                                                                                                                                                                                                                                                                                                    |
|:----------------------|:-----------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| event_name            | `VARCHAR2(128)`                                                        | Name indicating the type of event.                                                                                                                                                                                                                                                                                             |
| workspace_name        | `VARCHAR2(128)`                                                        | Workspace that caused the event to occur.                                                                                                                                                                                                                                                                                      |
| parent_workspace_name | `VARCHAR2(128)`                                                        | Parent workspace of the workspace that caused the event to occur.                                                                                                                                                                                                                                                              |
| user_name             | `VARCHAR2(128)`                                                        | User that caused the event to occur.                                                                                                                                                                                                                                                                                           |
| table_name            | `VARCHAR2(128)`                                                        | Version-enabled table on which the event occurred. If this parameter does not apply to an event, it is null.                                                                                                                                                                                                                   |
| aux_params            | `WMSYS.WM$NV_PAIR_NT_TYPE` (which is table of `WMSYS.WM$NV_PAIR_TYPE`) | A nested table of (name,value) pairs that can contain additional information about the event.<br>For `TABLE_`xxxevents, it has one row containing the `WHERE` clause string used for the operation.<br>For `WORKSPACE_VERSION` events, it has one row containing the savepoint name associated with the newly created version. |

**Parent topic:** Workspace Manager Events

### 2.3 ALLOW_CAPTURE_EVENTS System Parameter

The Workspace Manager system parameter `ALLOW_CAPTURE_EVENTS` can be used to capture events.

Before you can capture any Workspace Manager events, you must use the [SetSystemParameter](DBMS_WM-reference.md) procedure to set the Workspace Manager system parameter `ALLOW_CAPTURE_EVENTS` to the value `ON`. This does not, however, cause any events to be captured; to capture events, you must use the [SetCaptureEvent](DBMS_WM-reference.md) procedure.

You can later disallow the capture of Workspace Manager events by using the [SetSystemParameter](DBMS_WM-reference.md) procedure to set `ALLOW_CAPTURE_EVENTS` to the value `OFF`, but you must first ensure that no events are currently being captured. Example 2-1 shows the sequence of procedure calls for enabling and disabling the capture of all events, and starting and stopping the capture all events.

Example 2-1 Capturing Workspace Manager Events

    -- Allow Workspace Manager events to be captured. (Required for SetCaptureEvent)
    EXECUTE DBMS_WM.SetSystemParameter ('ALLOW_CAPTURE_EVENTS', 'ON');
    -- Start capturing all Workspace Manager events.
    EXECUTE DBMS_WM.SetCaptureEvent ('ALL_EVENTS','ON');
       .
       .
       .
    -- Stop capturing all Workspace Manager events.
    EXECUTE DBMS_WM.SetCaptureEvent ('ALL_EVENTS','OFF');
    -- Disallow capture of Workspace Manager events.
    EXECUTE DBMS_WM.SetSystemParameter ('ALLOW_CAPTURE_EVENTS', 'OFF');

**Parent topic:** Workspace Manager Events

### 2.4 AQ Operations and Workspace Manager Events

This section describes Advanced Queuing objects and techniques relevant to developers of applications that work with captured Workspace Manager events.

- Workspace Manager Event Queue Administration
- Privileges and Access Control for Queues
- Rule-Based Subscription
- Listening for Events
- Asynchronous Notification

**Parent topic:** Workspace Manager Events

#### 2.4.1 Workspace Manager Event Queue Administration

Workspace Manager creates a multiconsumer queue named `WMSYS.WM$EVENT_QUEUE` based on a queue table named `WMSYS.WM$EVENT_QUEUE_TABLE`. The queue payload type is `WMSYS.WM$EVENT_TYPE`, which is an object type.

AQ creates some views for the queue that can be used for administrative purposes. Table 2-3 describes the views of interest to developers of Workspace Manager applications.

Table 2-3 AQ Administrative Views for Workspace Manager

| View Name                         | Description                                                                                                                                                                                                                                                                                                                            |
|:----------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| WMSYS.AQ\$WM\$EVENT_QUEUE_TABLE   | Describes the queue table in which events are stored. This view can be used for querying the events. The `AQ_ADMINISTRATOR_ROLE` role and the `WM_ADMIN` system privilege are granted select privileges on this view.                                                                                                                  |
| WMSYS.AQ\$WM\$EVENT_QUEUE_TABLE_S | Displays all the subscribers for the event queue; also displays the transformation for the subscriber if it was created with one. The `AQ_ADMINISTRATOR_ROLE` role and the `WM_ADMIN` system privilege are granted select privileges on this view.                                                                                     |
| WMSYS.AQ\$WM\$EVENT_QUEUE_TABLE_R | Displays only the rule-based subscribers for all queues in a given queue table, as well as the text of the rule defined by each subscriber. Also displays the transformation for the subscriber if one was specified. The `AQ_ADMINISTRATOR_ROLE` role and the `WM_ADMIN` system privilege are granted select privileges on this view. |

**Parent topic:** AQ Operations and Workspace Manager Events

#### 2.4.2 Privileges and Access Control for Queues

The database administrator has several options for granting privileges and access to queues. Some possible scenarios include:

- Grant the system privileges `ENQUEUE ANY QUEUE` and `DEQUEUE ANY QUEUE` directly to a database user by using the `DBMS_AQADM.GRANT_SYSTEM_PRIVILEGE` procedure, and optionally later revoke privileges by using the `DBMS_AQADM.REVOKE_SYSTEM_PRIVILEGE` procedure.

- Grant the queue privileges `ENQUEUE` and `DEQUEUE` to the event queue `WMSYS.WM$EVENT_QUEUE` to a database user by using the `DBMS_AQADM.GRANT_QUEUE_PRIVILEGE` procedure, and optionally later revoke privileges by using the `DBMS_AQADM.REVOKE_QUEUE_PRIVILEGE` procedure.

- Grant the role `AQ_ADMINISTRATOR_ROLE` to a database user to give that user administrative privileges on any queue.

Example 2-2 shows privileges being granted for a user to subscribe to the event queue and dequeue events.

Example 2-2 Granting Privileges for Queue Access

    -- Do the following while connected as SYSDBA.
    -- These privileges are required for the user to execute AQ packages.
    grant execute on DBMS_AQ to SCOTT ;
    grant execute on DBMS_AQADM to SCOTT ;

    -- Grant privilege to SCOTT for subscribing to the event queue.
    exec DBMS_AQADM.GRANT_SYSTEM_PRIVILEGE('MANAGE_ANY','SCOTT') ;

    -- Grant privilege to SCOTT to dequeue events. (As an alternative, you could use
    -- DBMS_AQADM.GRANT_QUEUE_PRIVILEGE to grant the DEQUEUE privilege on
    -- WMSYS.WM$EVENT_QUEUE.)
    exec DBMS_AQADM.GRANT_SYSTEM_PRIVILEGE('DEQUEUE_ANY','SCOTT') ;

**Parent topic:** AQ Operations and Workspace Manager Events

#### 2.4.3 Rule-Based Subscription

An event can be delivered to multiple recipients based on event parameters. You can define a rule-based subscription for the event queue as the mechanism for specifying interest in receiving events. Subscriber rules are then used to evaluate recipients for event delivery. A null rule indicates that the subscriber wishes to receive all events.

Example 2-3 creates a rule-based subscription for user SCOTT to deliver WORKSPACE_MERGE_WO_REMOVE events when the parent workspace is the `LIVE` workspace.

Example 2-3 Rule-Based Subscription for Workspace Manager Events

    rem =================================================
    rem Create queue subscribers
    rem Register for MergeWorkspace event when
    rem a workspace is merged to LIVE
    rem =================================================

    connect scott
    -- Enter password when prompted.

    DECLARE
        subscriber sys.aq$_agent;
    BEGIN
        subscriber := sys.aq$_agent('MERGE_LISTENER', NULL, NULL);
        dbms_aqadm.add_subscriber(
          queue_name => 'WMSYS.WM$EVENT_QUEUE',
          subscriber => subscriber,
          rule => 'tab.user_data.event_name = ''WORKSPACE_MERGE_WO_REMOVE''
                   and tab.user_data.parent_workspace_name = ''LIVE''');
    END;
    /

**Parent topic:** AQ Operations and Workspace Manager Events

#### 2.4.4 Listening for Events

The listen call is a blocking call that can be used to wait for events on a queue or a list of subscriptions. If the listen returns successfully, a dequeue must be used to retrieve the event.

Example 2-4 listens for events on an event queue.

Example 2-4 Listening for a Workspace Manager Event

    rem ==============================================================
    rem The following example shows how an application can listen for
    rem an event. Explicit dequeue must be performed to get the actual
    rem event parameters. The user SCOTT must have sufficient privileges
    rem as described in the "Access Control" section.
    rem ==============================================================

    connect scott
    -- Enter password when prompted.

    set serveroutput on

    DECLARE
     qlist dbms_aq.aq$_agent_list_t;
     agent_w_msg sys.aq$_agent;
     listen_timeout exception;
     pragma exception_init(listen_timeout, -25254);
    BEGIN
     qlist(0) := sys.aq$_agent('MERGE_LISTENER', 'WMSYS.WM$EVENT_QUEUE', NULL);

     dbms_output.put_line ('Listening on event queue.');

     BEGIN

     DBMS_AQ.LISTEN(
             agent_list => qlist,
             wait => 30,
             agent =>  agent_w_msg);

             dbms_output.put_line(agent_w_msg.name) ;

             /* The event can be dequeued here to get the event data */

     EXCEPTION
            when listen_timeout THEN
                    null;
     END;

    END;
    /

**Parent topic:** AQ Operations and Workspace Manager Events

#### 2.4.5 Asynchronous Notification

Asynchronous notification allows clients to receive notification of an event of interest. The client can use it to monitor multiple subscriptions. The client does not have to be connected to the database to receive notifications regarding its subscriptions.

If an application registers for asynchronous notification of Workspace Manager events using callbacks, the minimum values for the following `init.ora` parameters should be:

- `aq_tm_processes` = 1

- `job_queue_processes` = 2

Example 2-5 registers for a callback to receive asynchronous notification of events.

Example 2-5 Receiving Asynchronous Notification of Events

    rem =====================================================
    rem Example of how to register for a callback to the event
    rem queue on behalf of a subscriber. Subscriber has already
    rem been defined in previous section. The callback is
    rem invoked by the AQ framework whenever an event satisfying the
    rem rule for the subscriber occurs. The minimum values for
    rem the following init.ora parameters should be set as follows.
    rem   aq_tm_processes = 1
    rem   job_queue_processes = 2
    rem The user SCOTT must have sufficient privileges.
    rem ===========================================================

    CONNECT scott
    -- Enter password when prompted.

    CREATE TABLE merge_log
    (
      event_name      varchar2(128),
      workspace_name  varchar2(128),
      parent_workspace_name varchar2(128),
      user_name       varchar2(128)
    );

    CREATE OR REPLACE PROCEDURE scott.event_callback(
       context RAW , reginfo sys.aq$_reg_info, descr sys.aq$_descriptor,
       payload VARCHAR2,  payloadl NUMBER)
    AS
        deq_msgid           RAW(16);
        dopt                dbms_aq.dequeue_options_t;
        mprop               dbms_aq.message_properties_t;
        event               WMSYS.WM$EVENT_TYPE;
        no_messages         exception;
        pragma exception_init(no_messages, -25228);

    BEGIN
        dopt.consumer_name := 'MERGE_LISTENER';
        dopt.wait := 30;
        dopt.msgid := descr.msg_id;

        dbms_aq.dequeue(
            queue_name => 'WMSYS.WM$EVENT_QUEUE',
            dequeue_options => dopt,
            message_properties => mprop,
            payload => event,
            msgid => deq_msgid);

        INSERT INTO merge_log VALUES (event.event_name, event.workspace_name,
          event.parent_workspace_name, event.user_name);

        /* Note: If there are additional parameters stored in
           "aux_params" attribute, it can be accessed using
           event.aux_params(1).name, event.aux_params(1).value,
           event.aux_params(2).name … and so on. The number of
           parameters can be accessed using event.aux_params.count
           when aux_params is not null.
         */
    END;
    /

    grant execute on scott.event_callback to public ;

    rem ==================================================
    rem Register a callback for the event
    rem Queue name and subscriber name have to be specified
    rem while registering for a callback
    rem ==================================================

    DECLARE
      reginfo1            sys.aq$_reg_info;
      reginfolist         sys.aq$_reg_info_list;
    BEGIN
      reginfo1 := sys.aq$_reg_info('WMSYS.WM$EVENT_QUEUE:MERGE_LISTENER',1,'plsql://scott.event_callback?PR=1',HEXTORAW('FF'));

      reginfolist := sys.aq$_reg_info_list(reginfo1);

      sys.dbms_aq.register(reginfolist, 1);

      COMMIT;

    END;
    /

**Parent topic:** AQ Operations and Workspace Manager Events
