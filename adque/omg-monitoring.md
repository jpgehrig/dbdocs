The following topics discuss means of monitoring the Oracle Messaging Gateway (MGW) agent, abnormal situations you may experience, several sources of information about Messaging Gateway errors and exceptions, and suggested remedies.

- Oracle Messaging Gateway Log Files

- Monitoring the Oracle Messaging Gateway Agent Status

- Monitoring Oracle Messaging Gateway Propagation

- Oracle Messaging Gateway Agent Error Messages

### Oracle Messaging Gateway Log Files

Messaging Gateway agent status, history, and errors are recorded in Messaging Gateway log files. A different log file is created each time the Messaging Gateway agent is started. You should monitor the log file because any errors, configuration information read at startup time, or dynamic configuration information is written to the log.

The format of the log file name for the default agent is:

    oramgw-hostname-timestamp-processid.log

The format of the log file name for a named agent is:

    oramgw-AGENTNAME-hostname-timestamp-processid.log

By default the Messaging Gateway log file is in `ORACLE_HOME``/mgw/log`. This location can overridden by the parameter `log_directory` in the Messaging Gateway initialization file used by the agent, usually `mgw.ora`.

This section contains these topics:

- Sample Oracle Messaging Gateway Log File

- Interpreting Exception Messages in an Oracle Messaging Gateway Log File

#### Sample Oracle Messaging Gateway Log File

The following sample log file shows the Messaging Gateway agent starting. The sample log file shows that a messaging link, a registered foreign queue, a propagation job, and a schedule associated with the job have been added. The log file shows that the propagation job has been activated. The last line indicates that the Messaging Gateway is up and running and ready to propagate messages.

Example 21-1 Sample Messaging Gateway Log File

    >>2007-01-16 15:04:49 MGW C-Bootstrap 0 LOG process-id=11080
    Bootstrap program starting
    >>2007-01-16 15:04:50 MGW C-Bootstrap 0 LOG process-id=11080
    JVM created -- heapsize = 64
    >>2007-01-16 15:04:53 MGW Engine 0 200 main
    MGW Agent version: 11.1.0.0
    >>2007-01-16 15:04:53 MGW AdminMgr 0 LOG main
    Connecting to database using connect string = jdbc:oracle:oci:@INST1
    >>2007-01-16 15:05:00 MGW Engine 0 200 main
    MGW Component version: 11.1.0.3.0
    >>2007-01-16 15:05:01 MGW Engine 0 200 main
    MGW agent name: DEFAULT_AGENT, MGW job instance id: 273006EC6ED255F1E040578C6D021A8C, MGW database instance: 1
    >>2007-01-16 15:05:09 MGW Engine 0 1 main
    Agent is initializing.
    >>2007-01-16 15:05:09 MGW Engine 0 23 main
    The number of worker threads is set to 1.
    >>2007-01-16 15:05:09 MGW Engine 0 22 main
    The default polling interval is set to 5000ms.
    >>2007-01-16 15:05:09 MGW MQD 0 LOG main
    Creating MQSeries messaging link:
    link : MQLINK
    link type : Base Java interface
    queue manager : my.queue.manager
    channel : channel1
    host : my.machine
    port : 1414
    user :
    ccdt url :
    ssl cipherSuite :
    connections : 1
    inbound logQ : logq1
    outbound logQ : logq2
    >>2007-01-16 15:05:09 MGW Engine 0 4 main
    Link MQLINK has been added.
    >>2007-01-16 15:05:09 MGW Engine 0 7 main
    Queue DESTQ@MQLINK has been registered; provider queue: MGWUSER.MYQUEUE.
    >>2007-01-16 15:05:09 MGW Engine 0 9 main
    Propagation Schedule JOB_AQ2MQ (MGWUSER.MGW_BASIC_SRC --> DESTQ@MQLINK) has been
    added.
    >>2007-01-16 15:05:09 MGW AQN 0 LOG main
    Creating AQ messaging link:
    link : oracleMgwAq
    link type : native
    database : INST1
    user : MGWAGENT
    connection type : JDBC OCI
    connections : 1
    inbound logQ : SYS.MGW_RECV_LOG
    outbound logQ : SYS.MGW_SEND_LOG
    >>2007-01-16 15:05:10 MGW Engine 0 19 main
    MGW propagation job JOB_AQ2MQ has been activated.
    >>2007-01-16 15:05:10 MGW Engine 0 14 main
    MGW propagation job JOB_AQ2MQ (MGWUSER.MGW_BASIC_SRC --> DESTQ@MQLINK) has been added.
    >>2007-01-16 15:05:11 MGW Engine 0 2 main
    Agent is up and running.

