You can monitor an XStream In configuration by querying data dictionary views.

This chapter provides instructions for monitoring XStream.

With XStream In, an Oracle Apply process functions as an inbound server. Therefore, you can also use the data dictionary views for apply processes to monitor inbound servers.

**Note:**

Whenever possible, this chapter uses `ALL_` static data dictionary views for query examples. In some cases, information in the `ALL_` views is more limited than the information in the `DBA_` views.

In SQL\*Plus, trusted XStream administrators can query the `ALL_` and `DBA_` views. Untrusted XStream administrators can query the `ALL_` views only.

- Displaying Session Information for Inbound Servers
  An example illustrates displaying session information for inbound servers.
- Displaying General Information About an Inbound Server
  An example illustrates displaying general information about an inbound server.
- Monitoring the History of Events for XStream In Components
  An example illustrates monitoring the history of events for XStream In components by querying the `DBA_REPLICATION_PROCESS_EVENTS` view.
- Displaying the Status and Error Information for an Inbound Server
  An example illustrates displaying the status and error information for an inbound server.
- Displaying Apply Parameter Settings for an Inbound Server
  An example illustrates displaying apply parameter settings for an inbound server.
- Displaying the Position Information for an Inbound Server
  An example illustrates displaying the position information for an inbound server.
- Displaying Information About DML Conflict Handlers
  The `DBA_APPLY_DML_CONF_HANDLERS` view displays information about DML conflict handlers.
- Displaying Information About Error Handlers
  The `DBA_APPLY_REPERROR_HANDLERS` view displays information about DML conflict handlers.
- Checking for Apply Errors
  An example illustrates checking for apply errors.
- Displaying Detailed Information About Apply Errors
  SQL scripts display detailed information about the error transactions in the error queue in a database.

**See Also:**

- "[XStream Out Concepts](xstream-out-concepts.md)"

- "[XStream Use Cases](introduction-to-xstream.md)"

- "[Troubleshooting XStream In](troubleshooting-xstream-in.md)"

**Parent topic:** [XStream In](xstream-in.md)

### 11.1 Displaying Session Information for Inbound Servers

An example illustrates displaying session information for inbound servers.

The query in this section displays the following session information about each XStream component in a database:

- The XStream component name

- The session identifier

- The serial number

- The operating system process identification number

- The XStream process number

This query is especially useful for determining the session information for specific XStream components when there are multiple XStream In components configured in a database.

#### To display this information for each XStream component in a database:

1.  Connect to the database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the following query:

        COLUMN ACTION HEADING 'XStream Component' FORMAT A30
        COLUMN SID HEADING 'Session ID' FORMAT 99999
        COLUMN SERIAL# HEADING 'Session|Serial|Number' FORMAT 99999999
        COLUMN PROCESS HEADING 'Operating System|Process Number' FORMAT A17
        COLUMN PROCESS_NAME HEADING 'XStream|Process|Number' FORMAT A7

        SELECT /*+PARAM('_module_action_old_length',0)*/ ACTION,
               SID,
               SERIAL#,
               PROCESS,
               SUBSTR(PROGRAM,INSTR(PROGRAM,'(')+1,4) PROCESS_NAME
          FROM V$SESSION
          WHERE MODULE ='XStream';

Your output for an XStream In configuration looks similar to the following:

                                                Session                   XStream
                                                 Serial Operating System  Process
    XStream Component              Session ID    Number Process Number    Number
    ------------------------------ ---------- --------- ----------------- -------
    XIN - Apply Reader                     19         9 27304             AS01
    XIN - Apply Server                     22         5 27308             AS03
    XIN - Apply Server                     25        31 27313             AS05
    XIN - Apply Coordinator               112         7 27302             AP01
    XIN - Apply Server                    113         5 27306             AS02
    XIN - Propagation Receiver            114        17 27342             TNS
    XIN - Apply Server                    115        39 27311             AS04

The row that shows `TNS` for the XStream process number contains information about the session for the XStream client application that is attached to the inbound server.

**Note:**

To run this query, a user must have the necessary privileges to query the `V$SESSION` view.

**See Also:**

[Oracle Database Reference](../refrn/V-SESSION.md) for more information about the `V$SESSION` view

**Parent topic:** Monitoring XStream In

### 11.2 Displaying General Information About an Inbound Server

An example illustrates displaying general information about an inbound server.

You can display the following information for an inbound server by running the query in this section:

- The inbound server name

- The owner of the queue used by the inbound server

- The name of the queue used by the inbound server

- The apply user for the inbound server

#### To display general information about an inbound server:

1.  Connect to the database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the following query:

        COLUMN SERVER_NAME HEADING 'Inbound Server Name' FORMAT A20
        COLUMN QUEUE_OWNER HEADING 'Queue Owner' FORMAT A15
        COLUMN QUEUE_NAME HEADING 'Queue Name' FORMAT A15
        COLUMN APPLY_USER HEADING 'Apply User' FORMAT A15

        SELECT SERVER_NAME,
               QUEUE_OWNER,
               QUEUE_NAME,
               APPLY_USER
          FROM ALL_XSTREAM_INBOUND;

Your output looks similar to the following:

    Inbound Server Name  Queue Owner     Queue Name      Apply User
    -------------------- --------------- --------------- ---------------
    XIN                  XSTRMADMIN      XIN_QUEUE       XSTRMADMIN

**See Also:**

[Oracle Database Reference](../refrn/ALL_XSTREAM_INBOUND.md)

**Parent topic:** Monitoring XStream In

### 11.3 Monitoring the History of Events for XStream In Components

An example illustrates monitoring the history of events for XStream In components by querying the `DBA_REPLICATION_PROCESS_EVENTS` view.

For example, this view can display when a component was created or started. It can also display when a component parameter was changed. If the component encountered an error, then it can display information about the error.

The query in this topic displays the following information about XStream Out component events:

- The XStream component name

- The component type

- The event name

- The description of the event

- The event time

#### To display this information for each XStream In component in a database:

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

Your output for an XStream In configuration looks similar to the following:

    STREAMS_NAME PROCESS_TYPE      EVENT_NAME DESCRIPTION          EVENT_TIME
    ------------ ----------------- ---------- -------------------- ---------------
    APP_JOBS     APPLY COORDINATOR CREATE     SUCCESS              03-NOV-15 07.19
                                                                   .27.238151 AM
    APP_JOBS     APPLY COORDINATOR START      SUCCESS              03-NOV-15 07.21
                                                                   .50.812534 AM
    APP_JOBS     APPLY READER      START      SUCCESS              03-NOV-15 07.21
                                                                   .51.713367 AM
    APP_JOBS     APPLY SERVER      START      SUCCESS              03-NOV-15 07.21
                                                                   .51.895019 AM

**Related Topics**

- [Oracle Database Reference](../refrn/ALL_REPLICATION_PROCESS_EVENTS.md)

**Parent topic:** Monitoring XStream In

### 11.4 Displaying the Status and Error Information for an Inbound Server

An example illustrates displaying the status and error information for an inbound server.

The `DBA_APPLY` view shows `XStream` `In` in the `PURPOSE` column for an apply process that is functioning as an inbound server.

#### To display the status of an inbound server:

1.  Connect to the database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the following query:

        COLUMN APPLY_NAME HEADING 'Inbound Server|Name' FORMAT A15
        COLUMN STATUS HEADING 'Status' FORMAT A8
        COLUMN ERROR_NUMBER HEADING 'Error Number' FORMAT 9999999
        COLUMN ERROR_MESSAGE HEADING 'Error Message' FORMAT A40

        SELECT APPLY_NAME,
               STATUS,
               ERROR_NUMBER,
               ERROR_MESSAGE
          FROM DBA_APPLY
          WHERE PURPOSE = 'XStream In';

Your output looks similar to the following:

    Inbound Server
    Name            Status   Error Number Error Message
    --------------- -------- ------------ ----------------------------------------
    XIN             ENABLED

This output shows that `XIN` is an apply process that is functioning as an inbound server.

**Note:**

This example queries the `DBA_APPLY` view. This view enables trusted users to see information for all apply users in the database. Untrusted users must query the `ALL_APPLY` view, which limits information to the current user.

**See Also:**

[Oracle Database Reference](../refrn/ALL_APPLY.md)

**Parent topic:** Monitoring XStream In

### 11.5 Displaying Apply Parameter Settings for an Inbound Server

An example illustrates displaying apply parameter settings for an inbound server.

Apply parameters determine how an inbound server operates.

#### To display the apply parameter settings for an inbound server:

1.  Connect to the database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the following query:

        COLUMN APPLY_NAME HEADING 'Inbound Server|Name' FORMAT A15
        COLUMN PARAMETER HEADING 'Parameter' FORMAT A30
        COLUMN VALUE HEADING 'Value' FORMAT A22
        COLUMN SET_BY_USER HEADING 'Set by|User?' FORMAT A10

        SELECT APPLY_NAME,
               PARAMETER,
               VALUE,
               SET_BY_USER
          FROM ALL_APPLY_PARAMETERS a, ALL_XSTREAM_INBOUND i
          WHERE a.APPLY_NAME=i.SERVER_NAME
          ORDER BY a.PARAMETER;

