You can diagnose and correct problems with an XStream In configuration.

- Diagnosing Problems with XStream In
  You can diagnose problems with XStream In by using several different techniques.
- Problems and Solutions for XStream In
  You can implement solutions for common problems with XStream In.
- How to Get More Help with XStream In
  Oracle Support can provide more help with XStream In.

**See Also:**

- "[XStream Out Concepts](xstream-out-concepts.md)"

- "[XStream Use Cases](introduction-to-xstream.md)"

- "[Configuring XStream Out](configuring-xstream-out.md)"

**Parent topic:** [XStream In](xstream-in.md)

### 12.1 Diagnosing Problems with XStream In

You can diagnose problems with XStream In by using several different techniques.

- Viewing Alerts
  An alert is a warning about a potential problem or an indication that a critical threshold has been crossed.
- Checking the Trace File and Alert Log for Problems
  Messages about inbound server are recorded in trace files for the database in which the process is running.

**Parent topic:** Troubleshooting XStream In

#### 12.1.1 Viewing Alerts

An alert is a warning about a potential problem or an indication that a critical threshold has been crossed.

There are two types of alerts:

- Stateless: Alerts that indicate single events that are not necessarily tied to the system state. For example, an alert that indicates that a capture aborted with a specific error is a stateless alert.

- Stateful: Alerts that are associated with a specific system state. Stateful alerts are usually based on a numeric value, with thresholds defined at warning and critical levels. For example, an alert on the current Streams pool memory usage percentage, with the warning level at 85% and the critical level at 95%, is a stateful alert.

An Oracle database generates a stateless alert when an inbound server aborts.

An Oracle database generates a stateful XStream alert when the Streams pool memory usage exceeds the percentage specified by the `STREAMS_POOL_USED_PCT` metric. You can manage this metric with the `SET_THRESHOLD` procedure in the `DBMS_SERVER_ALERT` package.

You can view alerts in Oracle Enterprise Manager Cloud Control, or you can query the following data dictionary views:

- The `DBA_OUTSTANDING_ALERTS` view records current stateful alerts. The `DBA_ALERT_HISTORY` view records stateless alerts and stateful alerts that have been cleared. For example, if the memory usage in the Streams pool exceeds the specified threshold, then a stateful alert is recorded in the `DBA_OUTSTANDING_ALERTS` view.

- The `DBA_ALERT_HISTORY` data dictionary view shows alerts that have been cleared from the `DBA_OUTSTANDING_ALERTS` view. For example, if the memory usage in the Streams pool falls below the specified threshold, then the alert recorded in the `DBA_OUTSTANDING_ALERTS` view is cleared and moved to the `DBA_ALERT_HISTORY` view.

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

**See Also:**

- [Oracle Database 2 Day + Performance Tuning Guide](../tdppt/monitoring-performance-alerts.md) for information about managing alerts and metric thresholds

- [Oracle Database Administrator’s Guide](../admin/monitoring-the-database.md) for information about alerts and for information about subscribing to the `ALERT_QUE` queue to receive notifications when new alerts are generated

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_SERVER_ALERT.md) for more information about the `DBMS_SERVER_ALERT` package

- "[Configure the Streams pool](configuring-xstream-in.md)"

**Parent topic:** Diagnosing Problems with XStream In

#### 12.1.2 Checking the Trace File and Alert Log for Problems

Messages about inbound server are recorded in trace files for the database in which the process is running.

These trace file messages can help you to identify and resolve problems in an XStream In configuration.

All trace files for background processes are written to the Automatic Diagnostic Repository. The names of trace files are operating system specific, but each file usually includes the name of the process writing the file.

For example, on some operating systems, the trace file name for a process is `sid_xxxx_iiiii``.trc`, where:

- `sid` is the system identifier for the database

- `xxxx` is the name of the process

- `iiiii` is the operating system process number

Also, you can set the `write_alert_log` parameter to `y` for both a capture process and an outbound server. When this parameter is set to `y`, which is the default setting, the alert log for the database contains messages about why the capture process or outbound server stopped.

You can control the information in the trace files by setting the `trace_level` inbound server apply parameter using the `SET_PARAMETER` procedure in the `DBMS_XSTREAM_ADM` package.

An inbound server is an Oracle background process named `AP``nn`, where `nn` can include letters and numbers. For example, on some operating systems, if the system identifier for a database running an inbound server is `hqdb` and the inbound server number is `01`, then the trace file for the inbound server starts with `hqdb_AP01`.

An inbound server also uses other processes. Information about an inbound server might be recorded in the trace file for one or more of these processes. The process name of the reader server and apply servers is `AS``nn`, where `nn` can include letters and numbers. So, on some operating systems, if the system identifier for a database running an inbound server is `hqdb` and the process number is `01`, then the trace file that contains information about a process used by an inbound server starts with `hqdb_AS01`.

**See Also:**

- "[Displaying Session Information for Inbound Servers](monitoring-xstream-in.md)"

- [Oracle Database Administrator’s Guide](../admin/diagnosing-and-resolving-problems.md)for more information about trace files and the alert log, and for more information about their names and locations

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_APPLY_ADM.md)for more information about setting the `trace_level` apply parameter