#### Interpreting Exception Messages in an Oracle Messaging Gateway Log File

Exception messages logged to the Messaging Gateway log file may include one or more linked exceptions, identified by `[Linked-exception]` in the log file. These are often the most useful means of determining the cause of a problem. For instance, a linked exception could be a `java.sql.SQLException`, possibly including an Oracle error message, a PL/SQL stack trace, or both.

The following example shows entries from a Messaging Gateway log file when an invalid value (`bad_service_name`) was specified for the `database` parameter of `DBMS_MGWADM`.`CREATE_AGENT` or `DBMS_MGWADM`.`ALTER_AGENT`. This resulted in the Messaging Gateway agent being unable to establish database connections.

Example 21-2 Sample Exception Message

    >>2003-07-22 15:27:26  MGW  AdminMgr  0  LOG  main
    Connecting to database using connect string = jdbc:oracle:oci8:@BAD_SERVICE_NAME
    >>2003-07-22 15:27:29  MGW  Engine  0  EXCEPTION  main
    oracle.mgw.admin.MgwAdminException: [241]  Failed to connect to database. SQL
    error: 12154, connect string: jdbc:oracle:oci8:@BAD_SERVICE_NAME
    [ …Java stack trace here…]
    [Linked-exception]
    java.sql.SQLException: ORA-12154: TNS:could not resolve the connect identifier
    specified
    [ …Java stack trace here…]
    >>2003-07-22 15:27:29  MGW  Engine  0  25  main
    Agent is shutting down.

### Monitoring the Oracle Messaging Gateway Agent Status

This section contains these topics:

- MGW_GATEWAY View

- Oracle Messaging Gateway Irrecoverable Error Messages

- Other Oracle Messaging Gateway Error Conditions

#### MGW_GATEWAY View

The `MGW_GATEWAY` view monitors the progress of the Messaging Gateway agent. Among the fields that can be used to monitor the agent are:

- `AGENT_NAME`

- `AGENT_INSTANCE`

- `AGENT_PING`

- `AGENT_STATUS`

- `LAST_ERROR_MSG`

- `SERVICE`

The `AGENT_STATUS` field shows the status of the agent. This column has the following possible values:

NOT_STARTED
Indicates that the agent is neither running nor scheduled to be run.

START_SCHEDULED
Indicates that the agent job is waiting to be run by the job scheduler.

STARTING
Indicates that the agent is in the process of starting.

INITIALIZING
Indicates that the agent has started and is reading configuration data.

RUNNING
Indicates that the agent is ready to propagate any available messages or process dynamic configuration changes.

SHUTTING_DOWN
Indicates that the agent is in the process of shutting down.

BROKEN
Indicates that, while attempting to start an agent process, Messaging Gateway has detected another agent already running. This situation should never occur under normal usage.

Querying the `AGENT_PING` field pings the Messaging Gateway agent. Its value is either `REACHABLE` or `UNREACHABLE`. An agent with status of `RUNNING` should almost always be `REACHABLE`.

The columns `LAST_ERROR_MSG`, `LAST_ERROR_DATE`, and `LAST_ERROR_TIME` give valuable information if an error in starting or running the Messaging Gateway agent occurs. `AGENT_INSTANCE` indicates the Oracle Database instance on which the Messaging Gateway instance was started.

**See Also:**

"DBMS_MGWADM" in [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_MGWADM.md) for more information on the `MGW_GATEWAY` view

#### Oracle Messaging Gateway Irrecoverable Error Messages

A status of `NOT_STARTED` in the `AGENT_STATUS` field of the `MGW_GATEWAY` view indicates that the Messaging Gateway agent is not running. If the `AGENT_STATUS` is `NOT_STARTED` and the `LAST_ERROR_MSG` field is not NULL, then the Messaging Gateway agent has encountered an irrecoverable error while starting or running. Check if a Messaging Gateway log file has been generated and whether it indicates any errors. If a log file is not present, then the Messaging Gateway agent process was probably not started.

This section describes the causes and solutions for some error messages that may appear in the `LAST_ERROR_MSG` field of the `MGW_GATEWAY` view. Unless indicated otherwise, the Messaging Gateway agent will not attempt to restart itself when one of these errors occurs.

