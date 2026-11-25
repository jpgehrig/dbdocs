You can monitor an XStream Out configuration.

**Note:**

Whenever possible, this chapter uses `ALL_` static data dictionary views for query examples. In some cases, information in the `ALL_` views is more limited than the information in the `DBA_` views.

- About Monitoring XStream Out
  You can query data dictionary views related to XStream for information about XStream components and statistics related to XStream.
- Monitoring Session Information About XStream Out Components
  An example illustrates monitoring session information about XStream Out components.
- Monitoring the History of Events for XStream Out Components
  An example illustrates monitoring the history of events for XStream components by querying the `DBA_REPLICATION_PROCESS_EVENTS` view.
- Monitoring an Outbound Server
  Sample queries illustrate how to monitor an outbound server.
- Monitoring the Capture Process for an Outbound Server
  Sample queries illustrate how to monitor the capture process for an outbound server.
- Monitoring XStream Rules
  A sample query illustrates how to monitor XStream rules.
- Monitoring Declarative Rule-Based Transformations
  A sample query illustrates how to monitor declarative rule-based transformations.

**See Also:**

- "[XStream Out Concepts](xstream-out-concepts.md)"

- "[XStream Use Cases](introduction-to-xstream.md)"

- "[Configuring XStream Out](configuring-xstream-out.md)"

- "[Troubleshooting XStream Out](troubleshooting-xstream-out.md)"

**Parent topic:** [XStream Out](xstream-out.md)

### 6.1 About Monitoring XStream Out

You can query data dictionary views related to XStream for information about XStream components and statistics related to XStream.

The main interface for monitoring XStream database components is SQL\*Plus, although you can monitor some aspects of an XStream configuring using Oracle Enterprise Manager Cloud Control. For example, you can view information about capture processes, outbound servers, inbound servers, and rules in Oracle Enterprise Manager Cloud Control.

In SQL\*Plus, trusted XStream administrators can query the `ALL_` and `DBA_` views. Untrusted XStream administrators can query the `ALL_` views only.

This chapter also describes using the Oracle Replication Performance Advisor to monitor an XStream configuration. The Oracle Replication Performance Advisor consists a collection of data dictionary views. The Oracle Replication Performance Advisor enables you to monitor the topology and performance of an XStream environment.

**Parent topic:** Monitoring XStream Out

### 6.2 Monitoring Session Information About XStream Out Components

An example illustrates monitoring session information about XStream Out components.

The query in this section displays the following session information about each XStream component in a database:

- The XStream component name

- The session identifier

- The serial number

- The operating system process identification number

- The XStream program name

This query is especially useful for determining the session information for specific XStream components when there are multiple XStream Out components configured in a database.

#### To display this information for each XStream component in a database:

1.  Connect to the database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the following query:

        COLUMN ACTION HEADING 'XStream Component' FORMAT A30
        COLUMN SID HEADING 'Session ID' FORMAT 99999
        COLUMN SERIAL# HEADING 'Session|Serial|Number' FORMAT 99999999
        COLUMN PROCESS HEADING 'Operating System|Process ID' FORMAT A17
        COLUMN PROCESS_NAME HEADING 'XStream|Program|Name' FORMAT A7

        SELECT /*+PARAM('_module_action_old_length',0)*/ ACTION,
               SID,
               SERIAL#,
               PROCESS,
               SUBSTR(PROGRAM,INSTR(PROGRAM,'(')+1,4) PROCESS_NAME
          FROM V$SESSION
          WHERE MODULE ='XStream';

Your output for an XStream Out configuration looks similar to the following:

                                                Session                   XStream
                                                 Serial Operating System  Program
    XStream Component              Session ID    Number Process ID        Name
    ------------------------------ ---------- --------- ----------------- -------
    XOUT - Apply Coordinator               21         9 27222             AP01
    CAP$_XOUT_18 - Capture                 28        33 27248             CP01
    XOUT - Apply Server                    97        43 27226             AS00
    XOUT - Apply Reader                   105         5 27224             AS01
    XOUT - Apply Server                   112        27 27342             TNS
    XOUT - Propagation Send/Rcv           117         5 27250             CS00

The row that shows `TNS` for the XStream program name contains information about the session for the XStream client application that is attached to the outbound server.

**See Also:**

[Oracle Database Reference](../refrn/V-SESSION.md) for more information about the `V$SESSION` view

**Parent topic:** Monitoring XStream Out

### 6.3 Monitoring the History of Events for XStream Out Components

An example illustrates monitoring the history of events for XStream components by querying the `DBA_REPLICATION_PROCESS_EVENTS` view.

For example, the view can display when a component was created or started. It can also display when a component parameter was changed. If the component encountered an error, the view can display information about the error.

The query in this topic displays the following information about XStream Out component events:

- The XStream component name

- The component type

- The event name

- The description of the event

- The event time

#### To display this information for each XStream Out component in a database:

1.  Connect to the database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the following query:

        COLUMN STREAMS_NAME FORMAT A12
        COLUMN PROCESS_TYPE FORMAT A17
        COLUMN EVENT_NAME FORMAT A10
        COLUMN DESCRIPTION FORMAT A20
        COLUMN EVENT_TIME FORMAT A15

        SELECT STREAMS_NAME,
               PROCESS_TYPE,
               EVENT_NAME,
               DESCRIPTION,
               EVENT_TIME
          FROM DBA_REPLICATION_PROCESS_EVENTS;

Your output for an XStream Out configuration looks similar to the following:

    STREAMS_NAME PROCESS_TYPE      EVENT_NAME DESCRIPTION          EVENT_TIME
    ------------ ----------------- ---------- -------------------- ---------------
    CAP$_XOUT_7  CAPTURE           CREATE     SUCCESS              10-NOV-15 12.30
                                                                   .13.845080 PM
    XOUT         APPLY COORDINATOR CREATE     SUCCESS              10-NOV-15 12.30
                                                                   .16.841110 PM
    "CAP$_XOUT_7 CAPTURE           ALTER      RULE_SET_NAME => "SY 10-NOV-15 12.30
    "                                         S"."RULESET$_12"     .17.373285 PM
    "XOUT"       APPLY COORDINATOR ALTER      RULE_SET_NAME => "SY 10-NOV-15 12.30
                                              S"."RULESET$_19"     .18.817718 PM
    "CAP$_XOUT_7 CAPTURE           PARAMETER  Change parameter 'XO 10-NOV-15 12.30
    "                              CHANGE     UT_CLIENT_EXISTS' to .19.100361 PM
                                               value 'Y'
    CAP$_XOUT_7  CAPTURE           START      SUCCESS              10-NOV-15 12.30
                                                                   .19.434029 PM
    XOUT         APPLY COORDINATOR START      SUCCESS              10-NOV-15 12.30
                                                                   .19.543379 PM
    XOUT         APPLY READER      START      SUCCESS              10-NOV-15 12.30
                                                                   .20.584332 PM
    XOUT         APPLY SERVER      START      SUCCESS              10-NOV-15 12.30
                                                                   .20.593923 PM
    CAP$_XOUT_7  CAPTURE SERVER    START      SUCCESS              10-NOV-15 12.30
                                                                   .20.926374 PM

**Related Topics**

- [Oracle Database Reference](../refrn/ALL_REPLICATION_PROCESS_EVENTS.md)

**Parent topic:** Monitoring XStream Out

