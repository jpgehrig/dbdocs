You can diagnose and correct problems with an XStream Out configuration.

- Diagnosing Problems with XStream Out
  You can diagnose problems with XStream Out by using several different techniques.
- Problems and Solutions for XStream Out
  You can implement solutions for common problems with XStream Out.
- How to Get More Help with XStream Out
  Oracle Support can provide more help with XStream Out.

**See Also:**

- "[XStream Out Concepts](xstream-out-concepts.md)"

- "[XStream Use Cases](introduction-to-xstream.md)"

- "[Configuring XStream Out](configuring-xstream-out.md)"

**Parent topic:** [XStream Out](xstream-out.md)

### 7.1 Diagnosing Problems with XStream Out

You can diagnose problems with XStream Out by using several different techniques.

- Viewing Alerts
  An alert is a warning about a potential problem or an indication that a critical threshold has been crossed.
- Checking the Trace File and Alert Log for Problems
  Messages about each capture process and outbound server are recorded in trace files for the database in which the process is running.

**Parent topic:** Troubleshooting XStream Out

#### 7.1.1 Viewing Alerts

An alert is a warning about a potential problem or an indication that a critical threshold has been crossed.

There are two types of alerts:

- Stateless: Alerts that indicate single events that are not necessarily tied to the system state. For example, an alert that indicates that a capture aborted with a specific error is a stateless alert.

- Stateful: Alerts that are associated with a specific system state. Stateful alerts are usually based on a numeric value, with thresholds defined at warning and critical levels. For example, an alert on the current Streams pool memory usage percentage, with the warning level at 85% and the critical level at 95%, is a stateful alert.

An Oracle database generates a stateless alert under the following conditions:

- A capture process aborts.

- An outbound server aborts.

An Oracle database generates a stateful XStream alert when the Streams pool memory usage exceeds the percentage specified by the `STREAMS_POOL_USED_PCT` metric. You can manage this metric with the `SET_THRESHOLD` procedure in the `DBMS_SERVER_ALERT` package.

You can view alerts in Oracle Enterprise Manager Cloud Control, or you can query the following data dictionary views:

- The `DBA_OUTSTANDING_ALERTS` view records current stateful alerts. The `DBA_ALERT_HISTORY` view records stateless alerts and stateful alerts that have been cleared. For example, if the memory usage in the Streams pool exceeds the specified threshold, then a stateful alert is recorded in the `DBA_OUTSTANDING_ALERTS` view.

- The `DBA_ALERT_HISTORY` data dictionary view shows alerts that have been cleared from the `DBA_OUTSTANDING_ALERTS` view. For example, if the memory usage in the streams pool falls below the specified threshold, then the alert recorded in the `DBA_OUTSTANDING_ALERTS` view is cleared and moved to the `DBA_ALERT_HISTORY` view.

For example, to list the current stateful alerts, run the following query on the `DBA_OUTSTANDING_ALERTS` view:

    COLUMN REASON HEADING 'Reason for Alert' FORMAT A35
    COLUMN SUGGESTED_ACTION HEADING 'Suggested Response' FORMAT A35

    SELECT REASON, SUGGESTED_ACTION
       FROM DBA_OUTSTANDING_ALERTS
       WHERE MODULE_ID LIKE '%XSTREAM%';

To list the stateless alerts and cleared XStream stateful alerts, run the following query on the `DBA_ALERT_HISTORY` view:

    COLUMN REASON HEADING 'Reason for Alert' FORMAT A35
    COLUMN SUGGESTED_ACTION HEADING 'Suggested Response' FORMAT A35

    SELECT REASON, SUGGESTED_ACTION
       FROM DBA_ALERT_HISTORY
       WHERE MODULE_ID LIKE '%XSTREAM%';

Most alerts are cleared automatically when the cause of the problem disappears or is acknowledged by the database administrator.

**See Also:**

- [Oracle Database Administrator’s Guide](../admin/monitoring-the-database.md) for information about alerts and for information about subscribing to the `ALERT_QUE` queue to receive notifications when new alerts are generated

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_SERVER_ALERT.md) for more information about the `DBMS_SERVER_ALERT` package

- "[Configure the Streams pool](configuring-xstream-out.md)"