##### ORA-01089: Immediate shutdown in progress - no operations are permitted

The Messaging Gateway agent has shut down because the `SHUTDOWN IMMEDIATE` command was used to shut down a running Oracle Database instance on which the agent was running. The agent will restart itself on the next available database instance on which it is set up to run.

##### ORA-06520: PL/SQL: Error loading external library

The Messaging Gateway agent process was unable to start because the shared library was not loaded. This may be because the Java shared library was not in the library path. Verify that the library path in `listener.ora` has been set correctly.

##### ORA-28575: Unable to open RPC connection to external procedure agent

The Messaging Gateway agent was unable to start. It will attempt to start again automatically.

Possible causes include:

- The listener is not running. If you have modified `listener.ora`, then you must stop and restart the listener before the changes will take effect.

- Values in `tnsnames.ora`, `listener.ora`, or both are not correct.

  In particular, `tnsnames.ora` must have a net service name entry of `MGW_AGENT`. This entry is not needed for Messaging Gateway on Windows. The SID value specified for `CONNECT_DATA` of the `MGW_AGENT` net service name in `tnsnames.ora` must match the `SID_NAME` value of the `SID_DESC` entry in `listener.ora`. If the `MGW_AGENT` net service name is set up for an [Inter-process Communication](glossary.md) (IPC) connection, then the `KEY` values for `ADDRESS` in `tnsnames.ora` and `listener.ora` must match. If the `names.default_domain` parameter for `sqlnet.ora` has been used to set a default domain, then that domain must be appended to the `MGW_AGENT` net service name in `tnsnames.ora`.

##### ORA-28576: Lost RPC connection to external procedure agent

The Messaging Gateway agent process ended prematurely. This may be because the process was stopped by an outside entity or because an internal error caused a malfunction. The agent will attempt to start again automatically. Check the Messaging Gateway log file to determine if further information is available. If the problem persists, then contact Oracle Support Services for assistance.

##### ORA-32830: Result code -2 returned by Messaging Gateway agent

An error occurred when the Messaging Gateway agent tried to read its initialization file, usually `mgw`.`ora`. Verify that the file is readable.

##### ORA-32830: Result code -3 returned by Messaging Gateway agent

An error occurred creating the Messaging Gateway log file. Verify that the log directory can be written to. The default location is `ORACLE_HOME``/mgw/log`.

##### ORA-32830: Result code -8 returned by Messaging Gateway agent

An error occurred starting the Java Virtual Machine (JVM). Verify that:

- You are using the correct Java version

- Your operating system version and patch level are sufficient for the JDK version

- You are using a reasonable value for the JVM heap size

  The heap size is specified by the `max_memory` parameter of `DBMS_MGWADM.ALTER_AGENT`

- On Windows platforms, verify the `MGW_PRE_PATH` set in `mgw.ora` contains the path to the correct JVM library (`jvm.dll`).

##### ORA-32830: Result code -12 returned by Messaging Gateway agent

An error occurred writing to the Messaging Gateway log file. Check the free disk space or any other issues that might result in file I/O problems.

##### ORA-32830: Result code -17 returned by Messaging Gateway agent

The JVM was successfully created but an error occurred trying to call the MGW Java agent program. Verify that the CLASSPATH set in `mgw.ora` is correct.

##### ORA-32830: Result code -19 returned by Messaging Gateway agent

The Messaging Gateway agent was configured to use a particular initialization file but that file does not exist. The `INITFILE` field of the `MGW_GATEWAY` view shows the full pathname of the file specified by the administrator. Either create that initialization file, or use `DBMS_MGWADM`.`ALTER_AGENT` to set `INITFILE` to another file or `NULL` to use the default initialization file.

##### ORA-32830: Result code -100 returned by Messaging Gateway agent

The Messaging Gateway agent JVM encountered a runtime exception or error on startup before it could write to the log file.

##### ORA-32830: Result code -101 returned by Messaging Gateway agent

An irrecoverable error caused the Messaging Gateway agent to shut down. Check the Messaging Gateway log file for further information. Verify that the values specified in `mgw.ora` are correct. Incorrect values can cause the Messaging Gateway agent to terminate due to unusual error conditions.

##### ORA-32830: Result code -102 returned by Messaging Gateway agent

The Messaging Gateway agent shut down because the version of file `ORACLE_HOME``/mgw/jlib/mgw.jar` does not match the version of the Messaging Gateway PL/SQL packages. Verify that all Messaging Gateway components are from the same release.