### 6.4 Monitoring an Outbound Server

Sample queries illustrate how to monitor an outbound server.

With XStream Out, an Oracle Apply process functions as an outbound server. Therefore, you can also use the data dictionary views for apply processes to monitor outbound servers. In addition, an XStream Out environment includes capture processes and queues, and might include other components, such as propagations, rules, and rule-based transformations.

- Displaying General Information About an Outbound Server
  A sample query illustrates how to display general information about an outbound server.
- Displaying Status and Error Information for an Outbound Server
  A sample query illustrates how to display status and error information for an outbound server.
- Displaying Information About an Outbound Server's Current Transaction
  A sample query illustrates how to display information about an outbound server’s current transaction.
- Displaying Statistics for an Outbound Server
  An example illustrates how to display statistics for an outbound server.
- Displaying the Processed Low Position for an Outbound Server
  A sample query illustrates how to display the processed low position for an outbound server.
- Determining the Process Information for an Outbound Server
  A sample query illustrates how to determine the process information for an outbound server.
- Displaying the Apply Parameter Settings for an Outbound Server
  A sample query illustrates how to display the apply parameter settings for an outbound server.

**Parent topic:** Monitoring XStream Out

#### 6.4.1 Displaying General Information About an Outbound Server

A sample query illustrates how to display general information about an outbound server.

You can display the following information for an outbound server by running the query in this section:

- The outbound server name

- The name of the connect user for the outbound server

  The connect user is the user who can attach to the outbound server to retrieve the logical change record (LCR) stream. The client application must attach to the outbound server as the specified connect user.

- The name of the capture user for the capture process that captures changes for the outbound server to process

- The name of the capture process that captures changes for the outbound server to process

- The name of the source database for the captured changes

- The owner of the queue used by the outbound server

- The name of the queue used by the outbound server

The `ALL_XSTREAM_OUTBOUND` view contains information about the capture user, the capture process, and the source database in either of the following cases:

- The outbound server was created using the `CREATE_OUTBOUND` procedure in the `DBMS_XSTREAM_ADM` package.

- The outbound server was created using the `ADD_OUTBOUND` procedure in the `DBMS_XSTREAM_ADM` package, and the capture process for the outbound server runs on the same database as the outbound server.

If the outbound server was created using the `ADD_OUTBOUND` procedure, and the capture process for the outbound server is on a different database, then the `ALL_XSTREAM_OUTBOUND` view does not contain information about the capture user, the capture process, or the source database.

##### To display this general information about an outbound server:

1.  Connect to the database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the following query:

        COLUMN SERVER_NAME HEADING 'Outbound|Server|Name' FORMAT A10
        COLUMN CONNECT_USER HEADING 'Connect|User' FORMAT A10
        COLUMN CAPTURE_USER HEADING 'Capture|User' FORMAT A10
        COLUMN CAPTURE_NAME HEADING 'Capture|Process|Name' FORMAT A12
        COLUMN SOURCE_DATABASE HEADING 'Source|Database' FORMAT A11
        COLUMN QUEUE_OWNER HEADING 'Queue|Owner' FORMAT A10
        COLUMN QUEUE_NAME HEADING 'Queue|Name' FORMAT A10

        SELECT SERVER_NAME,
               CONNECT_USER,
               CAPTURE_USER,
               CAPTURE_NAME,
               SOURCE_DATABASE,
               QUEUE_OWNER,
               QUEUE_NAME
          FROM ALL_XSTREAM_OUTBOUND;

Your output looks similar to the following:

    Outbound                         Capture
    Server     Connect    Capture    Process      Source      Queue      Queue
    Name       User       User       Name         Database    Owner      Name
    ---------- ---------- ---------- ------------ ----------- ---------- ----------
    XOUT       XSTRMADMIN XSTRMADMIN CAP$_XOUT_18 XOUT.EXAMPL XSTRMADMIN Q$_XOUT_19
                                                  E.COM

**See Also:**

[Oracle Database Reference](../refrn/ALL_XSTREAM_OUTBOUND.md)

**Parent topic:** Monitoring an Outbound Server

#### 6.4.2 Displaying Status and Error Information for an Outbound Server

A sample query illustrates how to display status and error information for an outbound server.

The `DBA_APPLY` view shows `XStream` `Out` in the `PURPOSE` column for an apply process that is functioning as an outbound server.

##### To display detailed information about an outbound server:

1.  Connect to the database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the following query:

        COLUMN APPLY_NAME HEADING 'Outbound Server|Name' FORMAT A15
        COLUMN STATUS HEADING 'Status' FORMAT A8
        COLUMN ERROR_NUMBER HEADING 'Error Number' FORMAT 9999999
        COLUMN ERROR_MESSAGE HEADING 'Error Message' FORMAT A40

        SELECT APPLY_NAME,
               STATUS,
               ERROR_NUMBER,
               ERROR_MESSAGE
          FROM DBA_APPLY
          WHERE PURPOSE = 'XStream Out';

Your output looks similar to the following:

    Outbound Server
    Name            Status   Error Number Error Message
    --------------- -------- ------------ ----------------------------------------
    XOUT            ENABLED

This output shows that `XOUT` is an apply process that is functioning as an outbound server.

**Note:**

This example queries the `DBA_APPLY` view. This view enables trusted users to see information for all apply users in the database. Untrusted users must query the `ALL_APPLY` view, which limits information to the current user.

**See Also:**

[Oracle Database Reference](../refrn/ALL_APPLY.md)

**Parent topic:** Monitoring an Outbound Server

#### 6.4.3 Displaying Information About an Outbound Server's Current Transaction

A sample query illustrates how to display information about an outbound server’s current transaction.

The `V$XSTREAM_OUTBOUND_SERVER` view contains the following information about the transaction currently being processed by an XStream outbound server:

- The name of the outbound server

- The transaction ID of the transaction currently being processed

- Commit system change number (SCN) of the transaction currently being processed

- Commit position of the transaction currently being processed

- The position of the last LCR sent to the XStream client application

- The message number of the current LCR being processed by the outbound server

Run this query to determine how many LCRs an outbound server has processed in a specific transaction. You can query the `TOTAL_MESSAGE_COUNT` column in the `V$XSTREAM_TRANSACTION` view to determine the total number of LCRs in a transaction.

##### To display information about an outbound server's current transaction:

1.  Connect to the database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the following query:

        COLUMN SERVER_NAME HEADING 'Outbound|Server|Name' FORMAT A10
        COLUMN 'Transaction ID' HEADING 'Transaction|ID' FORMAT A11
        COLUMN COMMITSCN HEADING 'Commit SCN' FORMAT 9999999999999
        COLUMN COMMIT_POSITION HEADING 'Commit Position' FORMAT A15
        COLUMN LAST_SENT_POSITION HEADING 'Last Sent|Position' FORMAT A15
        COLUMN MESSAGE_SEQUENCE HEADING 'Message|Number' FORMAT 999999999

        SELECT SERVER_NAME,
               XIDUSN ||'.'||
               XIDSLT ||'.'||
               XIDSQN "Transaction ID",
               COMMITSCN,
               COMMIT_POSITION,
               LAST_SENT_POSITION,
               MESSAGE_SEQUENCE
          FROM V$XSTREAM_OUTBOUND_SERVER;

