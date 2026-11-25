You can manage XStream Out components and their rules.

- About Managing XStream Out
  You can modify the database components that are part of an XStream Out configuration, such as outbound servers, capture processes, and rules.
- Managing an Outbound Server
  You can manage an outbound server by starting it, stopping it, setting an apply parameter for it, and changing its connect user.
- Managing the Capture Process for an Outbound Server
  You can manage the capture process for an outbound server. The capture process captures database changes and sends them to an outbound server.
- Managing Rules for an XStream Out Configuration
  You can manage the rules for an XStream Out configuration. Rules control which database changes are streamed to the outbound server and which database changes the outbound server streams to the client application.
- Managing Declarative Rule-Based Transformations
  Declarative rule-based transformations cover a set of common transformation scenarios for row LCRs.
- Dropping Components in an XStream Out Configuration
  To drop an outbound server, use the `DROP_OUTBOUND` procedure in the `DBMS_XSTREAM_ADM` package.
- Removing an XStream Out Configuration
  You run the `REMOVE_XSTREAM_CONFIGURATION` procedure in the `DBMS_XSTREAM_ADM` package to remove an XStream Out configuration in a multitenant container database (CDB) or non-CDB.

**Parent topic:** [XStream Out](xstream-out.md)

### 5.1 About Managing XStream Out

You can modify the database components that are part of an XStream Out configuration, such as outbound servers, capture processes, and rules.

The main interface for managing XStream Out database components is PL/SQL. Specifically, use the following Oracle supplied PL/SQL packages to manage XStream Out:

- `DBMS_XSTREAM_ADM`

  The `DBMS_XSTREAM_ADM` package is the main package for managing XStream Out. This package includes subprograms that enable you to configure, modify, or drop outbound servers. This package also enables you modify the rules used by capture processes and outbound servers.

  **Also:**

  [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_XSTREAM_ADM.md) for detailed information about this package

- `DBMS_XSTREAM_AUTH`

  The `DBMS_XSTREAM_AUTH` package enables you to configure and modify XStream administrators.

  **See Also:**

  - "[Configure an XStream Administrator on All Databases](configuring-xstream-out.md)" for information about using this package to create an XStream administrator

  - [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_XSTREAM_AUTH.md) for detailed information about this package

- `DBMS_APPLY_ADM`

  The `DBMS_APPLY_ADM` package enables you modify outbound servers.

  **See Also:**

  [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_APPLY_ADM.md) for detailed information about this package

- `DBMS_CAPTURE_ADM`

  The `DBMS_CAPTURE_ADM` package enables you configure and modify capture processes.

  **See Also:**

  [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_CAPTURE_ADM.md) for detailed information about this package

**Parent topic:** Managing XStream Out

### 5.2 Managing an Outbound Server

You can manage an outbound server by starting it, stopping it, setting an apply parameter for it, and changing its connect user.

- Starting an Outbound Server
  A outbound server must be enabled for it to send logical change records (LCRs) to an XStream client application. You run the `START_OUTBOUND` procedure in the `DBMS_OUTBOUND_ADM` package to start an existing outbound server.
- Stopping an Outbound Server
  You run the `STOP_SERVER` procedure in the `DBMS_XSTREAM_ADM` package to stop an existing outbound server. You might stop an outbound server when you are troubleshooting a problem in an XStream configuration.
- Setting an Apply Parameter for an Outbound Server
  You set an apply parameter for an outbound server using the `SET_PARAMETER` procedure in the `DBMS_XSTREAM_ADM` package. Apply parameters control the way an outbound server operates.
- Changing the Connect User for an Outbound Server
  A client application connects to an outbound server as the connect user. You can change the connect user for an outbound server using the `ALTER_OUTBOUND` procedure in the `DBMS_XSTREAM_ADM` package.

**Parent topic:** Managing XStream Out

#### 5.2.1 Starting an Outbound Server

A outbound server must be enabled for it to send logical change records (LCRs) to an XStream client application. You run the `START_OUTBOUND` procedure in the `DBMS_OUTBOUND_ADM` package to start an existing outbound server.

##### To start an outbound server:

1.  Connect to the outbound server database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the `START_OUTBOUND` procedure in the `DBMS_XSTREAM_ADM` package, and specify the outbound server for the `server_name` parameter.

The following example starts an outbound server named `xout`.

Example 5-1 Starting an Outbound Server Named xout

    BEGIN
      DBMS_XSTREAM_ADM.START_OUTBOUND(
        server_name => 'xout');
    END;
    /

**Note:**

When an XStream client application attaches to an outbound server, it starts the outbound server and the outbound server's capture process automatically if either of these components are disabled.

**See Also:**

The Oracle Enterprise Manager Cloud Control online help for instructions about starting an apply process or an outbound server with Oracle Enterprise Manager Cloud Control

**Parent topic:** Managing an Outbound Server

#### 5.2.2 Stopping an Outbound Server

You run the `STOP_SERVER` procedure in the `DBMS_XSTREAM_ADM` package to stop an existing outbound server. You might stop an outbound server when you are troubleshooting a problem in an XStream configuration.

##### To stop an outbound server:

1.  Connect to the outbound server database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the `STOP_SERVER` procedure in the `DBMS_XSTREAM_ADM` package, and specify the outbound server for the `server_name` parameter.

The following example stops an outbound server named `xout`.

Example 5-2 Stopping an Outbound Server Named xout

    BEGIN
      DBMS_XSTREAM_ADM.STOP_OUTBOUND(
        server_name => 'xout');
    END;
    /

**See Also:**

The Oracle Enterprise Manager Cloud Control online help for instructions about stopping an apply process or an outbound server with Oracle Enterprise Manager Cloud Control

**Parent topic:** Managing an Outbound Server

#### 5.2.3 Setting an Apply Parameter for an Outbound Server

You set an apply parameter for an outbound server using the `SET_PARAMETER` procedure in the `DBMS_XSTREAM_ADM` package. Apply parameters control the way an outbound server operates.

##### To set an outbound server parameter:

1.  Connect to the outbound server database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the `SET_PARAMETER` procedure in the `DBMS_XSTREAM_ADM` package.

Example 5-3 Setting an Outbound Server Parameter

The following example sets the `disable_on_error` parameter for an outbound server named `xout` to `N`.

    BEGIN
      DBMS_XSTREAM_ADM.SET_PARAMETER(
        streams_name => 'xout',
        streams_type => 'apply',
        parameter    => 'disable_on_error',
        value        => 'N');
    END;
    /

Example 5-4 Setting an Outbound Server Parameter to Its Default Value

If the `value` parameter is set to `NULL` or is not specified, then the parameter is set to its default value. The following example sets the `MAX_SGA_SIZE` apply parameter to `NULL`:

    BEGIN
      DBMS_XSTREAM_ADM.SET_PARAMETER(
        streams_name => 'xout',
        streams_type => 'apply',
        parameter    => 'max_sga_size',
        value        => NULL);
    END;
    /

**Note:**

- The value parameter is always entered as a `VARCHAR2` value, even if the parameter value is a number.

- If the `value` parameter is set to `NULL` or is not specified, then the parameter is set to its default value.

**See Also:**

- The Oracle Enterprise Manager Cloud Control online help for instructions about setting an apply parameter with Oracle Enterprise Manager Cloud Control

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_APPLY_ADM.md) for information about apply parameters

**Parent topic:** Managing an Outbound Server

#### 5.2.4 Changing the Connect User for an Outbound Server

