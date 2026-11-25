## 1 Listener Control Utility

This chapter describes the Listener Control Utility commands and syntax. The terms **SQL\*Net** and **Net Services** are used interchangeably throughout Oracle documentation.

- Listener Control Utility Overview
  To perform basic management functions on one or more listeners, you can use the Listener Control utility commands. You can also view and change parameter settings.
- SET and SHOW Commands of the Listener Control utility
  The `SET` and `SHOW` commands enable you to alter and view listener configuration parameters.
- Distributed Operations
  The Listener Control utility can perform operations on a local or a remote listener.
- Oracle Net Listener Security
  Authentication for listener administration depends on whether you access the listener locally, or remotely.
- Listener Control Utility Commands
  Use the Listener Control utility commands to manage and configure listeners.

### 1.1 Listener Control Utility Overview

The Listener Control utility enables you to administer [listeners](glossary.md). To perform basic management functions on one or more listeners, you can use the Listener Control utility commands. You can also view and change parameter settings.

The basic syntax of Listener Control utility commands is as follows:

    lsnrctl command listener_name

In the preceding command, `listener_name` is the name of the listener that you want to administer. If you do not specify a specific listener in the command string, then the command is directed to the default listener name, `LISTENER`.

You can also issue Listener Control utility commands at the `LSNRCTL>` program prompt. To obtain the prompt, enter `lsnrctl` with no arguments at the operating system command line. When you run `lsnrctl`, the program is started. You can then enter the necessary commands from the program prompt. The basic syntax of issuing commands from `LSNRCTL>` program prompt is as follows:

    lsnrctl
    LSNRCTL> command listener_name

You can combine commands in a standard text file, and then run them as a sequence of commands. To run in batch mode, use the following format:

`lsnrctl @``file_name`

To identify comments in the batch script, you can use either `REM` or \#. All other lines are considered commands. Any commands that typically require confirmation do not require confirmation during batch processing.

For most commands, the Listener Control utility establishes an Oracle Net connection with the listener that is used to transmit the command. To initiate an Oracle Net connection to the listener, the Listener Control utility must obtain the protocol addresses for the named listener or a listener named `LISTENER`. This is done by resolving the listener name with one of the following mechanisms:

- `listener.ora` file in the directory specified by the `TNS_ADMIN` environment variable.

- `listener.ora` file in the `ORACLE_HOME``/network/admin` directory.

- Naming method; for example, a `tnsnames.ora` file.

If none of the preceding mechanisms resolve the listener name, then the Listener Control utility uses the default listener name `LISTENER`, resolves the host name IP address, and uses port 1521.

The Listener Control utility supports the following types of commands:

- Operational commands, such as `START`, and `STOP`.

- Modifier commands, such as `SET TRC_LEVEL`.

- Informational commands, such as `STATUS`, and `SHOW LOG_FILE`.

**Related Topics**

- START
- STOP
- SET TRC_LEVEL
- STATUS

**Parent topic:** Listener Control Utility

### 1.2 SET and SHOW Commands of the Listener Control utility

The `SET` and `SHOW` commands enable you to alter and view listener configuration parameters.

You can use the `SET` command to alter parameter values for a specified listener. You set the name of the listener to administer using the `SET CURRENT_LISTENER` command. Parameter values remain in effect until the listener is shut down. If you want these settings to persist, then use the `SAVE_CONFIG` command to save changes to the `listener.ora` file. .

You can use the `SHOW` command to display the current value of a configuration setting.

SET

SET CURRENT_LISTENER

SAVE_CONFIG

SHOW

**Parent topic:** Listener Control Utility

### 1.3 Distributed Operations

The Listener Control utility can perform operations on a local or a remote listener.

#### Set Up a Computer to Remotely Administer a Listener

Ensure that the Listener Control utility (`lsnrctl`) executable is installed in the `ORACLE_HOME``/bin` directory. You can resolve the name of the listener that you want to administer either through a `listener.ora` file, or by a naming method.

When you administer a listener remotely, you can issue all commands except `START`. However, the Listener Control utility can only start the listener on the same computer from which the utility is running.

When issuing commands, specify the listener name as an argument. If you omit the listener name in the command, then the listener name set with the command `SET CURRENT_LISTENER` is used. If the listener name is not set with that command, then the command is directed to the default listener name, `LISTENER`.

Example 1-1 Issuing Commands Using the Listener Control Utility

    LSNRCTL> SERVICES lsnr

**Parent topic:** Listener Control Utility

### 1.4 Oracle Net Listener Security

Authentication for listener administration depends on whether you access the listener locally, or remotely.