Your output looks similar to the following:

    Outbound
    Server     Transaction                                Last Sent          Message
    Name       ID              Commit SCN Commit Position Position            Number
    ---------- ----------- -------------- --------------- --------------- ----------
    XOUT       2.22.304            820023 0000000C82E4000 0000000C8337000        616
                                          000010000000100 000010000000100
                                          00000C82E400000 00000C833700000
                                          0010000000101   0010000000101

**Note:**

The `COMMITSCN` and `COMMIT_POSITION` values are populated only if the `COMMITTED_DATA_ONLY` value is `YES` in `V$XSTREAM_OUTBOUND_SERVER`.

**See Also:**

[Oracle Database Reference](../refrn/V-XSTREAM_OUTBOUND_SERVER.md)

**Parent topic:** Monitoring an Outbound Server

#### 6.4.4 Displaying Statistics for an Outbound Server

An example illustrates how to display statistics for an outbound server.

The `V$XSTREAM_OUTBOUND_SERVER` view contains the following statistics about the database changes processed by an XStream outbound server:

- The name of the outbound server

- The number of transactions sent from the outbound server to the XStream client application since the last time the client application attached to the outbound server

- The number of LCRs sent from the outbound server to the XStream client application since the last time the client application attached to the outbound server

- The number of megabytes sent from the outbound server to the XStream client application since the last time the client application attached to the outbound server

- The amount of time the outbound server spent sending LCRs to the XStream client application since the last time the client application attached to the outbound server

- The message number of the last LCR sent by the outbound server to the XStream client application

- Creation time at the source database of the last LCR sent by the outbound server to the client application

##### To display statistics for an outbound server:

1.  Connect to the database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the following query:

        COLUMN SERVER_NAME HEADING 'Outbound|Server|Name' FORMAT A8
        COLUMN TOTAL_TRANSACTIONS_SENT HEADING 'Total|Trans|Sent' FORMAT 9999999
        COLUMN TOTAL_MESSAGES_SENT HEADING 'Total|LCRs|Sent' FORMAT 9999999999
        COLUMN BYTES_SENT HEADING 'Total|MB|Sent' FORMAT 99999999999999
        COLUMN ELAPSED_SEND_TIME HEADING 'Time|Sending|LCRs|(in seconds)' FORMAT 99999999
        COLUMN LAST_SENT_MESSAGE_NUMBER HEADING 'Last|Sent|Message|Number' FORMAT 99999999
        COLUMN LAST_SENT_MESSAGE_CREATE_TIME HEADING 'Last|Sent|Message|Creation|Time' FORMAT A9

        SELECT SERVER_NAME,
               TOTAL_TRANSACTIONS_SENT,
               TOTAL_MESSAGES_SENT,
               (BYTES_SENT/1024)/1024 BYTES_SENT,
               (ELAPSED_SEND_TIME/100) ELAPSED_SEND_TIME,
               LAST_SENT_MESSAGE_NUMBER,
               TO_CHAR(LAST_SENT_MESSAGE_CREATE_TIME,'HH24:MI:SS MM/DD/YY')
                  LAST_SENT_MESSAGE_CREATE_TIME
          FROM V$XSTREAM_OUTBOUND_SERVER;

Your output looks similar to the following:

                                                                         Last
                                                          Time      Last Sent
    Outbound    Total       Total           Total      Sending      Sent Message
    Server      Trans        LCRs              MB         LCRs   Message Creation
    Name         Sent        Sent            Sent (in seconds)    Number Time
    -------- -------- ----------- --------------- ------------ --------- ---------
    XOUT         4028      256632              67            1    820023 10:11:00
                                                                         02/28/11

**Note:**

The `TOTAL_TRANSACTIONS_SENT` value is populated only if the `COMMITTED_DATA_ONLY` value is `YES` in `V$XSTREAM_OUTBOUND_SERVER`.

**See Also:**

[Oracle Database Reference](../refrn/V-XSTREAM_OUTBOUND_SERVER.md)

**Parent topic:** Monitoring an Outbound Server

#### 6.4.5 Displaying the Processed Low Position for an Outbound Server

A sample query illustrates how to display the processed low position for an outbound server.

For an outbound server, the processed low position is the position below which all transactions have been committed and logged by the client application. The processed low position is important when the outbound server or the client application is restarted.

You can display the following information about the processed low position for an outbound server by running the query in this section:

- The outbound server name

- The name of the source database for the captured changes

- The processed low position, which indicates the low watermark position processed by the client application

- The time when the processed low position was last updated by the outbound server

##### To display the processed low position for an outbound server:

1.  Connect to the database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the following query:

        COLUMN SERVER_NAME HEADING 'Outbound|Server|Name' FORMAT A10
        COLUMN SOURCE_DATABASE HEADING 'Source|Database' FORMAT A20
        COLUMN PROCESSED_LOW_POSITION HEADING 'Processed|Low LCR|Position' FORMAT A30
        COLUMN PROCESSED_LOW_TIME HEADING 'Processed|Low|Time' FORMAT A9

        SELECT SERVER_NAME,
               SOURCE_DATABASE,
               PROCESSED_LOW_POSITION,
               TO_CHAR(PROCESSED_LOW_TIME,'HH24:MI:SS MM/DD/YY') PROCESSED_LOW_TIME
        FROM ALL_XSTREAM_OUTBOUND_PROGRESS;

Your output looks similar to the following:

    Outbound                        Processed                      Processed
    Server     Source               Low LCR                        Low
    Name       Database             Position                       Time
    ---------- -------------------- ------------------------------ ---------
    XOUT       XOUT.EXAMPLE.COM     0000000C84EA000000000000000000 10:18:37
                                    00000C84EA000000000000000001   02/28/11

**See Also:**

- [Oracle Database Reference](../refrn/ALL_XSTREAM_OUTBOUND_PROGRESS.md)

- "[The Processed Low Position and Restartability for XStream Out](xstream-out-concepts.md)"

**Parent topic:** Monitoring an Outbound Server

#### 6.4.6 Determining the Process Information for an Outbound Server

A sample query illustrates how to determine the process information for an outbound server.

An outbound server is an Oracle background process. This background process runs only when an XStream client application attaches to the outbound server. The `V$XSTREAM_OUTBOUND_SERVER` view contains information about this background process.

You can display the following information for an outbound server by running the query in this section:

- The outbound server name

- The session ID of the outbound server's session

- The serial number of the outbound server's session

- The process identification number of the operating-system process that sends LCRs to the client application

##### To display the process information for an outbound server:

1.  Connect to the database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the following query:

        COLUMN SERVER_NAME HEADING 'Outbound Server Name' FORMAT A20
        COLUMN SID HEADING 'Session ID' FORMAT 9999999999
        COLUMN SERIAL# HEADING 'Serial Number' FORMAT 9999999999
        COLUMN SPID HEADING 'Operating-System Process' FORMAT A25

        SELECT SERVER_NAME,
               SID,
               SERIAL#,
               SPID
          FROM V$XSTREAM_OUTBOUND_SERVER;

Your output looks similar to the following:

    Outbound Server Name  Session ID Serial Number Operating-System Process
    -------------------- ----------- ------------- -------------------------
    XOUT                          18            19 15906

**Note:**

The `V$XSTREAM_APPLY_SERVER` view provides additional information about the outbound server process, and information about the apply server background processes used by the outbound server.

**See Also:**