A client application connects to an outbound server as the connect user. You can change the connect user for an outbound server using the `ALTER_OUTBOUND` procedure in the `DBMS_XSTREAM_ADM` package.

The connect user is the user who can attach to the outbound server to retrieve the LCR stream. The client application must attach to the outbound server as the connect user.

You can change the `connect_user` when a client application must connect to an outbound server as a different user. Ensure that the connect user is granted the required privileges.

**Note:**

The default `connect_user` is the user that configured the outbound server. If you want to run the client application as a different user, follow the steps outlined below.

##### To change the connect_user for an outbound server:

1.  Connect to the outbound server database as the XStream administrator.

    The XStream administrator must be granted the `DBA` role to change the connect user for an outbound server.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the `ALTER_OUTBOUND` procedure, and specify the following parameters:

    - `server_name` - Specify the name of the outbound server.

    - `connect_user` - Specify the new connect user.

Example 5-5 Changing the Connect User for an Outbound Server

To change the connect user to `hr` for an outbound server named `xout`, run the following procedure:

    BEGIN
      DBMS_XSTREAM_ADM.ALTER_OUTBOUND(
        server_name  => 'xout',
        connect_user => 'hr');
    END;
    /

**See Also:**

- "[Privileges Required by the Connect User for an Outbound Server](xstream-out-concepts.md)"

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_XSTREAM_ADM.md)

**Parent topic:** Managing an Outbound Server

### 5.3 Managing the Capture Process for an Outbound Server

You can manage the capture process for an outbound server. The capture process captures database changes and sends them to an outbound server.

- Checking Whether the DBMS_XSTREAM_ADM Package Can Manage a Capture Process
  In some XStream Out configurations, you can use the `DBMS_XSTREAM_ADM` package to manage the capture process that captures changes for an outbound server.
- Starting a Capture Process
  A capture process must be enabled for it to capture database changes and send the changes to an XStream outbound server. You run the `START_CAPTURE` procedure in the `DBMS_CAPTURE_ADM` package to start an existing capture process.
- Stopping a Capture Process
  You run the `STOP_CAPTURE` procedure in the `DBMS_CAPTURE_ADM` package to stop an existing capture process. You might stop a capture process when you are troubleshooting a problem in an XStream configuration.
- Setting a Capture Process Parameter
  Capture process parameters control the way a capture process operates. You set a capture process parameter using the `SET_PARAMETER` procedure in the `DBMS_CAPTURE_ADM` package.
- Changing the Capture User of an Outbound Server's Capture Process
  A capture user is the user in whose security domain a capture process captures changes from the redo log.
- Changing the Start SCN or Start Time of an Outbound Server's Capture Process
  You can change the start system change number (SCN) or start time for a capture process that captures changes for an outbound server using the `ALTER_OUTBOUND` procedure in the `DBMS_XSTREAM_ADM` package.
- Setting the First SCN for a Capture Process
  You can set the first system change number (SCN) for an existing capture process. The first SCN is the SCN in the redo log from which a capture process can capture changes.

**Parent topic:** Managing XStream Out

#### 5.3.1 Checking Whether the DBMS_XSTREAM_ADM Package Can Manage a Capture Process

In some XStream Out configurations, you can use the `DBMS_XSTREAM_ADM` package to manage the capture process that captures changes for an outbound server.

Even when you cannot use the `DBMS_XSTREAM_ADM` package, you can always use the `DBMS_CAPTURE_ADM` package to manage the capture process.

The `DBMS_XSTREAM_ADM` package can manage an outbound server's capture process if either of the following conditions are met:

- The capture process was created by the `CREATE_OUTBOUND` procedure in the `DBMS_XSTREAM_ADM` package.

- The queue used by the capture process was created by the `CREATE_OUTBOUND` procedure.

If either of these conditions are met, then the `DBMS_XSTREAM_ADM` package can manage an outbound server's capture process in the following ways:

- Add rules to and remove rules from the capture process's rule sets

- Change the capture user for the capture process

- Set the start system change number (SCN) or start time

- Drop the capture process

The `DBMS_CAPTURE_ADM` package can manage a capture process in the following ways:

- Start and stop the capture process

- Alter the capture process, which includes changing the capture process's rule sets, capture user, first SCN, start SCN, and start time

- Set capture process parameters

- Drop the capture process

##### To check whether an outbound server's capture process can be managed by the `DBMS_XSTREAM_ADM` package:

1.  Connect to the outbound server database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the following query:

        COLUMN SERVER_NAME HEADING 'Outbound Server Name' FORMAT A30
        COLUMN CAPTURE_NAME HEADING 'Capture Process Name' FORMAT A30

        SELECT SERVER_NAME,
               CAPTURE_NAME
          FROM ALL_XSTREAM_OUTBOUND;

    Your output looks similar to the following:

        Outbound Server Name           Capture Process Name
        ------------------------------ ------------------------------
        XOUT                           CAP$_XOUT_4

    If the `Capture` `Process` `Name` for an outbound server is non-`NULL`, then the `DBMS_XSTREAM_ADM` package can manage the capture process. In this case, you can also manage the capture process using the `DBMS_CAPTURE_ADM` package. However, it is usually better to manage the capture process for an outbound server using the `DBMS_XSTREAM_ADM` package when it is possible.

    If the `Capture` `Process` `Name` for an outbound server is `NULL`, then the `DBMS_XSTREAM_ADM` package cannot manage the capture process. In this case, you must manage the capture process using the `DBMS_CAPTURE_ADM` package.

**See Also:**

- "Managing Rules for an XStream Out Configuration"

- "Changing the Capture User of an Outbound Server's Capture Process"

- [Oracle Database Reference](../refrn/ALL_XSTREAM_OUTBOUND.md)

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_CAPTURE_ADM.md)

**Parent topic:** Managing the Capture Process for an Outbound Server

#### 5.3.2 Starting a Capture Process

A capture process must be enabled for it to capture database changes and send the changes to an XStream outbound server. You run the `START_CAPTURE` procedure in the `DBMS_CAPTURE_ADM` package to start an existing capture process.

##### To start a capture process:

1.  Connect to the capture process database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the `START_CAPTURE` procedure in the `DBMS_CAPTURE_ADM` package, and specify the capture process for the `capture_name` parameter.

The following example starts a capture process named `xstream_capture`.

Example 5-6 Starting a Capture Process Named xstream_capture

    BEGIN
      DBMS_CAPTURE_ADM.START_CAPTURE(
        capture_name => 'xstream_capture');
    END;
    /

**Note:**

When an XStream client application attaches to an outbound server, it starts the outbound server's capture process automatically if the capture process is disabled.

**See Also:**

The Oracle Enterprise Manager Cloud Control online help for instructions about starting a capture process with Oracle Enterprise Manager Cloud Control

**Parent topic:** Managing the Capture Process for an Outbound Server

#### 5.3.3 Stopping a Capture Process

You run the `STOP_CAPTURE` procedure in the `DBMS_CAPTURE_ADM` package to stop an existing capture process. You might stop a capture process when you are troubleshooting a problem in an XStream configuration.

##### To stop a capture process:

1.  Connect to the capture process database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the `STOP_CAPTURE` procedure in the `DBMS_CAPTURE_ADM` package, and specify the capture process for the `capture_name` parameter.

The following example starts a capture process named `xstream_capture`.

Example 5-7 Stopping a Capture Process Named xstream_capture

    BEGIN
      DBMS_CAPTURE_ADM.STOP_CAPTURE(
        capture_name => 'xstream_capture');
    END;
    /