##### ORA-32830: Result code -103 returned by Messaging Gateway agent

The Messaging Gateway agent shut down because the database instance on which it was running was shutting down. The agent should restart automatically, either on another instance if set up to do so, or when the instance that shut down is restarted.

##### ORA-32830: Result code -104 returned by Messaging Gateway agent

See previous error.

##### ORA-32830: Result code -105 returned by Messaging Gateway agent

The Messaging Gateway agent detected that it was running when it should not be. This should not happen. If it does, `AGENT_STATUS` will be `BROKEN` and the agent will shut down automatically. If you encounter this error:

- Terminate any Messaging Gateway agent process that may still be running. The process is usually named `extprocmgwextproc`.

- Run `DBMS_MGWADM.CLEANUP_GATEWAY(DBMS_MGWADM.CLEAN_STARTUP_STATE)`.

- Start the Messaging Gateway agent using `DBMS_MGWADM.STARTUP`.

##### ORA-32830: Result code -106 returned by Messaging Gateway agent

See previous error.

**See Also:**

"DBMS_MGWADM" in [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_MGWADM.md)

#### Other Oracle Messaging Gateway Error Conditions

This section discusses possible causes for `AGENT_STATUS` remaining `START_SCHEDULED` in `MGW_GATEWAY` view for an extended period.

##### Database Service Not Started

Messaging Gateway uses an Oracle Scheduler job to start the Messaging Gateway agent. Oracle Scheduler allows you to specify a database service under which a job should be run (service affinity). Messaging Gateway allows an administrator to configure the Messaging Gateway agent with a database service that will be used to configure the Scheduler job class associated with that agent.

When you shutdown a database Oracle stops all services to that database. You may need to manually restart the services when you start the database. If a Scheduler job is associated with a service then the job will not run until the service is started. If `AGENT_STATUS` for a Messaging Gateway agent remains `START_SCHEDULED` for an extended period that might indicate that the database service is disabled or no database instances associated with the service are running. Use the `MGW_GATEWAY` view, Oracle Scheduler views, and service views to determine how the agent was configured and the current state of the Scheduler job and database service.

**Note:**

[Oracle Messaging Gateway Agent Scheduler Job](omg-working.md) for information about Oracle Scheduler objects used by Messaging Gateway.

##### Too Few Job Queue Processes

Messaging Gateway uses Oracle Scheduler to start the Messaging Gateway external process. When `AGENT_STATUS` is `START_SCHEDULED`, the Messaging Gateway agent Scheduler job is waiting to be run by the Scheduler. The Messaging Gateway job will not run until there is an available job process. Messaging Gateway holds its Scheduler job process for the lifetime of the Messaging Gateway agent session. If multiple Messaging Gateway agents have been started, each agent uses its own Scheduler job and require its own job process.

If the value of the database initialization parameter `JOB_QUEUE_PROCESSES` is zero, then no Oracle Scheduler jobs will run. If the value is non-zero, it effectively becomes the maximum number of Scheduler jobs and job queue jobs than can concurrently run.

If Messaging Gateway status remains `START_SCHEDULED` for an extended period of time, then it may indicate that the database has been started with a value for `JOB_QUEUE_PROCESSES` that is zero or is too low and that all job slaves are busy. Verify that the value is non-zero and that the database instance has been started with enough job queue processes so that one is available for each Messaging Gateway agent.

##### Scheduler Job Broken or Disabled

The Messaging Gateway agent status will remain `START_SCHEDULED` if the Oracle Scheduler job associated with a Messaging Gateway agent has become disabled or broken for some reason. To determine if this is the case, use the `DBA_SCHEDULER_JOBS` view to look at `STATE` field for the agent's Scheduler job. Normally the Scheduler job state will be `SCHEDULED` when the Messaging Gateway agent's Scheduler job is waiting to be run, or `RUNNING` when the Messaging Gateway agent is running. The agent's Scheduler job should not exist if the Messaging Gateway agent status is `NOT_STARTED`.

Check other Scheduler views, such as `DBA_SCHEDULER_JOB_RUN_DETAILS`, for additional information about the Messaging Gateway Scheduler jobs. Also check the `MGW_GATEWAY` view and the Messaging Gateway log file for any error messages that may indicate a problem.

**Note:**

[Oracle Messaging Gateway Agent Scheduler Job](omg-working.md) for information about Oracle Scheduler objects used by Messaging Gateway