Local listener administration is secure through local operating system authentication, which restricts listener administration to the user account that started the listener, or to the super user. By default, remote listener administration is disabled.

Oracle recommends that you perform listener administration in the default mode, and access the system remotely using a remote login. When you administer the listener remotely, use either Oracle Enterprise Manager Cloud Control or Secure Shell (SSH) to access the remote host.

**Parent topic:** Listener Control Utility

### 1.5 Listener Control Utility Commands

Use the Listener Control utility commands to manage and configure listeners.

- EXIT
  The Listener Control utility command `EXIT` exits from the Listener Control utility, and returns you to the operating system prompt.
- HELP
  The Listener Control utility command `HELP` provides a list of all the Listener Control utility commands, or provides syntax help for a particular Listener Control utility command.
- QUIT
  The Listener Control utility command `QUIT` exits from the Listener Control utility and returns you to the operating system prompt.
- RELOAD
  The Listener Control utility command `RELOAD` reloads the `listener.ora` file, so that you can add or change statically configured services without stopping the listener.
- SAVE_CONFIG
  The Listener Control utility command `SAVE_CONFIG` save the current configuration state of the listener to the `listener.ora` file.
- SERVICES
  The Listener Control utility command `SERVICES` returns detailed information about the database services, instances, and service handlers to which the listener forwards client connection requests.
- SET
  The Listener Control utility command `SET` alters the parameter values for the listener.
- SET CURRENT_LISTENER
  The Listener Control utility command `SET CURRENT_LISTENER` sets the name of the listener that you want to administer.
- SET DISPLAYMODE
  The Listener Control utility command `SET DISPLAYMODE`
- SET INBOUND_CONNECT_TIMEOUT
  The Listener Control utility command `SET INBOUND_CONNECT_TIMEOUT` specifies the time, in seconds, for the client to complete its connect request to the listener after establishing the network connection.
- SET LOG_DIRECTORY
  The Listener Control utility command `SET LOG_DIRECTORY` sets the destination directory where the listener log file is written.
- SET LOG_FILE
  The Listener Control utility command `SET LOG_FILE` sets the name for the listener log file.
- SET LOG_STATUS
  The Listener Control utility command `SET LOG_STATUS` turns listener logging on or off.
- SET SAVE_CONFIG_ON_STOP
  The Listener Control utility command `SET SAVE_CONFIG_ON_STOP` specifies whether changes made to the parameter values for the listener by the `SET` command are saved to the `listener.ora` file at the time that the listener is stopped with the `STOP` command.
- SET TRC_DIRECTORY
  The Listener Control utility command `SET TRC_DIRECTORY` sets the destination directory where the listener trace files are written.
- SET TRC_FILE
  The Listener Control utility command `SET TRC_FILE` sets the name of the listener trace file.
- SET TRC_LEVEL
  The Listener Control utility command `SET TRC_LEVEL` sets a specific level of tracing for the listener.
- SHOW
  The Listener Control utility command `SHOW` displays the current parameter values for the listener.
- SPAWN
  The Listener Control utility command SPAWN starts a program stored on the computer on which the listener is running,and that is listed with an alias in the `listener.ora` file.
- START
  The Listener Control utility command `START` starts the named listener.
- STATUS
  The Listener Control utility command `STATUS` displays basic status information about a listener.
- STOP
  The Listener Control utility command `STOP` stops the named listener.
- TRACE
  The Listener Control utility command `TRACE` sets tracing for the listener.
- VERSION
  The Listener Control utility command `VERSION` displays the current version of the Listener Control utility.

**Parent topic:** Listener Control Utility

#### 1.5.1 EXIT

The Listener Control utility command `EXIT` exits from the Listener Control utility, and returns you to the operating system prompt.

##### Purpose

To exit from the Listener Control utility, and return to the operating system prompt.

##### Prerequisites

None

##### Syntax

From the Listener Control utility:

    LSNRCTL> EXIT

##### Arguments

None

##### Usage Notes

This command is identical to the `QUIT` command.

##### Example

    LSNRCTL> EXIT

**Parent topic:** Listener Control Utility Commands

#### 1.5.2 HELP

The Listener Control utility command `HELP` provides a list of all the Listener Control utility commands, or provides syntax help for a particular Listener Control utility command.

##### Purpose

To provide a list of all the Listener Control utility commands or provide syntax help for a particular Listener Control utility command.

##### Prerequisites

None

##### Syntax

From the operating system:

    lsnrctl HELP command

From the Listener Control utility:

    LSNRCTL> HELP command

##### Arguments