**See Also:**

The Oracle Enterprise Manager Cloud Control online help for instructions about stopping a capture process with Oracle Enterprise Manager Cloud Control

**Parent topic:** Managing the Capture Process for an Outbound Server

#### 5.3.4 Setting a Capture Process Parameter

Capture process parameters control the way a capture process operates. You set a capture process parameter using the `SET_PARAMETER` procedure in the `DBMS_CAPTURE_ADM` package.

##### To set a capture process parameter:

1.  Connect to the capture process database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the `SET_PARAMETER` procedure in the `DBMS_CAPTURE_ADM` package.

The following example sets the `parallelism` parameter for a capture process named `xstream_capture` to `1` from the default value of `0`. The parallelism parameter controls the number of processes that concurrently mine the redo log for changes. It is a good idea to monitor the effect of increasing the parallelism for the capture process since additional processes are started.

Example 5-8 Setting a Capture Process Parameter

    BEGIN
      DBMS_CAPTURE_ADM.SET_PARAMETER(
        capture_name => 'xstream_capture',
        parameter    => 'parallelism',
        value        => '1');
    END;
    /

**Note:**

- Setting the parallelism parameter automatically stops and restarts a capture process.

- The value parameter is always entered as a `VARCHAR2` value, even if the parameter value is a number.

- If the value parameter is set to `NULL` or is not specified, then the parameter is set to its default value.

**See Also:**

- The Oracle Enterprise Manager Cloud Control online help for instructions about setting a capture process parameter with Oracle Enterprise Manager Cloud Control

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_CAPTURE_ADM.md) for information about capture process parameters

**Parent topic:** Managing the Capture Process for an Outbound Server

#### 5.3.5 Changing the Capture User of an Outbound Server's Capture Process

A capture user is the user in whose security domain a capture process captures changes from the redo log.

You can change the capture user for a capture process that captures changes for an outbound server using the `ALTER_OUTBOUND` procedure in the `DBMS_XSTREAM_ADM` package.

You can change the capture user when the capture process must capture changes in a different security domain. Only a user granted `DBA` role can change the capture user for a capture process. Ensure that the capture user is granted the required privileges. When you change the capture user, the `ALTER_OUTBOUND` procedure grants the new capture user enqueue privilege on the queue used by the capture process and configures the user as a secure queue user.

**Note:**

If Oracle Database Vault is installed, then the user who changes the capture user must be granted the `BECOME` `USER` system privilege. Granting this privilege to the user is not required if Oracle Database Vault is not installed. You can revoke the `BECOME` `USER` system privilege from the user after capture user is changed, if necessary.

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_XSTREAM_ADM.md) for information about the privileges required by a capture user

##### To change the capture user of the capture process for an outbound server:

1.  Determine whether the `DBMS_XSTREAM_ADM` package can manage the capture process. See "Checking Whether the DBMS_XSTREAM_ADM Package Can Manage a Capture Process".

    If the capture process can be managed using the `DBMS_XSTREAM_ADM` package, then proceed to Step 2.

2.  Connect to the outbound server database as the XStream administrator.

    To change the capture user, the user who invokes the `ALTER_OUTBOUND` procedure must be granted `DBA` role. Only the `SYS` user can set the capture user to `SYS`.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

3.  Run the `ALTER_OUTBOUND` procedure, and specify the following parameters:

    - `server_name` - Specify the name of the outbound server.

    - `capture_user` - Specify the new capture user.

Example 5-9 Changing the Capture User of the Capture Process for an Outbound Server

To change the capture user to `hq_admin` for an outbound server named `xout`, run the following procedure:

    BEGIN
      DBMS_XSTREAM_ADM.ALTER_OUTBOUND(
        server_name  => 'xout',
        capture_user => 'hq_admin');
    END;
    /

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_XSTREAM_ADM.md)

**Parent topic:** Managing the Capture Process for an Outbound Server

#### 5.3.6 Changing the Start SCN or Start Time of an Outbound Server's Capture Process

You can change the start system change number (SCN) or start time for a capture process that captures changes for an outbound server using the `ALTER_OUTBOUND` procedure in the `DBMS_XSTREAM_ADM` package.

The start SCN is the SCN from which a capture process begins to capture changes. The start time is the time from which a capture process begins to capture changes. When you reset a start SCN or start time for a capture process, ensure that the required redo log files are available to the capture process.

Typically, you reset the start SCN or start time for a capture process if point-in-time recovery was performed on one of the destination databases that receive changes from the capture process.

**Note:**

- The `start_scn` and `start_time` parameters in the `ALTER_OUTBOUND` procedure are mutually exclusive.

- You do not need to set the start SCN for a capture process after a normal restart of the database.

<!-- -->

- Changing the Start SCN of an Outbound Server's Capture Process
  You can change the start SCN of the capture process for an outbound server.
- Changing the Start Time of an Outbound Server's Capture Process
  You can change the start time of the capture process for an outbound server.

**Parent topic:** Managing the Capture Process for an Outbound Server

##### 5.3.6.1 Changing the Start SCN of an Outbound Server's Capture Process

You can change the start SCN of the capture process for an outbound server.

##### To change the start SCN for a capture process:

1.  Determine whether the `DBMS_XSTREAM_ADM` package can manage the capture process. See "Checking Whether the DBMS_XSTREAM_ADM Package Can Manage a Capture Process".

    If the capture process can be managed using the `DBMS_XSTREAM_ADM` package, then proceed to Step 2.

2.  Connect to the outbound server database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

3.  Check the first SCN of the capture process:

        COLUMN CAPTURE_PROCESS HEADING 'Capture Process Name' FORMAT A30
        COLUMN FIRST_SCN HEADING 'First SCN' FORMAT 99999999999999

        SELECT CAPTURE_NAME, FIRST_SCN FROM ALL_CAPTURE;

        CAPTURE_NAME                         First SCN
        ------------------------------ ---------------
        CAP$_XOUT_1                             604426

    When you reset the start SCN, the specified start SCN must be equal to or greater than the first SCN for the capture process.

4.  Run the `ALTER_OUTBOUND` procedure, and specify the following parameters:

    - `server_name` - Specify the name of the outbound server.

    - `start_scn` - Specify the SCN from which the capture process begins to capture changes.

    If the capture process is enabled, then the `ALTER_OUTBOUND` procedure automatically stops and restarts the capture process when the `start_scn` parameter is non-`NULL`.

    If the capture process is disabled, then the `ALTER_OUTBOUND` procedure automatically starts the capture process when the `start_scn` parameter is non-`NULL`.

Example 5-10 Setting the Start SCN of the Capture Process for an Outbound Server

Run the following procedure to set the start SCN to `650000` for the capture process used by the `xout` outbound server:

    BEGIN
      DBMS_XSTREAM_ADM.ALTER_OUTBOUND(
        server_name => 'xout',
        start_scn    => 650000);
    END;
    /

**See Also:**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_XSTREAM_ADM.md)

- "[SCN Values Related to a Capture Process](xstream-out-concepts.md)"

**Parent topic:** Changing the Start SCN or Start Time of an Outbound Server's Capture Process

##### 5.3.6.2 Changing the Start Time of an Outbound Server's Capture Process

You can change the start time of the capture process for an outbound server.

##### To change the start time for a capture process:

1.  Determine whether the `DBMS_XSTREAM_ADM` package can manage the capture process. See "Checking Whether the DBMS_XSTREAM_ADM Package Can Manage a Capture Process".

    If the capture process can be managed using the `DBMS_XSTREAM_ADM` package, then proceed to Step 2.