[Oracle Database Reference](../refrn/V-XSTREAM_OUTBOUND_SERVER.md)

**Parent topic:** Monitoring an Outbound Server

#### 6.4.7 Displaying the Apply Parameter Settings for an Outbound Server

A sample query illustrates how to display the apply parameter settings for an outbound server.

Apply parameters determine how an outbound server operates.

##### To display the apply parameter settings for an outbound server:

1.  Connect to the database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the following query:

        COLUMN APPLY_NAME HEADING 'Outbound Server|Name' FORMAT A15
        COLUMN PARAMETER HEADING 'Parameter' FORMAT A30
        COLUMN VALUE HEADING 'Value' FORMAT A22
        COLUMN SET_BY_USER HEADING 'Set by|User?' FORMAT A10

        SELECT APPLY_NAME,
               PARAMETER,
               VALUE,
               SET_BY_USER
          FROM ALL_APPLY_PARAMETERS a, ALL_XSTREAM_OUTBOUND o
          WHERE a.APPLY_NAME=o.SERVER_NAME
          ORDER BY a.PARAMETER;

Your output looks similar to the following:

    Outbound Server                                                       Set by
    Name            Parameter                      Value                  User?
    --------------- ------------------------------ ---------------------- ----------
    XOUT            ALLOW_DUPLICATE_ROWS           N                      NO
    XOUT            APPLY_SEQUENCE_NEXTVAL         Y                      NO
    XOUT            COMMIT_SERIALIZATION           DEPENDENT_TRANSACTIONS NO
    XOUT            COMPARE_KEY_ONLY               N                      NO
    XOUT            COMPUTE_LCR_DEP_ON_ARRIVAL     N                      NO
    XOUT            DISABLE_ON_ERROR               Y                      NO
    XOUT            DISABLE_ON_LIMIT               N                      NO
    XOUT            EAGER_SIZE                     9500                   NO
    XOUT            ENABLE_XSTREAM_TABLE_STATS     Y                      NO
    XOUT            EXCLUDETAG                                            NO
    XOUT            EXCLUDETRANS                                          NO
    XOUT            EXCLUDEUSER                                           NO
    XOUT            EXCLUDEUSERID                                         NO
    XOUT            GETAPPLOPS                     Y                      NO
    XOUT            GETREPLICATES                  N                      NO
    XOUT            GROUPTRANSOPS                  10000                  NO
    XOUT            HANDLECOLLISIONS               N                      NO
    XOUT            IGNORE_TRANSACTION                                    NO
    XOUT            MAXIMUM_SCN                    INFINITE               NO
    XOUT            MAX_PARALLELISM                1                      NO
    XOUT            MAX_SGA_SIZE                   INFINITE               NO
    XOUT            OPTIMIZE_PROGRESS_TABLE        Y                      NO
    XOUT            OPTIMIZE_SELF_UPDATES          Y                      NO
    XOUT            PARALLELISM                    1                      NO
    XOUT            PRESERVE_ENCRYPTION            Y                      NO
    XOUT            RTRIM_ON_IMPLICIT_CONVERSION   Y                      NO
    XOUT            STARTUP_SECONDS                0                      NO
    XOUT            SUPPRESSTRIGGERS               Y                      NO
    XOUT            TIME_LIMIT                     INFINITE               NO
    XOUT            TRACE_LEVEL                    0                      NO
    XOUT            TRANSACTION_LIMIT              INFINITE               NO
    XOUT            TXN_AGE_SPILL_THRESHOLD        900                    NO
    XOUT            TXN_LCR_SPILL_THRESHOLD        10000                  NO
    XOUT            WRITE_ALERT_LOG                Y                      NO

Outbound servers ignore some apply parameter settings.

**Note:**

If the `Set` `by` `User?` column is `NO` for a parameter, then the parameter is set to its default value. If the `Set` `by` `User?` column is `YES` for a parameter, then the parameter was set by a user and might or might not be set to its default value.

**See Also:**

- "[Setting an Apply Parameter for an Outbound Server](managing-xstream-out.md)"

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_APPLY_ADM.md) for information about apply parameters

**Parent topic:** Monitoring an Outbound Server

### 6.5 Monitoring the Capture Process for an Outbound Server

Sample queries illustrate how to monitor the capture process for an outbound server.

- Displaying Change Capture Information About Each Capture Process
  A sample query illustrates how to display change capture information about each capture process.
- Displaying the Registered Redo Log Files for Each Capture Process
  A sample query illustrates how to display information about the archived redo log files that are registered for each capture process in a database.
- Displaying Redo Log Files That Are Required by Each Capture Process
  A sample query illustrates how to display redo log files that are required by each capture process.
- Displaying SCN Values for Each Redo Log File Used by Each Capture Process
  A sample query illustrates how to display information about the SCN values for archived redo log files that are registered for each capture process in a database.
- Listing the Parameter Settings for Each Capture Process
  A sample query illustrates how to list the parameter settings for each capture process.
- Determining the Applied SCN for Each Capture Process
  A sample query illustrates how to determine the applied SCN for each capture process.
- Displaying the Redo Log Scanning Latency for Each Capture Process
  A sample query illustrates how to display the redo log scanning latency for each capture process.
- Displaying the Extra Attributes Captured by a Capture Process
  A sample query illustrates how to display the extra attributes captured by a capture process.

**Parent topic:** Monitoring XStream Out

#### 6.5.1 Displaying Change Capture Information About Each Capture Process

A sample query illustrates how to display change capture information about each capture process.

The query in this section displays the following information about each capture process in a database:

- The name of the capture process.

- The current state of the capture process

  See "[Capture Process States](xstream-out-concepts.md)".

- The total number of redo entries passed by LogMiner to the capture process for detailed rule evaluation. A capture process converts a redo entry into an LCR and performs detailed rule evaluation on the LCR when capture process prefiltering cannot discard the change.

- The total number LCRs enqueued since the capture process was last started.

##### To display this change capture information about each capture process in a database:

1.  Connect to the database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the following query:

        COLUMN CAPTURE_NAME HEADING 'Capture|Name' FORMAT A15
        COLUMN STATE HEADING 'State' FORMAT A25
        COLUMN TOTAL_MESSAGES_CAPTURED HEADING 'Redo|Entries|Evaluated|In Detail' FORMAT 99999999999999
        COLUMN TOTAL_MESSAGES_ENQUEUED HEADING 'Total|LCRs|Enqueued' FORMAT 99999999999999

        SELECT CAPTURE_NAME,
               STATE,
               TOTAL_MESSAGES_CAPTURED,
               TOTAL_MESSAGES_ENQUEUED
          FROM V$XSTREAM_CAPTURE;

Your output looks similar to the following:

                                                         Redo
                                                      Entries           Total
    Capture                                         Evaluated            LCRs
    Name            State                           In Detail        Enqueued
    --------------- ------------------------- --------------- ---------------
    CAP$_XOUT_1     WAITING FOR TRANSACTION            297666          261798

The number of redo entries scanned can be higher than the number of DML and DDL redo entries captured by a capture process. Only DML and DDL redo entries that satisfy the rule sets of a capture process are captured and sent to an outbound server. Also, the total LCRs enqueued includes LCRs that contain transaction control statements. These row LCRs contain directives such as `COMMIT` and `ROLLBACK`. Therefore, the total LCRs enqueued is a number higher than the number of row changes and DDL changes enqueued by a capture process.