- [Oracle Database 2 Day + Performance Tuning Guide](../tdppt/monitoring-performance-alerts.md) for more information on clearing and purging alerts with Oracle Enterprise Manager Cloud Control

**Parent topic:** Diagnosing Problems with XStream Out

#### 7.1.2 Checking the Trace File and Alert Log for Problems

Messages about each capture process and outbound server are recorded in trace files for the database in which the process is running.

A local capture process runs on a source database and a downstream capture process runs on a downstream database. These trace file messages can help you to identify and resolve problems in an XStream Out configuration.

All trace files for background processes are written to the Automatic Diagnostic Repository. The names of trace files are operating system specific, but each file usually includes the name of the process writing the file.

For example, on some operating systems, the trace file name for a process is `sid_xxxx_iiiii``.trc`, where:

- `sid` is the system identifier for the database

- `xxxx` is the name of the process

- `iiiii` is the operating system process number

Also, you can set the `write_alert_log` parameter to `y` for both a capture process and an outbound server. When this parameter is set to `y`, which is the default setting, the alert log for the database contains messages about why the capture process or outbound server stopped.

You can control the information in the trace files by setting the `trace_level` capture process or outbound server apply parameter using the `SET_PARAMETER` procedure in the `DBMS_XSTREAM_ADM` package.

- Capture Process Trace Files
  A capture process is an Oracle background process named `CP``nn`, where `nn` can include letters and numbers.
- Logminer Trace Files
  Logminer trace files are useful in understanding issues with XStream Out.
- Outbound Server Trace File
  An outbound server is an Oracle background process named `AP``nn`, where `nn` can include letters and numbers.
- Client Application Trace Files
  Client application trace files can help to isolate a problem with XStream Out.

**See Also:**

- [Oracle Database Administrator’s Guide](../admin/diagnosing-and-resolving-problems.md)for more information about trace files and the alert log, and for more information about their names and locations

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/index.md)for more information about setting the [`trace_level` capture process parameter](../arpls/DBMS_CAPTURE_ADM.md) and the [`trace_level` apply parameter](../arpls/DBMS_APPLY_ADM.md)

- Your operating system specific Oracle documentation for more information about the names and locations of trace files

**Parent topic:** Diagnosing Problems with XStream Out

##### 7.1.2.1 Capture Process Trace Files

A capture process is an Oracle background process named `CP``nn`, where `nn` can include letters and numbers.

For example, on some operating systems, if the system identifier for a database running a capture process is `hqdb` and the capture process number is `01`, then the trace file for the capture process starts with `hqdb_CP01`.

**See Also:**

"[Displaying Change Capture Information About Each Capture Process](monitoring-xstream-out.md)" for a query that displays the capture process number of a capture process

**Parent topic:** Checking the Trace File and Alert Log for Problems

##### 7.1.2.2 Logminer Trace Files

Logminer trace files are useful in understanding issues with XStream Out.

The logminer trace files are created when the parallelism capture process parameter is set to a value greater than 0. There are at least 3 logminer trace files that are generated and written to the Automated Diagnostic Repository.

**Parent topic:** Checking the Trace File and Alert Log for Problems

##### 7.1.2.3 Outbound Server Trace File

An outbound server is an Oracle background process named `AP``nn`, where `nn` can include letters and numbers.

For example, on some operating systems, if the system identifier for a database running an outbound server is `hqdb` and the outbound server number is `01`, then the trace file for the outbound server starts with `hqdb_ap01_xxxx.trc`.

An outbound server also uses other processes. Information about an outbound server might be recorded in the trace file for one or more of these processes. The process name of the reader server and apply servers is `AS``nn`, where `nn` can include letters and numbers. So, on some operating systems, if the system identifier for a database running an outbound server is `hqdb` and the process number is `01`, then the trace file that contains information about a process used by an outbound server starts with `hqdb_AS01`.

**See Also:**

"[Monitoring Session Information About XStream Out Components](monitoring-xstream-out.md)"

**Parent topic:** Checking the Trace File and Alert Log for Problems

##### 7.1.2.4 Client Application Trace Files

Client application trace files can help to isolate a problem with XStream Out.

When troubleshooting errors, isolating a problem to a key component, or identifying potential performance issues, it is a good idea to examine the trace files from all of the key sources in your XStream environment. One key source to check is the client application trace files. The client trace files are located in the directory: `$ORACLE_HOME/diag/clients/`.