2.  Connect to the outbound server database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

3.  Check the time that corresponds with the first SCN of the capture process:

        COLUMN CAPTURE_PROCESS HEADING 'Capture Process Name' FORMAT A30
        COLUMN FIRST_SCN HEADING 'First SCN' FORMAT A40

        SELECT CAPTURE_NAME, SCN_TO_TIMESTAMP(FIRST_SCN) FIRST_SCN FROM ALL_CAPTURE;

        CAPTURE_NAME                   First SCN
        ------------------------------ ----------------------------------------
        CAP$_XOUT_1                    05-MAY-10 08.11.17.000000000 AM

    When you reset the start time, the specified start time must be greater than or equal to the time that corresponds with the first SCN for the capture process.

4.  Run the `ALTER_OUTBOUND` procedure, and specify the following parameters:

    - `server_name` - Specify the name of the outbound server.

    - `start_time` - Specify the time from which the capture process begins to capture changes.

    If the capture process is enabled, then the `ALTER_OUTBOUND` procedure automatically stops and restarts the capture process when the `start_time` parameter is non-`NULL`.

    If the capture process is disabled, then the `ALTER_OUTBOUND` procedure automatically starts the capture process when the `start_time` parameter is non-`NULL`.

    The following examples set the `start_time` parameter for the capture process that captures changes for an outbound server named `xout`.

Example 5-11 Set the Start Time to a Specific Time

Run the following procedure to set the start time to `05-MAY-10 11.11.17 AM` for the capture process used by the `xout` outbound server:

    BEGIN
      DBMS_XSTREAM_ADM.ALTER_OUTBOUND(
        server_name => 'xout',
        start_time  => '05-MAY-10 11.11.17 AM');
    END;
    /

Example 5-12 Set the Start Time Using the NUMTODSINTERVAL SQL Function

Run the following procedure to set the start time to four hours earlier than the current time for the capture process used by the `xout` outbound server:

    DECLARE
      ts  TIMESTAMP;
    BEGIN
      ts := SYSTIMESTAMP - NUMTODSINTERVAL(4, 'HOUR');
      DBMS_XSTREAM_ADM.ALTER_OUTBOUND(
        server_name => 'xout',
        start_time  => ts);
    END;
    /

**See Also:**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_XSTREAM_ADM.md)

- "[SCN Values Related to a Capture Process](xstream-out-concepts.md)"

**Parent topic:** Changing the Start SCN or Start Time of an Outbound Server's Capture Process

#### 5.3.7 Setting the First SCN for a Capture Process

You can set the first system change number (SCN) for an existing capture process. The first SCN is the SCN in the redo log from which a capture process can capture changes.

The specified first SCN must meet the following requirements:

- It must be greater than the current first SCN for the capture process.

- It must be less than or equal to the current applied SCN for the capture process. However, this requirement does not apply if the current applied SCN for the capture process is zero.

- It must be less than or equal to the required checkpoint SCN for the capture process.

You can determine the current first SCN, applied SCN, and required checkpoint SCN for each capture process in a database using the following query:

    SELECT CAPTURE_NAME, FIRST_SCN, APPLIED_SCN, REQUIRED_CHECKPOINT_SCN   FROM ALL_CAPTURE;

When you reset a first SCN for a capture process, information below the new first SCN setting is purged from the LogMiner data dictionary for the capture process automatically. Therefore, after the first SCN is reset for a capture process, the start SCN for the capture process cannot be set lower than the new first SCN. Also, redo log files that contain information before the new first SCN setting will never be needed by the capture process.

You set the first SCN for a capture process using the `ALTER_CAPTURE` procedure in the `DBMS_CAPTURE_ADM` package.

##### To set the first SCN for a capture process:

1.  Connect to the capture process database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the `ALTER_CAPTURE` procedure in the `DBMS_CAPTURE_ADM` package, and specify the new first SCN in the `first_scn` parameter.

The following example sets the first SCN to `351232` for the `xstream_capture` capture process.

Example 5-13 Setting the First SCN for a Capture Process

    BEGIN
      DBMS_CAPTURE_ADM.ALTER_CAPTURE(
        capture_name => 'xstream_capture',
        first_scn    => 351232);
    END;
    /

**Note:**

- If the specified first SCN is higher than the current start SCN for the capture process, then the start SCN is set automatically to the new value of the first SCN.

- If you must capture changes in the redo log from a point in time in the past, then you can create a capture process and specify a first SCN that corresponds to a previous data dictionary build in the redo log. The `BUILD` procedure in the `DBMS_CAPTURE_ADM` package performs a data dictionary build in the redo log.

- You can query the `DBA_LOGMNR_PURGED_LOG` data dictionary view to determine which redo log files will never be needed by any capture process.

**See Also:**

"[SCN Values Related to a Capture Process](xstream-out-concepts.md)"

**Parent topic:** Managing the Capture Process for an Outbound Server

### 5.4 Managing Rules for an XStream Out Configuration

You can manage the rules for an XStream Out configuration. Rules control which database changes are streamed to the outbound server and which database changes the outbound server streams to the client application.

- Adding Rules to an XStream Out Configuration
  You can add schema rules, table rules, and subset rules to an XStream Out configuration.
- Removing Rules from an XStream Out Configuration
  You can remove rules from an XStream Out configuration.

**Parent topic:** Managing XStream Out

#### 5.4.1 Adding Rules to an XStream Out Configuration

You can add schema rules, table rules, and subset rules to an XStream Out configuration.

- Adding Schema Rules and Table Rules to an XStream Out Configuration
  You can add schema rules and table rules to an XStream Out configuration using the `ALTER_OUTBOUND` procedure in the `DBMS_XSTREAM_ADM` package.
- Adding Subset Rules to an Outbound Server's Positive Rule Set
  You can add subset rules to an outbound server's positive rule set using the `ADD_SUBSET_OUTBOUND_RULES` procedure in the `DBMS_XSTREAM_ADM` package.
- Adding Rules With Custom Conditions to XStream Out Components
  Some of the procedures that create rules in the `DBMS_XSTREAM_ADM` package include an `and_condition` parameter. This parameter enables you to add conditions to system-created rules.

**Parent topic:** Managing Rules for an XStream Out Configuration

##### 5.4.1.1 Adding Schema Rules and Table Rules to an XStream Out Configuration

You can add schema rules and table rules to an XStream Out configuration using the `ALTER_OUTBOUND` procedure in the `DBMS_XSTREAM_ADM` package.

The `ALTER_OUTBOUND` procedure adds rules for both data manipulation language (DML) and data definition language (DDL) changes.

When you follow the instructions in this section, the `ALTER_OUTBOUND` procedure always adds rules for the specified schemas and tables to one of the outbound server's rule sets. If the `DBMS_XSTREAM_ADM` package can manage the outbound server's capture process, then the `ALTER_OUTBOUND` procedure also adds rules for the specified schemas and tables to one of the rule sets used by this capture process.

To determine whether the `DBMS_XSTREAM_ADM` package can manage the outbound server's capture process, see "Checking Whether the DBMS_XSTREAM_ADM Package Can Manage a Capture Process". If the `DBMS_XSTREAM_ADM` package cannot manage the outbound server's capture process, then the `ALTER_OUTBOUND` procedure adds rules to the outbound server's rule set only. In this case, if rules for same schemas and tables should be added to the capture process's rule set as well, then use the `ADD_*_RULES` procedures in the `DBMS_XSTREAM_ADM` package to add them.

