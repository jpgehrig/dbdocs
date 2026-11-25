The following topics describe Oracle Messaging Gateway (MGW) prerequisites and how to load, set up, and unload Messaging Gateway. They also describe how to set up and modify the `mgw.ora` initialization file.

- Oracle Messaging Gateway Prerequisites

- Loading and Setting Up Oracle Messaging Gateway

- Setting Up Non-Oracle Messaging Systems

- Verifying the Oracle Messaging Gateway Setup

- Unloading Oracle Messaging Gateway

- Understanding the mgw.ora Initialization File

### Oracle Messaging Gateway Prerequisites

Messaging Gateway uses one Oracle Scheduler job for each Messaging Gateway agent. If the value of the `JOB_QUEUE_PROCESSES` database initialization parameter is zero, then no Oracle Scheduler jobs will run. If the value is non-zero, it effectively becomes the maximum number of Scheduler jobs and job queue jobs that can run concurrently.

Verify that a non-zero value is set, and that it is large enough to accommodate a Scheduler job for each Messaging Gateway agent to be started.

### Loading and Setting Up Oracle Messaging Gateway

Perform the following procedures before running Messaging Gateway:

- Loading Database Objects into the Database

- Modifying listener.ora for the External Procedure

- Modifying tnsnames.ora for the External Procedure

- Setting Up an mgw.ora Initialization File

- Creating an Oracle Messaging Gateway Administrator User

- Creating an Oracle Messaging Gateway Agent User

- Configuring Oracle Messaging Gateway Connection Information

- Configuring Oracle Messaging Gateway in an Oracle RAC Environment

  **Note:**

  These setup instructions are specific to 32-bit and 64-bit versions of the Windows and 64-bit versions of the Unix-based operating systems. The tasks apply to both Windows and Unix-based operating systems, except where "Windows Operating System Only" or "Linux Operating System Only" is indicated. For other operating systems, see operating-system specific documentation.

#### Loading Database Objects into the Database

Using SQL\*Plus, run `ORACLE_HOME``/mgw/admin/catmgw.sql` as user `SYS` as `SYSDBA`. This script loads the database objects necessary for Messaging Gateway, including roles, tables, views, object types, and PL/SQL packages. It creates public synonyms for Messaging Gateway PL/SQL packages. It creates two roles, `MGW_ADMINISTRATOR_ROLE` and `MGW_AGENT_ROLE,` with certain privileges granted. All objects are owned by `SYS`.

**Note:**

In a CDB environment, run `ORACLE_HOME``/mgw/admin/catmgw.sql` as PDB root.

#### Modifying listener.ora for the External Procedure

This procedure is for Unix-based operating systems only. Static service information for the listener is not necessary on the Windows operating system.

You must modify `listener.ora` so that the Messaging Gateway PL/SQL packages can call the external procedure.