`command`: The Listener Control utility command. Commands are shown in the following example output.

When you enter a command as an argument to `HELP`, the Listener Control utility displays information about how to use the command. When you enter `HELP` without an argument, the Listener Control utility displays a list of all the commands.

##### Example

    LSNRCTL> HELP
    The following operations are available
    An asterisk (*) denotes a modifier or extended command:
    exit
    quit
    reload
    services
    set*
    show*
    spawn
    start
    status
    stop
    trace
    version

**Parent topic:** Listener Control Utility Commands

#### 1.5.3 QUIT

The Listener Control utility command `QUIT` exits from the Listener Control utility and returns you to the operating system prompt.

##### Purpose

To exit from the Listener Control utility and return to the operating system prompt.

##### Prerequisites

None

##### Syntax

From the Listener Control utility:

    LSNRCTL> QUIT

##### Arguments

None

##### Usage Notes

This command is identical to the `EXIT` command.

##### Example

    LSNRCTL> QUIT

**Parent topic:** Listener Control Utility Commands

#### 1.5.4 RELOAD

The Listener Control utility command `RELOAD` reloads the `listener.ora` file, so that you can add or change statically configured services without stopping the listener.

##### Purpose

To reload the `listener.ora` file. This command enables you to add or change statically configured services without actually stopping the listener.

When you run this command, the database services, instances, service handlers, and listening endpoints previously registered dynamically with the listener are unregistered, and subsequently registered again.

To obtain a lightweight reload without dropping registration, use the option `–with_ha`. Using this option ensures that registered services remain available to clients during reload.

##### Prerequisites

None

##### Syntax

From the operating system:

    lsnrctl RELOAD [-with_ha] listener_name

From the Listener Control utility:

    LSNRCTL> RELOAD [-with_ha] listener_name

##### Arguments

`listener_name`: The listener name, if the default name of `LISTENER` is not used.

`-with_ha`: command option used with `RELOAD` that indicates that the reload of `listener.ora` is completed without dropping existing registrations.

##### Example

    LSNRCTL> RELOAD
    Connecting to (DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=sales-server)(PORT=1521)))
    The command completed successfully

**Parent topic:** Listener Control Utility Commands

#### 1.5.5 SAVE_CONFIG

The Listener Control utility command `SAVE_CONFIG` save the current configuration state of the listener to the `listener.ora` file.

##### Purpose

To save the current configuration state of the listener, including trace level, trace file, trace directory, and logging to the `listener.ora` file. Any changes are stored in `listener.ora`, preserving formatting, comments, and case as much as possible. Before modification of the `listener.ora` file, a backup of the file, called `listener.bak`, is created.

##### Syntax

From the operating system:

    lsnrctl SAVE_CONFIG listener_name

From the Listener Control utility:

    LSNRCTL> SAVE_CONFIG listener_name

##### Arguments

`listener_name`: The listener name, if the default name of `LISTENER` is not used.

##### Usage Notes

This command enables you to save all runtime configuration changes to the `listener.ora` file.

##### Example

    LSNRCTL> SAVE_CONFIG listener
    Connecting to (DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=sales-server)(PORT=1521)))
    Saved LISTENER configuration parameters.
    Listener Parameter File   /oracle/network/admin/listener.ora
    Old Parameter File   /oracle/network/admin/listener.bak
    The command completed successfully

**Parent topic:** Listener Control Utility Commands

#### 1.5.6 SERVICES

The Listener Control utility command `SERVICES` returns detailed information about the database services, instances, and service handlers to which the listener forwards client connection requests.

##### Purpose

To obtain detailed information about the database services, instances, and service handlers (dispatchers and dedicated servers) to which the listener forwards client connection requests.

##### Prerequisites

None

##### Syntax

##### Arguments

From the operating system:

    lsnrctl SERVICES listener_name

From the Listener Control utility:

    LSNRCTL> SERVICES listener_name

`listener_name`: The listener name, if the default name of `LISTENER` is not used.

##### Usage Notes

The `SET DISPLAYMODE` command changes the format and the detail level of the output.

**See Also:**