**Parent topic:** Checking the Trace File and Alert Log for Problems

### 7.2 Problems and Solutions for XStream Out

You can implement solutions for common problems with XStream Out.

In general, you can troubleshoot XStream outbound servers in the same way that you troubleshoot Oracle Apply processes. In addition, an XStream Out environment includes capture processes and queues, and might include other components, such as propagations, rules, and rule-based transformations.

- An OCI Client Application Cannot Attach to the Outbound Server
  An XStream client application cannot attach to an outbound server using the Oracle Call Interface (OCI) `OCIXStreamOutAttach()` function.
- Changes Are Failing to Reach the Client Application in XStream Out
  In an XStream Out configuration, database changes that should be captured and streamed to the XStream client application are not reaching the client application.
- The Capture Process Is Missing Required Redo Log Files
  When a capture process is started or stopped and restarted, it might need to scan redo log files that were generated before the log file that contains the SCN that corresponds to the required checkpoint SCN, and these files might have been removed.
- LCRs Streaming from an Outbound Server Are Missing Extra Attributes
  LCRs streaming from an outbound server are expected to include extra attributes, but these attributes are not included in the LCRs.
- The XStream Out Client Application Is Unresponsive
  The XStream client application in an XStream Out configuration is unresponsive.

**Parent topic:** Troubleshooting XStream Out

#### 7.2.1 An OCI Client Application Cannot Attach to the Outbound Server

An XStream client application cannot attach to an outbound server using the Oracle Call Interface (OCI) `OCIXStreamOutAttach()` function.

The following sections describe possible problems and their solutions.

##### Problem 1: Client Application Not Connected as Connect User

The client application is not connected as the outbound server's connect user to the outbound server's database. The client application connected to the database as a different user.

##### To display information about the XStream Out servers that are accessible to the connect user:

1.  Connect to the outbound server database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the following query to determine the connect user:

        SELECT SERVER_NAME,
               CONNECT_USER,
               CAPTURE_NAME,
               SOURCE_DATABASE,
               CAPTURE_USER,
               QUEUE_OWNER
          FROM ALL_XSTREAM_OUTBOUND;

    This query displays the name of the user (`connect_user`) who can connect to the outbound server and process the outbound LCRs.

##### Solution 1

##### To correct problem 1:

- Modify the client application to connect to the database as the connect user before attaching to the outbound server.

##### Problem 2: Client Application Not Passing Service Handle

The client application is not passing a service handle to the outbound server.

##### Solution 2

##### To correct problem 2:

- Modify the client application so that it passes a service handle using `OCISvcCtx` and not `OCIServer`.

**See Also:**

- "[XStream Out and Security](xstream-out-concepts.md)"