In addition, if the capture process is running on a different database than the outbound server, then add schema and table rules to the propagation that sends logical change records (LCRs) to the outbound server's database. Use the `ADD_*_PROPAGATION_RULES` procedures in the `DBMS_XSTREAM_ADM` package to add them.

##### To add schema rules and table rules to an XStream Out configuration:

1.  Connect to the outbound server database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the `ALTER_OUTBOUND` procedure, and specify the following parameters:

    - `server_name` - Specify the name of the outbound server.

    - `table_names` - Specify the tables for which to add rules, or specify `NULL` to add no table rules.

    - `schema_name` - Specify the schemas for which to add rules, or specify `NULL` to add no schema rules.

    - `add` - Specify `TRUE` so that the rules are added. (Rules are removed if you specify `FALSE`.)

    - `inclusion_rule` - Specify `TRUE` to add rules to the positive rule set of the outbound server, or specify `FALSE` to add rules to the negative rule set of the outbound server. If the `DBMS_XSTREAM_ADM` package can manage the outbound server's capture process, then rules are also added to this capture process's rule set.

The following examples add rules to the configuration of an outbound server named `xout`.

Example 5-14 Adding Rules for the hr Schema, oe.orders Table, and oe.order_items Table to the Positive Rule Set

    BEGIN
      DBMS_XSTREAM_ADM.ALTER_OUTBOUND(
        server_name    => 'xout',
        table_names    => 'oe.orders, oe.order_items',
        schema_names   => 'hr',
        add            => TRUE,
        inclusion_rule => TRUE);
    END;
    /

Example 5-15 Adding Rules for the hr Schema to the Negative Rule Set

    BEGIN
      DBMS_XSTREAM_ADM.ALTER_OUTBOUND(
        server_name    => 'xout',
        table_names    => NULL,
        schema_names   => 'hr',
        add            => TRUE,
        inclusion_rule => FALSE);
    END;
    /

**See Also:**

- "[Rules and Rule Sets](general-xstream-concepts.md)"

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_XSTREAM_ADM.md)

**Parent topic:** Adding Rules to an XStream Out Configuration

##### 5.4.1.2 Adding Subset Rules to an Outbound Server's Positive Rule Set

You can add subset rules to an outbound server's positive rule set using the `ADD_SUBSET_OUTBOUND_RULES` procedure in the `DBMS_XSTREAM_ADM` package.

The `ADD_SUBSET_OUTBOUND_RULES` procedure only adds rules for DML changes to an outbound server's positive rule set. It does not add rules for DDL changes, and it does not add rules to a capture process's rule set.

##### To add subset rules to an outbound server's positive rule set:

1.  Connect to the outbound server database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the `ADD_SUBSET_OUTBOUND_RULES` procedure, and specify the following parameters:

    - `server_name` - Specify the name of the outbound server.

    - `table_name` - Specify the table for which you want to capture and stream a subset of data.

    - `condition` - Specify the subset condition, which is similar to the `WHERE` clause in a SQL statement, to stream changes to a subset of rows in the table.

    - `column_list` - Specify the subset of columns to keep or discard, or specify `NULL` to keep all of the columns.

    - `keep` - Specify `TRUE` to keep the columns listed in the `column_list` parameter, or specify `FALSE` to discard the columns in the `column_list` parameter.

    When `column_list` is non-`NULL` and `keep` is set to `TRUE`, the procedure creates a keep columns declarative rule-based transformation for the columns listed in `column_list`.

    When `column_list` is non-`NULL` and `keep` is set to `FALSE`, the procedure creates a delete column declarative rule-based transformation for each column listed in `column_list`.

3.  If subset rules should also be added to the rule set of a capture process or propagation that streams row LCRs to the outbound server, then use the `ADD_*_RULES` procedures in the `DBMS_XSTREAM_ADM` package to add them.

Example 5-16 Adding Rules That Stream Changes to a Subset of Rows in a Table

The following procedure creates rules that only evaluate to `TRUE` for row changes where the `department_id` value is `40` in the `hr.employees` table:

    DECLARE
      cols DBMS_UTILITY.LNAME_ARRAY;
    BEGIN
        cols(1) := 'employee_id';
        cols(2) := 'first_name';
        cols(3) := 'last_name';
        cols(4) := 'email';
        cols(5) := 'phone_number';
        cols(6) := 'hire_date';
        cols(7) := 'job_id';
        cols(8) := 'salary';
        cols(9) := 'commission_pct';
        cols(10) := 'manager_id';
        cols(11) := 'department_id';
      DBMS_XSTREAM_ADM.ADD_SUBSET_OUTBOUND_RULES(
        server_name => 'xout',
        table_name  => 'hr.employees',
        condition   => 'department_id=40',
        column_list => cols);
    END;
    /

Example 5-17 Adding Rules That Stream Changes to a Subset of Rows and Columns in a Table

The following procedure creates rules that only evaluate to `TRUE` for row changes where the `department_id` value is `40` for the `hr.employees` table. The procedure also creates delete column declarative rule-based transformations for the `salary` and `commission_pct` columns.

    BEGIN
      DBMS_XSTREAM_ADM.ADD_SUBSET_OUTBOUND_RULES(
        server_name => 'xout',
        table_name  => 'hr.employees',
        condition   => 'department_id=40',
        column_list => 'salary,commission_pct',
        keep        => FALSE);
    END;
    /

**See Also:**

- "[Rules and Rule Sets](general-xstream-concepts.md)"

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_XSTREAM_ADM.md)

- "[Declarative Rule-Based Transformations](general-xstream-concepts.md)"

**Parent topic:** Adding Rules to an XStream Out Configuration

##### 5.4.1.3 Adding Rules With Custom Conditions to XStream Out Components

Some of the procedures that create rules in the `DBMS_XSTREAM_ADM` package include an `and_condition` parameter. This parameter enables you to add conditions to system-created rules.

The condition specified by the `and_condition` parameter is appended to the system-created rule condition using an `AND` clause in the following way:

    (system_condition) AND (and_condition)

The variable in the specified condition must be `:lcr`.

##### To add a rule with a custom condition to an XStream Out component:

1.  Connect to the database running the XStream Out component as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run an `ADD_*_RULES` procedure and specify the custom condition in the `and_condition` parameter.

    See "[System-Created Rules and XStream](general-xstream-concepts.md)" for information about these procedures.

If you are specifying an LCR member subprogram that is dependent on the LCR type (row or DDL), then ensure that this procedure only generates the appropriate rule. Specifically, if you specify an LCR member subprogram that is valid only for row LCRs, then specify `TRUE` for the `include_dml` parameter and `FALSE` for the `include_ddl` parameter. If you specify an LCR member subprogram that is valid only for DDL LCRs, then specify `FALSE` for the `include_dml` parameter and `TRUE` for the `include_ddl` parameter.

For example, the `GET_OBJECT_TYPE` member function only applies to DDL LCRs. Therefore, if you use this member function in an `and_condition`, then specify `FALSE` for the `include_dml` parameter and `TRUE` for the `include_ddl` parameter.

Example 5-18 Adding a Table Rule With a Custom Condition