Your output looks similar to the following:

    Inbound Server                                                        Set by
    Name            Parameter                      Value                  User?
    --------------- ------------------------------ ---------------------- ----------
    XIN             ALLOW_DUPLICATE_ROWS           N                      NO
    XIN             APPLY_SEQUENCE_NEXTVAL         Y                      NO
    XIN             COMMIT_SERIALIZATION           DEPENDENT_TRANSACTIONS NO
    XIN             COMPARE_KEY_ONLY               Y                      NO
    XIN             COMPUTE_LCR_DEP_ON_ARRIVAL     N                      NO
    XIN             DISABLE_ON_ERROR               Y                      NO
    XIN             DISABLE_ON_LIMIT               N                      NO
    XIN             EAGER_SIZE                     9500                   NO
    XIN             ENABLE_XSTREAM_TABLE_STATS     Y                      NO
    XIN             EXCLUDETAG                                            NO
    XIN             EXCLUDETRANS                                          NO
    XIN             EXCLUDEUSER                                           NO
    XIN             EXCLUDEUSERID                                         NO
    XIN             GETAPPLOPS                     Y                      NO
    XIN             GETREPLICATES                  N                      NO
    XIN             GROUPTRANSOPS                  250                    NO
    XIN             HANDLECOLLISIONS               N                      NO
    XIN             IGNORE_TRANSACTION                                    NO
    XIN             MAXIMUM_SCN                    INFINITE               NO
    XIN             MAX_PARALLELISM                50                     NO
    XIN             MAX_SGA_SIZE                   INFINITE               NO
    XIN             OPTIMIZE_PROGRESS_TABLE        Y                      NO
    XIN             OPTIMIZE_SELF_UPDATES          Y                      NO
    XIN             PARALLELISM                    4                      NO
    XIN             PRESERVE_ENCRYPTION            Y                      NO
    XIN             RTRIM_ON_IMPLICIT_CONVERSION   Y                      NO
    XIN             STARTUP_SECONDS                0                      NO
    XIN             SUPPRESSTRIGGERS               Y                      NO
    XIN             TIME_LIMIT                     INFINITE               NO
    XIN             TRACE_LEVEL                    0                      NO
    XIN             TRANSACTION_LIMIT              INFINITE               NO
    XIN             TXN_AGE_SPILL_THRESHOLD        900                    NO
    XIN             TXN_LCR_SPILL_THRESHOLD        10000                  NO
    XIN             WRITE_ALERT_LOG                Y                      NO

Inbound servers ignore some apply parameter settings.

**Note:**

If the `Set` `by` `User?` column is `NO` for a parameter, then the parameter is set to its default value. If the `Set` `by` `User?` column is `YES` for a parameter, then the parameter was set by a user and might or might not be set to its default value.

**See Also:**

- "[Setting an Apply Parameter for an Inbound Server](managing-xstream-in.md)"

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_APPLY_ADM.md) for information about apply parameters

**Parent topic:** Monitoring XStream In

### 11.6 Displaying the Position Information for an Inbound Server

An example illustrates displaying the position information for an inbound server.

For an inbound server, you can view position information by querying the `ALL_XSTREAM_INBOUND_PROGRESS` view. Specifically, you can display the following position information by running the query in this section:

- The inbound server name

- The applied low position for the inbound server

- The spill position for the inbound server

- The applied high position for the inbound server

- The processed low position for the inbound server

#### To display the position information for an inbound server:

1.  Connect to the database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the following query:

        COLUMN SERVER_NAME HEADING 'Inbound|Server|Name' FORMAT A10
        COLUMN APPLIED_LOW_POSITION HEADING 'Applied Low|Position' FORMAT A15
        COLUMN SPILL_POSITION HEADING 'Spill Position' FORMAT A15
        COLUMN APPLIED_HIGH_POSITION HEADING 'Applied High|Position' FORMAT A15
        COLUMN PROCESSED_LOW_POSITION HEADING 'Processed Low|Position' FORMAT A15

        SELECT SERVER_NAME,
               APPLIED_LOW_POSITION,
               SPILL_POSITION,
               APPLIED_HIGH_POSITION,
               PROCESSED_LOW_POSITION
          FROM ALL_XSTREAM_INBOUND_PROGRESS;

Your output looks similar to the following:

    Inbound
    Server     Applied Low                     Applied High    Processed Low
    Name       Position        Spill Position  Position        Position
    ---------- --------------- --------------- --------------- ---------------
    XIN        C10A            C11D            C10A            C11D

The values of the positions shown in the output were set by the client application that attaches to the inbound server. However, the inbound server determines which values are the current applied low position, spill position, applied high position, and processed low position.

**See Also:**

- [Oracle Database Reference](../refrn/ALL_XSTREAM_INBOUND_PROGRESS.md)

- "[Position Order in an LCR Stream](general-xstream-concepts.md)"