**See Also:**

"[Row LCRs](general-xstream-concepts.md)" for more information about transaction control statements

**Parent topic:** Monitoring the Capture Process for an Outbound Server

#### 6.5.2 Displaying the Registered Redo Log Files for Each Capture Process

A sample query illustrates how to display information about the archived redo log files that are registered for each capture process in a database.

The sample query displays information about these files for both local capture processes and downstream capture processes.

The query displays the following information for each registered archived redo log file:

- The name of a capture process that uses the file

- The source database of the file

- The sequence number of the file

- The name and location of the file at the local site

- Whether the file contains the beginning of a data dictionary build

- Whether the file contains the end of a data dictionary build

##### To display the registered redo log files for each capture process:

1.  Connect to the database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the following query:

        COLUMN CONSUMER_NAME HEADING 'Capture|Process|Name' FORMAT A15
        COLUMN SOURCE_DATABASE HEADING 'Source|Database' FORMAT A10
        COLUMN SEQUENCE# HEADING 'Sequence|Number' FORMAT 99999
        COLUMN NAME HEADING 'Archived Redo Log|File Name' FORMAT A20
        COLUMN DICTIONARY_BEGIN HEADING 'Dictionary|Build|Begin' FORMAT A10
        COLUMN DICTIONARY_END HEADING 'Dictionary|Build|End' FORMAT A10

        SELECT r.CONSUMER_NAME,
               r.SOURCE_DATABASE,
               r.SEQUENCE#,
               r.NAME,
               r.DICTIONARY_BEGIN,
               r.DICTIONARY_END
          FROM DBA_REGISTERED_ARCHIVED_LOG r, ALL_CAPTURE c
          WHERE r.CONSUMER_NAME = c.CAPTURE_NAME;

Your output looks similar to the following:

    Capture                                                  Dictionary Dictionary
    Process         Source     Sequence Archived Redo Log    Build      Build
    Name            Database     Number File Name            Begin      End
    --------------- ---------- -------- -------------------- ---------- ----------
    CAP$_XOUT_1     DBS2.EXAMP       15 /orc/dbs/log/arch2_1 NO         NO
                    LE.COM              _15_478347508.arc
    CAP$_XOUT_1     DBS2.EXAMP       16 /orc/dbs/log/arch2_1 NO         NO
                    LE.COM              _16_478347508.arc
    CAP$_XOUT_2     DBS1.EXAMP       45 /remote_logs/arch1_1 YES        YES
                    LE.COM              _45_478347335.arc
    CAP$_XOUT_2     DBS1.EXAMP       46 /remote_logs/arch1_1 NO         NO
                    LE.COM              _46_478347335.arc
    CAP$_XOUT_2     DBS1.EXAMP       47 /remote_logs/arch1_1 NO         NO
                    LE.COM              _47_478347335.arc

Assume that this query was run at the `dbs2.example.com` database, and that `cap$_xout_1` is a local capture process, and `cap$_xout_2` is a downstream capture process. The source database for the `cap$_xout_2` downstream capture process is `dbs1.example.com`. This query shows that there are two registered archived redo log files for `cap$_xout_1` and three registered archived redo log files for `cap$_xout_2`. This query shows the name and location of each of these files in the local file system.

**See Also:**

- "[Capture Process Overview](xstream-out-concepts.md)"

- "[Local Capture and Downstream Capture](xstream-out-concepts.md)"

- "[SCN Values Related to a Capture Process](xstream-out-concepts.md)" for information about dictionary builds

**Parent topic:** Monitoring the Capture Process for an Outbound Server

#### 6.5.3 Displaying Redo Log Files That Are Required by Each Capture Process

A sample query illustrates how to display redo log files that are required by each capture process.

A capture process needs the redo log file that includes the required checkpoint SCN, and all subsequent redo log files. You can query the `REQUIRED_CHECKPOINT_SCN` column in the `ALL_CAPTURE` data dictionary view to determine the required checkpoint SCN for a capture process. Redo log files before the redo log file that contains the required checkpoint SCN are no longer needed by the capture process. These redo log files can be stored offline if they are no longer needed for any other purpose. If you reset the start SCN for a capture process to a lower value in the future, then these redo log files might be needed.

The query displays the following information for each required archived redo log file:

- The name of a capture process that uses the file

- The source database of the file

- The sequence number of the file

- The name and location of the required redo log file at the local site

To display this information about each required archive redo log file in a database, run the following query:

1.  Connect to the database as the XStream administrator.
    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.
2.  Run the following query:
        COLUMN CONSUMER_NAME HEADING 'Capture|Process|Name' FORMAT A15
        COLUMN SOURCE_DATABASE HEADING 'Source|Database' FORMAT A10
        COLUMN SEQUENCE# HEADING 'Sequence|Number' FORMAT 99999
        COLUMN NAME HEADING 'Required|Archived Redo Log|File Name' FORMAT A40

        SELECT r.CONSUMER_NAME,
               r.SOURCE_DATABASE,
               r.SEQUENCE#,
               r.NAME
          FROM DBA_REGISTERED_ARCHIVED_LOG r, ALL_CAPTURE c
          WHERE r.CONSUMER_NAME =  c.CAPTURE_NAME AND
                r.NEXT_SCN      >= c.REQUIRED_CHECKPOINT_SCN;

Your output looks similar to the following:

    Capture                             Required
    Process         Source     Sequence Archived Redo Log
    Name            Database     Number File Name
    --------------- ---------- -------- ----------------------------------------
    CAP$_XOUT_1     DBS2.EXAMP       16 /orc/dbs/log/arch2_1_16_478347508.arc
                    LE.COM
    CAP$_XOUT_2     DBS1.EXAMP       47 /remote_logs/arch1_1_47_478347335.arc
                    LE.COM

**See Also:**

"[Capture Process Overview](xstream-out-concepts.md)"

**Parent topic:** Monitoring the Capture Process for an Outbound Server

#### 6.5.4 Displaying SCN Values for Each Redo Log File Used by Each Capture Process

A sample query illustrates how to display information about the SCN values for archived redo log files that are registered for each capture process in a database.

This query displays the SCN values for these files for both local capture processes and downstream capture processes. This query also identifies redo log files that are no longer needed by any capture process at the local database.

The query displays the following information for each registered archived redo log file:

- The capture process name of a capture process that uses the file

- The name and location of the file at the local site

- The lowest SCN value for the information contained in the redo log file

- The lowest SCN value for the next redo log file in the sequence

- Whether the redo log file is purgeable

##### To display SCN values for each redo log file used by each capture process:

1.  Connect to the database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the following query:

        COLUMN CONSUMER_NAME HEADING 'Capture|Process|Name' FORMAT A15
        COLUMN NAME HEADING 'Archived Redo Log|File Name' FORMAT A25
        COLUMN FIRST_SCN HEADING 'First SCN' FORMAT 99999999999
        COLUMN NEXT_SCN HEADING 'Next SCN' FORMAT 99999999999
        COLUMN PURGEABLE HEADING 'Purgeable?' FORMAT A10

        SELECT r.CONSUMER_NAME,
               r.NAME,
               r.FIRST_SCN,
               r.NEXT_SCN,
               r.PURGEABLE
          FROM DBA_REGISTERED_ARCHIVED_LOG r, ALL_CAPTURE c
          WHERE r.CONSUMER_NAME = c.CAPTURE_NAME;