This example specifies that the table rules generated by the `ADD_TABLE_RULES` procedure evaluate to `TRUE` only if the table is `hr.departments`, the source database is `dbs1.example.com`, and the tag value is the hexadecimal equivalent of `'02'`.

    BEGIN
      DBMS_XSTREAM_ADM.ADD_TABLE_RULES(
        table_name          =>  'hr.departments',
        streams_type        =>  'capture',
        streams_name        =>  'xout_capture',
        queue_name          =>  'xstream_queue',
        include_dml         =>  TRUE,
        include_ddl         =>  TRUE,
        include_tagged_lcr  =>  TRUE,
        source_database     =>  'dbs1.example.com',
        inclusion_rule      =>  TRUE,
        and_condition       =>  ':lcr.get_tag() = HEXTORAW(''02'')');
    END;
    /

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/Logical-Change-Record-TYPEs.md) for more information about LCR member subprograms

**Parent topic:** Adding Rules to an XStream Out Configuration

#### 5.4.2 Removing Rules from an XStream Out Configuration

You can remove rules from an XStream Out configuration.

- Removing Schema Rules and Table Rules From an XStream Out Configuration
  You can remove schema rules and table rules from an XStream Out configuration using the `ALTER_OUTBOUND` procedure in the `DBMS_XSTREAM_ADM` package. The `ALTER_OUTBOUND` procedure removes rules for both DML and DDL changes.
- Removing Subset Rules from an Outbound Server's Positive Rule Set
  You can remove subset rules from an outbound server's positive rule set using the `REMOVE_SUBSET_OUTBOUND_RULES` procedure in the `DBMS_XSTREAM_ADM` package.
- Removing Rules Using the REMOVE_RULE Procedure
  You can remove a single rule from an XStream Out component's rule set or all rules from the rule set using the `REMOVE_RULE` procedure in the `DBMS_XSTREAM_ADM` package.

**Parent topic:** Managing Rules for an XStream Out Configuration

##### 5.4.2.1 Removing Schema Rules and Table Rules From an XStream Out Configuration

You can remove schema rules and table rules from an XStream Out configuration using the `ALTER_OUTBOUND` procedure in the `DBMS_XSTREAM_ADM` package. The `ALTER_OUTBOUND` procedure removes rules for both DML and DDL changes.

When you follow the instructions in this section, the `ALTER_OUTBOUND` procedure always removes rules for the specified schemas and tables from one of the outbound server's rule sets. If the `DBMS_XSTREAM_ADM` package can manage the outbound server's capture process, then the `ALTER_OUTBOUND` procedure also removes rules for the specified schemas and tables from one of the rule sets used by this capture process.

To determine whether the `DBMS_XSTREAM_ADM` package can manage the outbound server's capture process, see "Checking Whether the DBMS_XSTREAM_ADM Package Can Manage a Capture Process". If the `DBMS_XSTREAM_ADM` package cannot manage the outbound server's capture process, then the `ALTER_OUTBOUND` procedure removes rules from the outbound server's rule set only. In this case, if you must remove the rules for same schemas and tables from the capture process's rule set as well, then see "Removing Rules Using the REMOVE_RULE Procedure" for instructions.

In addition, if the capture process is running on a different database than the outbound server, then remove the schema and table rules from the propagation that sends LCRs to the outbound server's database. See "Removing Rules Using the REMOVE_RULE Procedure" for instructions.

##### To remove schema rules and table rules from an XStream Out configuration:

1.  Connect to the outbound server database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the `ALTER_OUTBOUND` procedure, and specify the following parameters:

    - `server_name` - Specify the name of the outbound server.

    - `table_names` - Specify the tables for which to remove rules, or specify `NULL` to remove no table rules.

    - `schema_name` - Specify the schemas for which to remove rules, or specify `NULL` to remove no schema rules.

    - `add` - Specify `FALSE` so that the rules are removed. (Rules are added if you specify `TRUE`.)

    - `inclusion_rule` - Specify `TRUE` to remove rules from the positive rule set of the outbound server, or specify `FALSE` to remove rules from the negative rule set of the outbound server. If the `DBMS_XSTREAM_ADM` package can manage the outbound server's capture process, then rules are also removed from this capture process's rule set.

    The following examples remove rules from the configuration of an outbound server named `xout`.

Example 5-19 Removing Rules for the hr Schema, oe.orders Table, and oe.order_items Table from the Positive Rule Set

    BEGIN
      DBMS_XSTREAM_ADM.ALTER_OUTBOUND(
        server_name    => 'xout',
        table_names    => 'oe.orders, oe.order_items',
        schema_names   => 'hr',
        add            => FALSE,
        inclusion_rule => TRUE);
    END;
    /

Example 5-20 Removing Rules for the hr Schema from the Negative Rule Set

    BEGIN
      DBMS_XSTREAM_ADM.ALTER_OUTBOUND(
        server_name    => 'xout',
        table_names    => NULL,
        schema_names   => 'hr',
        add            => FALSE,
        inclusion_rule => FALSE);
    END;
    /

**See Also:**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_XSTREAM_ADM.md)

- "[Declarative Rule-Based Transformations](general-xstream-concepts.md)"

**Parent topic:** Removing Rules from an XStream Out Configuration

##### 5.4.2.2 Removing Subset Rules from an Outbound Server's Positive Rule Set

You can remove subset rules from an outbound server's positive rule set using the `REMOVE_SUBSET_OUTBOUND_RULES` procedure in the `DBMS_XSTREAM_ADM` package.

The `REMOVE_SUBSET_OUTBOUND_RULES` procedure only removes rules for DML changes. It does not remove rules for DDL changes, and it does not remove rules from a capture process's rule set.

##### To remove subset rules from an outbound server's positive rule set:

1.  Connect to the outbound server database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Determine the rule names for the subset rules by running the following query:

        SELECT RULE_OWNER, SUBSETTING_OPERATION, RULE_NAME
           FROM ALL_XSTREAM_RULES
           WHERE SUBSETTING_OPERATION IS NOT NULL;

3.  Run the `REMOVE_SUBSET_OUTBOUND_RULES` procedure, and specify the rules to remove from the list of rules displayed in Step 2.

    For example, assume that Step 2 returned the following results:

        RULE_OWNER                     SUBSET RULE_NAME
        ------------------------------ ------ ------------------------------
        XSTRMADMIN                     INSERT EMPLOYEES71
        XSTRMADMIN                     UPDATE EMPLOYEES72
        XSTRMADMIN                     DELETE EMPLOYEES73

4.  If subset rules should also be removed from the rule set of a capture process and propagation that streams row LCRs to the outbound server, then see "Removing Rules Using the REMOVE_RULE Procedure" for information about removing rules.

Example 5-21 Removing Subset Rules From an Outbound Server's Positive Rule Set

To remove these rules from the positive rule set of the `xout` outbound server, run the following procedure:

    BEGIN
      DBMS_XSTREAM_ADM.REMOVE_SUBSET_OUTBOUND_RULES(
        server_name      => 'xout',
        insert_rule_name => 'xstrmadmin.employees71',
        update_rule_name => 'xstrmadmin.employees72',
        delete_rule_name => 'xstrmadmin.employees73');
    END;
    /

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_XSTREAM_ADM.md)

**Parent topic:** Removing Rules from an XStream Out Configuration

##### 5.4.2.3 Removing Rules Using the REMOVE_RULE Procedure

You can remove a single rule from an XStream Out component's rule set or all rules from the rule set using the `REMOVE_RULE` procedure in the `DBMS_XSTREAM_ADM` package.

The XStream Out component can be a capture process, propagation, or outbound server.

The `REMOVE_RULE` procedure only can remove rules for both DML and DDL changes, and it can remove rules from either the component's positive rule set or negative rule set.