- "[Position of LCRs and XStream In](xstream-in-concepts.md)"

**Parent topic:** Monitoring XStream In

### 11.7 Displaying Information About DML Conflict Handlers

The `DBA_APPLY_DML_CONF_HANDLERS` view displays information about DML conflict handlers.

You can configure DML conflict handlers using the `SET_DML_CONFLICT_HANDLER` procedure in the `DBMS_APPLY_ADM` package.

1.  Connect to the database as the XStream administrator.
2.  Query the `DBA_APPLY_DML_CONF_HANDLERS` view.

Example 11-1 Displaying Information About DML Conflict Handlers

    COLUMN APPLY_NAME FORMAT A8
    COLUMN OBJECT_OWNER FORMAT A5
    COLUMN OBJECT_NAME FORMAT A12
    COLUMN COMMAND_TYPE FORMAT A6
    COLUMN CONFLICT_TYPE FORMAT A11
    COLUMN METHOD_NAME FORMAT A12
    COLUMN CONFLICT_HANDLER_NAME FORMAT A20

    SELECT APPLY_NAME,
           OBJECT_OWNER,
           OBJECT_NAME,
           COMMAND_TYPE,
           CONFLICT_TYPE,
           METHOD_NAME,
           CONFLICT_HANDLER_NAME
      FROM DBA_APPLY_DML_CONF_HANDLERS
      ORDER BY OBJECT_OWNER, OBJECT_NAME, CONFLICT_HANDLER_NAME;

Your output looks similar to the following:

    APPLY_NA OBJEC OBJECT_NAME  COMMAN CONFLICT_TY METHOD_NAME  CONFLICT_HANDLER_NAM
    -------- ----- ------------ ------ ----------- ------------ --------------------
    APP_JOBS HR    JOBS         DELETE ROW_MISSING IGNORE       JOBS_HANDLER_DELETE
    APP_JOBS HR    JOBS         INSERT ROW_EXISTS  OVERWRITE    JOBS_HANDLER_INSERT
    APP_JOBS HR    JOBS         UPDATE ROW_EXISTS  OVERWRITE    JOBS_HANDLER_UPDATE

**Related Topics**

- [Setting a DML Conflict Handler](managing-xstream-in.md)

**Parent topic:** Monitoring XStream In

### 11.8 Displaying Information About Error Handlers

The `DBA_APPLY_REPERROR_HANDLERS` view displays information about DML conflict handlers.

You can configure error handlers using the `SET_REPERROR_HANDLER` procedure in the `DBMS_APPLY_ADM` package.

1.  Connect to the database as the XStream administrator.
2.  Query the `DBA_APPLY_REPERROR_HANDLERS` view.

Example 11-2 Displaying Information About DML Conflict Handlers

    COLUMN APPLY_NAME FORMAT A15
    COLUMN OBJECT_OWNER FORMAT A15
    COLUMN OBJECT_NAME FORMAT A15
    COLUMN ERROR_NUMBER 999999999
    COLUMN METHOD FORMAT A15

    SELECT APPLY_NAME,
           OBJECT_OWNER,
           OBJECT_NAME,
           ERROR_NUMBER,
           METHOD
      FROM DBA_APPLY_REPERROR_HANDLERS
      ORDER BY OBJECT_OWNER, OBJECT_NAME;

Your output looks similar to the following:

    APPLY_NAME      OBJECT_OWNER    OBJECT_NAME     ERROR_NUMBER METHOD
    --------------- --------------- --------------- ------------ ---------------
    APP_OE          OE              ORDERS                 26787 IGNORE

**Related Topics**

- [Setting and Unsetting an Error Handler](managing-xstream-in.md)

**Parent topic:** Monitoring XStream In

### 11.9 Checking for Apply Errors

An example illustrates checking for apply errors.

Trusted users can check for apply errors by querying the `DBA_APPLY_ERROR` data dictionary view or by using Oracle Enterprise Manager Cloud Control. Untrusted users can check for apply errors by querying the `ALL_APPLY_ERROR` data dictionary view.

#### To check for apply errors:

1.  Connect to the database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the following query:

        COLUMN APPLY_NAME HEADING 'Inbound|Server|Name' FORMAT A7
        COLUMN SOURCE_DATABASE HEADING 'Source|Database' FORMAT A8
        COLUMN SOURCE_TRANSACTION_ID HEADING 'Source|Transaction|ID' FORMAT A11
        COLUMN MESSAGE_NUMBER HEADING 'Failed Message|in Error|Transaction' FORMAT 99999999
        COLUMN ERROR_NUMBER HEADING 'Error Number' FORMAT 99999999
        COLUMN ERROR_MESSAGE HEADING 'Error Message' FORMAT A10
        COLUMN MESSAGE_COUNT HEADING 'Messages in|Error|Transaction' FORMAT 99999999

        SELECT APPLY_NAME,
               SOURCE_DATABASE,
               SOURCE_TRANSACTION_ID,
               MESSAGE_NUMBER,
               ERROR_NUMBER,
               ERROR_MESSAGE,
               MESSAGE_COUNT
          FROM ALL_APPLY_ERROR;