- [Oracle Call Interface Programmer's Guide](../lnoci/oci-XStream-functions.md)

**Parent topic:** Problems and Solutions for XStream Out

#### 7.2.2 Changes Are Failing to Reach the Client Application in XStream Out

In an XStream Out configuration, database changes that should be captured and streamed to the XStream client application are not reaching the client application.

The following sections describe possible problems and their solutions.

##### Problem 1: Capture Process Has Fallen Behind

The capture process has fallen behind.

##### To determine whether the capture process has fallen behind:

1.  Connect to the outbound server database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the following query:

        COLUMN CAPTURE_NAME HEADING 'Capture|Name' FORMAT A15
        COLUMN STATE HEADING 'State' FORMAT A15
        COLUMN CREATE_MESSAGE HEADING 'Last LCR|Create Time'
        COLUMN ENQUEUE_MESSAGE HEADING 'Last|Enqueue Time'

        SELECT CAPTURE_NAME, STATE,
               TO_CHAR(CAPTURE_MESSAGE_CREATE_TIME, 'HH24:MI:SS MM/DD/YY') CREATE_MESSAGE,
               TO_CHAR(ENQUEUE_MESSAGE_CREATE_TIME, 'HH24:MI:SS MM/DD/YY') ENQUEUE_MESSAGE
          FROM V$XSTREAM_CAPTURE;

    This query shows the current state of the capture process. This query also displays the time when the capture process last created a logical change record (LCR) and the time when the capture process last enqueued an LCR. If the times returned are before the time when the database changes were made, then the capture process must catch up and capture the changes.

##### Solution 1

No action is required. Normally, the capture process will catch up on its own without the need for intervention.

**See Also:**

[Oracle Database Reference](../refrn/V-XSTREAM_CAPTURE.md)

##### Problem 2: Rules or Rule-Based Transformation Excluding Changes

Rules or rule-based transformations are excluding the changes that should be captured.

Rules determine which LCRs are captured by a capture process, sent from a source queue to a destination queue by a propagation, and sent to an XStream client application by an outbound server. If the rules are not configured properly, then the client application might not receive the LCRs it should receive. The client application might also receive LCRs that it should not receive.

Rule-based transformations modify the contents of LCRs. Therefore, if the expected change data is not reaching the client application, it might be because a rule-based transformation modified the data or deleted the data. For example, a `DELETE_COLUMN` declarative rule-based transformation removes a column from an LCR.

##### Solution 2

##### To correct problem 2:

- Check the rules and rule-based transformations that are configured for each component in the stream from the capture process to the client application, and correct any problems.

##### Problem 3: LCRs Blocked in the Stream

If the capture process has not fallen behind, and there are no problems with rules or rule-based transformations, then LCRs might be blocked in the stream for some other reason. For example, a propagation or outbound server might be disabled, a database link might be broken, or there might be another problem.

You can track an LCR through a stream using one of the following methods:

- Setting the `message_tracking_frequency` capture process parameter to `1` or another relatively low value

  To disable LCR tracking when you use this method, set the `message_tracking_frequency` capture process parameter to `NULL` or exit the session.

- Running the `SET_MESSAGE_TRACKING` procedure in the `DBMS_XSTREAM_ADM` package

  To disable LCR tracking when you use this method, set the `tracking_label` parameter to `NULL` in the `SET_MESSAGE_TRACKING` procedure or exit the session.

After using one of these methods, use the `V$XSTREAM_MESSAGE_TRACKING` view to monitor the progress of LCRs through a stream. By tracking an LCR through the stream, you can determine where the LCR is blocked.

In addition, if a propagation is used to send LCRs in the configuration, then you can check the current state of the propagation sender by running the following query:

    SELECT STATE FROM V$PROPAGATION_SENDER;

You can check the current state of an outbound server by running the following query:

    SELECT SERVER_NAME, STATE FROM V$XSTREAM_OUTBOUND_SERVER;

You can verify that the client application is attached to the outbound server by running the following query:

    COLUMN SERVER_NAME HEADING 'Capture|Name' FORMAT A30
    COLUMN STATUS HEADING 'Status' FORMAT A8

    SELECT SERVER_NAME, STATUS FROM ALL_XSTREAM_OUTBOUND;

The `STATUS` column shows `ATTACHED` when the client application is attached to the outbound server.

##### Solution 3

##### To correct problem 3:

- Take the appropriate action based on the reason that the LCR is blocked. For example, if a propagation is disabled, then enable it.

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_CAPTURE_ADM.md) for information about the `message_tracking_frequency` capture process parameter

**Parent topic:** Problems and Solutions for XStream Out

#### 7.2.3 The Capture Process Is Missing Required Redo Log Files

When a capture process is started or stopped and restarted, it might need to scan redo log files that were generated before the log file that contains the SCN that corresponds to the required checkpoint SCN, and these files might have been removed.

You can query the `ALL_CAPTURE` data dictionary view to determine the required checkpoint SCN for a capture process. It is also helpful to query the `V$XSTREAM_CAPTURE` and check the `STATE` column. The state of a capture process describes what the capture process is doing currently. In this case, you can gain additional insight as to why the capture process is missing or waiting for redo log files.

    COLUMN CAPTURE_NAME HEADING 'Capture Name' FORMAT A30
    COLUMN STATE HEADING 'State' FORMAT A30

    SELECT CAPTURE_NAME, STATE FROM V$XSTREAM_CAPTURE;

    CAPTURE_NAME            STATE
    ------------------      -----------------
    XOUT_SRC_CAPTURE        WAITING FOR REDO