1.  Verify that the default [Inter-process Communication](glossary.md) (IPC) protocol address for the external procedures is set.
        LISTENER = (ADDRESS_LIST=
        (ADDRESS=(PROTOCOL=IPC)(KEY=EXTPROC))
2.  Add static service information for the listener in step 1. This involves setting a `SID_DESC` for the listener. Within the `SID_DESC`, the parameters described in Table 18-1 are important to Messaging Gateway and must be specified according to your own situation.

Example 18-1 Adding Static Service Information for a Listener

    # Add a SID_DESC
    SID_LIST_LISTENER= (SID_LIST=
    (SID_DESC =
       (SID_NAME= mgwextproc)
       (ENVS=
         "LD_LIBRARY_PATH=JRE_HOME/lib/amd64:JRE_HOME/lib/amd64/server:ORACLE_HOME/lib")
       (ORACLE_HOME=ORACLE_HOME)
       (PROGRAM = extproc))

Table 18-1 SID_DESC Parameters

| Parameter     | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `SID_NAME`    | The SID that is specified in the net service name in `tnsnames.ora`. In the following example, the `SID_NAME` is `mgwextproc`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `ENVS`        | Set up the `LD_LIBRARY_PATH` environment needed for the external procedure to run. The `LD_LIBRARY_PATH` must contain the following paths:<br>`JRE_HOME/lib/PLATFORM_TYPE`<br>`JRE_HOME/lib/PLATFORM_TYPE/server`<br>`ORACLE_HOME/lib`<br>It should also contain any additional libraries required by third-party messaging systems. See "Setting Up Non-Oracle Messaging Systems".<br>The `ENVS` value is `LD_LIBRARY_PATH_64` for Oracle Solaris on SPARC (64-Bit) and Oracle Solaris on x86-64 (64-Bit), `LIBPATH` for IBM AIX on POWER Systems, and `LD_LIBRARY_PATH` for the remaining platforms. |
| `ORACLE_HOME` | Your Oracle home directory. Using `$ORACLE_HOME` does not work.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `PROGRAM`     | The name of the external procedure agent, which is `extproc`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |

**Note:**

`JRE_HOME` represents the root directory of a JRE installation, just as `ORACLE_HOME` represents the root directory of an Oracle installation. Oracle recommends that you use the JRE installed with Oracle Database.

Example 18-1 adds `SID_NAME` `mgwextproc` to a listener.ora file for Linux x86.

#### Modifying tnsnames.ora for the External Procedure

For the external procedure, configure a net service name `MGW_AGENT` in `tnsnames.ora` whose connect descriptor matches the information configured in `listener.ora`, as shown in Example 18-2. The net service name must be `MGW_AGENT` (this value is fixed). The `KEY` value must match the `KEY` value specified for the IPC protocol in `listener.ora`. The SID value must match the value specified for `SID_NAME` of the `SID_DESC` entry in `listener.ora`.

**Note:**

If the `names.default_domain` parameter for `sqlnet.ora` has been used to set a default domain, then that domain must be appended to the `MGW_AGENT` net service name in `tnsnames.ora`. For example, if `sqlnet.ora` contains the entry `names.default_domain=acme.com`, then the net service name in `tnsnames.ora` must be `MGW_AGENT.acme.com`.

Example 18-2 Configuring MGW_AGENT

    MGW_AGENT =
    (DESCRIPTION=
       (ADDRESS_LIST= (ADDRESS= (PROTOCOL=IPC)(KEY=EXTPROC)))
       (CONNECT_DATA= (SID=mgwextproc)))

#### Setting Up an mgw.ora Initialization File

The Messaging Gateway default initialization file `ORACLE_HOME``/mgw/admin/mgw.ora` is a text file. The Messaging Gateway external procedure uses it to get initialization parameters to start the Messaging Gateway agent. Copy `ORACLE_HOME``/mgw/admin/sample_mgw.ora` to `mgw.ora` and modify it according to your situation.

The following procedure sets environment variables and other parameters required for all applications of Messaging Gateway:

1.  Windows Operating System Only: Set the `MGW_PRE_PATH` variable. Its value is the path to the `jvm.dll` library:
        set MGW_PRE_PATH = JRE_HOME\bin\client

    This variable is prepended to the path inherited by the Messaging Gateway agent process.
2.  Set `CLASSPATH` to include at least the following:
    - JRE runtime classes:

          JRE_HOME/lib/rt.jar

    - Oracle JDBC classes:

          ORACLE_HOME/jdbc/lib/ojdbc6.jar

    - Oracle internationalization classes:

          ORACLE_HOME/jlib/orai18n.jar

    - SQLJ runtime:

          ORACLE_HOME/sqlj/lib/runtime12.jar

    - [Java Message Service](glossary.md) (JMS) interface

          ORACLE_HOME/rdbms/jlib/jmscommon.jar

    - Oracle JMS implementation classes

          ORACLE_HOME/rdbms/jlib/aqapi.jar

    - Java transaction [API](glossary.md)

          ORACLE_HOME/jlib/jta.jar

    - Any additional classes needed for Messaging Gateway to access non-Oracle messaging systems

      **Note:**

      Replace `ORACLE_HOME` with the appropriate, spelled-out value. Using `$ORACLE_HOME`, for example, does not work.

      Users of the Windows operating system must set `CLASSPATH` using the Windows operating system path syntax.

      **See Also:**

      "Setting Up Non-Oracle Messaging Systems"

#### Creating an Oracle Messaging Gateway Administrator User

To perform Messaging Gateway administration work, a database user must be created with `MGW_ADMINISTRATOR_ROLE` privileges, as shown in Example 18-3.

Example 18-3 Creating a Messaging Gateway Administrator User

    CREATE USER admin_user IDENTIFIED BY admin_password;
    GRANT CREATE SESSION to admin_user;
    GRANT MGW_ADMINISTRATOR_ROLE to admin_user;

#### Creating an Oracle Messaging Gateway Agent User

To establish the Messaging Gateway agent connection back to the database, a database user with `MGW_AGENT_ROLE` privileges must be created, as shown in Example 18-4.

Example 18-4 Creating a Messaging Gateway Agent User

    CREATE USER agent_user IDENTIFIED BY agent_password;
    GRANT CREATE SESSION to agent_user;
    GRANT MGW_AGENT_ROLE to agent_user;

#### Configuring Oracle Messaging Gateway Connection Information

After the Messaging Gateway agent user is created, the administration user uses `DBMS_MGWADM.ALTER_AGENT` to configure Messaging Gateway with the user name, password, and database connect string used by the Messaging Gateway agent to connect back to the database, as shown in Example 18-5. Use the Messaging Gateway user name and password that you created in "Creating an Oracle Messaging Gateway Agent User". The database connect string parameter can be set to either a net service name in `tnsnames.ora` (with IPC protocol for better performance) or `NULL`. If `NULL`, then the `oracle_sid` parameter must be set in `mgw.ora`.

For this release, always specify a not `NULL` value for the database connect string parameter when calling `DBMS_MGWADM.ALTER_AGENT`.

Example 18-5 Configuring Messaging Gateway Connection Information

    set echo off
    set verify off
    connect admin_user

    ACCEPT password CHAR PROMPT 'Enter the password for AGENT_USER: ' HIDE

    EXEC DBMS_MGWADM.ALTER_AGENT(
          agent_name  => 'default_agent',
          username    => 'agent_user',
          password    => '&password',
          database    => 'agent_database');

#### Configuring Oracle Messaging Gateway in an Oracle RAC Environment

This section contains these topics:

- Configuring Connection Information for the MGW Agent Connections

- Setting the Oracle RAC Instance for the Messaging Gateway Agent

##### Configuring Connection Information for the MGW Agent Connections

You must make all database connections made by the Messaging Gateway agent to the instance on which the Messaging Gateway agent process is running. This ensures correct failover behavior in an Oracle RAC environment. You can configure connections this way by having the instances use slightly different `tnsnames.ora` files. Each file contains an entry with the same net service name, but the connect data refers to only the instance associated with that `tnsnames.ora` file. The common net service name would then be used for the database parameter when `DBMS_MGWADM.ALTER_AGENT` is used to configure the Messaging Gateway agent database connection information.

For example, in a two-instance Oracle RAC environment with instances `OraDB1` and `OraDB2`, where the net service name `AGENT_DB` is to be used, the `tnsnames.ora` for instance `OraDB1` would look like this:

    AGENT_DB =
      (DESCRIPTION =
        (ADDRESS = (PROTOCOL = TCP)(HOST = myhost1.mycorp.com)(PORT = 1521))
        (CONNECT_DATA =
          (SERVER = DEDICATED)
          (SERVICE_NAME = OraDB10.mycorp.com)
          (INSTANCE_NAME = OraDB1)
        )
      )

The `tnsnames.ora` for `OraDB2` would look like this:

    AGENT_DB =
      (DESCRIPTION =
        (ADDRESS = (PROTOCOL = TCP)(HOST = myhost2.mycorp.com)(PORT = 1521))
        (CONNECT_DATA =
          (SERVER = DEDICATED)
          (SERVICE_NAME = OraDB10.mycorp.com)
          (INSTANCE_NAME = OraDB2)
        )
      )

You would then configure Messaging Gateway agent user connection information by running the following command:

    EXEC DBMS_MGWADM.ALTER_AGENT(
       agent_name   => 'default_agent',
       username     => 'agent_user',
       password     => 'agent_password',
       database     => 'agent_db');

##### Setting the Oracle RAC Instance for the Messaging Gateway Agent

Messaging Gateway provides service affinity for the Messaging Gateway agent external process by leveraging the database service support of the Oracle Scheduler. By default, a Messaging Gateway agent will use the default database service that is mapped to all instances. If you want a Messaging Gateway agent to start on a select group of database instances, you must create a database service for those instances and then assign the database service to the Messaging Gateway agent using the `SERVICE` parameter of the `DBMS_MGWADM`.`CREATE_AGENT` or `DBMS_MGWADM`.`ALTER_AGENT` procedures. The `DBMS_MGWADM`.`STARTUP` procedure submits an Oracle Scheduler job that starts the Messaging Gateway agent external process when the Scheduler job is executed. The Scheduler job will use the database service configured for the Messaging Gateway agent.

The database service specified by the `SERVICE` parameter is only used for the service affinity of the Oracle Scheduler job and thus the service affinity for the Messaging Gateway external process. It is not used for the database connections made by the Messaging Gateway agent user. Those JDBC client connections are based on the values specified for the `DATABASE` and `CONNTYPE` parameters.

**See Also:**

"[Running the Oracle Messaging Gateway Agent on Oracle RAC](omg-working.md)"

### Setting Up Non-Oracle Messaging Systems

This section contains these topics:

- Setting Up for TIB/Rendezvous

- Setting Up for WebSphere MQ Base Java or JMS

#### Setting Up for TIB/Rendezvous

Running as a TIB/Rendezvous Java client application, the Messaging Gateway agent requires TIB/Rendezvous software to be installed on the computer where the Messaging Gateway agent runs. In this section `TIBRV_HOME` refers to the installed TIB/Rendezvous software location.

##### Modifying listener.ora

On the Linux operating system, `LD_LIBRARY_PATH` in the entry for Messaging Gateway must include `TIBRV_HOME``/lib` for the agent to access TIB/Rendezvous shared library files.

**See Also:**

"Modifying listener.ora for the External Procedure"

On the Windows operating system, you are not required to modify `listener.ora`. But the system environment variable `PATH` must include `TIBRV_HOME``\bin`.

##### Modifying mgw.ora

`MGW_PRE_PATH` must include the directory that contains the TIB/Rendezvous license ticket file (`tibrv.tkt`), which usually is located in `TIBRV_HOME/bin`.

`CLASSPATH` must include the TIB/Rendezvous jar file `TIBRV_HOME``/lib/tibrvj.jar`. If you use your own customized TIB/Rendezvous advisory message callback, then the location of the callback class must also be included.

You can set the following Java properties to change the default setting:

- `oracle.mgw.tibrv.encoding`

- `oracle.mgw.tibrv.intraProcAdvSubjects`

- `oracle.mgw.tibrv.advMsgCallback`

  **See Also:**

  "Understanding the mgw.ora Initialization File"

Example 18-6 Setting Java Properties

    setJavaProp oracle.mgw.tibrv.encoding=ISO8859_1
    setJavaProp oracle.mgw.tibrv.intraProcAdvSubjects=_RV.>
    setJavaProp oracle.mgw.tibrv.advMsgCallback=MyadvCallback

#### Setting Up for WebSphere MQ Base Java or JMS

The WebSphere MQ client and WebSphere MQ classes for Java and JMS must be installed on the computer where the Messaging Gateway agent runs. In this section `MQ_HOME` refers to the location of the installed client. On the Linux operating system, this location is always `/opt/mqm`. On the Windows operating system, the installed location can vary.

##### Modifying listener.ora

No extra modification of `listener.ora` is necessary for Messaging Gateway to access WebSphere MQ.

##### Modifying mgw.ora

When using WebSphere MQ Base Java (non-JMS) interface, set `CLASSPATH` to include at least the following (in addition to those in "Setting Up an mgw.ora Initialization File"):

- `MQ_HOME``/java/lib/com.ibm.mq.jar`

- `MQ_HOME``/java/lib/connector.jar`

When using WebSphere MQ JMS interface, set `CLASSPATH` to include at least the following (in addition to those in "Setting Up an mgw.ora Initialization File"):

- `MQ_HOME``/java/lib/com.ibm.mqjms.jar`

- `MQ_HOME``/java/lib/com.ibm.mq.jar`

- `MQ_HOME``/java/lib/connector.jar`

### Verifying the Oracle Messaging Gateway Setup

The following procedure verifies the setup and includes a simple startup and shutdown of the Messaging Gateway agent:

1.  Start the database listeners.
    Start the listener for the external procedure and other listeners for the regular database connection.
2.  Test the database connect string for the Messaging Gateway agent user.
    Run` sqlplus ``agent_user``/``agent_password``@``agent_database`.

    If it is successful, then the Messaging Gateway agent can connect to the database.
3.  Linux Operating System Only: Test the net service entry used to call the external procedure.
    Run` sqlplus ``agent_user``/``agent_password``@``MGW_AGENT`.

    This should fail with "ORA-28547: connection to server failed, probable Oracle Net admin error". Any other error indicates that the `tnsnames.ora`, `listener.ora`, or both are not correct.
4.  Connect as `admin_user` and call `DBMS_MGWADM.STARTUP` to start the Messaging Gateway agent.
5.  Using the `MGW_GATEWAY` view, wait for `AGENT_STATUS` to change to `RUNNING` and `AGENT_PING` to change to `REACHABLE`.
6.  Connect as `admin_user` and call `DBMS_MGWADM.SHUTDOWN` to shut down the Messaging Gateway agent.
7.  Using the `MGW_GATEWAY` view, wait for `AGENT_STATUS` to change to `NOT_STARTED`.

### Unloading Oracle Messaging Gateway

Use this procedure to unload Messaging Gateway:

1.  Shut down Messaging Gateway.
2.  Remove any user-created queues whose payload is a Messaging Gateway [canonical](glossary.md) type (for example, `SYS.MGW_BASIC_MSG_T`).
3.  Using SQL\*Plus, run `ORACLE_HOME``/mgw/admin/catnomgw.sql` as user `SYS` as `SYSDBA`.
    This drops the database objects used by Messaging Gateway, including roles, tables, views, packages, object types, and synonyms.
4.  Remove entries for Messaging Gateway created in `listener.ora` and `tnsnames.ora`.

### Understanding the mgw.ora Initialization File

Messaging Gateway reads initialization information from a text file when the Messaging Gateway agent starts. The initialization file contains lines for setting initialization parameters, environment variables, and Java properties. Each entity must be specified on one line. Leading whitespace is trimmed in all cases.

A Messaging Gateway administrator can specify the initialization file to be used for a Messaging Gateway agent via `DBMS_MGWADM`.`CREATE_AGENT` and `DBMS_MGWADM`.`ALTER_AGENT`. If an initialization file is not specified then a default initialization file will be used.

The default initialization file for the default agent is `ORACLE_HOME/mgw/admin/mgw.ora`.

The default initialization file for a named agent is `ORACLE_HOME`/`mgw`/`admin`/`mgw_AGENTNAME`.`ora` where `AGENTNAME` is the name in uppercase of the Messaging Gateway agent. For example, if the agent name is `my_agent` then the name of the agent's default initialization file is `ORACLE_HOME`/`mgw`/`admin`/`mgw_MY_AGENT`.`ora`. If the default initialization file for a named agent is not found then `ORACLE_HOME`/`mgw`/`admin`/`mgw`.`ora` will be used.

#### mgw.ora Initialization Parameters

The initialization parameters are typically specified by lines having a "`name``=``value``<NL>`" format where `name` represents the parameter name, `value` represents its value and `<NL>` represents a new line.

##### log_directory

##### Usage:

Specifies the directory where the Messaging Gateway log/trace file is created.

##### Format:

    log_directory = value

##### Default:

    ORACLE_HOME/mgw/log

##### Example:

    log_directory = /private/mgwlog

##### log_level

##### Usage:

Specifies the level of logging detail recorded by the Messaging Gateway agent. The logging level can be dynamically changed by calling `DBMS_MGWADM.SET_LOG_LEVEL` while the Messaging Gateway agent is running. Oracle recommends that log level `0` (the default value) be used at all times.

##### Format:

    log_level = value

##### Values:

`0` for basic logging; equivalent to `DBMS_MGWADM.BASIC_LOGGING`

`1` for light tracing; equivalent to `DBMS_MGWADM.TRACE_LITE_LOGGING`

`2` for high tracing; equivalent to `DBMS_MGWADM.TRACE_HIGH_LOGGING`

`3` for debug tracing; equivalent to `DBMS_MGWADM.TRACE_DEBUG_LOGGING`

`4` for high debug tracing; equivalent to `DBMS_MGWADM.TRACE_DEBUG_HIGH_LOGGING`

##### Example:

    log_level = 0

#### mgw.ora Environment Variables

Because the Messaging Gateway process environment is not under the direct control of the user, certain environment variables should be set using the initialization file. The environment variables currently used by the Messaging Gateway agent are `CLASSPATH`, `MGW_PRE_PATH`, and `ORACLE_SID`.

Environment variables such as `CLASSPATH` and `MGW_PRE_PATH` are set so the Messaging Gateway agent can find the required shared objects, Java classes, and so on. Environment variables are specified by lines having a `"set` `env_var``=value``<NL>"` or `"setenv ``env_var``=``value``<NL>"` format where `env_var` represents the name of the environment variable to set, `value` represents the value of the environment variable, and `<NL>` represents a new line.

##### CLASSPATH

##### Usage:

Used by the [Java Virtual Machine](glossary.md) to find Java classes needed by the Messaging Gateway agent for [propagation](glossary.md) between Oracle Database Advanced Queuing and non-Oracle messaging systems.

##### Format:

    set CLASSPATH=value

##### Example:

    set CLASSPATH=ORACLE_HOME/jdbc/lib/ojdbc6.jar:JRE_HOME/lib/rt.jar:
    ORACLE_HOME/sqlj/lib/runtime12.jar:ORACLE_HOME/jlib/orai18n.jar:ORACLE_HOME/rdbms/
    jlib/jmscommon.jar:ORACLE_HOME/rdbms/jlib/aqapi.jar:ORACLE_HOME/jlib/jta.jar:
    /opt/mqm/java/lib/com.ibm.mq.jar:/opt/mqm/java/lib/com.ibm.mqjms.jar:/opt/mqm/java
    /lib/connector.jar

##### MGW_PRE_PATH

##### Usage:

Appended to the front of the path inherited by the Messaging Gateway process. For the Windows operating system, this variable must be set to indicate where the library `jvm.dll` is found.

##### Format:

    set MGW_PRE_PATH=value

##### Example:

    set MGW_PRE_PATH=JRE_HOME\bin\client

##### ORACLE_SID

##### Usage:

Can be used when a service name is not specified when configuring Messaging Gateway.

##### Format:

    set ORACLE_SID=value

##### Example:

    set ORACLE_SID=my_sid

#### mgw.ora Java Properties

You must specify Java system properties for the Messaging Gateway JVM when working with TIB/Rendezvous subjects. You can use the `setJavaProp` parameter of the Messaging Gateway initialization file for this. Java properties are specified by lines having a `"setJavaProp` `prop_name``=``value``<NL>"` format, where `prop_name` represents the name of the Java property to set, `value` represents the value of the Java property, and `<NL>` represents a new line character.

##### oracle.mgw.batch_size

##### Usage:

This Java property represents the maximum number of messages propagated in one transaction. It serves as a default value if the Messaging Gateway job option, `MsgBatchSize`, is not specified. If altered from the default, then consideration should be given to the expected [message](glossary.md) size and the Messaging Gateway agent memory (see `max_memory` parameter of `DBMS_MGWADM.ALTER_AGENT`). The minimum value of this Java property is 1, the maximum is 100, and the default is 30.

**See Also:**

"DBMS_MGWADM" in [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_MGWADM.md)

##### Syntax:

    setJavaProp oracle.mgw.batch_size=value

##### Example:

    setJavaProp oracle.mgw.batch_size=10

##### oracle.mgw.polling_interval

##### Usage:

This parameter specifies the time (in milliseconds) that must elapse between polls for available messages of a propagation source [queue](glossary.md). The default polling interval used by Messaging Gateway is 5000 milliseconds (5 seconds). The minimum value of this Java property is 100 millisecond, and the maximum value is 60 seconds.

##### Syntax:

    setJavaProp oracle.mgw.polling_interval=value

##### Example:

    setJavaProp oracle.mgw.polling_interval=1000

##### oracle.mgw.tibrv.encoding

##### Usage:

This parameter specifies the character encoding to be used by the TIB/Rendezvous messaging system links. Only one character set for all configured TIB/Rendezvous links is allowed due to TIB/Rendezvous restrictions. The default is ISO 8859-1 or the character set specified by the Java system property `file.encoding`.

##### Syntax:

    setJavaProp oracle.mgw.tibrv.encoding=value

##### Example:

    setJavaProp oracle.mgw.tibrv.encoding=ISO8859_1

##### oracle.mgw.tibrv.intraProcAdvSubjects

##### Usage

Used for all TIB/Rendezvous messaging system links, this parameter specifies the names of system advisory subjects that present on the intraprocess transport.

##### Syntax

    setJavaProp oracle.mgw.tibrv.intraProcAdvSubjects=
    advisorySubjectName[:advisorySubjectName]

##### Example:

    setJavaProp oracle.mgw.tibrv.intraProcAdvSubjects=_RV.>

##### oracle.mgw.tibrv.advMsgCallback

##### Usage:

Used for all TIB/Rendezvous messaging system links, this parameter specifies the name of the Java class that implements the `TibrvMsgCallback` interface to handle system advisory messages. If it is not specified, then the default system advisory message handler provided by Messaging Gateway is used, which writes system advisory messages into Messaging Gateway log files. If it is specified, then the directory where the class file is stored must be included in the `CLASSPATH` in `mgw.ora`.

##### Syntax:

    setJavaProp oracle.mgw.tibrv.advMsgCallback=className

##### Example:

    setJavaProp oracle.mgw.tibrv.advMsgCallback=MyAdvCallback

##### oracle.net.tns_admin

##### Usage:

This parameter specifies the directory of the tnsnames.ora file. It must be set if the Messaging Gateway agent is configured to use the JDBC Thin driver and the database specifier of the agent connection information is a TNSNames alias. This does not need to be set if the JDBC OCI driver is used or the database specifier is something other than a TNSNames alias.

##### Syntax:

    setJavaProp oracle.net.tns_admin=value

##### Example:

    setJavaProp oracle.net.tns_admin=/myoraclehome/network/admin

#### mgw.ora Comment Lines

Comment lines are designated with a `#` character as the first character of the line.