**Note:**

Trusted users should replace `ALL_APPLY_ERROR` with `DBA_APPLY_ERROR` in the query.

If there are any apply errors, then your output looks similar to the following:

    Inbound          Source      Failed Message                         Messages in
    Server  Source   Transaction       in Error                               Error
    Name    Database ID             Transaction Error Number Error Mess Transaction
    ------- -------- ----------- -------------- ------------ ---------- -----------
    XIN     OUTX.EXA 19.20.215                1         1031 ORA-01031:           1
            MPLE.COM                                          insuffici
                                                             ent privil
                                                             eges
    XIN     OUTX.EXA 11.21.158                1         1031 ORA-01031:           1
            MPLE.COM                                          insuffici
                                                             ent privil
                                                             eges

If there are apply errors, then you can either try to reexecute the transactions that encountered the errors, or you can delete the transactions. To reexecute a transaction that encountered an error, first correct the condition that caused the transaction to raise an error.

If you want to delete a transaction that encountered an error, and if you are sharing data between multiple databases, then you might need to resynchronize data manually. Remember to set an appropriate session tag, if necessary, when you resynchronize data manually.

**See Also:**

- "[The Error Queue for an Inbound Server](xstream-in-concepts.md)"

- "[Managing Apply Errors](managing-xstream-in.md)"

**Parent topic:** Monitoring XStream In

### 11.10 Displaying Detailed Information About Apply Errors

SQL scripts display detailed information about the error transactions in the error queue in a database.

- Step 1: Grant Explicit SELECT Privilege on the ALL_APPLY_ERROR View
  Running the `GRANT_ADMIN_PRIVILEGE` procedure in the `DBMS_XSTREAM_AUTH` package on a user grants the `SELECT` privilege on the `ALL_APPLY_ERROR` view to the user.
- Step 2: Create a Procedure that Prints the Value in an ANYDATA Object
  Create a procedure that prints the value in a specified `ANYDATA` object for some selected data types. Optionally, you can add more data types to this procedure.
- Step 3: Create a Procedure that Prints a Specified LCR
  Create a procedure that prints a specified LCR.
- Step 4: Create a Procedure that Prints All the LCRs in the Error Queue
  Create a procedure that prints all of the LCRs in all of the error queues.
- Step 5: Create a Procedure that Prints All the Error LCRs for a Transaction
  Create a procedure that prints all the LCRs in the error queue for a particular transaction.

**See Also:**

- "[The Error Queue for an Inbound Server](xstream-in-concepts.md)"

- "[Managing Apply Errors](managing-xstream-in.md)"

**Parent topic:** Monitoring XStream In

#### 11.10.1 Step 1: Grant Explicit SELECT Privilege on the ALL_APPLY_ERROR View

Running the `GRANT_ADMIN_PRIVILEGE` procedure in the `DBMS_XSTREAM_AUTH` package on a user grants the `SELECT` privilege on the `ALL_APPLY_ERROR` view to the user.

The user who creates and runs the `print_errors` and `print_transaction` procedures described in the following sections must be granted explicit `SELECT` privilege on the `ALL_APPLY_ERROR` data dictionary view. This privilege cannot be granted through a role.

##### To grant explicit SELECT privilege on the `ALL_APPLY_ERROR` view:

1.  In SQL\*Plus, connect as an administrative user who can grant privileges.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Grant `SELECT` privilege on the `ALL_APPLY_ERROR` data dictionary view to the appropriate user. For example, to grant this privilege to the `xstrmadmin` user, run the following statement:

        GRANT SELECT ON ALL_APPLY_ERROR TO xstrmadmin;

3.  Grant `EXECUTE` privilege on the `DBMS_APPLY_ADM` package. For example, to grant this privilege to the `xstrmadmin` user, run the following statement:

        GRANT EXECUTE ON DBMS_APPLY_ADM TO xstrmadmin;

4.  Connect to the database as the user to whom you granted the privilege in Step 2 and 3.

**Parent topic:** Displaying Detailed Information About Apply Errors

#### 11.10.2 Step 2: Create a Procedure that Prints the Value in an ANYDATA Object