##### Oracle Real Application Clusters (Oracle RAC) Environment

If Messaging Gateway is being used in an Oracle RAC environment and the agent has been configured with a database service but no database instances are running that have the service enabled, then the Messaging Gateway `AGENT_STATUS` will remain `START_SCHEDULED` until the service is started on a running database instance.

### Monitoring Oracle Messaging Gateway Propagation

Messaging Gateway [propagation](glossary.md) can be monitored using the `MGW_JOBS` view and the Messaging Gateway log file. The view provides information on propagated messages and errors that may have occurred during propagation attempts. The log file can be used to determine the cause of the errors.

Besides showing configuration information, the `MGW_JOBS` view also has dynamic information that can be used to monitor [message](glossary.md) propagation. Applicable fields include `STATUS`, `ENABLED`, `PROPAGATED_MSGS`, `EXCEPTIONQ_MSGS`, `FAILURES`, `LAST_ERROR_MSG`, `LAST_ERROR_DATE`, and `LAST_ERROR_TIME`.

The `STATUS` field indicates current status of the job. `READY` means that the job is ready for propagation (but only if the `ENABLED` field is `TRUE`). `RETRY` means that a propagation failure occurred but that propagation will be retried. `FAILED` means that the agent has stopped propagation for the job due to an unrecoverable error or the maximum number of consecutive propagation failures has been reached. `DELETE_PENDING` means job removal is pending due to `DBMS_MGWADM`.`REMOVE_JOB` being called but certain cleanup tasks pertaining to the job are still outstanding. `SUBSCRIBER_DELETE_PENDING` means that `DBMS_MGWADM`.`REMOVE_SUBSCRIBER` has been called on an old style propagation job but certain cleanup tasks pertaining to the job are still outstanding.

The `ENABLED` field indicates whether the propagation job is currently enabled. `TRUE` indicates the job is enabled while `FALSE` indicates the job is disabled. No propagation will occur unless the job is enabled.

The `PROPAGATED_MSGS` field of the `MGW_JOBS` view indicates how many messages have been successfully propagated. This field is reset to zero when the Messaging Gateway agent is started.

If a Messaging Gateway propagation job has been configured with an [exception queue](glossary.md), then the Messaging Gateway agent will move messages to that exception queue the first time the Messaging Gateway agent encounters a propagation failure caused by a message conversion failure. A message conversion failure is indicated by `oracle.mgw.common.MessageException` in the Messaging Gateway log file. The `EXCEPTIONQ_MSGS` field indicates how many messages have been moved to the exception queue. This field is reset to zero when the Messaging Gateway agent is started.

If an error occurs during message propagation for a propagation job, a count is incremented in the `FAILURES` field. This field indicates the number of failures encountered since the last successful propagation of messages. Each time a failure occurs, an error message and the time it occurred will be shown by `LAST_ERROR_MSG`, `LAST_ERROR_DATE`, and `LAST_ERROR_TIME`. When the number of failures reaches sixteen, Messaging Gateway halts propagation attempts for this propagation job. To resume propagation attempts you must call `DBMS_MGWADM`.`RESET_JOB` for the propagation job.

If an error occurs, then examine the Messaging Gateway log file for further information.

**See Also:**

"DBMS_MGWADM" in [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_MGWADM.md)

### Oracle Messaging Gateway Agent Error Messages

This section lists some of the most commonly occurring errors that are shown in the `LAST_ERROR_MSG` column of the `MGW_JOBS` view and logged to the Messaging Gateway agent log file. Also shown are some errors that require special action. When you notice that a failure has occurred, look at the linked exceptions in the log file to determine the root cause of the problem.

Two primary types of errors are logged to the Messaging Gateway agent log file:

- `oracle.mgw.common.MessageException`

  This error type is logged when a message conversion failure occurs. The Messaging Gateway agent probably cannot propagate the message causing the failure, and the propagation job will eventually be stopped.

- `oracle.mgw.common.GatewayException`

  This error type is logged when some failure other than message conversion occurs. Depending on the cause, the problem may fix itself or require user action.

#### \[221\] Failed to access \<messaging_system\> queue: \<queue\>

An error occurred while trying to access either an Oracle Database Advanced Queuing queue or a non-Oracle queue. Check the linked exception error code and message in the log file.

#### \[241\] Failed to connect to database. SQL error: \<error\>, connect string: \<connect_string\>