Your output looks similar to the following:

    Capture
    Process         Archived Redo Log
    Name            File Name                    First SCN     Next SCN Purgeable?
    --------------- ------------------------- ------------ ------------ ----------
    CAP$_XOUT_1     /private1/ARCHIVE_LOGS/1_       509686       549100 YES
                    3_502628294.dbf

    CAP$_XOUT_1     /private1/ARCHIVE_LOGS/1_       549100       587296 YES
                    4_502628294.dbf

    CAP$_XOUT_1     /private1/ARCHIVE_LOGS/1_       587296       623107 NO
                    5_502628294.dbf

The redo log files with `YES` for `Purgeable?` for all capture processes will never be needed by any capture process at the local database. These redo log files can be removed without affecting any existing capture process at the local database. The redo log files with `NO` for `Purgeable?` for one or more capture processes must be retained.

**Parent topic:** Monitoring the Capture Process for an Outbound Server

#### 6.5.5 Listing the Parameter Settings for Each Capture Process

A sample query illustrates how to list the parameter settings for each capture process.

Capture process parameters determine how a capture process operates.

##### To list the parameter settings for each capture process:

1.  Connect to the database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the following query:

        COLUMN CAPTURE_NAME HEADING 'Capture|Process|Name' FORMAT A25
        COLUMN PARAMETER HEADING 'Parameter' FORMAT A30
        COLUMN VALUE HEADING 'Value' FORMAT A10
        COLUMN SET_BY_USER HEADING 'Set by|User?' FORMAT A10

        SELECT c.CAPTURE_NAME,
               PARAMETER,
               VALUE,
               SET_BY_USER
          FROM ALL_CAPTURE_PARAMETERS c, ALL_XSTREAM_OUTBOUND o
          WHERE c.CAPTURE_NAME=o.CAPTURE_NAME
          ORDER BY PARAMETER;

Your output looks similar to the following:

    Capture
    Process                                                             Set by
    Name                      Parameter                      Value      User?
    ------------------------- ------------------------------ ---------- ----------
    CAP$_XOUT_1               CAPTURE_IDKEY_OBJECTS          N          NO
    CAP$_XOUT_1               CAPTURE_SEQUENCE_NEXTVAL       N          NO
    CAP$_XOUT_1               DISABLE_ON_LIMIT               N          NO
    CAP$_XOUT_1               DOWNSTREAM_REAL_TIME_MINE      Y          NO
    CAP$_XOUT_1               EXCLUDETAG                                NO
    CAP$_XOUT_1               EXCLUDETRANS                              NO
    CAP$_XOUT_1               EXCLUDEUSER                               NO
    CAP$_XOUT_1               EXCLUDEUSERID                             NO
    CAP$_XOUT_1               GETAPPLOPS                     Y          NO
    CAP$_XOUT_1               GETREPLICATES                  N          NO
    CAP$_XOUT_1               IGNORE_TRANSACTION                        NO
    CAP$_XOUT_1               IGNORE_UNSUPPORTED_TABLE       *          NO
    CAP$_XOUT_1               INCLUDE_OBJECTS                           NO
    CAP$_XOUT_1               INLINE_LOB_OPTIMIZATION        N          NO
    CAP$_XOUT_1               MAXIMUM_SCN                    INFINITE   NO
    CAP$_XOUT_1               MAX_SGA_SIZE                   INFINITE   NO
    CAP$_XOUT_1               MERGE_THRESHOLD                60         NO
    CAP$_XOUT_1               MESSAGE_LIMIT                  INFINITE   NO
    CAP$_XOUT_1               MESSAGE_TRACKING_FREQUENCY     2000000    NO
    CAP$_XOUT_1               PARALLELISM                    0          NO
    CAP$_XOUT_1               SKIP_AUTOFILTERED_TABLE_DDL    Y          NO
    CAP$_XOUT_1               SPLIT_THRESHOLD                1800       NO
    CAP$_XOUT_1               STARTUP_SECONDS                0          NO
    CAP$_XOUT_1               TIME_LIMIT                     INFINITE   NO
    CAP$_XOUT_1               TRACE_LEVEL                    0          NO
    CAP$_XOUT_1               USE_RAC_SERVICE                N          NO
    CAP$_XOUT_1               WRITE_ALERT_LOG                Y          NO
    CAP$_XOUT_1               XOUT_CLIENT_EXISTS             Y          NO

**Note:**

If the `Set` `by` `User?` column is `NO` for a parameter, then the parameter is set to its default value. If the `Set` `by` `User?` column is `YES` for a parameter, then the parameter was set by a user and might or might not be set to its default value.

**See Also:**

- "[Capture Process Subcomponents](xstream-out-concepts.md)"

- "[Setting a Capture Process Parameter](managing-xstream-out.md)"

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_CAPTURE_ADM.md) for information about capture process parameters

**Parent topic:** Monitoring the Capture Process for an Outbound Server

#### 6.5.6 Determining the Applied SCN for Each Capture Process

A sample query illustrates how to determine the applied SCN for each capture process.

The applied system change number (SCN) for a capture process is the SCN of the most recent logical change record (LCR) dequeued by the relevant outbound servers. All changes below this applied SCN have been processed by all outbound servers that process changes captured by the capture process.

##### To determine the applied SCN for each capture process:

1.  Connect to the database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the following query:

        COLUMN CAPTURE_NAME HEADING 'Capture Process Name' FORMAT A30
        COLUMN APPLIED_SCN HEADING 'Applied SCN' FORMAT 99999999999

        SELECT CAPTURE_NAME, APPLIED_SCN FROM ALL_CAPTURE;

Your output looks similar to the following:

    Capture Process Name            Applied SCN
    ------------------------------ ------------
    CAP$_XOUT_1                          824825

**Parent topic:** Monitoring the Capture Process for an Outbound Server

#### 6.5.7 Displaying the Redo Log Scanning Latency for Each Capture Process

A sample query illustrates how to display the redo log scanning latency for each capture process.

You can find the following information about each capture process by running the query in this section:

- The redo log scanning latency, which specifies the number of seconds between the creation time of the most recent redo log entry scanned by a capture process and the current time. This number might be relatively large immediately after you start a capture process.

- The seconds since last recorded status, which is the number of seconds since a capture process last recorded its status.

- The current capture process time, which is the latest time when the capture process recorded its status.

- The logical change record (LCR) creation time, which is the time when the data manipulation language (DML) or data definition language (DDL) change generated the redo data at the source database for the most recently captured LCR.

The information displayed by this query is valid only for an enabled capture process.

##### To display the redo log scanning latency for each capture process:

1.  Connect to the database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the following query:

        COLUMN CAPTURE_NAME HEADING 'Capture|Process|Name' FORMAT A12
        COLUMN LATENCY_SECONDS HEADING 'Latency|in|Seconds' FORMAT 999999
        COLUMN LAST_STATUS HEADING 'Seconds Since|Last Status' FORMAT 999999
        COLUMN CAPTURE_TIME HEADING 'Current|Process|Time'
        COLUMN CREATE_TIME HEADING 'Message|Creation Time' FORMAT 999999

        SELECT CAPTURE_NAME,
               ((SYSDATE - CAPTURE_MESSAGE_CREATE_TIME)*86400) LATENCY_SECONDS,
               ((SYSDATE - CAPTURE_TIME)*86400) LAST_STATUS,
               TO_CHAR(CAPTURE_TIME, 'HH24:MI:SS MM/DD/YY') CAPTURE_TIME,
               TO_CHAR(CAPTURE_MESSAGE_CREATE_TIME, 'HH24:MI:SS MM/DD/YY') CREATE_TIME
          FROM V$XSTREAM_CAPTURE;

