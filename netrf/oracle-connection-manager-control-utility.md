## 2 Oracle Connection Manager Control Utility

This chapter describes the commands and syntax of the Oracle Connection Manager Control Utility.

- Command Modes and Syntax
  The Oracle Connection Manager Control Utility (CMCTL) enables you to start up, configure and alter how client connection requests are managed.
- Oracle Connection Manager Control Utility Overview
  You can use Oracle Connection Manager Control utility commands to perform basic management functions on one or more Oracle Connection Manager instances. Additionally, you can view and change parameter settings.
- Oracle Connection Manager Control Utility Commands
  Use the Oracle Connection Manager Control utility commands to manage and configure Oracle Connection Manager instances.

### 2.1 Command Modes and Syntax

The Oracle Connection Manager Control Utility (CMCTL) enables you to start up, configure and alter how client connection requests are managed.

The basic syntax of the Oracle Connection Manager Control utility is as follows:

    cmctl command [argument]

The Oracle Connection Manager Control utility supports the following types of commands:

- Initialization and termination commands such as `STARTUP` and `SHUTDOWN`

- Alter commands such as `SET LOG_LEVEL` and `SET EVENT`

- Display commands, such as `SHOW STATUS` and `SHOW RULES`

- Gateway commands such as `SHOW GATEWAYS` and `RESUME GATEWAYS`

**Note:**

You can use `SET` commands to dynamically alter configuration parameters that control how the listener receives client connections. The changes only remain in effect until Oracle Connection Manager is shut down. You cannot save them to the `cman.ora` file. The one exception is the Oracle Connection Manager password, which you can save using the command `SAVE_PASSWD`.

You can use the Oracle Connection Manager Control utility in command mode, or batch mode.

- Using command mode:

  - From the Oracle Connection Manager Control utility:

    Enter `cmctl` at the command line to obtain the program prompt, and then issue the command:

        cmctl
        CMCTL> command

  - From the operating system:

    Enter the entire command from the operating system command prompt:

        cmctl [command] [argument1 . . . argumentN] [-c instance_name]

    Each command issued this way can have an Oracle Connection Manager instance name appended as an argument. If an Oracle Connection Manager instance name is not provided, then the default instance name is assumed. The default name is `cman_``hostname`. If a password was set in a previous CMCTL session, then you can be prompted for a password. If a password has been set, then to issue commands from an Oracle Connection Manager Control utility session of Oracle Connection Manager, you must enter a password once, at the beginning of the session.

    **Caution:**

    There is an option to specify the password on the command line. However, doing so exposes the password on the screen, and is a potential security risk. Oracle recommends not using the password option (`-p`) on the command line.

- Using batch mode:

  You can combine commands in a standard text file, and then run them as a sequence of commands. To run in batch mode, use the following syntax:

      cmctl @input_file

**See Also:**