This is probably caused by incorrect MGW agent connection information specified for `DBMS_MGWADM`.`CREATE_AGENT` or `DBMS_MGWADM`.`ALTER_AGENT`. Either the Messaging Gateway agent user or password is incorrect or the database specifier (database parameter) is incorrect. Verify that the connection information is correct for the connection type used by the agent, JDBC OCI or JDBC Thin.

If the `database` parameter is `NULL`, then check the Messaging Gateway log file for the following Oracle linked errors:

    ORA-01034: ORACLE not available
    ORA-27101: shared memory realm does not exist

These two errors together indicate that the Messaging Gateway agent is attempting to connect to the database using a local IPC connection, but the `ORACLE_SID` value is not correct.

A local connection is used when the database parameter is set to `NULL`. If a local connection is desired, the correct `ORACLE_SID` value must be set in the Messaging Gateway agent process. This can be done by adding the following line to the MGW initialization file, usually `mgw`.`ora`:

    set ORACLE_SID = sid_value

`ORACLE_SID` need not be set in the MGW initialization file if the database parameter is not `NULL`.

If setting `ORACLE_SID` in the MGW initialization file does not work, then the database parameter must be set to a value that is not `NULL`.

If the JDBC Thin connection is used, then the database parameter must be not `NULL`. If the JDBC Thin connection is used and the database parameter is a TNSNames alias, make sure that the `oracle`.`net`.`tns_names` Java property is set in the MGW initialization file. The property can be set by adding the following line to the MGW initialization file:

    setJavaProp oracle.net.tns_admin=<directory containing tnsnames.ora>

**Note:**

"[oracle.net.tns_admin](omg-getting-started.md)" for more information

#### \[415\] Missing messages from source queue of job \<job_name\>

Possible causes include:

- The agent partially processed persistent messages that were dequeued by someone other than the Messaging Gateway agent.

- The propagation source queue was purged or re-created.

- A message was moved to the Oracle Database Advanced Queuing exception queue.

If this error occurs, then call procedure `CLEANUP_GATEWAY` in the `DBMS_MGWADM` package:

    DBMS_MGWADM.CLEANUP_GATEWAY (
           action => DBMS_MGWADM.RESET_SUB_MISSING_MESSAGE,
           sarg => <job_name>);

The call takes effect only if the propagation job has encountered the missing message problem and the agent is running. The agent treats the missing messages as [nonpersistent](glossary.md) messages and continues processing the propagation job.

**See Also:**

"[Propagation Job Overview](omg-working.md)" for more information on Messaging Gateway exception queues

#### \[416\] Missing log records in receiving log queue for job \<job_name\>

Possible causes include:

- Log records were dequeued from the log queues by someone other than the Messaging Gateway agent.

- The log queues were purged or re-created.

If this error occurs, then call procedure `CLEANUP_GATEWAY` in the `DBMS_MGWADM` package:

    DBMS_MGWADM.CLEANUP_GATEWAY (
           action => DBMS_MGWADM.RESET_SUB_MISSING_LOG_REC,
           sarg => <job_name>);

The call takes effect only if the propagation job has encountered the missing log records problem and the agent is running.

**Note:**

Calling procedure `DBMS_MGWADM.CLEANUP_GATEWAY` may result in duplicated messages if the missing messages have already been propagated to the destination queue. Users should check the source and destination queues for any messages that exist in both places. If such messages exist, then they should be removed from either the source or destination queue before calling this procedure.

#### \[417\] Missing log records in sending log queue for job \<job_name\>

See previous error.

#### \[421\] WARNING: Unable to get connections to recover job \<job_name\>

This message is a warning message indicating that the Messaging Gateway agent failed to get a connection to recover the propagation job, because other propagation jobs are using them all. The agent will keep trying to get a connection until it succeeds.

If this message is repeated many times for a WebSphere MQ link, then increase the maximum number of connections used by the Messaging Gateway link associated with the propagation job.

**See Also:**

"[Altering a Messaging System Link](omg-working.md)"

#### \[434\] Failed to access queue \<queue\>; provider queue \<queue\>

This message indicates that a messaging system native queue cannot be accessed. The queue may have been registered by `DBMS_MGWADM.REGISTER_FOREIGN_QUEUE`, or it may be an Oracle Database Advanced Queuing queue. The linked exceptions should give more information.

Possible causes include:

- The foreign queue was registered incorrectly, or the Messaging Gateway link was configured incorrectly.

  Verify configuration information. If possible, use the same configuration information to run a sample application of the non-Oracle messaging system.