Your output looks similar to the following:

    Capture      Latency               Current
    Process           in Seconds Since Process           Message
    Name         Seconds   Last Status Time              Creation Time
    ------------ ------- ------------- ----------------- -----------------
    CAP$_XOUT_1        1             1 10:32:52 02/28/11 10:32:52 02/28/11

The `"Latency` `in` `Seconds"` returned by this query is the difference between the current time (`SYSDATE`) and the `"Message` `Creation` `Time."` The `"Seconds` `Since` `Last` `Status"` returned by this query is the difference between the current time (`SYSDATE`) and the `"Current` `Process` `Time."`

**Parent topic:** Monitoring the Capture Process for an Outbound Server

#### 6.5.8 Displaying the Extra Attributes Captured by a Capture Process

A sample query illustrates how to display the extra attributes captured by a capture process.

You can use the `INCLUDE_EXTRA_ATTRIBUTE` procedure in the `DBMS_CAPTURE_ADM` package to instruct a capture process to capture one or more extra attributes and include the extra attributes in logical change records (LCRs).

##### To display extra attributes captured by a capture process:

1.  Connect to the database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the following query:

        COLUMN CAPTURE_NAME HEADING 'Capture Process' FORMAT A20
        COLUMN ATTRIBUTE_NAME HEADING 'Attribute Name' FORMAT A15
        COLUMN INCLUDE HEADING 'Include Attribute in LCRs?' FORMAT A30

        SELECT CAPTURE_NAME, ATTRIBUTE_NAME, INCLUDE
          FROM ALL_CAPTURE_EXTRA_ATTRIBUTES
          ORDER BY CAPTURE_NAME;

Your output looks similar to the following:

    Capture Process      Attribute Name  Include Attribute in LCRs?
    -------------------- --------------- ------------------------------
    CAP$_XOUT_1          ROW_ID          NO
    CAP$_XOUT_1          SERIAL#         NO
    CAP$_XOUT_1          SESSION#        NO
    CAP$_XOUT_1          THREAD#         NO
    CAP$_XOUT_1          TX_NAME         YES
    CAP$_XOUT_1          USERNAME        NO

Based on this output, the capture process named `xcapture` includes the transaction name (`tx_name`) in the LCRs that it captures, but this capture process does not include any other extra attributes in the LCRs that it captures.

**See Also:**

- "[Extra Information in Row LCRs and DDL LCRs](general-xstream-concepts.md)"

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_CAPTURE_ADM.md)for more information about the `INCLUDE_EXTRA_ATTRIBUTE` procedure

**Parent topic:** Monitoring the Capture Process for an Outbound Server

### 6.6 Monitoring XStream Rules

A sample query illustrates how to monitor XStream rules.

The `ALL_XSTREAM_RULES` view contains information about the rules used by outbound servers and inbound servers. If an outbound server was created using the `CREATE_OUTBOUND` procedure in the `DBMS_XSTREAM_ADM` package, then these views also contain information about the rules used by the capture process that sends changes to the outbound server. However, if an outbound server was created using the `ADD_OUTBOUND` procedure, then these views do not contain information about the capture process rules. Also, these views do not contain information about the rules used by any propagation in the stream from a capture process to an outbound server.

#### To display information about the rules used by XStream components:

1.  Connect to the database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the following query:

        COLUMN STREAMS_NAME HEADING 'XStream|Component|Name' FORMAT A9
        COLUMN STREAMS_TYPE HEADING 'XStream|Component|Type' FORMAT A9
        COLUMN RULE_NAME HEADING 'Rule|Name' FORMAT A13
        COLUMN RULE_SET_TYPE HEADING 'Rule Set|Type' FORMAT A8
        COLUMN STREAMS_RULE_TYPE HEADING 'Rule|Level' FORMAT A7
        COLUMN SCHEMA_NAME HEADING 'Schema|Name' FORMAT A6
        COLUMN OBJECT_NAME HEADING 'Object|Name' FORMAT A11
        COLUMN RULE_TYPE HEADING 'Rule|Type' FORMAT A4

        SELECT STREAMS_NAME,
               STREAMS_TYPE,
               RULE_NAME,
               RULE_SET_TYPE,
               STREAMS_RULE_TYPE,
               SCHEMA_NAME,
               OBJECT_NAME,
               RULE_TYPE
          FROM ALL_XSTREAM_RULES;

Your output looks similar to the following:

    XStream   XStream
    Component Component Rule          Rule Set Rule    Schema Object      Rule
    Name      Type      Name          Type     Level   Name   Name        Type
    --------- --------- ------------- -------- ------- ------ ----------- ----
    XOUT      APPLY     ORDERS11      POSITIVE TABLE   OE     ORDERS      DML
    XOUT      APPLY     ORDERS12      POSITIVE TABLE   OE     ORDERS      DDL
    XOUT      APPLY     ORDER_ITEMS14 POSITIVE TABLE   OE     ORDER_ITEMS DML
    XOUT      APPLY     ORDER_ITEMS15 POSITIVE TABLE   OE     ORDER_ITEMS DDL
    XOUT      APPLY     HR16          POSITIVE SCHEMA  HR                 DML
    XOUT      APPLY     HR17          POSITIVE SCHEMA  HR                 DDL

Notice that the `STREAMS_TYPE` is `APPLY` even though the rules are in the positive rule set for the outbound server `xout`. You can determine the purpose of an apply component by querying the `PURPOSE` column in the `ALL_APPLY` view.

The `ALL_XSTREAM_RULES` view contains more information about the rules used in an XStream configuration than what is shown in this example. For example, you can query this view to show information about the rule sets used by XStream components.

To view information about the rules used by all components, including capture processes, propagations, apply processes, outbound servers, and inbound servers, you can query the `ALL_XSTREAM_RULES` view.

**See Also:**

[Oracle Database Reference](../refrn/ALL_XSTREAM_RULES.md)

**Parent topic:** Monitoring XStream Out

### 6.7 Monitoring Declarative Rule-Based Transformations

A sample query illustrates how to monitor declarative rule-based transformations.

A declarative rule-based transformations is a rule-based transformation that covers one of a common set of transformation scenarios for row LCRs. Declarative rule-based transformations are run internally without using PL/SQL.

The query in this section displays the following information about each declarative rule-based transformation in a database:

- The owner of the rule for which a declarative rule-based transformation is specified.

- The name of the rule for which a declarative rule-based transformation is specified.

- The type of declarative rule-based transformation specified. The following types are possible: `ADD` `COLUMN`, `DELETE` `COLUMN`, `KEEP` `COLUMNS`, `RENAME` `COLUMN`, `RENAME` `SCHEMA`, and `RENAME` `TABLE`.

- The precedence of the declarative rule-based transformation. The precedence is the execution order of a transformation in relation to other transformations with the same step number specified for the same rule. For transformations with the same step number, the transformation with the lowest precedence is executed first.

- The step number of the declarative rule-based transformation. If more than one declarative rule-based transformation is specified for the same rule, then the transformation with the lowest step number is executed first. You can specify the step number for a declarative rule-based transformation when you create the transformation.