[Oracle Database Net Services Administrator's Guide](../netag/understanding-oracle-net-architecture.md) for more information about Oracle Connection Manager architecture

**Parent topic:** Oracle Connection Manager Control Utility

### 2.2 Oracle Connection Manager Control Utility Overview

The Oracle Connection Manager Control utility (CMCTL) enables you to administer [Oracle Connection Manager](glossary.md). You can use Oracle Connection Manager Control utility commands to perform basic management functions on one or more Oracle Connection Manager instances. Additionally, you can view and change parameter settings.

**Parent topic:** Oracle Connection Manager Control Utility

### 2.3 Oracle Connection Manager Control Utility Commands

Use the Oracle Connection Manager Control utility commands to manage and configure Oracle Connection Manager instances.

- ADMINISTER
  The ADMINISTER command can be issued only from the Oracle Connection Manager utility and lets you select the Oracle Connection Manager instance to administer.
- CLOSE CONNECTIONS
  It is an Oracle Connection Manager utility command to terminate connections but Oracle Connection Manager must be running at that time.
- EXIT
  Oracle Connection Manager Control utility command `EXIT` is used to exit from the Oracle Connection Manager utility.
- HELP
- QUIT
- RELOAD
  Reload Oracle Connection Manager Control utility command dynamically rereads parameters and rules.
- RESUME GATEWAYS
- SAVE_PASSWD
- SET
- SET ASO_AUTHENTICATION_FILTER
- SET CONNECTION_STATISTICS
- SET EVENT
- SET IDLE_TIMEOUT
- SET INBOUND_CONNECT_TIMEOUT
- SET LOG_DIRECTORY
- SET LOG_LEVEL
- SET OUTBOUND_CONNECT_TIMEOUT
- SET PASSWORD
- SET SESSION_TIMEOUT
- SET TRACE_DIRECTORY
- SET TRACE_LEVEL
- SHOW
- SHOW ALL
- SHOW CONNECTIONS
- SHOW DEFAULTS
- SHOW EVENTS
- SHOW GATEWAYS
- SHOW PARAMETERS
- SHOW RULES
- SHOW SERVICES
- SHOW STATUS
- SHOW VERSION
- SHUTDOWN
- STARTUP
- SUSPEND GATEWAY

**Parent topic:** Oracle Connection Manager Control Utility

#### 2.3.1 ADMINISTER

The ADMINISTER command can be issued only from the Oracle Connection Manager utility and lets you select the Oracle Connection Manager instance to administer.

##### Purpose

To select an Oracle Connection Manager instance.

##### Prerequisites

None

##### Syntax

From the Oracle Connection Manager Control utility:

`CMCTL> ADMINISTER [-c] ``instance_name`

##### Arguments

instance_name: The instance name of Oracle Connection Manager that you would like to administer. Instances are defined in the `cman.ora` file.

##### Usage Notes

You can issue the `ADMINISTER` command only within the utility. You cannot issue the command from the operating system.

`ADMINISTER` enables you to choose which Oracle Connection Manager instance to administer. To start the Oracle Connection Manager instance, you must issue the STARTUP command.

When you omit the instance name from the command, the instance administered defaults to the local instance.

Use the `-c` option when to administer an instance that is not the local instance.

A password is required only if one was provided at installation time or during a previous session of the Oracle Connection Manager.

##### Example

    CMCTL> ADMINISTER cman_indl040ad
    Enter CMAN password: password
    Current instance cman_indl040ad is already started
    Connections refer to (address=(protocol=TCP)(host=indl040ad)(port=1560)).
    The command completed successfully

**Related Topics**

- STARTUP

**Parent topic:** Oracle Connection Manager Control Utility Commands

#### 2.3.2 CLOSE CONNECTIONS

It is an Oracle Connection Manager utility command to terminate connections but Oracle Connection Manager must be running at that time.

##### Purpose

To terminate connections, using specific qualifiers to select connections.

##### Prerequisites

Oracle Connection Manager must be running.

##### Syntax

From the operating system:

    cmctl CLOSE CONNECTIONS [in state] [gt time] [from source] [to destination]
    [for service] [using gateway_process_id] [connect_identifier_list]
    [-c cman_name]

From the Oracle Connection Manager Control utility:

    CMCTL> CLOSE CONNECTIONS [in state] [gt time] [from source] [to destination]
    [for service] [using gateway_process_id] [connect_identifier_list

##### Arguments

state`:` One of the following values to specify the connection state:` `

- `idle`: Connections that are inactive in the established state.

- `connecting`: Connections that are in the process of connecting.

- `established`: Connections that are connected and are transferring data.

- `terminating`: Connections that are disconnecting.

If no state is specified, then `CLOSE CONNECTIONS` defaults to all possible states. If the time qualifier is included under these conditions, then the time specified is the amount of time that has elapsed since a client initiated a connection.

time: The time format. Use the following format to specify connections greater than the time indicated:

`gt[``hh``:``mm``:]``ss`

source: The source address. Use one of the following formats to specify the source address:

- `from ``IP`

- `from ``hostname `

- `from ``subnet`

destination: The destination address. Use one of the following formats to specify the destination address:

- `to ``IP`

- `to ``hostname `

- `to ``subnet`

service: The service name. Use the `service_name` parameter to specify the service, such as `sales.us.example.com`.

gateway_process_id: The gateway process identifier is a number. Use this number to specify connections that are proxied by the gateway process indicated. To determine the gateway process identifier, use the Oracle Connection Manager control utility `show gateways` command.

connect_identifier_list: The connection identifiers. Use a space between multiple connection identifiers in a list.

##### Usage Notes

Because the `CLOSE` `CONNECTIONS` command terminates connections, it might generate error messages on both client and server sides.

The `IDLE` state qualifier always requires a time qualifier.

Issuing `CLOSE CONNECTIONS` without an argument closes all connections.

##### Examples

The following example shuts down connections in any state. The elapsed time of the connection must be greater than 1 hour and 30 minutes. The connection source is the specified subnet, and the destination is the specified host name.

`CMCTL> CLOSE CONNECTIONS gt 1:30:00 from 192.0.2.32/24 to host1`

The following example shuts down those connections proxied by gateway process `0` that have been in the idle state more than 30 minutes:

`CMCTL> CLOSE idle CONNECTIONS gt 30:00 using 0`

The following example shuts down connections that are connected to the service `sales.us.example.com`:

`CMCTL> CLOSE established CONNECTIONS for sales.us.example.com`

**Parent topic:** Oracle Connection Manager Control Utility Commands

#### 2.3.3 EXIT

Oracle Connection Manager Control utility command `EXIT` is used to exit from the Oracle Connection Manager utility.

##### Purpose

To exit from the Oracle Connection Manager Control utility.

##### Prerequisites

None

##### Syntax

From the operating system:

`cmctl EXIT [-c ``instance_name``] `

From the Oracle Connection Manager Control utility:

`CMCTL> EXIT`

##### Usage Notes

This command is identical to the `QUIT` command.

Example 2-1 Example

`CMCTL> EXIT`

**Parent topic:** Oracle Connection Manager Control Utility Commands

#### 2.3.4 HELP

##### Purpose

To provide a list of all commands for the Oracle Connection Manager Control utility or to provide help with the syntax of a particular command.

##### Prerequisites

None

##### Syntax

From the operating system:

    cmctl HELP [command] [-c instance_name]

From the Oracle Connection Manager Control utility:

    CMCTL> HELP [command]

##### Arguments

command: Specify a `HELP` command. Commands are shown in the following sample output.

When you enter a command as an argument to `HELP`, the Oracle Connection Manager Control utility displays information about how to use the command. When you enter `HELP` without an argument, the Oracle Connection Manager Control utility displays a list of all the commands.

##### Example

    CMCTL> HELP
    The following operations are available
    An asterisk (*) denotes a modifier or extended command:

    administer      close*          exit            reload
    resume*         save_passwd     set*            show*
    shutdown        sleep           startup         suspend*
    show_version    quit

**Parent topic:** Oracle Connection Manager Control Utility Commands

#### 2.3.5 QUIT

##### Purpose

To exit the Oracle Connection Manager Control utility and return to the operating system prompt.

##### Prerequisites

None

##### Syntax

From the operating system:

    cmctl QUIT

From the Oracle Connection Manager Control utility:

    CMCTL> QUIT

##### Usage Notes

This command is identical to the `EXIT` command.

##### Example

    CMCTL> QUIT

**Parent topic:** Oracle Connection Manager Control Utility Commands

#### 2.3.6 RELOAD

Reload Oracle Connection Manager Control utility command dynamically rereads parameters and rules.

##### Purpose

To dynamically reread parameters and rules.

##### Prerequisites

Oracle Connection Manager must be running.

##### Syntax

From the operating system:

    cmctl RELOAD [-with_ha] [-c instance_name]

From the Oracle Connection Manager Control utility:

    CMCTL> RELOAD [-with_ha]

##### Arguments

`-with_ha`: It is used to reload `cman.ora` without dropping registrations

##### Usage Notes

Configuration information modified using the `RELOAD` command applies only to new connections. Existing connections are unaffected. The `SET RELOAD` command restores configurations set in `cman.ora`, and override the `SET` command.

`RELOAD` reregisters gateways with the Oracle Connection Manager listener during which some new connections might be refused until the registration process is complete.

`-with_ha` option can be used with `RELOAD` to not drop registrations, thus providing high service availability during reload.

##### Example

    CMCTL> RELOAD
    The command completed successfully

**Parent topic:** Oracle Connection Manager Control Utility Commands

#### 2.3.7 RESUME GATEWAYS

##### Purpose

To resume gateway processes that have been suspended.

##### Prerequisites

Oracle Connection Manager must be running.

##### Syntax

From the operating system:

    cmctl RESUME GATEWAYS [gateway_process_id] [cman_name]

From the Oracle Connection Manager Control utility:

    CMCTL> RESUME GATEWAYS [gateway_process_id]

##### Arguments

gateway_process_id: One or more gateway processes to reopen. Separate multiple gateway processes using a space between the process identifiers.

##### Usage Notes

Issuing `RESUME GATEWAYS` without an argument reopens all gateway processes that have been closed.

##### Example

    CMCTL> RESUME GATEWAYS 1
    The command completed successfully

**Parent topic:** Oracle Connection Manager Control Utility Commands

#### 2.3.8 SAVE_PASSWD

##### Purpose

To save the current password to the `cman.ora` file, the configuration file for Oracle Connection Manager.

##### Prerequisites

Oracle Connection Manager must be running.

##### Syntax

From the operating system:

    cmctl SAVE_PASSWD [-c instance_name]

From the Oracle Connection Manager Control utility:

    CMCTL> SAVE_PASSWD

##### Usage Notes

If you run this command, then the next session of Oracle Connection Manager uses the password. The password is stored in an encrypted format in the `cman.ora` file.

##### Example

    CMCTL> SAVE_PASSWD

**Parent topic:** Oracle Connection Manager Control Utility Commands

#### 2.3.9 SET

##### Purpose

To display a list of parameters that can be modified using this command.

##### Prerequisites

None

##### Syntax

From the operating system:

    cmctl SET

From the Oracle Connection Manager Control utility:

    CMCTL> SET

##### Example

    CMCTL> SET
    The following operations are available after set
    An asterisk (*) denotes a modifier or extended command:

    aso_authentication_filter     outbound_connect_timeout
    connection_statistics         password
    event                         session_timeout
    idle_timeout                  trace_directory
    inbound_connect_timeout        trace_level
    log_directory
    log_level

**Parent topic:** Oracle Connection Manager Control Utility Commands

#### 2.3.10 SET ASO_AUTHENTICATION_FILTER

##### Purpose

To indicate whether the client must use Oracle Database security to authenticate.

##### Prerequisites

Oracle Connection Manager must be running.

##### Syntax

From the operating system:

    cmctl SET ASO_AUTHENTICATION_FILTER {on | off}[-c instance_name]

From the Oracle Connection Manager Control utility:

    CMCTL> SET ASO_AUTHENTICATION_FILTER {on | off}

##### Arguments

`on`: To reject connections that are not using Secure Network Service (SNS) to perform client authentication. SNS is part of Oracle Database security.

`off`: To specify whether no authentication is required for client connections. This is the default.

##### Example

    CMCTL> set aso_authentication_filter ON
    CMAN_user.us.example.com parameter aso_authentication_filter set to ON
    The command completed successfully

**Parent topic:** Oracle Connection Manager Control Utility Commands

#### 2.3.11 SET CONNECTION_STATISTICS

##### Purpose

To specify whether gateway processes collect connection statistics.

##### Prerequisites

Oracle Connection Manager must be running.

##### Syntax

From the operating system:

    cmctl SET CONNECTION_STATISTICS {yes | no}[-c instance_name]

From the Oracle Connection Manager Control utility:

    CMCTL> SET CONNECTION_STATISTICS {yes | no}

##### Arguments

`yes`: To have gateway processes collect connection statistics.

`no`: To not have gateway processes collect connection statistics. This is the default.

##### Usage Notes

If `SET CONNECTION_STATISTICS` is set to `yes`, then you can obtain statistics by issuing the SHOW CONNECTIONS command.

##### Example

    CMCTL> set connection_statistics ON
    CMAN_user.us.example.com parameter connection_statistics set to ON
    The command completed successfully

**Parent topic:** Oracle Connection Manager Control Utility Commands

#### 2.3.12 SET EVENT

##### Purpose

To log information for a particular event.

##### Syntax

From the operating system:

    cmctl SET EVENT event_group [-c instance_name]

From the Oracle Connection Manager Control utility:

    CMCTL> SET EVENT event_group {on | off}

##### Arguments

event_group: Specify one of the following event groups:

- `init_and_term`: Initialization and termination event group.

- `memory_ops`: Memory operations event group.

- `conn_hdlg`: Connection handling event group.

- `proc_mgmt`: Process management event group.

- `reg_and_load`: Registration and load update event group.

- `wake_up`: Events related to Connection Manager Administration (CMADMIN) wakeup queue event group.

- `timer`: Gateway timeouts event group.

- `cmd_proc`: Command processing event group.

- `relay`: Events associated with connection control blocks event group.

`on`: To turn an event group on.

`off`: To turn an event group off.

##### Usage Notes

The `SET EVENT` command accepts only one argument. To log multiple events, you must issue the command for each event separately.

##### Example

    CMCTL> set event memory_ops off
    cman11 event memory_ops set to OFF.
    The command completed successfully

**Parent topic:** Oracle Connection Manager Control Utility Commands

#### 2.3.13 SET IDLE_TIMEOUT

##### Purpose

To specify the amount of time a client can be idle without transmitting data.

##### Prerequisites

Oracle Connection Manager must be running.

##### Syntax

From the operating system:

    cmctl SET IDLE_TIMEOUT [time] [-c instance_name]

From the From the Oracle Connection Manager Control utility:

    CMCTL> SET IDLE_TIMEOUT [time]

##### Arguments

time: Specify the idle timeout in seconds. The default is 0 (zero), which disables this feature.

##### Example

    CMCTL> SET IDLE_TIMEOUT 30
    CMAN_user.us.example.com parameter idle_timeout set to 30
    The command completed successfully

**Parent topic:** Oracle Connection Manager Control Utility Commands

#### 2.3.14 SET INBOUND_CONNECT_TIMEOUT

##### Purpose

To specify the maximum amount of time the Oracle Connection Manager listener waits for a valid connection request from the client before timing out.

##### Prerequisites

Oracle Connection Manager must be running.

##### Syntax

From the operating system:

    cmctl SET INBOUND_CONNECT_TIMEOUT [time] [-c instance_name]

From the Oracle Connection Manager Control utility:

    CMCTL> SET INBOUND_CONNECT_TIMEOUT [time]

##### Arguments

time: The inbound connect timeout in seconds. The default is 0 (zero), which disables this feature.

##### Example

    CMCTL> SET INBOUND_CONNECT_TIMEOUT 30
    CMAN_user.us.example.com parameter inbound_connect_timeout set to 30
    The command completed successfully

**Parent topic:** Oracle Connection Manager Control Utility Commands

#### 2.3.15 SET LOG_DIRECTORY

**Note:**

This command works only if Automatic Diagnostic Repository (ADR) is not enabled. The default is for ADR to be enabled, and use the log directory `ORACLE_HOME/log`.

##### Purpose

To designate where the log files for Oracle Connection Manager are written.

##### Prerequisites

Oracle Connection Manager must be running.

##### Syntax

From the operating system:

    cmctl SET LOG_DIRECTORY [directory_path] [-c instance_name]

From the Oracle Connection Manager Control utility:

    CMCTL> SET LOG_DIRECTORY [directory_path]

##### Arguments

directory_path: The location of the log directory. The default path is as follows:

- Linux and UNIX:

      ORACLE_HOME/network/log directory

- Microsoft Windows:

      ORACLE_HOME\network\log directory

##### Usage Notes

Use the SHOW PARAMETERS command to determine the location of the log files.

##### Example

    CMCTL>
    SET LOG_DIRECTORY /disk1/user_cman_test/oracle/network/admin

    CMAN_user.us.example.com parameter log_directory set to
    /disk1/user_cman_test/oracle/network/admin

    The command completed successfully

**Parent topic:** Oracle Connection Manager Control Utility Commands

#### 2.3.16 SET LOG_LEVEL

##### Purpose

To set the log level for Oracle Connection Manager.

##### Prerequisites

Oracle Connection Manager must be running.

##### Syntax

From the operating system:

    cmctl SET LOG_LEVEL [level] [-c instance_name]

From the Oracle Connection Manager Control utility:

    CMCTL> SET LOG_LEVEL [level]

##### Arguments

level: Specify one of the following log levels:

- `off`: No logging.

- `user`: User log information.

- `admin`: Administrative log information.

- `support`: Oracle Support Services log information. This is the default.

##### Usage Notes

Specify `off` to capture the minimum amount of log information. Specify `support` to capture the maximum amount.

##### Example

    CMCTL> SET LOG_LEVEL SUPPORT
    CMAN_user.us.example.com parameter log_level set to SUPPORT
    The command completed successfully

**Parent topic:** Oracle Connection Manager Control Utility Commands

#### 2.3.17 SET OUTBOUND_CONNECT_TIMEOUT

##### Purpose

To specify the maximum amount of time the Oracle Connection Manager instance waits for a valid connection with the server before timing out.

##### Prerequisites

Oracle Connection Manager must be running.

##### Syntax

From the operating system:

    cmctl SET OUTBOUND_CONNECT_TIMEOUT [time] [-c instance_name]

From the From the Oracle Connection Manager Control utility:

    CMCTL> SET OUTBOUND_CONNECT_TIMEOUT [time]

##### Arguments

time: The outbound connect timeout in seconds. The default is `0`.

##### Example

    CMCTL> SET OUTBOUND_CONNECT_TIMEOUT 30
    CMAN_user.us.example.com parameter outbound_connect_timeout set to 30
    The command completed successfully

**Parent topic:** Oracle Connection Manager Control Utility Commands

#### 2.3.18 SET PASSWORD

##### Purpose

To assign a password to the Oracle Connection Manager instance.

##### Prerequisites

Oracle Connection Manager must be running.

##### Syntax

From the operating system:

    cmctl SET PASSWORD

From the Oracle Connection Manager Control utility:

    CMCTL> SET PASSWORD

##### Arguments

None.

##### Usage Notes

This command may be used either to set a password for the first time or to change an existing one.

This command does not save the password to `cman.ora`. As a result the password is valid only for the current session. To save the password after you have set it, run the SAVE_PASSWD command.

##### Example

    CMCTL> SET PASSWORD

    Enter Old password: old_password
    Enter New password: new_password
    Reenter New password: new_password

    The command completed successfully

**Parent topic:** Oracle Connection Manager Control Utility Commands

#### 2.3.19 SET SESSION_TIMEOUT

##### Purpose

To specify the maximum amount of time for a session of Oracle Connection Manager.

##### Prerequisites

Oracle Connection Manager must be running.

##### Syntax

From the operating system:

    cmctl SET SESSION_TIMEOUT [time] [-c  instance_name]

From the Oracle Connection Manager Control utility:

    CMCTL> SET SESSION_TIMEOUT [time]

##### Arguments

time: The session timeout in seconds. The default is 0 (zero), which disables this feature.

##### Example

    CMCTL> SET SESSION_TIMEOUT 60
    CMAN_user.us.example.com parameter session_timeout set to 60
    The command completed successfully

**Parent topic:** Oracle Connection Manager Control Utility Commands

#### 2.3.20 SET TRACE_DIRECTORY

**Note:**

This command works only if Automatic Diagnostic Repository (ADR) is not enabled. The default is for ADR to be enabled.

##### Purpose

To designate where the trace files for an Oracle Connection Manager instance are written.

##### Prerequisites

Oracle Connection Manager must be running.

##### Syntax

From the operating system:

    cmctl SET TRACE_DIRECTORY [directory_path] [-c instance_name]

From the Oracle Connection Manager Control utility:

    CMCTL> SET TRACE_DIRECTORY [directory_path]

##### Arguments

directory_path: The location of the trace directory. The default path is `ORACLE_HOME/network/trace`.

##### Usage Notes

Use the SHOW PARAMETERS command to determine the location of the trace files.

##### Example

    CMCTL> SET TRACE_DIRECTORY /disk1/mpurayat_newtest/oracle/network/trace
    cman1 parameter trace_directory set to /disk1/mpurayat_newtest/oracle/network
    /trace
    The command completed successfully

**Parent topic:** Oracle Connection Manager Control Utility Commands

#### 2.3.21 SET TRACE_LEVEL

##### Purpose

To set the trace level for an Oracle Connection Manager instance.

##### Prerequisites

Oracle Connection Manager must be running.

##### Syntax

From the operating system:

    cmctl SET TRACE_LEVEL [level] [-c instance_name]

From the Oracle Connection Manager Control utility:

    CMCTL> SET TRACE_LEVEL [level]

##### Arguments

level: Specify one of the following log levels:

- `off`: No tracing. This is the default.

- `user`: User trace information.

- `admin`: Administrative trace information.

- `support`: Oracle Support Services trace information.

##### Usage Notes

Specify `off` to capture the minimum amount of trace information. Specify `support` to capture the maximum amount.

Use the SHOW PARAMETERS command to determine the current trace level.

##### Example

    CMCTL> SET TRACE_LEVEL USER
    CMAN_user.us.example.com parameter trace_level set to USER
    The command completed successfully

**Parent topic:** Oracle Connection Manager Control Utility Commands

#### 2.3.22 SHOW

##### Purpose

To display a list of parameters that may be used as arguments for this command. Entering one of these parameters with the command displays the parameter value or values.

##### Prerequisites

None

##### Syntax

From the operating system:

    cmctl SHOW [-c instance_name]

From the Oracle Connection Manager Control utility:

    CMCTL> SHOW

##### Example

    CMCTL> SHOW
    The following operations are available after show
    An asterisk (*) denotes a modifier or extended command:

    all             gateways        status
    connections     parameters      version
    defaults        rules
    events          services

**Parent topic:** Oracle Connection Manager Control Utility Commands

#### 2.3.23 SHOW ALL

##### Purpose

To combine and display output from the `SHOW PARAMETERS` and `SHOW RULES` commands.

##### Prerequisites

Oracle Connection Manager must be running.

##### Syntax

From the operating system:

    cmctl SHOW ALL [-c instance_name]

From the Oracle Connection Manager Control utility:

    CMCTL> SHOW ALL

##### Example

    CMCTL> SHOW ALL
    listener_address          |
    (address=(protocol=tcp)(host=users.us.example.com)(port=1630))
    aso_authentication_filter |   OFF
    connection_statistics     |   OFF
    event_group               |   OFF
    log_directory             | /disk1/user_cman_test/oracle/network/log/
    log_level                 | SUPPORT
    max_connections           |   256
    idle_timeout              |     0
    inbound_connect_timeout   |     0
    session_timeout           |     0
    outbound_connect_timeout  |     0
    max_gateway_processes     |    16
    min_gateway_processes     |     2
    max_cmctl_sessions        |     4
    password                  |   OFF
    trace_directory           | /disk1/user_cman_test/oracle/network/trace/
    trace_level               |   OFF
    trace_timestamp           |   OFF
    trace_filelen             |     0
    trace_fileno              |     0
    (rule_list=
     (rule=
      (src=*)
      (dst=*)
      (srv=*)
      (act=accept)
     )
    )
    The command completed successfully

**Parent topic:** Oracle Connection Manager Control Utility Commands

#### 2.3.24 SHOW CONNECTIONS

##### Purpose

To display information about specific connections or all connections.

##### Prerequisites

Oracle Connection Manager must be running.

##### Syntax

From the operating system:

    cmctl SHOW CONNECTIONS [information] [in state] [gt time] [from source]
    [to destination] [for service] [using gateway_process_id]
    [connect_identifier_list] [-c instance_name]

From the Oracle Connection Manager Control utility:

    CMCTL> SHOW CONNECTIONS [information][in state] [gt time] [from source]
    [to destination] [for service] [using gateway_process_id]
    [connect_identifier_list]

##### Arguments

information: Specify one of the following values to display information about connections. Information categories include connection identifier, source, destination, service, current state, total idle time, and total elapsed time.

- `count`: The total number of connections that meet the criteria specified by the other qualifiers. This is the default.

- `detail`: All information about connections specified by the other qualifiers.

state: Specify one of the following values to specify the connection state:` `

- `idle`: Connections that are inactive in the established state.

- `connecting`: Connections that are in the process of connecting.

- `established`: Connections that are connected and are transferring data.

- `terminating`: Connections that are disconnecting.

If no state is specified, then `SHOW CONNECTIONS` defaults to all possible states. If the time qualifier is included under these conditions, then the time specified is the amount of time that has elapsed since a client initiated a connection.

**Note:**

This argument is not supported with Oracle Connection Manager in Traffic Director mode.

time: Use the following format to specify connections greater than the time indicated:

`gt[``hh``:``mm``:]``ss`

**Note:**

This argument is not supported with Oracle Connection Manager in Traffic Director mode.

source: Specify one of the following formats to specify the source address:

- `from ``IP`

- `from ``hostname `

- `from ``subnet`

destination: Specify one of the following formats to specify the destination address:

- `to ``IP`

- `to ``hostname `

- `to ``subnet`

service: Use the service_name format to request a service:

gateway_process_id: Use the following format to specify connections that are proxied by the gateway process indicated:

    using gateway_process_id

connect_identifier_list: Separate multiple connection identifiers using a space.

##### Usage Notes

Connections are sorted by gateway process identifier and connection identifier, in ascending order.

Issuing `SHOW CONNECTIONS` without an argument displays all connections.

##### Examples

The following command displays a detailed description of connections in any state. The elapsed time of the connection must be greater than 1 hour and 30 minutes. The connection source is the specified subnet, and the destination the specified host name.

    CMCTL> SHOW CONNECTIONS gt 1:30:00 from 192.0.2.32/24 to host1

The following command displays the number of connections proxied by Oracle Connection Manager using the gateway process identifier 0 that have been in the idle state more than 30 minutes:

    CMCTL> SHOW idle CONNECTIONS count gt 30:00 using 0

The following command displays a detailed description of connections that are connected to the service `sales.us.example.com`:

    CMCTL> SHOW established CONNECTIONS detail for sales.us.example.com

##### Additional Statistics Shown in Traffic Director Mode

Each connection to Oracle Connection Manager in Traffic Director mode displays these additional statistics:

- `Source Host Name`: Host name of the client connection.

- `Source Process Id`: Process Id of the connected client.

- `Source Program Name`: The name of the connected client program.

- `Destination Hostname`: Host name of the database server to which the client is connected through Oracle Connection Manager.

- `State`: State of the inbound connection with one of the following values

  - `THREAD WAIT`: Connection is waiting for a worker thread, not seen in dedicated threads mode

  - `ACTIVE`: Connection is transferring data, occupying the thread

  - `IDLE`: Connection is established but inactive, can still occupy the thread if `tdm_bind_thread=true` in `cman.ora`

- `Idle time`: Cumulative time in`µs` the connection is in`IDLE` state.

- `Thread Wait time`: Cumulative time in`µs` the connection is in `THREAD WAIT` state. It is always `0` in dedicated threads mode.

- `Active time`: Cumulative time in µs the connection is in `ACTIVE` state.

- `PRCP State`: State of the inbound connection with respect to the Proxy Resident Connection Pool (`PRCP`) and can be one of the following values

  - `WAIT`: Connection is waiting for a session from the `PRCP`

  - `CHECKED-OUT`: Connection is holding an outbound session from `PRCP` but not making any OCI calls

  - `ACTIVE`: Connection is holding an outbound session from `PRCP` and busy with OCI calls

  - `CHECKED-IN`: Connection released the `CHECKED-OUT` session back to the `PRCP`

  - `NO STATE`: Clients to a service without a configured `PRCP` configured have this state

- `PRCP Wait time`, `PRCP Checked-out time`, and `PRCP Active time`: Cumulative time in`µs` the connection is in `PRCP WAIT`, `CHECKED-OUT`, and `ACTIVE` states. All these three states are zero in case of non-`PRCP` service.

- `Total Session Gets`: Total count of`PRCP` session get requests from this connection. It is always `1` if `PRCP` is not configured.

- `Session Get Hits`: Number of times a session is found existing in the `PRCP` out of all the requests. It is always `0` if `PRCP` is not configured.

**Parent topic:** Oracle Connection Manager Control Utility Commands

#### 2.3.25 SHOW DEFAULTS

##### Purpose

To display default parameter settings.

##### Prerequisites

Oracle Connection Manager must be running.

##### Syntax

From the operating system:

    cmctl SHOW DEFAULTS [-c instance_name]

From the Oracle Connection Manager Control utility:

    CMCTL> SHOW DEFAULTS

##### Example

    CMCTL> SHOW DEFAULTS
    listener_address          |
    (address=(protocol=tcp)(host=users.us.example.com)(port=1521))
    aso_authentication_filter |   OFF
    connection_statistics     |   OFF
    event_group               |   OFF
    log_directory             | /disk1/user_cman_test/oracle/network/log/
    log_level                 | SUPPORT
    max_connections           |   256
    idle_timeout              |     0
    inbound_connect_timeout   |     0
    session_timeout           |     0
    outbound_connect_timeout  |     0
    max_gateway_processes     |    16
    min_gateway_processes     |     2
    max_cmctl_sessions        |     4
    password                  |   OFF
    trace_directory           | /disk1/user_cman_test/oracle/network/trace/
    trace_level               |   OFF
    trace_timestamp           |   OFF
    trace_filelen             |     0
    trace_fileno              |     0
    The command completed successfully

**Parent topic:** Oracle Connection Manager Control Utility Commands

#### 2.3.26 SHOW EVENTS

##### Purpose

To display the events that are in operation.

##### Prerequisites

Oracle Connection Manager must be running.

##### Syntax

From the operating system:

    cmctl SHOW EVENTS [-c instance_name]

From the Oracle Connection Manager Control utility:

    CMCTL> SHOW EVENTS

##### Example

    CMCTL> SHOW EVENTS
    Event Groups:
    memory_ops
    The command completed successfully

**Parent topic:** Oracle Connection Manager Control Utility Commands

#### 2.3.27 SHOW GATEWAYS

##### Purpose

To display the current status of a specific gateway process or processes. Statistics displayed include number of active connections, number of peak active connections, total number of connections handled, and number of connections refused.

##### Prerequisites

Oracle Connection Manager must be running.

##### Syntax

From the operating system:

    cmctl SHOW GATEWAYS [gateway] [-c instance_name]

From the Oracle Connection Manager Control utility:

    CMCTL> SHOW GATEWAYS [gateway]

##### Arguments

gateway: The identifier of the gateway or gateways whose status to display.

Issuing `SHOW GATEWAYS` without an argument displays the status of all gateway processes.

##### Usage Notes

To display multiple gateways, use a space to separate the identifiers when entering the command.

##### Example

    CMCTL> SHOW GATEWAYS 1
    Gateway ID                     1
    Gateway state                  READY
    Number of active connections   0
    Peak active connections        0
    Total connections              0
    Total connections refused      0
    The command completed successfully

**Parent topic:** Oracle Connection Manager Control Utility Commands

#### 2.3.28 SHOW PARAMETERS

##### Purpose

To display current parameter settings for an instance.

##### Prerequisites

Oracle Connection Manager must be running.

##### Syntax

From the operating system:

    cmctl SHOW PARAMETERS [-c instance_name]

From the Oracle Connection Manager Control utility:

    CMCTL> SHOW PARAMETERS

##### Usage Notes

Several configuration parameters can be dynamically modified using the SET command. Therefore, the information that SHOW PARAMETERS displays might be different from what appears in the `cman.ora` file.

##### Example

    CMCTL> SHOW PARAMETERS
    listener_address          |
    (address=(protocol=tcp)(host=users.us.example.com)(port=1630))
    aso_authentication_filter |    ON
    connection_statistics     |    ON
    event_group               | (memory_ops)
    log_directory             | /disk1/user_cman_test/oracle/network/log/
    log_level                 | SUPPORT
    max_connections           |   256
    idle_timeout              |     0
    inbound_connect_timeout   |     0
    session_timeout           |     0
    outbound_connect_timeout  |     0
    max_gateway_processes     |    16
    min_gateway_processes     |     2
    max_cmctl_sessions        |     4
    password                  |   OFF
    trace_directory           | /disk1/user_cman_test/oracle/network/trace/
    trace_level               | SUPPORT
    trace_timestamp           |   OFF
    trace_filelen             |     0
    trace_fileno              |     0
    The command completed successfully

**Parent topic:** Oracle Connection Manager Control Utility Commands

#### 2.3.29 SHOW RULES

##### Purpose

To display the access control list currently used by the instance.

##### Prerequisites

Oracle Connection Manager must be running.

##### Syntax

From the operating system:

    cmctl SHOW RULES [-c instance_name]

From the Oracle Connection Manager Control utility:

    CMCTL> SHOW RULES

##### Usage Notes

You can update the rules list by issuing the RELOAD command.

##### Example

    CMCTL> SHOW RULES
    Number of filtering rules currently in effect: 5
    (rule_list=
      (rule=
        (src=usunnae12)
        (dst=usunnae13)
        (srv=*)
        (act=accept)
        (action_list=(mit=120)(mct=1800)(conn_stats=on)(aut=off))
      )
      (rule=
        (src=usunnae12)
        (dst=usunnae14)
        (srv=service2)
        (act=accept)
      )
      (rule=
        (src=*)
        (dst=usunnae15)
        (srv=*)
        (act=accept)
        (action_list=(mit=120)(mct=3000)(moct=200)(aut=on))
      )

      (rule=
        (src=*)
        (dst=usunnae16)
        (srv=*)
        (act=reject)
        (action_list=(moct=20)(aut=on))
      )

      (rule=
        (src=users.us.example.com)
        (dst=users.us.example.com)
        (srv=cmon)
        (act=accept)
        (action_list=(mit=100)(mct=1130)(moct=200)(aut=on))
      )
    )

**Parent topic:** Oracle Connection Manager Control Utility Commands

#### 2.3.30 SHOW SERVICES

##### Purpose

To display comprehensive information about the Oracle Connection Manager instance. The information displayed includes number of handlers for gateway and CMADMIN processes, listening ports of handlers, and number of connections, both refused and current.

##### Prerequisites

Oracle Connection Manager must be running.

##### Syntax

From the operating system:

    cmctl SHOW SERVICES [-c instance_name]

From the Oracle Connection Manager Control utility:

    CMCTL> SHOW SERVICES

##### Example

    CMCTL> SHOW SERVICES
    Services Summary...
    Proxy service "cmgw" has 1 instance(s).
      Instance "cman", status READY, has 2 handler(s) for this service...
        Handler(s):
          "cmgw001" established:0 refused:0 current:0 max:256 state:ready
             <machine: user-sun, pid: 29190>
             (ADDRESS=(PROTOCOL=tcp)(HOST=user-sun)(PORT=33175))
          "cmgw000" established:0 refused:0 current:0 max:256 state:ready
             <machine: user-sun, pid: 29188>
             (ADDRESS=(PROTOCOL=tcp)(HOST=user-sun)(PORT=33174))
    Service "cmon" has 1 instance(s).
      Instance "cman", status READY, has 1 handler(s) for this service...
        Handler(s):
          "cmon" established:0 refused:0 current:0 max:4 state:ready
             <machine: user-sun, pid: 29184>
             (ADDRESS=(PROTOCOL=tcp)(HOST=users)(PORT=33168))
    The command completed successfully

**Parent topic:** Oracle Connection Manager Control Utility Commands

#### 2.3.31 SHOW STATUS

##### Purpose

To display basic information about the instance, including version, start time, and current statistics.

##### Prerequisites

Oracle Connection Manager must be running.

##### Syntax

From the operating system:

    cmctl SHOW STATUS

From the Oracle Connection Manager Control utility:

    CMCTL> SHOW STATUS

##### Example

    CMCTL> SHOW STATUS
    Status of the Instance
    ----------------------
    Instance name             CMAN_user.us.example.com
    Version                   CMAN for Linux: Version 18.0.0.0.0
    Start date                12-JAN-2018 14:50:35
    Uptime                    0 days 1 hr. 25 min. 24 sec
    Num of gateways started   2
    Average Load level        0
    Log Level                 SUPPORT
    Trace Level               OFF
    Instance Config file      /disk1/user_cman_test/oracle/network/admin/cman.ora
    Instance Log directory    /disk1/user_cman_test/oracle/network/log/
    Instance Trace directory  /disk1/user_cman_test/oracle/network/trace/
    The command completed successfully

**Parent topic:** Oracle Connection Manager Control Utility Commands

#### 2.3.32 SHOW VERSION

##### Purpose

To display the current version and name of the Oracle Connection Manager Control utility.

##### Prerequisites

None

##### Syntax

From the operating system:

    cmctl SHOW VERSION [-c instance_name]

From the Oracle Connection Manager Control utility:

    CMCTL> SHOW VERSION

##### Examples

    CMCTL> SHOW VERSION
    CMAN for Linux: Version 18.0.0.0.0
    The command completed successfully

**Parent topic:** Oracle Connection Manager Control Utility Commands

#### 2.3.33 SHUTDOWN

##### Purpose

To shut down specific gateway processes or the entire Oracle Connection Manager instance.

##### Prerequisites

Oracle Connection Manager must be running.

##### Syntax

From the operating system:

    cmctl SHUTDOWN [gateways gateway] [normal | abort] [-c instance_name]

From the Oracle Connection Manager Control utility:

    CMCTL> SHUTDOWN [gateways gateway] {normal | abort}

##### Arguments

`gateways`: To shut down a specific gateway.

`normal`: To reject new connections and terminate after existing connections close. This is the default.

`abort`: To shut down Oracle Connection Manager immediately, and close all open connections.

To specify more than one gateway, separate gateways using a space.

##### Usage Notes

Issuing `SHUTDOWN` without an argument shuts down all gateways.

##### Example

    CMCTL> SHUTDOWN GATEWAYS 0
    The command completed successfully

**Parent topic:** Oracle Connection Manager Control Utility Commands

#### 2.3.34 STARTUP

##### Purpose

To start Oracle Connection Manager.

##### Prerequisites

Another Oracle Connection Manager instance configured with the same protocol address must not be running.

##### Syntax

From the operating system:

    cmctl STARTUP [-c instance_name]

From the Oracle Connection Manager Control utility:

    CMCTL> STARTUP

##### Usage Notes

Before issuing this command, you must use the `ADMINISTER` command to select an instance to start.

Issuing this command starts all instance components, which are the listener, CMADMIN, and the gateway processes. The command fails if any one of these components is already running.

The utility may prompt for a password if Oracle Connection Manager was installed with secure installation option.

##### Example

    CMCTL> STARTUP
    Starting Oracle Connection Manager instance cman_1. Please wait...
    CMAN for Linux: Version 18.0.0.0.0
    Status of the Instance
    ----------------------
    Instance name             cman_1
    Version                   CMAN for Linux: Version 18.0.0.0.0
    Start date                22-JAN-2018 01:16:55
    Uptime                    0 days 0 hr. 0 min. 9 sec
    Num of gateways started   8
    Average Load level        0
    Log Level                 SUPPORT
    Trace Level               OFF
    Instance Config file      $ORACLE_HOME/network/admin/cman.ora
    Instance Log directory    $ORACLE_BASE/diag/netcman/node_name/cman_1/alert
    Instance Trace directory  $ORACLE_BASE/diag/netcman/node_name/cman_1/trace
    The command completed successfully

**Parent topic:** Oracle Connection Manager Control Utility Commands

#### 2.3.35 SUSPEND GATEWAY

##### Purpose

To specify which gateway processes will no longer accept new client connections.

##### Prerequisites

Oracle Connection Manager must be running.

##### Syntax

From the operating system:

    cmctl SUSPEND GATEWAY [gateway_process_id] [-c instance_name]

From the Oracle Connection Manager Control utility:

    CMCTL> SUSPEND GATEWAY [gateway_process_id]

##### Arguments

gateway_process_id: The gateway process that will no longer accept new connections. Specify multiple gateway processes by putting a space between entries.

Issuing `SUSPEND GATEWAY` without an argument suspends all gateway processes.

##### Usage Notes

Use the RESUME GATEWAYS command to enable gateway processes to accept new connections.

##### Example

    CMCTL> SUSPEND GATEWAY 1
    The command completed successfully

**Parent topic:** Oracle Connection Manager Control Utility Commands