[Oracle Database Net Services Administrator's Guide](../netag/configuring-and-administering-oracle-net-listener.md) for a complete description of `SERVICES` output

##### Example

This example shows `SERVICES` output in the default display mode. The output shows the following:

- An instance named `sales` belonging to two services, `sales1.us.example.com` and `sales2.us.example.com`, with a total of three service handlers.

- Service `sales1.us.example.com` is handled by one dispatcher only.

- Service `sales2.us.example.com` is handled by one dispatcher and one dedicated server, as specified by in the following output.

<!-- -->

    LSNRCTL> SERVICES
    Connecting to (DESCRIPTION=(ADDRESS=(PROTOCOL=ipc)(KEY=net)))
    Services Summary...
    Service "sales1.us.example.com" has 1 instance(s).
      Instance "sales", status READY, has 1 handler(s) for this service...
        Handler(s):
          "D000" established:0 refused:0 current:0 max:10000 state:ready
             DISPATCHER <machine: sales-server, pid: 5696>
             (ADDRESS=(PROTOCOL=tcp)(HOST=sales-server)(PORT=53411))
    Service "sales2.us.example.com" has 1 instance(s).
      Instance "sales", status READY, has 2 handler(s) for this service...
        Handler(s):
          "DEDICATED" established:0 refused:0 state:ready
             LOCAL SERVER
          "D001" established:0 refused:0 current:0 max:10000 state:ready
             DISPATCHER <machine: sales-server, pid: 5698>
             (ADDRESS=(PROTOCOL=tcp)(HOST=sales-server)(PORT=52618))
    The command completed successfully

**Related Topics**

- SET DISPLAYMODE

**Parent topic:** Listener Control Utility Commands

#### 1.5.7 SET

The Listener Control utility command `SET` alters the parameter values for the listener.

##### Purpose

To alter the parameter values for the listener. Parameter value changes remain in effect until the listener is shut down. To make the changes permanent, use the SAVE_CONFIG command to save changes to the `listener.ora` file.

##### Prerequisites

None

##### Syntax

From the operating system:

    lsnrctl SET parameter

From the Listener Control utility:

    LSNRCTL> SET parameter

##### Arguments

`parameter`: A `SET` parameter to modify its configuration setting. Parameters are shown in the example output.

When you enter `SET` without an argument, the Listener Control utility displays a list of all the parameters.

##### Usage Notes

If you are using the `SET` commands to alter the configuration of a listener other than the default `LISTENER` listener, then use the `SET CURRENT_LISTENER` command to set the name of the listener to administer.

##### Example

    LSNRCTL> SET
    The following operations are available with set.
    An asterisk (*) denotes a modifier or extended command.
    current_listener
    displaymode
    inbound_connect_timeout
    log_file
    log_directory
    log_status
    rawmode
    save_config_on_stop
    trc_file
    trc_directory
    trc_level

**Related Topics**

- SAVE_CONFIG
- SET CURRENT_LISTENER

**Parent topic:** Listener Control Utility Commands

#### 1.5.8 SET CURRENT_LISTENER

The Listener Control utility command `SET CURRENT_LISTENER` sets the name of the listener that you want to administer.

##### Purpose

To set the name of the listener that you want to administer. After you set the listener name with this command, you can issue subsequent commands that normally require `listener_name` without specifying the listener.

##### Syntax

From the Listener Control utility:

    LSNRCTL> SET CURRENT_LISTENER listener_name

##### Arguments

`listener_name`: The listener name, if you are not using the default name `LISTENER`.

##### Usage Notes

When you specify a listener name using `SET CURRENT_LISTENER`, the Listener Control utility commands act on the listener name that you specify with this command. You do not have to continue to specify the name of the listener.

##### Example

    LSNRCTL> SET CURRENT_LISTENER lsnr
    Current Listener is lsnr

**Parent topic:** Listener Control Utility Commands

#### 1.5.9 SET DISPLAYMODE

The Listener Control utility command `SET DISPLAYMODE`

##### Purpose

To change the format and level of detail for the `SERVICES` and `STATUS` commands.

##### Syntax

From the Listener Control utility:

    LSNRCTL> SET DISPLAYMODE {compat | normal | verbose | raw}

##### Arguments

Specify one of the following modes:

`compat`: Output that is compatible with earlier releases of the listener.

`normal`: Output that is formatted and descriptive. Oracle recommends this mode.

`verbose`: All data received from the listener in a formatted and descriptive output.

`raw`: All data received from the listener without any formatting. This argument should be used only if recommended by Oracle Support Services.

##### Example

    LSNRCTL> SET DISPLAYMODE normal
    Service display mode is NORMAL

**Related Topics**

- SERVICES
- STATUS

**Parent topic:** Listener Control Utility Commands

#### 1.5.10 SET INBOUND_CONNECT_TIMEOUT

The Listener Control utility command `SET INBOUND_CONNECT_TIMEOUT` specifies the time, in seconds, for the client to complete its connect request to the listener after establishing the network connection.

##### Purpose

To specify the time, in seconds, for the client to complete its connect request to the listener after establishing the network connection.

If the listener does not receive the client request in the time specified, then it terminates the connection. In addition, the listener logs the IP address of the client and an `ORA-12525:TNS: listener has not received client's request in time allowed` error message to the `listener.log` file.

**See Also:**

[Oracle Database Net Services Administrator's Guide](../netag/configuring-profiles.md) for additional information about specifying the time out for client connections

##### Syntax

From the Listener Control utility:

    LSNRCTL> SET INBOUND_CONNECT_TIMEOUT time

##### Arguments

`time`: The time in seconds. Default setting is 60 seconds.

##### Example

    LSNRCTL> SET INBOUND_CONNECT_TIMEOUT 2
    Connecting to (ADDRESS=(PROTOCOL=TCP)(HOST=sales-server)(PORT=1521))
    LISTENER parameter "inbound_connect_timeout" set to 2
    The command completed successfully.

**Parent topic:** Listener Control Utility Commands

#### 1.5.11 SET LOG_DIRECTORY

The Listener Control utility command `SET LOG_DIRECTORY` sets the destination directory where the listener log file is written.

##### Purpose

To set destination directory where the listener log file is written. By default, the log file is written to the `ORACLE_HOME/network/log` directory.

**Note:**

This command works only if Automatic Diagnostic Repository (ADR) is not enabled. The default is for ADR to be enabled, and to use the log directory `ORACLE_HOME/log/diag/``product_type`.

##### Prerequisites

None

##### Syntax

From the operating system:

    lsnrctl SET LOG_DIRECTORY directory

From the Listener Control utility:

    LSNRCTL> SET LOG_DIRECTORY directory

##### Arguments

`directory`: The directory path of the listener log file.

##### Example

    LSNRCTL> SET LOG_DIRECTORY /usr/oracle/admin
    Connecting to (ADDRESS=(PROTOCOL=TCP)(HOST=sales-server)(PORT=1521))
    LISTENER parameter "log_directory" set to /usr/oracle/admin
    The command completed successfully

**Parent topic:** Listener Control Utility Commands

#### 1.5.12 SET LOG_FILE

The Listener Control utility command `SET LOG_FILE` sets the name for the listener log file.

##### Purpose

To set the name for the listener log file. By default, the log file name is `listener.log`.

**Note:**

This command works only if Automatic Diagnostic Repository (ADR) is not enabled. The default is for ADR to be enabled, and use the log directory `ORACLE_HOME/log/diag/``product_type`.

##### Prerequisites

None

##### Syntax

From the operating system:

    lsnrctl SET LOG_FILE file_name

From the Listener Control utility:

    LSNRCTL> SET LOG_FILE file_name

##### Arguments

`file_name`: The file name of the listener log.

##### Example

    LSNRCTL> SET LOG_FILE list.log
    Connecting to (ADDRESS=(PROTOCOL=TCP)(HOST=sales-server)(PORT=1521))
    LISTENER parameter "log_file" set to list.log
    The command completed successfully

**Parent topic:** Listener Control Utility Commands

#### 1.5.13 SET LOG_STATUS

The Listener Control utility command `SET LOG_STATUS` turns listener logging on or off.

##### Purpose

To turn listener logging on or off.

##### Prerequisites

None

##### Syntax

From the operating system:

    lsnrctl SET LOG_STATUS {on | off}

From the Listener Control utility:

    LSNRCTL> SET LOG_STATUS {on | off}

##### Arguments

`on`: To turn logging on.

`off`: To turn logging off.

##### Example

    LSNRCTL> SET LOG_STATUS on
    Connecting to (ADDRESS=(PROTOCOL=TCP)(HOST=sales-server)(PORT=1521))
    LISTENER parameter "log_status" set to ON
    The command completed successfully

**Parent topic:** Listener Control Utility Commands

#### 1.5.14 SET SAVE_CONFIG_ON_STOP

The Listener Control utility command `SET SAVE_CONFIG_ON_STOP` specifies whether changes made to the parameter values for the listener by the `SET` command are saved to the `listener.ora` file at the time that the listener is stopped with the `STOP` command.

##### Purpose

To specify whether changes made to the parameter values for the listener by the `SET` command are saved to the `listener.ora` file at the time that the listener is stopped with the `STOP` command.

When changes are saved, the Listener Control utility tries to preserve formatting, comments, and letter case. Before the command modifies the `listener.ora` file, it creates a backup of the file, called `listener.bak`.

To have all parameters saved immediately, use the `SAVE_CONFIG` command.

##### Syntax

From the operating system:

    lsnrctl SET SAVE_CONFIG_ON_STOP  {on | off}

From the Listener Control utility:

    LSNRCTL> SET SAVE_CONFIG_ON_STOP  {on | off}

##### Arguments

`on`: To save configuration to `listener.ora`.

`off`: To not save configuration to `listener.ora`.

##### Example

    LSNRCTL> SET SAVE_CONFIG_ON_STOP on
    LISTENER parameter "save_config_on_stop" set to ON
    The command completed successfully

**Related Topics**

- SET
- STOP
- SAVE_CONFIG

**Parent topic:** Listener Control Utility Commands

#### 1.5.15 SET TRC_DIRECTORY

The Listener Control utility command `SET TRC_DIRECTORY` sets the destination directory where the listener trace files are written.

##### Purpose

To set the destination directory where the listener trace files are written. By default, the trace file are written to the `ORACLE_HOME/network/trace` directory.

**Note:**

This command works only if Automatic Diagnostic Repository (ADR) is not enabled. The default is for ADR to be enabled, and use the log directory `ORACLE_HOME/log/diag/``product_type`.

##### Prerequisites

None

##### Syntax

From the operating system:

    lsnrctl SET TRC_DIRECTORY directory

From the Listener Control utility:

    LSNRCTL> SET TRC_DIRECTORY directory

##### Arguments

`directory`: The directory path of the listener trace files.

##### Example

    LSNRCTL> SET TRC_DIRECTORY /usr/oracle/admin
    Connecting to (ADDRESS=(PROTOCOL=TCP)(HOST=sales-server)(PORT=1521))
    LISTENER parameter "trc_directory" set to /usr/oracle/admin
    The command completed successfully

**Parent topic:** Listener Control Utility Commands

#### 1.5.16 SET TRC_FILE

The Listener Control utility command `SET TRC_FILE` sets the name of the listener trace file.

##### Purpose

To set the name of the listener trace file. By default, the trace file name is `listener.trc`.

**Note:**

This command works only if Automatic Diagnostic Repository (ADR) is not enabled. The default is for ADR to be enabled, and use the log directory `ORACLE_HOME/log/diag/``product_type`.

##### Prerequisites

None

##### Syntax

From the operating system:

    lsnrctl SET TRC_FILE file_name

From the Listener Control utility:

    LSNRCTL> SET TRC_FILE file_name

##### Arguments

`file_name`: The file name of the listener trace.

##### Example

    LSNRCTL> SET TRC_FILE list.trc
    Connecting to (ADDRESS=(PROTOCOL=TCP)(HOST=sales-server)(PORT=1521))
    LISTENER parameter "trc_file" set to list.trc
    The command completed successfully

**Parent topic:** Listener Control Utility Commands

#### 1.5.17 SET TRC_LEVEL

The Listener Control utility command `SET TRC_LEVEL` sets a specific level of tracing for the listener.

##### Purpose

To set a specific level of tracing for the listener.

##### Prerequisites

None

##### Syntax

From the operating system:

    lsnrctl SET TRC_LEVEL level

From the Listener Control utility:

    LSNRCTL> SET TRC_LEVEL level

##### Arguments

`level`: One of the following trace levels:

- `off` for no trace output

- `user` for user trace information

- `admin` for administration trace information

- `support` for Oracle Support Services trace information

##### Usage Notes

This command has the same functionality as the `TRACE` command.

##### Example

    LSNRCTL> SET TRC_LEVEL admin
    Connecting to (ADDRESS=(PROTOCOL=TCP)(HOST=sales-server)(PORT=1521))
    LISTENER parameter "trc_level" set to admin
    The command completed successfully

**Related Topics**

- TRACE

**Parent topic:** Listener Control Utility Commands

#### 1.5.18 SHOW

The Listener Control utility command `SHOW` displays the current parameter values for the listener.

##### Purpose

To view the current parameter values for the listener.

All of the `SET` parameters have equivalent `SHOW` parameters.

##### Prerequisites

None

##### Syntax

From the operating system:

    lsnrctl SHOW parameter

From the Listener Control utility:

    LSNRCTL> SHOW parameter

##### Arguments

`parameter`: A parameter whose configuration settings you want to review. Parameters are shown in the example output.

When you enter `SHOW` without an argument, the Listener Control utility displays a list of all the parameters.

##### Example

    LSNRCTL> SHOW
    The following properties are available with SHOW:
    An asterisk (*) denotes a modifier or extended command:
    current_listener
    displaymode
    inbound_connect_timeout
    log_file
    log_directory
    log_status
    rawmode
    save_config_on_stop
    trc_file
    trc_directory
    trc_level

**Related Topics**

- SET

**Parent topic:** Listener Control Utility Commands

#### 1.5.19 SPAWN

The Listener Control utility command SPAWN starts a program stored on the computer on which the listener is running,and that is listed with an alias in the `listener.ora` file.

##### Purpose

To start a program stored on the computer on which the listener is running, and that is listed with an alias in the `listener.ora` file.

##### Prerequisites

None

##### Syntax

From the operating system:

    lsnrctl SPAWN listener_name alias (arguments='arg1,arg2,...')

From the Listener Control utility:

    LSNRCTL> SPAWN listener_name alias (arguments='arg1,arg2,...')

##### Arguments

`listener_name`: The listener name, if the default name of `LISTENER` is not used.

`alias`: The alias of the program to be spawned off is specified by a `listener.ora` file entry, similar to the following:

    alias = (PROGRAM=(NAME=)(ARGS=)(ENVS=))

For example:

    nstest = (PROGRAM=(NAME=nstest)(ARGS=test1)(ENVS='ORACLE_HOME=/usr/oracle'))

##### Example

The `nstest` program, shown in the preceding section, can then be spawned off using the following command:

    lsnrctl SPAWN listener_name nstest

**Parent topic:** Listener Control Utility Commands

#### 1.5.20 START

The Listener Control utility command `START` starts the named listener.

##### Purpose

To start the named listener.

##### Prerequisites

The listener must not be running.

##### Syntax

From the operating system:

    lsnrctl START listener_name

From the Listener Control utility:

    LSNRCTL> START listener_name

**Note:**

On Microsoft Windows, if the database was installed with the Oracle Home User, then the utility can prompt for a password. The password is the operating system password for the Oracle Home User. The prompt is displayed only if the listener service does not exist, and it needs to be created as part of starting the listener.

##### Arguments

`listener_name`: The listener name, if the default name of `LISTENER` is not used.

##### Usage Notes

To start a listener configured in the `listener.ora` file with a name other than `LISTENER`, include that name.

For example, if the listener name is `tcp_lsnr`, enter:

    lsnrctl START tcp_lsnr

From the Listener Control utility:

    LSNRCTL> START tcp_lsnr

##### Example

    LSNRCTL> START

    Starting /private/sales_group/sales/bin/tnslsnr: please wait...

    TNSLSNR for Linux: Version 18.0.0.0.0
    System parameter file is $ORACLE_HOME/network/admin/listener.ora
    Log messages written to $ORACLE_BASE/diag/tnslsnr/node_name/listener/alert/log.xml
    Listening on: (DESCRIPTION=(ADDRESS=(PROTOCOL=tcp)(HOST=sales-server)(PORT=1521)))

    Connecting to (DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=sales-server)(PORT=1521)))
    STATUS of the LISTENER
    ------------------------
    Alias                     LISTENER
    Version                   TNSLSNR for Linux: Version 18.0.0.0.0
    Start Date                21-JAN-2018 21:50:49
    Uptime                    0 days 0 hr. 0 min. 0 sec
    Trace Level               off
    Security                  ON: Local OS Authetication
    SNMP                      OFF
    Listener Parameter File  $ORACLE_HOME/network/admin/listener.ora
    Listener Log File        $ORACLE_BASE/diag/tnslsnr/node_name/listener/alert/log.xml
    Listening Endpoints Summary...
      (DESCRIPTION=(ADDRESS=(PROTOCOL=tcp)(HOST=sales-server)(PORT=1521)))
    The listener supports no services
    The command completed successfully