Create a procedure that prints the value in a specified `ANYDATA` object for some selected data types. Optionally, you can add more data types to this procedure.

    CREATE OR REPLACE PROCEDURE print_any(data IN ANYDATA) IS
      tn  VARCHAR2(61);
      str VARCHAR2(4000);
      chr VARCHAR2(1000);
      num NUMBER;
      dat DATE;
      rw  RAW(4000);
      res NUMBER;
    BEGIN
      IF data IS NULL THEN
        DBMS_OUTPUT.PUT_LINE('NULL value');
        RETURN;
      END IF;
      tn := data.GETTYPENAME();
      IF tn = 'SYS.VARCHAR2' THEN
        res := data.GETVARCHAR2(str);
        DBMS_OUTPUT.PUT_LINE(SUBSTR(str,0,253));
      ELSIF tn = 'SYS.CHAR' then
        res := data.GETCHAR(chr);
        DBMS_OUTPUT.PUT_LINE(SUBSTR(chr,0,253));
      ELSIF tn = 'SYS.VARCHAR' THEN
        res := data.GETVARCHAR(chr);
        DBMS_OUTPUT.PUT_LINE(chr);
      ELSIF tn = 'SYS.NUMBER' THEN
        res := data.GETNUMBER(num);
        DBMS_OUTPUT.PUT_LINE(num);
      ELSIF tn = 'SYS.DATE' THEN
        res := data.GETDATE(dat);
        DBMS_OUTPUT.PUT_LINE(dat);
      ELSIF tn= 'SYS.TIMESTAMP' THEN
        res := data.GETTIMESTAMP(dat);
        DBMS_OUTPUT.PUT_LINE(TO_CHAR(dat,'DD-MON-RR HH.MI.SSXFF AM'));
      ELSIF tn= 'SYS.TIMESTAMPTZ' THEN
        res := data.GETTIMESTAMPTZ(dat);
        DBMS_OUTPUT.PUT_LINE(TO_CHAR(dat,'DD-MON-RR HH.MI.SSXFF AM'));
      ELSIF tn= 'SYS.TIMESTAMPLTZ' THEN
        res := data.GETTIMESTAMPLTZ(dat);
        DBMS_OUTPUT.PUT_LINE(TO_CHAR(dat,'DD-MON-RR HH.MI.SSXFF AM'));
      ELSIF tn = 'SYS.RAW' THEN
        -- res := data.GETRAW(rw);
        -- DBMS_OUTPUT.PUT_LINE(SUBSTR(DBMS_LOB.SUBSTR(rw),0,253));
        DBMS_OUTPUT.PUT_LINE('BLOB Value');
      ELSIF tn = 'SYS.BLOB' THEN
        DBMS_OUTPUT.PUT_LINE('BLOB Found');
      ELSE
        DBMS_OUTPUT.PUT_LINE('typename is ' || tn);
      END IF;
    END print_any;
    /

**Parent topic:** Displaying Detailed Information About Apply Errors

#### 11.10.3 Step 3: Create a Procedure that Prints a Specified LCR

Create a procedure that prints a specified LCR.