Additional information might be displayed along with the state information when you query the `V$XSTREAM_CAPTURE` view. The additional information can help you to determine why the capture process is waiting for redo. For example, a statement similar to the following might appear for the `STATE` column when you query the view:

    WAITING FOR REDO: LAST SCN MINED 6700345

In this case, the output shows the last system change number (SCN) scanned by the capture process. In other cases, the output might display the redo log file name explicitly. Either way, the additional information can help you identify the redo log file for which the capture process is waiting. To correct the problem, make any missing redo log files available to the capture process.

##### Problem: Required Redo Log Files Were Removed

Removing required redo log files before they are scanned by a capture process causes the capture process to abort and results in the following error in a capture process trace file:

    ORA-01291: missing logfile

##### Solution: Restore Missing Redo Log Files and Prevent Future Problems

If you see this error, then try restoring any missing redo log files and restarting the capture process. You can check the `V$LOGMNR_LOGS` dynamic performance view to determine the missing SCN range, and add the relevant redo log files. A capture process needs the redo log file that includes the required checkpoint SCN and all subsequent redo log files. You can query the `REQUIRED_CHECKPOINT_SCN` column in the `ALL_CAPTURE` data dictionary view to determine the required checkpoint SCN for a capture process.

If the capture process is disabled for longer than the amount of time specified in the `CONTROL_FILE_RECORD_KEEP_TIME` initialization parameter, then information about the missing redo log files might have been replaced in the control file. You can query the `V$ARCHIVE_LOG` view to see if the log file names are listed. If they are not listed, then you can register them with a `ALTER DATABASE REGISTER OR REPLACE LOGFILE` SQL statement.

If you are using the fast recovery area feature of Recovery Manager (RMAN) on a source database in an XStream environment, then RMAN might delete archived redo log files that are required by a capture process. RMAN might delete these files when the disk space used by the recovery-related files is nearing the specified disk quota for the fast recovery area. To prevent this problem in the future, complete one or more of the following actions:

- Increase the disk quota for the fast recovery area. Increasing the disk quota makes it less likely that RMAN will delete a required archived redo log file, but it will not always prevent the problem.

- Configure the source database to store archived redo log files in a location other than the fast recovery area. A local capture process will be able to use the log files in the other location if the required log files are missing in the fast recovery area. In this case, a database administrator must manage the log files manually in the other location.

RMAN always ensures that archived redo log files are backed up before it deletes them. If RMAN deletes an archived redo log file that is required by a capture process, then RMAN records this action in the alert log.

**See Also:**

- "[Capture Processes](xstream-out-concepts.md)"

- "[XStream Out and Recovery Manager](xstream-out-concepts.md)"

- "[Displaying Redo Log Files That Are Required by Each Capture Process](monitoring-xstream-out.md)"

**Parent topic:** Problems and Solutions for XStream Out

#### 7.2.4 LCRs Streaming from an Outbound Server Are Missing Extra Attributes

LCRs streaming from an outbound server are expected to include extra attributes, but these attributes are not included in the LCRs.

LCRs can contain the following extra attributes related to database changes:

- `row_id`

- `serial#`

- `session#`

- `thread#`

- `tx_name`

- `username`

By default, a capture process does not capture these extra attributes. If you want extra attributes to be included in LCRs streamed from an outbound server to an XStream client application, but the LCRs do not contain values for extra attributes, then make sure the capture process that captures changes for the outbound server is configured to capture values for the extra attributes.

The following sections describe the possible problem and its solution.

##### Problem: Capture Process Not Configured to Capture Extra Attributes

The capture process is not configured to capture the required extra attributes.

##### To display the extra attributes currently being captured by the capture processes in a database:

1.  Connect to the database running the capture process as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the following query:

        COLUMN CAPTURE_NAME HEADING 'Capture Process' FORMAT A30
        COLUMN ATTRIBUTE_NAME HEADING 'Attribute Name' FORMAT A30

        SELECT CAPTURE_NAME, ATTRIBUTE_NAME
          FROM ALL_CAPTURE_EXTRA_ATTRIBUTES
          WHERE INCLUDE = 'YES'
          ORDER BY CAPTURE_NAME;

    If an extra attribute is not displayed by this query, then it is not being captured.

##### Solution

##### To solve the problem, configure the capture process to capture the required extra attributes:

1.  Connect to the outbound server database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the `INCLUDE_EXTRA_ATTRIBUTE` procedure in the `DBMS_CAPTURE_ADM` package.

Example 7-1 Including the tx_name Attribute for the Capture Process xcapture

    BEGIN
      DBMS_CAPTURE_ADM.INCLUDE_EXTRA_ATTRIBUTE(
        capture_name   => 'xcapture',
        attribute_name => 'tx_name',
        include        => TRUE);
    END;
    /

**Parent topic:** Problems and Solutions for XStream Out

#### 7.2.5 The XStream Out Client Application Is Unresponsive

The XStream client application in an XStream Out configuration is unresponsive.

The following sections describe the possible problem and its solution.

##### Problem 1: Streams Pool Size Is Too Small

The Streams pool size might be too small.

##### To determine whether the Streams pool size is too small:

1.  Connect to the outbound server database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the following queries at the database that contains the outbound server:

    - Query the `V$PROPAGATION_RECEIVER` view.:

          SELECT STATE FROM V$PROPAGATION_RECEIVER;

      If the state is `WAITING` `FOR` `MEMORY`, then consider increasing the Streams pool size.

    - Query the `V$STREAMS_POOL_STATISTICS` view.:

          SELECT TOTAL_MEMORY_ALLOCATED/CURRENT_SIZE FROM V$STREAMS_POOL_STATISTICS;

      If the value returned is.90 or greater, then consider increasing the Streams pool size.

##### Solution 1

##### To correct problem 1:

- Increase the Streams pool size by modifying the `STREAMS_POOL_SIZE` initialization parameter or by modifying other initialization parameters related to memory.

**See Also:**

- [Oracle Database Reference](../refrn/V-XSTREAM_CAPTURE.md)

- [Oracle Database Administrator’s Guide](../admin/creating-and-configuring-an-oracle-database.md) for information about setting initialization parameters

##### Problem 2: The Maximum SGA Size for the Capture Process Is Too Small

The `max_sga_size` capture process parameter controls the amount of system global area (SGA) memory allocated specifically to the capture process, in megabytes.

##### To determine whether the maximum SGA size for the capture process is too small:

1.  Connect to the database running the XStream component as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the following queries at the database:

    - Query the `V$XSTREAM_CAPTURE` view:

          SELECT CAPTURE_NAME AS CAP,
                  SGA_USED/(1024*1024) AS USED,
                  SGA_ALLOCATED/(1024*1024) AS ALLOCATED,
                  TOTAL_MESSAGES_CAPTURED AS CAPTURED,
                  TOTAL_MESSAGES_ENQUEUED AS ENQUEUED
            FROM V$XSTREAM_CAPTURE;

      If the `USED` field is equal to or almost equal to the `ALLOCATED` field in the output, then you might need to increase the maximum SGA size for the capture process.

    - Query the `V$LOGMNR_SESSION` view:

          SELECT SESSION_NAME AS CAP,
                  MAX_MEMORY_SIZE/(1024*1024) AS LMMAX,
                  USED_MEMORY_SIZE/(1024*1024) AS LMUSED,
                  USED_MEMORY_SIZE/MAX_MEMORY_SIZE AS PCT
            FROM V$LOGMNR_SESSION;

      If the `PCT` field is equal to or almost equal to 1 in the output, then you might need to increase the maximum SGA size for the capture process.

##### Solution 2

##### To correct problem 2:

- Increase the maximum SGA size for the capture process by modifying the `max_sga_size` capture process parameter.

**See Also:**

"[Setting a Capture Process Parameter](managing-xstream-out.md)"

##### Problem 3: Programming Errors

If there is enough memory in the Streams pool and the `MAX_SGA_SIZE` capture process parameter and apply parameter are set correctly, then check your client application for programming errors.

##### Solution 3

##### To correct problem 3:

- Correct the programming errors.

**Parent topic:** Problems and Solutions for XStream Out

### 7.3 How to Get More Help with XStream Out

Oracle Support can provide more help with XStream Out.

You can check My Oracle Support at [`http://support.oracle.com`](http://support.oracle.com) for more solutions to your problem.

You can visit [`http://www.oracle.com/support/contact.html`](http://www.oracle.com/support/contact.html) for more information about Oracle Support.

**Parent topic:** Troubleshooting XStream Out