**See Also:**

[Oracle Database Administrator’s Reference for Microsoft Windows](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/netrf&id=NTQRF-GUID-0D0DC406-98C7-467A-A5C8-2FBCF5B1A9F8) for information about the Oracle Home User

**Parent topic:** Listener Control Utility Commands

#### 1.5.21 STATUS

The Listener Control utility command `STATUS` displays basic status information about a listener.

##### Purpose

To display basic status information about a listener, including a summary of listener configuration settings, listening protocol addresses, and a summary of services registered with the listener.

**Note:**

You can also obtain the status of the listener through the Oracle Enterprise Manager Cloud Control console.

##### Prerequisites

None

##### Syntax

From the operating system:

    lsnrctl STATUS listener_name

From the Listener Control utility:

    LSNRCTL> STATUS listener_name

##### Arguments

`listener_name`: The listener name, if the default name of `LISTENER` is not used.

##### Usage Notes

The SET DISPLAYMODE command changes the format and level of the detail of the output.

**See Also:**

[Oracle Database Net Services Administrator's Guide](../netag/configuring-and-administering-oracle-net-listener.md) for a complete description of `STATUS` output

##### Example

The following example shows `STATUS` output in the default display mode. The output contains:

- Listener configuration settings

- Listening endpoints summary

- Services summary, which is an abbreviated version of the `SERVICES` command output

<!-- -->

    LSNRCTL> STATUS
    Connecting to (DESCRIPTION=(ADDRESS=(PROTOCOL=ipc)(KEY=net)))
    STATUS of the LISTENER
    ------------------------
    Alias                     LISTENER
    Version                   TNSLSNR for Linux: Version 18.0.0.0.0 -
    Production
    Start Date                12-JAN-2018 12:02:00
    Uptime                    0 days 0 hr. 5 min. 29 sec
    Trace Level               support
    Security                  OFF
    SNMP                      OFF
    Listener Parameter File   /oracle/network/admin/listener.ora
    Listener Log File         /oracle/network/log/listener.log
    Listener Trace File       /oracle/network/trace/listener.trc

    Listening Endpoints Summary...
      (DESCRIPTION=(ADDRESS=(PROTOCOL=ipc)(KEY=net)))
      (DESCRIPTION=(ADDRESS=(PROTOCOL=tcp)(HOST=sales-server)(PORT=1521)))
      (DESCRIPTION=(ADDRESS=(PROTOCOL=tcps)(HOST=sales-server)(PORT=2484)))

    Services Summary...
    Service "sales1.us.example.com" has 1 instance(s).
      Instance "sales", status READY, has 1 handler(s) for this service...
    Service "sales2.us.example.com" has 1 instance(s).
      Instance "sales", status READY, has 2 handler(s) for this service...
    The command completed successfully

**Related Topics**

- SET DISPLAYMODE
- SERVICES

**Parent topic:** Listener Control Utility Commands

#### 1.5.22 STOP

The Listener Control utility command `STOP` stops the named listener.

##### Purpose

To stop the named listener.

##### Prerequisites

The listener must be running.

##### Syntax

From the operating system:

    lsnrctl STOP listener_name


From the Listener Control utility:

    LSNRCTL> STOP listener_name

##### Arguments

`listener_name`: The listener name, if the default name of `LISTENER` is not used.

##### Example

    LSNRCTL> STOP
    Connecting to (ADDRESS=(PROTOCOL=TCP)(HOST=sales-server)(PORT=1521))
    The command completed successfully

**Parent topic:** Listener Control Utility Commands

#### 1.5.23 TRACE

The Listener Control utility command `TRACE` sets tracing for the listener.

##### Purpose

To set tracing for the listener.

##### Syntax

From the operating system:

    lsnrctl trace level listener_name

From the Listener Control utility:

    LSNRCTL> trace level listener_name

##### Arguments

`level`: One of the following trace levels:

- `off` for no trace output

- `user` for user trace information

- `admin` for administration trace information

- `support` for Oracle Support Services trace information

`listener_name`: Specify the listener name, if the default name of `LISTENER` is not used.

##### Usage Notes

This command has the same functionality as the `SET TRC_LEVEL` command.

##### Example

    LSNRCTL> TRACE ADMIN lsnr
    Connecting to (ADDRESS=(PROTOCOL=TCP)(HOST=sales-server)(PORT=1521))
    Opened trace file: /oracle/network/trace/listener.trc
    The command completed successfully

**Parent topic:** Listener Control Utility Commands

#### 1.5.24 VERSION

The Listener Control utility command `VERSION` displays the current version of the Listener Control utility.

##### Purpose

To display the current version of Listener Control utility.

##### Prerequisites

None

##### Syntax

From the operating system:

    lsnrctl VERSION listener_name

From the Listener Control utility:

    LSNRCTL> VERSION listener_name

##### Arguments

`listener_name`: The listener name, if the default name of `LISTENER` is not used.

##### Example

    LSNRCTL> version listener
    Connecting to ADDRESS=(PROTOCOL=TCP)(HOST=sales-server)(PORT=1521))
    TNSLSNR for Linux: Version 19.0.0.0.0
            TNS for Linux: Version 19.0.0.0.0
            Oracle Bequeath NT Protocol Adapter for Linux: Version 19.0.0.0.0
            Unix Domain Socket IPC NT Protocol Adaptor for Linux: Version 19.0.0.0.0
            TCP/IP NT Protocol Adapter for Linux: Version 19.0.0.0.0
    The command completed successfully

**Parent topic:** Listener Control Utility Commands