The procedure calls the `print_any` procedure created in "Step 2: Create a Procedure that Prints the Value in an ANYDATA Object".

    CREATE OR REPLACE PROCEDURE print_lcr(lcr IN ANYDATA) IS
      typenm    VARCHAR2(61);
      ddllcr    SYS.LCR$_DDL_RECORD;
      proclcr   SYS.LCR$_PROCEDURE_RECORD;
      rowlcr    SYS.LCR$_ROW_RECORD;
      res       NUMBER;
      newlist   SYS.LCR$_ROW_LIST;
      oldlist   SYS.LCR$_ROW_LIST;
      ddl_text  CLOB;
      ext_attr  ANYDATA;
    BEGIN
      typenm := lcr.GETTYPENAME();
      DBMS_OUTPUT.PUT_LINE('type name: ' || typenm);
      IF (typenm = 'SYS.LCR$_DDL_RECORD') THEN
        res := lcr.GETOBJECT(ddllcr);
        DBMS_OUTPUT.PUT_LINE('source database: ' ||
                             ddllcr.GET_SOURCE_DATABASE_NAME);
        DBMS_OUTPUT.PUT_LINE('owner: ' || ddllcr.GET_OBJECT_OWNER);
        DBMS_OUTPUT.PUT_LINE('object: ' || ddllcr.GET_OBJECT_NAME);
        DBMS_OUTPUT.PUT_LINE('is tag null: ' || ddllcr.IS_NULL_TAG);
        DBMS_LOB.CREATETEMPORARY(ddl_text, TRUE);
        ddllcr.GET_DDL_TEXT(ddl_text);
        DBMS_OUTPUT.PUT_LINE('ddl: ' || ddl_text);
        -- Print extra attributes in DDL LCR
        ext_attr := ddllcr.GET_EXTRA_ATTRIBUTE('serial#');
          IF (ext_attr IS NOT NULL) THEN
            DBMS_OUTPUT.PUT_LINE('serial#: ' || ext_attr.ACCESSNUMBER());
          END IF;
        ext_attr := ddllcr.GET_EXTRA_ATTRIBUTE('session#');
          IF (ext_attr IS NOT NULL) THEN
            DBMS_OUTPUT.PUT_LINE('session#: ' || ext_attr.ACCESSNUMBER());
          END IF;
        ext_attr := ddllcr.GET_EXTRA_ATTRIBUTE('thread#');
          IF (ext_attr IS NOT NULL) THEN
            DBMS_OUTPUT.PUT_LINE('thread#: ' || ext_attr.ACCESSNUMBER());
          END IF;
        ext_attr := ddllcr.GET_EXTRA_ATTRIBUTE('tx_name');
          IF (ext_attr IS NOT NULL) THEN
            DBMS_OUTPUT.PUT_LINE('transaction name: ' || ext_attr.ACCESSVARCHAR2());
          END IF;
        ext_attr := ddllcr.GET_EXTRA_ATTRIBUTE('username');
          IF (ext_attr IS NOT NULL) THEN
            DBMS_OUTPUT.PUT_LINE('username: ' || ext_attr.ACCESSVARCHAR2());
          END IF;
        DBMS_LOB.FREETEMPORARY(ddl_text);
      ELSIF (typenm = 'SYS.LCR$_ROW_RECORD') THEN
        res := lcr.GETOBJECT(rowlcr);
        DBMS_OUTPUT.PUT_LINE('source database: ' ||
                             rowlcr.GET_SOURCE_DATABASE_NAME);
        DBMS_OUTPUT.PUT_LINE('owner: ' || rowlcr.GET_OBJECT_OWNER);
        DBMS_OUTPUT.PUT_LINE('object: ' || rowlcr.GET_OBJECT_NAME);
        DBMS_OUTPUT.PUT_LINE('is tag null: ' || rowlcr.IS_NULL_TAG);
        DBMS_OUTPUT.PUT_LINE('command_type: ' || rowlcr.GET_COMMAND_TYPE);
        oldlist := rowlcr.GET_VALUES('old');
        FOR i IN 1..oldlist.COUNT LOOP
          IF oldlist(i) IS NOT NULL THEN
            DBMS_OUTPUT.PUT_LINE('old(' || i || '): ' || oldlist(i).column_name);
            print_any(oldlist(i).data);
          END IF;
        END LOOP;
        newlist := rowlcr.GET_VALUES('new', 'n');
        FOR i in 1..newlist.count LOOP
          IF newlist(i) IS NOT NULL THEN
            DBMS_OUTPUT.PUT_LINE('new(' || i || '): ' || newlist(i).column_name);
            print_any(newlist(i).data);
          END IF;
        END LOOP;
        -- Print extra attributes in row LCR
        ext_attr := rowlcr.GET_EXTRA_ATTRIBUTE('row_id');
          IF (ext_attr IS NOT NULL) THEN
            DBMS_OUTPUT.PUT_LINE('row_id: ' || ext_attr.ACCESSUROWID());
          END IF;
        ext_attr := rowlcr.GET_EXTRA_ATTRIBUTE('serial#');
          IF (ext_attr IS NOT NULL) THEN
            DBMS_OUTPUT.PUT_LINE('serial#: ' || ext_attr.ACCESSNUMBER());
          END IF;
        ext_attr := rowlcr.GET_EXTRA_ATTRIBUTE('session#');
          IF (ext_attr IS NOT NULL) THEN
            DBMS_OUTPUT.PUT_LINE('session#: ' || ext_attr.ACCESSNUMBER());
          END IF;
        ext_attr := rowlcr.GET_EXTRA_ATTRIBUTE('thread#');
          IF (ext_attr IS NOT NULL) THEN
            DBMS_OUTPUT.PUT_LINE('thread#: ' || ext_attr.ACCESSNUMBER());
          END IF;
        ext_attr := rowlcr.GET_EXTRA_ATTRIBUTE('tx_name');
          IF (ext_attr IS NOT NULL) THEN
            DBMS_OUTPUT.PUT_LINE('transaction name: ' || ext_attr.ACCESSVARCHAR2());
          END IF;
        ext_attr := rowlcr.GET_EXTRA_ATTRIBUTE('username');
          IF (ext_attr IS NOT NULL) THEN
            DBMS_OUTPUT.PUT_LINE('username: ' || ext_attr.ACCESSVARCHAR2());
          END IF;
      ELSE
        DBMS_OUTPUT.PUT_LINE('Non-LCR Message with type ' || typenm);
      END IF;
    END print_lcr;
    /

**Parent topic:** Displaying Detailed Information About Apply Errors

#### 11.10.4 Step 4: Create a Procedure that Prints All the LCRs in the Error Queue