You must have `DBA` role in order to access the `DBA_XSTREAM_TRANSFORMATIONS` view.

Run the following query to display this information for the declarative rule-based transformations in a database:

1.  Connect to the database as the XStream administrator.
    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.
2.  Run the following query:
        COLUMN RULE_OWNER HEADING 'Rule Owner' FORMAT A15
        COLUMN RULE_NAME HEADING 'Rule Name' FORMAT A15
        COLUMN DECLARATIVE_TYPE HEADING 'Declarative|Type' FORMAT A15
        COLUMN PRECEDENCE HEADING 'Precedence' FORMAT 99999
        COLUMN STEP_NUMBER HEADING 'Step Number' FORMAT 99999

        SELECT RULE_OWNER,
               RULE_NAME,
               DECLARATIVE_TYPE,
               PRECEDENCE,
               STEP_NUMBER
          FROM DBA_XSTREAM_TRANSFORMATIONS
          WHERE TRANSFORM_TYPE = 'DECLARATIVE TRANSFORMATION';

Your output looks similar to the following:

                                    Declarative
    Rule Owner      Rule Name       Type            Precedence Step Number
    --------------- --------------- --------------- ---------- -----------
    XSTRMADMIN      JOBS26          RENAME TABLE             4           0
    XSTRMADMIN      EMPLOYEES22     ADD COLUMN               3           0

Based on this output, the `ADD` `COLUMN` transformation executes before the `RENAME` `TABLE` transformation because the step number is the same (zero) for both transformations and the `ADD` `COLUMN` transformation has the lower precedence.

The `DBA_XSTREAM_TRANSFORMATIONS` view can display more detailed information about each transformation based on the declarative type of the transformation. Include a `WHERE` clause in the query with the `DECLARATIVE_TYPE` equal to the type of transformation, such as `ADD` `COLUMN`, `DELETE` `COLUMN`, and so on.

For example, the previous query listed an `ADD` `COLUMN` transformation and a `RENAME` `TABLE` transformation.

**Note:**

Precedence and step number pertain only to declarative rule-based transformations. They do not pertain to subset rule transformations or custom rule-based transformations.

- Displaying Information About ADD COLUMN Transformations
  A sample query illustrates how to display detailed information about the `ADD` `COLUMN` declarative rule-based transformations in a database.
- Displaying Information About RENAME TABLE Transformations
  A sample query illustrates how to display detailed information about the `RENAME` `TABLE` declarative rule-based transformations in a database.

**See Also:**

- "[Rule-Based Transformations](general-xstream-concepts.md)"

- "[Managing Declarative Rule-Based Transformations](managing-xstream-out.md)"

**Parent topic:** Monitoring XStream Out

#### 6.7.1 Displaying Information About ADD COLUMN Transformations

A sample query illustrates how to display detailed information about the `ADD` `COLUMN` declarative rule-based transformations in a database.

You use the view `DBA_XTREAM_TRANSFORMATIONS` to display information about the columns that are added to row LCRs with the declarative rule-based transformation procedure `DBMS_XSTREAM_ADM`.

##### To display information about `ADD` `COLUMN` transformations:

1.  Connect to the database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the following query:

        COLUMN RULE_OWNER HEADING 'Rule|Owner' FORMAT A10
        COLUMN RULE_NAME HEADING 'Rule|Name' FORMAT A11
        COLUMN SCHEMA_NAME HEADING 'Schema|Name' FORMAT A6
        COLUMN TABLE_NAME HEADING 'Table|Name' FORMAT A9
        COLUMN COLUMN_NAME HEADING 'Column|Name' FORMAT A10
        COLUMN COLUMN_VALUE HEADING 'Column|Value' FORMAT A10
        COLUMN COLUMN_TYPE HEADING 'Column|Type' FORMAT A8

        SELECT RULE_OWNER,
               RULE_NAME,
               SCHEMA_NAME,
               TABLE_NAME,
               COLUMN_NAME,
               ANYDATA.AccessDate(COLUMN_VALUE) "Value",
               COLUMN_TYPE
          FROM DBA_XSTREAM_TRANSFORMATIONS
          WHERE DECLARATIVE_TYPE = 'ADD COLUMN';

Your output looks similar to the following:

    Rule       Rule        Schema   Table    Column     Column      Column
    Owner      Name        Name     Name     Name       Value       Type
    ----------  ----------- ------  --------- ---------- ---------- --------
    XSTRMADMIN  EMPLOYEES22 HR      EMPLOYEES BIRTH_DATE            SYS.DATE

This output show the following information about the `ADD` `COLUMN` declarative rule-based transformation:

- It is specified on the `employees22` rule in the `xstrmadmin` schema.

- It adds a column to row LCRs that involve the `employees` table in the `hr` schema.

- The column name of the added column is `BIRTH_DATE`.

- The value of the added column is `NULL`. The `COLUMN_VALUE` column in the `ALL_XSTREAM_TRANSFORMATIONS` view is type `ANYDATA`. In this example, because the column type is `DATE`, the `ANYDATA.AccessDate` member function is used to display the value. Use the appropriate member function to display values of other types.

- The column type of the added column is `DATE`.

**Parent topic:** Monitoring Declarative Rule-Based Transformations

#### 6.7.2 Displaying Information About RENAME TABLE Transformations

A sample query illustrates how to display detailed information about the `RENAME` `TABLE` declarative rule-based transformations in a database.

You use the view `DBA_XSTREAM_TRANSFORMATIONS` to display information about declarative rule-based transformations that rename a table in a row logical change record (LCR).

##### To display information about `RENAME` `TABLE` transformations:

1.  Connect to the database as the XStream administrator.

    See [Oracle Database Administrator's Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the following query:

        COLUMN RULE_OWNER HEADING 'Rule|Owner' FORMAT A10
        COLUMN RULE_NAME HEADING 'Rule|Name' FORMAT A10
        COLUMN FROM_SCHEMA_NAME HEADING 'From|Schema|Name' FORMAT A10
        COLUMN TO_SCHEMA_NAME HEADING 'To|Schema|Name' FORMAT A10
        COLUMN FROM_TABLE_NAME HEADING 'From|Table|Name' FORMAT A15
        COLUMN TO_TABLE_NAME HEADING 'To|Table|Name' FORMAT A15

        SELECT RULE_OWNER,
               RULE_NAME,
               FROM_SCHEMA_NAME,
               TO_SCHEMA_NAME,
               FROM_TABLE_NAME,
               TO_TABLE_NAME
          FROM DBA_XSTREAM_TRANSFORMATIONS
          WHERE DECLARATIVE_TYPE = 'RENAME TABLE';

Your output looks similar to the following:

                          From       To         From            To
    Rule       Rule       Schema     Schema     Table           Table
    Owner      Name       Name       Name       Name            Name
    ---------- ---------- ---------- ---------- --------------- ---------------
    XSTRMADMIN JOBS26     HR         HR         HR.JOBS         HR.ASSIGNMENTS

This output show the following information about the `RENAME` `TABLE` declarative rule-based transformation:

- It is specified on the `jobs26` rule in the `xstrmadmin` schema.

- It renames the `hr.jobs` table in row LCRs to the `hr.assignments` table.

**Parent topic:** Monitoring Declarative Rule-Based Transformations