##### To remove a single rule or all rules from an outbound server's rule set:

1.  Connect to the database running the XStream Out component as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Determine the rule name and XStream component name.

    See "[Monitoring XStream Rules](monitoring-xstream-out.md)" for a query that displays this information.

3.  Run the `REMOVE_RULE` procedure.

The `inclusion_rule` parameter is set to `TRUE` to indicate the positive rule set.

The `rule_name` parameter is set to `NULL` to specify that all of the rules are removed from the rule set, and the `inclusion_rule` parameter is set to `FALSE` to indicate the negative rule set.

Example 5-22 Removing a Rule From an Outbound Server's Rule Set

This example removes a rule named `orders12` from positive rule set of the `xout` outbound server.

    BEGIN
      DBMS_XSTREAM_ADM.REMOVE_RULE(
       rule_name      => 'orders12',
       streams_type   => 'APPLY',
       streams_name   => 'xout',
       inclusion_rule => TRUE);
    /

Example 5-23 Removing All of the Rules From an Outbound Server's Rule Set

This example removes all of the rules from the negative rule set of the `xout` outbound server.

    BEGIN
      DBMS_XSTREAM_ADM.REMOVE_RULE(
       rule_name      => NULL,
       streams_type   => 'APPLY',
       streams_name   => 'xout',
       inclusion_rule => FALSE);
    /

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_XSTREAM_ADM.md)

**Parent topic:** Removing Rules from an XStream Out Configuration

### 5.5 Managing Declarative Rule-Based Transformations

Declarative rule-based transformations cover a set of common transformation scenarios for row LCRs.

You can use the following procedures in the `DBMS_XSTREAM_ADM` package to manage declarative rule-based transformations: `ADD_COLUMN`, `DELETE_COLUMN`, `KEEP_COLUMNS`, `RENAME_COLUMN`, `RENAME_SCHEMA`, and `RENAME_TABLE`.

- Adding Declarative Rule-Based Transformations
  Examples illustrate adding declarative rule-based transformations to DML rules.
- Overwriting Existing Declarative Rule-Based Transformations
  You can overwrite existing declarative rule-based transformations using the `DBMS_XSTREAM_ADM` package.
- Removing Declarative Rule-Based Transformations
  To remove a declarative rule-based transformation from a rule, use the same procedure used to add the transformation, but specify `REMOVE` for the `operation` parameter.

**See Also:**

"[Declarative Rule-Based Transformations](general-xstream-concepts.md)"

**Parent topic:** Managing XStream Out

#### 5.5.1 Adding Declarative Rule-Based Transformations

Examples illustrate adding declarative rule-based transformations to DML rules.

**Note:**

Declarative rule-based transformations can be specified for DML rules only. They cannot be specified for DDL rules.

- Adding a Declarative Rule-Based Transformation That Renames a Table
  Use the `RENAME_TABLE` procedure in the `DBMS_XSTREAM_ADM` package to add a declarative rule-based transformation that renames a table in a row LCR.
- Adding a Declarative Rule-Based Transformation That Adds a Column
  Use the `ADD_COLUMN` procedure in the `DBMS_XSTREAM_ADM` package to add a declarative rule-based transformation that adds a column to a row in a row LCR.

**Parent topic:** Managing Declarative Rule-Based Transformations

##### 5.5.1.1 Adding a Declarative Rule-Based Transformation That Renames a Table

Use the `RENAME_TABLE` procedure in the `DBMS_XSTREAM_ADM` package to add a declarative rule-based transformation that renames a table in a row LCR.

The example in this section adds a declarative rule-based transformation to the `jobs12` rule in the `xstrmadmin` schema.

1.  Connect to the outbound server database as the XStream administrator.
    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.
2.  Run the following procedure:
        BEGIN
          DBMS_XSTREAM_ADM.RENAME_TABLE(
            rule_name       => 'xstrmadmin.jobs12',
            from_table_name => 'hr.jobs',
            to_table_name   => 'hr.assignments',
            step_number     => 0,
            operation       => 'ADD');
        END;
        /

The declarative rule-based transformation added by this procedure renames the table `hr.jobs` to `hr.assignments` in a row LCR when the rule `jobs12` evaluates to `TRUE` for the row LCR. If more than one declarative rule-based transformation is specified for the `jobs12` rule, then this transformation follows default transformation ordering because the `step_number` parameter is set to `0` (zero). In addition, the `operation` parameter is set to `ADD` to indicate that the transformation is being added to the rule, not removed from it.

The `RENAME_TABLE` procedure can also add a transformation that renames the schema in addition to the table. For example, in the previous example, to specify that the schema should be renamed to `oe`, specify `oe.assignments` for the `to_table_name` parameter.

**Parent topic:** Adding Declarative Rule-Based Transformations

##### 5.5.1.2 Adding a Declarative Rule-Based Transformation That Adds a Column

Use the `ADD_COLUMN` procedure in the `DBMS_XSTREAM_ADM` package to add a declarative rule-based transformation that adds a column to a row in a row LCR.

The example in this section adds a declarative rule-based transformation to the `employees35` rule in the `xstrmadmin` schema.

1.  Connect to the outbound server database as the XStream administrator.
    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.
2.  Run the following procedure:
        BEGIN
          DBMS_XSTREAM_ADM.ADD_COLUMN(
            rule_name    => 'xstrmadmin.employees35',
            table_name   => 'hr.employees',
            column_name  => 'birth_date',
            column_value => ANYDATA.ConvertDate(NULL),
            value_type   => 'NEW',
            step_number  => 0,
            operation    => 'ADD');
        END;
        /

The declarative rule-based transformation added by this procedure adds a `birth_date` column of data type `DATE` to an `hr.employees` table row in a row LCR when the rule `employees35` evaluates to `TRUE` for the row LCR.

Notice that the `ANYDATA.ConvertDate` function specifies the column type and the column value. In this example, the added column value is `NULL`, but a valid date can also be specified. Use the appropriate `ANYDATA` function for the column being added. For example, if the data type of the column being added is `NUMBER`, then use the `ANYDATA.ConvertNumber` function.

The `value_type` parameter is set to `NEW` to indicate that the column is added to the new values in a row LCR. You can also specify `OLD` to add the column to the old values.

If more than one declarative rule-based transformation is specified for the `employees35` rule, then the transformation follows default transformation ordering because the `step_number` parameter is set to `0` (zero). In addition, the `operation` parameter is set to `ADD` to indicate that the transformation is being added, not removed.

**Note:**

The `ADD_COLUMN` procedure is overloaded. A `column_function` parameter can specify that the current system date or time stamp is the value for the added column. The `column_value` and `column_function` parameters are mutually exclusive.

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/ANYDATA-TYPE.md) for more information about `AnyData` type functions

**Parent topic:** Adding Declarative Rule-Based Transformations

#### 5.5.2 Overwriting Existing Declarative Rule-Based Transformations

You can overwrite existing declarative rule-based transformations using the `DBMS_XSTREAM_ADM` package.

When the `operation` parameter is set to `ADD` in a procedure that adds a declarative rule-based transformation, an existing declarative rule-based transformation is overwritten if the parameters in the following list match the existing transformation parameters:

- `ADD_COLUMN` procedure: `rule_name`, `table_name`, `column_name`, and `step_number` parameters

- `DELETE_COLUMN` procedure: `rule_name`, `table_name`, `column_name`, and `step_number` parameters