- Your operating system specific Oracle documentation for more information about the names and locations of trace files

**Parent topic:** Diagnosing Problems with XStream In

### 12.2 Problems and Solutions for XStream In

You can implement solutions for common problems with XStream In.

In general, you can troubleshoot XStream inbound servers in the same way that you troubleshoot Oracle Apply processes.

- XStream In Cannot Identify an Inbound Server
  When an XStream In configuration cannot identify an inbound server, then there might be multiple subscribers to the inbound server’s queue.
- Inbound Server Encounters an ORA-03135 Error
  If the connection is broken between the inbound server and the XStream client application, restart the client application.
- Changes Are Failing to Reach the Client Application in XStream In
  In an XStream In configuration, database changes that should be streamed to apply handlers or to the XStream client application are not reaching the apply handler or client application.

**Parent topic:** Troubleshooting XStream In

#### 12.2.1 XStream In Cannot Identify an Inbound Server

When an XStream In configuration cannot identify an inbound server, then there might be multiple subscribers to the inbound server’s queue.

If an XStream In configuration cannot identify an inbound server, then an error is returned.

The following sections describe the possible problem and its solution.

##### Problem: Multiple Subscribers to the Inbound Server's Queue

The `ORA-26840` error indicates that there are multiple subscribers to the queue used by the inbound server. Subscribers can include inbound servers, outbound servers, apply processes, and propagations.

##### To determine whether there are multiple subscribers to the inbound server's queue:

1.  Connect to the inbound server database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the following query:

        SELECT OWNER, QUEUE_NAME, CONSUMER_NAME, ADDRESS
          FROM DBA_QUEUE_SUBSCRIBERS;

    You can add a `WHERE` clause to the query to limit the output to the inbound server's queue.

##### Solution

##### To correct the problem:

- If the query returns multiple subscribers to the inbound server's queue, then reconfigure the subscribers so that the inbound server is the only subscriber.

**See Also:**

"[Configuring XStream In](configuring-xstream-in.md)"

**Parent topic:** Problems and Solutions for XStream In

#### 12.2.2 Inbound Server Encounters an ORA-03135 Error

If the connection is broken between the inbound server and the XStream client application, restart the client application.

An inbound server encounters the following error:

    ORA-03135: connection lost contact

##### Problem: Connection Broken Between the Inbound Server and the Client Application

The `ORA-03135` error indicates that the connection between the inbound server and the XStream client application was broken.

##### Solution

##### To correct the problem:

- Restart the XStream client application.

**See Also:**

"[Sample XStream Client Application](sample-xstream-client-application.md)"

**Parent topic:** Problems and Solutions for XStream In

#### 12.2.3 Changes Are Failing to Reach the Client Application in XStream In

In an XStream In configuration, database changes that should be streamed to apply handlers or to the XStream client application are not reaching the apply handler or client application.

The following sections describe possible problems and their solutions.

##### Problem: LCRs Blocked in the Stream

LCRs might be blocked after reaching the inbound server. For example, the inbound server might be encountering errors and moving transactions to the error queue, or there might be another problem.

You can track an LCR through a stream using one of the following methods:

- Setting the `message_tracking_frequency` apply parameter to `1` or another relatively low value

  To disable LCR tracking when you use this method, set the `message_tracking_frequency` apply parameter to `NULL` or exit the session.

- Running the `SET_MESSAGE_TRACKING` procedure in the `DBMS_XSTREAM_ADM` package

  To disable LCR tracking when you use this method, set the `tracking_label` parameter to `NULL` in the `SET_MESSAGE_TRACKING` procedure or exit the session.

After using one of these methods, use the `V$XSTREAM_MESSAGE_TRACKING` view to monitor the progress of LCRs through a stream. If you are using Oracle GoldenGate to process the LCR, then you can use the `V$GOLDENGATE_MESSAGE_TRACKING` view to monitor the progress of LCRs through Oracle GoldenGate components. By tracking an LCR through the stream, you can determine where the LCR is blocked.

##### Solution

##### To correct problem:

- Take the appropriate action based on the reason that the LCR is blocked. For example, the following actions might correct the problem:

  - If an inbound server is encountering errors, then correct the problem that is causing the errors.

  - If an apply handler is not processing LCRs correctly, then correct the apply handler.

  - If an Oracle GoldenGate component is not processing LCRs correctly, then correct the Oracle GoldenGate component.

**See Also:**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_APPLY_ADM.md) for information about the `message_tracking_frequency` apply parameter

- The Oracle GoldenGate documentation for more information about Oracle GoldenGate

**Parent topic:** Problems and Solutions for XStream In

### 12.3 How to Get More Help with XStream In

Oracle Support can provide more help with XStream In.

You can check My Oracle Support at [`http://support.oracle.com`](http://support.oracle.com) for more solutions to your problem.

You can visit [`http://www.oracle.com/support/contact.html`](http://www.oracle.com/support/contact.html) for more information about Oracle Support.

**Parent topic:** Troubleshooting XStream In