- The non-Oracle messaging system is not accessible.

  Check that the non-Oracle messaging system is running and can be accessed using the information supplied in the Messaging Gateway link.

- The Oracle Database Advanced Queuing queue does not exist. Perhaps the queue was removed after the Messaging Gateway propagation job was created.

  Check that the Oracle Database Advanced Queuing queue still exists.

#### \[436\] LOW MEMORY WARNING: total memory = \< \>, free_mem = \< \>

The Messaging Gateway agent JVM is running low on memory. Java garbage collection will be invoked, but this may represent a JVM heap size that is too small. Use the `max_memory` parameter of `DBMS_MGWADM.ALTER_AGENT` to increase the JVM heap size. If the Messaging Gateway agent is running, then it must be restarted for this change to take effect.

#### \[703\] Failed to retrieve information for transformation \<transformation_id\>

The Messaging Gateway agent could not obtain all the information it needs about the [transformation](glossary.md). The transformation parameter of `DBMS_MGWADM.CREATE_JOB` must specify the name of the registered transformation and not the name of the transformation function.

Possible causes include:

- The transformation does not exist. Verify that the transformation has been created. You can see this from the following query performed as user SYS:

      SELECT TRANSFORMATION_ID, OWNER FROM DBA_TRANSFORMATIONS;

- The wrong transformation is registered with Messaging Gateway. Verify that the transformation registered is the one intended.

- The Messaging Gateway agent user does not have `EXECUTE` privilege on the [object type](glossary.md) used for the `from_type` or the `to_type` of the transformation indicated in the exception.

  It is not sufficient to grant `EXECUTE` to `MGW_AGENT_ROLE` and then grant `MGW_AGENT_ROLE` to the agent user. You must grant `EXECUTE` privilege on the object type directly to the agent user or to `PUBLIC`.

  The following example shows such a case for the `from_type`. It also shows the use of linked exceptions for determining the precise cause of the error.

  No EXECUTE Privilege on Object Type

      Errors occurred during processing of job JOB_AQ2MQ_2
      oracle.mgw.common.GatewayException: [703] Failed to retrieve information for
      transformation mgwuser.SAMPLEADT_TO_MGW_BASIC_MSG
      […Java stack trace here…]
      [Linked-exception]
      java.sql.SQLException: "from_type" is null
      […Java stack trace here…]

#### \[720\] AQ payload type \<type\> not supported; queue: \<queue\>

The payload type of the Oracle Database Advanced Queuing queue used by a Messaging Gateway propagation job is not directly supported by Messaging Gateway. For non-JMS propagation, Messaging Gateway directly supports the payload types `RAW`, `SYS.MGW_BASIC_MSG_T` and `SYS.MGW_TIBRV_MSG_T`.

Possible actions include:

- Configure the Messaging Gateway propagation job to use a transformation that converts the queue payload type to a supported type.

- Remove the Messaging Gateway propagation job and create a new job that uses an Oracle Database Advanced Queuing queue with a supported payload type.

  For [Java Message Service](glossary.md) (JMS) propagation, the Messaging Gateway propagation job must be removed and a new job created whose Oracle Database Advanced Queuing payload type is supported by [Oracle Java Message Service](glossary.md) (Oracle JMS). Transformations are not supported for JMS propagation.

#### \[721\] Transformation type \<type\> not supported; queue: \<queue_name\>, transform: \<transformation\>

A Messaging Gateway propagation job was configured with a transformation that uses an object type that is not one of the Messaging Gateway [canonical](glossary.md) types.

For an outbound job, the transformation `from_type` must be the Oracle Database Advanced Queuing payload type, and the `to_type` must be a Messaging Gateway canonical type. For an inbound job, the transformation `from_type` must be a Messaging Gateway canonical type and the `to_type` must be the Oracle Database Advanced Queuing payload type.

#### \[722\] Message transformation failed; queue: \<queue_name\>, transform: \<transformation\>

An error occurred while attempting execution of the transformation. ORA-25229 is typically thrown by Oracle Database Advanced Queuing when the transformation function raises a PL/SQL exception or some other Oracle error occurs when attempting to use the transformation.

Possible causes include:

- The Messaging Gateway agent user does not have `EXECUTE` privilege on the transformation function. This is illustrated in the following example.

  It is not sufficient to grant `EXECUTE` to `MGW_AGENT_ROLE` and then grant `MGW_AGENT_ROLE` to the Messaging Gateway agent user. You must grant `EXECUTE` privilege on the transformation function directly to the Messaging Gateway agent user or to `PUBLIC`.

  No EXECUTE Privilege on Transformation Function

      Errors occurred during processing of job JOB_MQ2AQ_2
      oracle.mgw.common.GatewayException: [722] Message transformation failed queue:
      MGWUSER.DESTQ_SIMPLEADT, transform: MGWUSER.MGW_BASIC_MSG_TO_SIMPLEADT
      […Java stack trace here…]
      [Linked-exception]
      oracle.mgw.common.MessageException: [722] Message transformation failed;
      queue: MGWUSER.DESTQ_SIMPLEADT, transform:
      MGWUSER.MGW_BASIC_MSG_TO_SIMPLEADT
      […Java stack trace here…]
      [Linked-exception]
      java.sql.SQLException: ORA-25229: error on transformation of message msgid:
      9749DB80C85B0BD4E03408002086745E
      ORA-00604: error occurred at recursive SQL level 1
      ORA-00904: invalid column name
      […Java stack trace here…]

- The transformation function does not exist, even though the registered transformation does. If the transformation function does not exist, it must be re-created.

- The Messaging Gateway agent user does not have `EXECUTE` privilege on the payload object type for the queue indicated in the exception.

  It is not sufficient to grant `EXECUTE` to `MGW_AGENT_ROLE` and then grant `MGW_AGENT_ROLE` to the Messaging Gateway agent user. You must grant `EXECUTE` privilege on the object type directly to the Messaging Gateway agent user or to `PUBLIC`.

- The transformation function raised the error. Verify that the transformation function can handle all messages it receives.

#### \[724\] Message conversion not supported; to AQ payload type: \<type\>, from type: \<type\>

A Messaging Gateway propagation job is configured for inbound propagation where the canonical message type generated by the non-Oracle messaging system link is not compatible with the Oracle Database Advanced Queuing queue payload type. For example, propagation from a TIB/Rendezvous messaging system to an Oracle Database Advanced Queuing queue with a `SYS.MGW_BASIC_MSG_T` payload type, or propagation from WebSphere MQ to an Oracle Database Advanced Queuing queue with a `SYS.MGW_TIBRV_MSG_T` payload type.

Possible actions include:

- Configure the Messaging Gateway propagation job with a transformation that maps the canonical message type generated by the non-Oracle messaging link to the Oracle Database Advanced Queuing payload type.

- Remove the Messaging Gateway propagation job and create a new job whose Oracle Database Advanced Queuing queue payload type matches the canonical message type generated by the non-Oracle link.

#### \[725\] Text message not supported for RAW payload

A Messaging Gateway propagation job is configured for inbound propagation to an Oracle Database Advanced Queuing destination having a `RAW` payload type. A text message was received from the source (non-Oracle) queue resulting in a message conversion failure.

If support for text data is required, remove the Messaging Gateway propagation job and create a new job to an Oracle Database Advanced Queuing destination whose payload type supports text data.

#### \[726\] Message size \<size\> too large for RAW payload; maximum size is \<size\>

A Messaging Gateway propagation job is configured for inbound propagation to an Oracle Database Advanced Queuing destination having a `RAW` payload type. A message conversion failure occurred when a message containing a large `RAW` value was received from the source (non-Oracle) queue.

If large data support is required, remove the Messaging Gateway propagation job and create a new job to an Oracle Database Advanced Queuing destination whose payload type supports large data, usually in the form of an object type with a [BLOB](glossary.md) attribute.

#### \[728\] Message contains too many large (BLOB) fields

The source message contains too many fields that must be stored in `BLOB` types. `SYS.MGW_TIBRV_MSG_T` is limited to three `BLOB` fields. Reduce the number of large fields in the message, perhaps by breaking them into smaller fields or combining them into fewer large fields.

#### \[729\] Message contains too many large (CLOB) fields

The source message contains too many fields that contain a large text value that must be stored in a `CLOB`. `SYS.MGW_TIBRV_MSG_T` is limited to three `CLOB` fields. Reduce the number of large fields in the message, perhaps by breaking them into smaller fields or combining them into fewer large fields.

#### \[805\] MQSeries Message error while enqueuing to queue: \<queue\>

WebSphere MQ returned an error when an attempt was made to put a message in a WebSphere MQ queue. Check the linked exception error code and message in the log file. Consult WebSphere MQ documentation.