- `KEEP_COLUMNS` procedure: `rule_name`, `table_name`, `column_list`, and `step_number` parameters, or `rule_name`, `table_name`, `column_table`, and `step_number` parameters (The `column_list` and `column_table` parameters are mutually exclusive.)

- `RENAME_COLUMN` procedure: `rule_name`, `table_name`, `from_column_name`, and `step_number` parameters

- `RENAME_SCHEMA` procedure: `rule_name`, `from_schema_name`, and `step_number` parameters

- `RENAME_TABLE` procedure: `rule_name`, `from_table_name`, and `step_number` parameters

##### To overwrite an existing rule-based transformation:

1.  Connect to the outbound server database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the appropriate procedure in the `DBMS_XSTREAM_ADM` package, and specify the appropriate parameters.

Example 5-24 Overwriting a RENAME_COLUMN Declarative Rule-Based Transformation

Suppose an existing declarative rule-based transformation was creating by running the following procedure:

    BEGIN
      DBMS_XSTREAM_ADM.RENAME_COLUMN(
        rule_name         => 'departments33',
        table_name        => 'hr.departments',
        from_column_name  => 'manager_id',
        to_column_name    => 'lead_id',
        value_type        => 'NEW',
        step_number       => 0,
        operation         => 'ADD');
    END;
    /

Running the following procedure overwrites this existing declarative rule-based transformation:

    BEGIN
      DBMS_XSTREAM_ADM.RENAME_COLUMN(
        rule_name         => 'departments33',
        table_name        => 'hr.departments',
        from_column_name  => 'manager_id',
        to_column_name    => 'lead_id',
        value_type        => '*',
        step_number       => 0,
        operation         => 'ADD');
    END;
    /

In this case, the `value_type` parameter in the declarative rule-based transformation was changed from `NEW` to `*`. That is, in the original transformation, only new values were renamed in row LCRs, but, in the new transformation, both old and new values are renamed in row LCRs.

**Parent topic:** Managing Declarative Rule-Based Transformations

#### 5.5.3 Removing Declarative Rule-Based Transformations

To remove a declarative rule-based transformation from a rule, use the same procedure used to add the transformation, but specify `REMOVE` for the `operation` parameter.

##### To remove a declarative rule-based transformation:

1.  Connect to the outbound server database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the appropriate procedure in the `DBMS_XSTREAM_ADM` package and specify `REMOVE` for the `operation` parameter.

When the `operation` parameter is set to `REMOVE` in any of the declarative transformation procedures listed in "Managing Declarative Rule-Based Transformations", the other parameters in the procedure are optional, excluding the `rule_name` parameter. If these optional parameters are set to `NULL`, then they become wildcards.

The `RENAME_TABLE` procedure in the previous example behaves in the following way when one or more of the optional parameters are set to `NULL`:

Table 5-1 Behavior of Optional Parameters in the RENAME_TABLE Procedure

| from_table_name Parameter | to_table_name Parameter | step_number Parameter | Result                                                                                                                  |
|:--------------------------|:------------------------|:----------------------|:------------------------------------------------------------------------------------------------------------------------|
| `NULL`                    | `NULL`                  | `NULL`                | Remove all rename table transformations for the specified rule                                                          |
| non-`NULL`                | `NULL`                  | `NULL`                | Remove all rename table transformations with the specified `from_table_name` for the specified rule                     |
| `NULL`                    | non-`NULL`              | `NULL`                | Remove all rename table transformations with the specified `to_table_name` for the specified rule                       |
| `NULL`                    | `NULL`                  | non-`NULL`            | Remove all rename table transformations with the specified `step_number` for the specified rule                         |
| non-`NULL`                | non-`NULL`              | `NULL`                | Remove all rename table transformations with the specified `from_table_name` and `to_table_name` for the specified rule |
| `NULL`                    | non-`NULL`              | non-`NULL`            | Remove all rename table transformations with the specified `to_table_name` and `step_number` for the specified rule     |
| non-`NULL`                | `NULL`                  | non-`NULL`            | Remove all rename table transformations with the specified `from_table_name` and `step_number` for the specified rule   |

The other declarative transformation procedures work in a similar way when optional parameters are set to `NULL` and the operation parameter is set to `REMOVE`.

Example 5-25 Removing a RENAME_TABLE Declarative Rule-Based Transformation

To remove the transformation added in "Adding a Declarative Rule-Based Transformation That Renames a Table", run the following procedure:

    BEGIN
      DBMS_XSTREAM_ADM.RENAME_TABLE(
        rule_name       => 'strmadmin.jobs12',
        from_table_name => 'hr.jobs',
        to_table_name   => 'hr.assignments',
        step_number     => 0,
        operation       => 'REMOVE');
    END;
    /

**Parent topic:** Managing Declarative Rule-Based Transformations

### 5.6 Dropping Components in an XStream Out Configuration

To drop an outbound server, use the `DROP_OUTBOUND` procedure in the `DBMS_XSTREAM_ADM` package.

This procedure always drops the specified outbound server. This procedure also drops the queue used by the outbound server if both of the following conditions are met:

- The queue was created by the `ADD_OUTBOUND` or `CREATE_OUTBOUND` procedure in the `DBMS_XSTREAM_ADM` package.

- The outbound server is the only subscriber to the queue.

If either one of the preceding conditions is not met, then the `DROP_OUTBOUND` procedure only drops the outbound server. It does not drop the queue.

This procedure also drops the capture process for the outbound server if both of the following conditions are met:

- The procedure can drop the outbound server's queue.

- The `DBMS_XSTREAM_ADM` package can manage the outbound server's capture process. See "Checking Whether the DBMS_XSTREAM_ADM Package Can Manage a Capture Process".

If the procedure can drop the queue but cannot manage the capture process, then it drops the queue without dropping the capture process.

#### To drop an outbound server:

1.  Connect to the outbound server database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the `DROP_OUTBOUND` procedure.

Example 5-26 Dropping an Outbound Server

To drop an outbound server named `xout`, run the following procedure:

    exec DBMS_XSTREAM_ADM.DROP_OUTBOUND('xout');

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_XSTREAM_ADM.md) for information about the `DROP_OUTBOUND` procedure

**Parent topic:** Managing XStream Out

### 5.7 Removing an XStream Out Configuration

You run the `REMOVE_XSTREAM_CONFIGURATION` procedure in the `DBMS_XSTREAM_ADM` package to remove an XStream Out configuration in a multitenant container database (CDB) or non-CDB.

**Note:**

Run this procedure only if you are sure you want to remove the entire XStream Out configuration at a database. This procedure also removes all XStream In components, Oracle GoldenGate components, and Oracle Replication components from the database.

#### To remove the XStream Out configuration:

1.  Connect to the outbound server database as the XStream administrator.

    In a CDB, connect to the CDB root.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the `REMOVE_XSTREAM_CONFIGURATION` procedure.

    In a non-CDB, run the following procedure:

        EXEC DBMS_XSTREAM_ADM.REMOVE_XSTREAM_CONFIGURATION();

    In a CDB, ensure that all containers are open in read/write mode and run the following procedure:

        EXEC DBMS_XSTREAM_ADM.REMOVE_XSTREAM_CONFIGURATION(container => 'ALL');

    Setting the `container` parameter to `ALL` removes the XStream configuration from all containers in the CDB.

3.  Drop the XStream administrator at the database, if possible.

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_XSTREAM_ADM.md) for detailed information about the actions performed by the `REMOVE_XSTREAM_CONFIGURATION` procedure

**Parent topic:** Managing XStream Out