Create a procedure that prints all of the LCRs in all of the error queues.

The procedure calls the `print_lcr` procedure created in "Step 3: Create a Procedure that Prints a Specified LCR".

    CREATE OR REPLACE PROCEDURE print_errors IS
      CURSOR c IS
        SELECT LOCAL_TRANSACTION_ID,
               SOURCE_DATABASE,
               MESSAGE_NUMBER,
               MESSAGE_COUNT,
               ERROR_NUMBER,
               ERROR_MESSAGE
          FROM ALL_APPLY_ERROR
          ORDER BY SOURCE_DATABASE, SOURCE_COMMIT_SCN;
      i      NUMBER;
      txnid  VARCHAR2(30);
      source VARCHAR2(128);
      msgno  NUMBER;
      msgcnt NUMBER;
      errnum NUMBER := 0;
      errno  NUMBER;
      errmsg VARCHAR2(2000);
      lcr    ANYDATA;
      r      NUMBER;
    BEGIN
      FOR r IN c LOOP
        errnum := errnum + 1;
        msgcnt := r.MESSAGE_COUNT;
        txnid  := r.LOCAL_TRANSACTION_ID;
        source := r.SOURCE_DATABASE;
        msgno  := r.MESSAGE_NUMBER;
        errno  := r.ERROR_NUMBER;
        errmsg := r.ERROR_MESSAGE;
    DBMS_OUTPUT.PUT_LINE('*************************************************');
        DBMS_OUTPUT.PUT_LINE('----- ERROR #' || errnum);
        DBMS_OUTPUT.PUT_LINE('----- Local Transaction ID: ' || txnid);
        DBMS_OUTPUT.PUT_LINE('----- Source Database: ' || source);
        DBMS_OUTPUT.PUT_LINE('----Error in Message: '|| msgno);
        DBMS_OUTPUT.PUT_LINE('----Error Number: '||errno);
        DBMS_OUTPUT.PUT_LINE('----Message Text: '||errmsg);
        FOR i IN 1..msgcnt LOOP
          DBMS_OUTPUT.PUT_LINE('--message: ' || i);
            lcr := DBMS_APPLY_ADM.GET_ERROR_MESSAGE(i, txnid);
            print_lcr(lcr);
        END LOOP;
      END LOOP;
    END print_errors;
    /

To run this procedure after you create it, enter the following:

    SET SERVEROUTPUT ON SIZE 1000000

    EXEC print_errors

**Parent topic:** Displaying Detailed Information About Apply Errors

#### 11.10.5 Step 5: Create a Procedure that Prints All the Error LCRs for a Transaction

Create a procedure that prints all the LCRs in the error queue for a particular transaction.

The procedure calls the `print_lcr` procedure created in "Step 3: Create a Procedure that Prints a Specified LCR".

    CREATE OR REPLACE PROCEDURE print_transaction(ltxnid IN VARCHAR2) IS
      i      NUMBER;
      txnid  VARCHAR2(30);
      source VARCHAR2(128);
      msgno  NUMBER;
      msgcnt NUMBER;
      errno  NUMBER;
      errmsg VARCHAR2(2000);
      lcr    ANYDATA;
    BEGIN
      SELECT LOCAL_TRANSACTION_ID,
             SOURCE_DATABASE,
             MESSAGE_NUMBER,
             MESSAGE_COUNT,
             ERROR_NUMBER,
             ERROR_MESSAGE
          INTO txnid, source, msgno, msgcnt, errno, errmsg
          FROM ALL_APPLY_ERROR
          WHERE LOCAL_TRANSACTION_ID =  ltxnid;
      DBMS_OUTPUT.PUT_LINE('----- Local Transaction ID: ' || txnid);
      DBMS_OUTPUT.PUT_LINE('----- Source Database: ' || source);
      DBMS_OUTPUT.PUT_LINE('----Error in Message: '|| msgno);
      DBMS_OUTPUT.PUT_LINE('----Error Number: '||errno);
      DBMS_OUTPUT.PUT_LINE('----Message Text: '||errmsg);
      FOR i IN 1..msgcnt LOOP
      DBMS_OUTPUT.PUT_LINE('--message: ' || i);
        lcr := DBMS_APPLY_ADM.GET_ERROR_MESSAGE(i, txnid); -- gets the LCR
        print_lcr(lcr);
      END LOOP;
    END print_transaction;
    /

To run this procedure after you create it, pass to it the local transaction identifier of an error transaction. For example, if the local transaction identifier is `1.17.2485`, then enter the following:

    SET SERVEROUTPUT ON SIZE 1000000

    EXEC print_transaction('1.17.2485')

**Parent topic:** Displaying Detailed Information About Apply Errors
