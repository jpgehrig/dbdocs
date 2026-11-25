This chapter describes features about building and configuring OCI applications on Linux, UNIX, and Windows operating systems.

For other supported operating systems, see the platform specific installation guides for more information.

This chapter includes the following topics:

- Header File and Makefile Locations

- Building an OCI Application on Linux and UNIX

- Building an Application on Windows

- Database Connection Strings

- Client and Server Operating with Different Versions of Time Zone Files

- OCI Client-Side Deployment Parameters Using oraaccess.xml

- About Compatibility and Upgrading

- Fault Diagnosability in OCI

### 3.1 Header File and Makefile Locations

The OCI and OCCI header files that are required for OCI and OCCI client application development on Linux and UNIX operating systems reside in the `$ORACLE_HOME/rdbms/public` directory.

These files are available both with the Oracle Database Server installation, and with the Oracle Database Client Administration and Custom installations. See the [SDK for Oracle Instant Client](instant-client.md) for information about it containing C and C++ header files and a Makefile for developing OCI and OCCI applications while in an Instant Client environment.

All demonstration programs and their related header files reside in the `$ORACLE_HOME/rdbms/demo` directory once they are installed. These demonstration files are installable only from the Examples media. See [OCI Demonstration Programs](oci-demo-programs.md) for the names of these programs and their purposes.

Several makefiles are provided in the `demo` directory. Each makefile contains comments with instructions on its use in building OCI executables. Oracle recommends that you use these demonstration makefiles whenever possible to avoid errors in compilation and linking.

The `demo_rdbms.mk` file in the `demo` directory and is an example makefile. See the comments on how to build the demonstration OCI programs. The `demo_rdbms.mk` file includes the `$ORACLE_HOME/rdbms/public` directory. Ensure that your own customized makefiles have the `$ORACLE_HOME/rdbms/public` directory in the `INCLUDE` path.

The `ociucb.mk` file is a makefile in `demo` for building a callback shared library.

### 3.2 Building an OCI Application on Linux and UNIX

How to build an OCI application on Linux and UNIX.

This topic describes the features of OCI that apply to building applications on Linux and UNIX in the following topics:

- Oracle Directory Structure

- Demonstration OCI Programs

**See Also:**

- Oracle Database Client Installation Guide for Linux for operating system requirements for x86–64 Linux platforms, supported Oracle Linux and Red Hat Enterprise distributions for x86-64 platforms, and installation requirements for programming environments for Linux x86-64

- Oracle Database Instant Client Installation Guide for Apple Mac OS X (Intel) for checking the software requirements

#### 3.2.1 Oracle Directory Structure

The `$ORACLE_HOME` directory contains the following directories described in the following table that are relevant to OCI.

These directories are for the full client and Oracle Database, but not for the Oracle Instant Client. These files include the library files needed to link and run OCI applications, and link with other Oracle products.

Table 3-1 ORACLE_HOME Directories and Contents

| Directory Name | Contents                                             |
|:---------------|:-----------------------------------------------------|
| `/admin`       | Configuration files                                  |
| `/demo`        | Sample programs, make files, SQL files, and so forth |
| `/imclude`     | Header files                                         |
| `/lib`         | Library files                                        |
| `/mesg`        | Message files                                        |
| `/public`      | Public header files                                  |

#### 3.2.2 Demonstration OCI Programs

A set of OCI demonstration programs and their corresponding project files are optionally installed after an Oracle Database installation and set up in the `ORACLE_BASE/ORACLE_HOME``/demo` subdirectory.

Build and run these OCI demonstration programs to familiarize yourself with the steps involved in developing OCI applications.

To build a demo OCI program, run the `make` file (`demo_rdbms.mk`) located in the `/demo` directory. For example, to build a single OCI demo, use the following `make` command syntax:

    make -f demo_rdbms.mk build EXE=demo OBJS="demo.o ..."

For example, to build the OCI `cdemo81.c` program, enter the following `make` command:

    make -f demo_rdbms.mk build EXE=cdemo81 OBJS=cdemo81.o

In this example, the executable file is created or updated from the object file, which in turn is made by compiling the source file `cdemo81.c`.

**See Also:**

- [Oracle Database Examples Installation Guide](../exmpl/index.md) for information about installing the demonstration OCI programs using Oracle Universal Installer

- [ORACLE Linux](https://www.oracle.com/linux/?source=WWMK210224P00028)

- Review the contents of the `demo_rdbms.mk` file to learn more about running the many other OCI demonstration programs that are available in the `demo` subdirectory.

- [OCI Demonstration Programs](oci-demo-programs.md) for more information about OCI demonstration programs

### 3.3 Building an Application on Windows

How to build an OCI application on Windows.

See [Getting Started with OCI for Windows](getting-started-with-oci-for-windows.md) for complete information.

**See Also:**

[Oracle Database Client Installation Guide for Microsoft Windows](../ntcli/software-requirements.md) for information about Oracle Database software client requirements.

### 3.4 Database Connection Strings

This topic describes Oracle Net naming methods that do not use `ORACLE_BASE_HOME`, or `ORACLE_HOME` (to locate configuration files such as `tnsnames.ora`, `sqlnet.ora`, or `oraaccess.xml`).

In particular, the `connect_identifier` in the `OCIServerAttach()` call can be specified in the following formats:

- An easy connect naming string is of the form:

      [[protocol:]//]host1{,host12}[:port1]{,host2:port2}[/service_name][:server][/instance_name][?parameter_name=value{&parameter_name=value}]

  Starting with Oracle Database Release 19c, the easy connect naming syntax has been extended, see [Easy Connect Naming Enhancements](../admqs/configuring-the-network-environment.md).

- As a local naming parameters `tnsnames.ora` configuration file entry of the form:

      net_service_name=
       (DESCRIPTION=
      (ADDRESS=(protocol_address_information))
         (CONNECT_DATA=
           (SERVICE_NAME=service_name)))

- As an Oracle Net connect descriptor of the form:

      "(DESCRIPTION=(ADDRESS=(PROTOCOL=protocol-name) (HOST=host-name) (PORT=port-number))
      (CONNECT_DATA=(SERVICE_NAME=service-name)))"

- A Connection Name that is resolved through Directory Naming where the site is configured for LDAP server discovery.

For naming methods such as `tnsnames.ora` and directory naming to work, the `TNS_ADMIN` environment variable can also be set.

If the `TNS_ADMIN` environment variable is not set, and `tnsnames.ora` entries such as `inst1`, and so on, are used, then the `ORACLE_HOME` variable must be set, and the configuration files are expected to be in the `$ORACLE_HOME/network/admin` directory. Note that the `ORACLE_HOME` variable in this case is only used for locating Oracle Net configuration files, and no other component of Client Code Library (OCI, NLS, and so on) uses the value of `ORACLE_HOME`. So it is preferred and easier to set the `TNS_ADMIN` environment variable to establish the location of the `tnsnames.ora` file.

If a `NULL` string, "", is used as the connection string in the `OCIServerAttach()` call, then the `TWO_TASK` environment variable can be set to the `connect_identifier`. On a Windows operating system, the `LOCAL` environment variable is used instead of `TWO_TASK`.

Similarly, for OCI applications such as SQL\*Plus, the `TWO_TASK` (or `LOCAL` on Windows) environment variable can be set to the connect_identifier. Its value can be anything that would have gone to the right of the '@' on a typical connect string.

**See Also:**

- [Oracle Database Net Services Administrator's Guide](../netag/configuring-naming-methods.md) chapter on "Configuring Naming Methods" for more about connect descriptors

#### 3.4.1 Examples of Oracle Database Connection String Connect Identifiers

If you are using OCI applications, for example SQL\*Plus, then you can specify the database connection string in the following ways:

If the `listener.ora` file on the Oracle database contains the following:

    LISTENER = (ADDRESS_LIST=
     (ADDRESS=(PROTOCOL=tcp)(HOST=server6)(PORT=1573))
    )

    SID_LIST_LISTENER = (SID_LIST=
     (SID_DESC=(SID_NAME=rdbms3)(GLOBAL_DBNAME=rdbms3.server6.us.alchemy.com)
    (ORACLE_HOME=/home/dba/rdbms3/oracle))
    )

The OCI application, connect identifier is:

    "server6:1573/rdbms3.server6.us.alchemy.com"

The connect identifier can also be specified as:

    "(DESCRIPTION=(ADDRESS=(PROTOCOL=tcp)(HOST=server6)(PORT=1573))(CONNECT_DATA=
    (SERVICE_NAME=rdbms3.server6.us.alchemy.com)))"

Alternatively, you can set the `TWO_TASK` environment variable to any of the previous connect identifiers and connect without specifying the connect identifier. For example:

    export TWO_TASK=//server6:1573/rdbms3.server6.us.alchemy.com

You can also specify the `TWO_TASK` environment variable as:

    export TWO_TASK=(DESCRIPTION=(ADDRESS=(PROTOCOL=tcp)(HOST=server6)(PORT=1573))
    (CONNECT_DATA=(SERVICE_NAME=rdbms3.server6.us.alchemy.com)))

Then you can invoke the OCI application with an empty connect identifier. For example, to run SQL\*Plus:

    sqlplus user

The connect descriptor can also be stored in the `tnsnames.ora` file. For example, if the `tnsnames.ora` file contains the following connect descriptor:

    conn_str = (DESCRIPTION=(ADDRESS=(PROTOCOL=tcp)(HOST=server6)(PORT=1573))(CONNECT_DATA=
    (SERVICE_NAME=rdbms3.server6.us.alchemy.com)))

If the `tnsnames.ora` file is located in the `/home/webuser/myconfigs `directory, then you can set the variable `TNS_ADMIN` (or `LOCAL` on Windows) as:

    export TNS_ADMIN=/home/webuser/myconfigs

Then you can use the connect identifier `conn_str` for invoking OCI application, for example SQL\*Plus, or for your OCI connection.

**Note:**

`TNS_ADMIN` specifies the directory where the `tnsnames.ora` file is located and `TNS_ADMIN` is not the full path of the `tnsnames.ora` file.

If the preceding `tnsnames.ora` file is located in an installation based Oracle home, in the /`network/server6/home/dba/oracle/network/admin` directory, then the `ORACLE_HOME` environment variable can be set as follows and OCI application, for example SQL\*Plus can be invoked as previously, with the identifier `conn_str`:

    export ORACLE_HOME=/network/server6/home/dba/oracle

Finally, if `tnsnames.ora` can be located by `TNS_ADMIN` or `ORACLE_HOME`, then the `TWO_TASK` environment variable can be set as follows enabling you to invoke OCI application, for example SQL\*Plus without a connect identifier:

    export TWO_TASK=conn_str

### 3.5 Client and Server Operating with Different Versions of Time Zone Files

In Oracle Database Release 11.2 (or later) you can use different versions of the time zone file on the client and server; this mode of operation was not supported before Oracle Database Release 11.2.

Both client and server must be 11.2 or later to operate in such a mixed mode. This section discusses the ramifications of operating in such a mode. To avoid these ramifications use the same time zone file version for client and server.

The following behavior is seen when the client and server use different time zones file versions. Note that the use of different time zone file versions only affects the handling of `TIMESTAMP` `WITH` `TIMEZONE` (`TSTZ`) data type values.

- The OCI Datetime and Interval APIs listed here unconditionally raise an error when the input parameters are of `TSTZ` type. This is because these operations depend on the local time zone file on the client that is not synchronized with the database. Continuing with the computation in such a configuration can result in inconsistent computations across the client and database tiers.

      OCIDateTimeCompare()
      OCIDateTimeConstruct()
      OCIDateTimeConvert()
      OCIDateTimeSubtract()
      OCIIntervalAdd()
      OCIIntervalSubtract()
      OCIIntervalFromTZ()
      OCIDateTimeGetTimeZoneName()
      OCIDateTimeGetTimeZoneOffset()Foot 1
      OCIDateTimeSysTimeStamp()

- There is a performance penalty when you retrieve or modify `TSTZ` values. The performance penalty arises because of the additional conversions needed to compensate for the client and server using different time zone file versions.

- If new time zone regions are defined by the more recent time zone file, you can see an error operating on a `TIMESTAMP` `WITH` `TIMEZONE` value belonging to the new region on a node that has a time zone file version that does not recognize the new time zone region.

Applications that manipulate opaque type or `XMLType` instances or both containing `TSTZ` type attributes must use the same time zone file version on client and server to avoid data loss.

**See Also:**

[Oracle Database Globalization Support Guide](../nlspg/datetime-data-types-and-time-zone-support.md) for information about upgrading the time zone file and timestamp with time zone data

### 3.6 OCI Client-Side Deployment Parameters Using oraaccess.xml

This topic describes the OCI client-side deployment parameters using oraaccess.xml.

This section includes the following topics:

- About oraaccess.xml

- About Client-Side Deployment Parameters Specified in oraaccess.xml

- High Level Structure of oraaccess.xml

- About Specifying Global Parameters in oraaccess.xml

- About Specifying Defaults for Connection Parameters

- Overriding Connection Parameters at the Connection-String Level

- About OCI Session Pool Configuration in oraaccess.xml

- File (oraaccess.xml) Properties

#### 3.6.1 About oraaccess.xml

Starting with Oracle Database Release 12c Release 1 (12.1), Oracle provides an `oraaccess.xml` file, a client-side configuration file.

You can use the `oraaccess.xml` file to configure selected OCI parameters (some of which are accepted programatically in various OCI API calls), thereby allowing OCI behavior to be changed during deployment without modifying the source code that calls OCI.

Updates to the `oraaccess.xml` file will not affect already running clients. In order to pick up any updates to the `oraaccess.xml` file, already running clients need to be restarted.

The `oraaccess.xml` file is read from the directory specified by the `TNS_ADMIN` environment variable in regular and instant client installations. This is the `$ORACLE_HOME``/network/admin` directory on UNIX operating systems and the `%ORACLE_HOME%``\NETWORK\ADMIN` directory on Microsoft Windows operating systems, if `TNS_ADMIN` is not set in regular client installations.

#### 3.6.2 About Client-Side Deployment Parameters Specified in oraaccess.xml

When equivalent parameters are set both in the `sqlnet.ora` and `oraaccess.xml` files, the `oraaccess.xml` file setting takes precedence over the corresponding `sqlnet.ora` file setting.

In such cases, Oracle recommends using the `oraaccess.xml` file settings moving forward. For any network configuration, the `sqlnet.ora` file continues to be the primary file as network level settings are not supported in the `oraaccess.xml` file.

#### 3.6.3 High Level Structure of oraaccess.xml

Describes the high-level structure of the `oraaccess.xml` file.

The `oraaccess.xml` file has a top-level node `<oraaccess>` with the following three elements:

- `<default_parameters>` - This element describes any default parameter settings shared across connections. These default parameters include:

  - Defaults for global parameters - These global parameters can only be specified once and hence are applicable to all connections and cannot be overridden at the connection level. These parameters are specified using the following tags:

    - `<events>` - Creates the OCI Environment in `OCI_EVENTS` mode, which is required for Fast Application Notification (FAN) and runtime connection load balancing

    - `<result_cache>` - Sets OCI client result cache parameters

    - `<diag>` - Sets OCI fault diagnosability parameters

  - Defaults for connection-specific parameters - Connection parameters can be set to different values for specific connections. However, they too can be defaulted, and overridden on a per connection string basis as needed. These defaults are shared across all connections (unless overridden at the connection level, which is described in the `<config_descriptions>` list item) that follows. These defaults are specified by the following tags:

    - `<prefetch>` - Sets the number of prefetch rows for all queries; specified using the `<rows>` parameter.

    - `<statement_cache>` - Sets the maximum number of statements that can be cached per session; specified using the `<size>` parameter.

    - `<auto tune>` - Consists of: `<enable>` to turn auto tuning on or off; `<ram_threshold>`, which sets the memory threshold for auto-tuning to stop using more memory when available physical memory on the client system has reached this threshold; and `<memory_target>`, which sets the memory limit that OCI auto-tuning can use per client process.

    - `<fan_subscription_failure_action>` - Sets the action upon subscription failure to be either the value `trace` or `error`.

    - `<ons>` - Sets a variety of ONS client-side deployment configuration parameters used for FAN notifications.

- `<config_descriptions>` - This element associates a configuration alias element (`<config_alias>`), which is basically a name, with a specific set of parameters (`<parameters>`) that contain one or more connection parameters. These connection parameters are the same connection parameters within the element `<default_parameters>` described previously, namely: `<prefetch>`, `<statement_cache>`, `<auto_tune>`, `<fan_subscription_failure_action> `and `<ons>`.

- `<connection_configs>` - This element associates one or more connection strings used by an application with a config alias, thus allowing multiple connection string elements to share the same set of parameters.

  A connection configuration element (`<connection_config>`) associates a connection string element (`<connection_string>`) with a configuration alias element (`<config_alias>`).

  A connection string is indirectly associated with a set of parameters through the configuration alias, which allows multiple connection string elements to share the same set of parameters.

The sections that follow describe these client-side deployment parameters in more detail.

**See Also:**

About Specifying Defaults for Connection Parameters

#### 3.6.4 About Specifying Global Parameters in oraaccess.xml

As described, the `<default_parameters>` tag allows specifying default values for various OCI parameters.

Of these, some parameters can only be specified once and hence apply to all connections. These global parameters are described using the following tags:

- `<events>`

  This creates the OCI Environment in `OCI_EVENTS` mode, which is required for Fast Application Notification (FAN) and runtime connection load balancing.

      <events>
        true <!--value could be false also -->
      </events>

- `<result_cache>`

  - `<max_rset_rows>` - Maximum size of any result set in rows in the per-process query cache. Equivalent to `OCI_RESULT_CACHE_MAX_RSET_ROWS` in the `sqlnet.ora` file.

  - `<max_rset_size>` - Maximum client result cache size. Set the size to 32,768 bytes (32 Kilobytes (KB)) or greater. Equivalent to `OCI_RESULT_CACHE_MAX_RSET_SIZE` in the `sqlnet.ora` file.

  - `<max_size>` - Maximum size in bytes for the per-process query cache. Specifying a size less than 32,768 in the client disables the client result cache feature. Equivalent to `OCI_RESULT_CACHE_MAX_SIZE` in the `sqlnet.ora` file.

  <!-- -->

      <result_cache>
            <max_rset_rows>10</max_rset_rows>
            <max_rset_size>65535</max_rset_size>
            <max_size>65535</max_size>
      </result_cache>

  When equivalent parameters are set both in the `sqlnet.ora` and `oraaccess.xml` files, the `oraaccess.xml` file setting takes precedence over the corresponding `sqlnet.ora` file setting.

  See Table 3-2 for a listing of equivalent OCI parameter settings.

- `<diag>`

  You can specify the following elements:

  - `<adr_enabled>` - Enables or disables diagnosability. Equivalent to `DIAG_ADR_ENABLED` in the `sqlnet.ora` file. Values: true or false.

  - `<dde_enabled>` - Enables or disables DDE. Values: true or false.

  - `<adr_base>` - Sets the ADR base directory, which is a system-dependent directory path string to designate the location of the ADR base to use in the current ADRCI session. Equivalent to `ADR_BASE` in the `sqlnet.ora` file. Value: directory path for ADR base directory.

  - `<sighandler_enabled>` - Enables or disables OCI signal handler. Values: true or false.

  - `<restricted>` - Enables or disables full dump files. Oracle Database client contains advanced features for diagnosing issues, including the ability to dump diagnostic information when important errors are detected. By default, these dumps are restricted to a small subset of available information, to ensure that application data is not dumped. However, in many installations, secure locations for dump files may be configured, ensuring the privacy of such logs. In such cases, it is recommended to turn on full dumps; this can greatly speed resolution of issues. Full dumps can be enabled by specifying a value of false. Values: true or false.

  - `<trace_events>` - Indicates the trace event number and the level of tracing to be in effect. Currently only event 10883 is supported. The available levels are 5 and 10.

  <!-- -->

      <diag>
         <adr_enabled>false</adr_enabled>
         <dde_enabled>false</dde_enabled>
         <adr_base>/foo/adr</adr_base>
         <sighandler_enabled>false</sighandler_enabled>
         <restricted>true</restricted>
         <trace_events>
           <trace_event>
             <number>10883</number>
             <level>5</level>
           </trace_event>
         </trace_events>
      </diag>

  When equivalent parameters are set both in the `sqlnet.ora` and `oraaccess.xml` files, the `oraaccess.xml` file setting takes precedence over the corresponding `sqlnet.ora` file setting.

  See Table 3-2 for a listing of equivalent OCI parameter settings.

  Table 3-2 Equivalent OCI Parameter Settings in oraaccess.xml and sqlnet.ora

  | Parameter Group          | oraaccess.xml Parameters | sqlnet.ora Parameters            |
  |:-------------------------|:-------------------------|:---------------------------------|
  | OCI client result cache  | `<max_rset_rows>`        | `OCI_RESULT_CACHE_MAX_RSET_ROWS` |
  | OCI client result cache  | `<max_rset_size>`        | `OCI_RESULT_CACHE_MAX_RSET_SIZE` |
  | OCI client result cache  | `<max_size>`             | `OCI_RESULT_CACHE_MAX_SIZE`      |
  | OCI fault diagnosability | `<adr_enabled>`          | `DIAG_ADR_ENABLED`               |
  | OCI fault diagnosability | `<dde_enabled>`          | `DIAG_DDE_ENABLED`               |
  | OCI fault diagnosability | `<adr_base>`             | `ADR_BASE`                       |

**See Also:**

- [Oracle Database Development Guide](../adfns/performance-and-scalability.md) for information about deployment time settings for client result cache and client configuration file parameters

- [Oracle Database Net Services Reference](../netrf/index.md) for more information about ADR diagnostic parameters in the `sqlnet.ora` file

#### 3.6.5 About Specifying Defaults for Connection Parameters

Describes the default values you can set for connection parameters shared across connections.

You can specify the following connection parameters that are shared across connections:

- `<prefetch>` - Specifies prefetch row count for `SELECT` statements.

      <prefetch>
        <rows>100</rows>
      </prefetch>

  Setting this parameter appropriately can help reduce round-trips to the database, thereby improving application performance.

  Note that this only overrides the `OCI_ATTR_PREFETCH_ROWS` parameter (whether explicitly specified by the application or not). If the application has specified `OCI_ATTR_PREFETCH_MEMORY` explicitly, then the actual prefetch row count will be determined by using both constraints. The `OCI_ATTR_PREFETCH_MEMORY` constraint equivalent cannot be specified in the `oraaccess.xml` file.

  Also note that OCI prefetching may still get disabled if the `SELECT` statement fetches columns of specific data types. For more details, see [About Fetching Results](using-sql_statements-in-oci.md) for information about limitations of OCI prefetch.

- `<statement_cache>` - Specifies the number of OCI Statement handles that can be cached per session.

      <statement_cache>
        <size>100</size>
      </statement_cache>

  Caching statement handles improves repeat execute performance by reducing client side and server side CPU consumption and network traffic.

  Note that for this parameter to take effect, the application must be programmed to use `OCIStatementPrepare2()` and `OCIStatementRelease()` calls (and not the older `OCISatementPrepare()` and `OCIHandleFree()` equivalents for getting and disposing of statement handles.

- `<auto_tune>` - Used to enable OCI Auto tuning.

      <auto_tune>
        <enable>true</enable>
        <ram_threshold>0.1</ram_threshold><!--percentage -->
        <memory target>2M</memory_target>
      </auto_tune>

  Enabling auto-tuning can help OCI automatically tune the statement-cache size based on specified memory constraints. This can help dynamically tune the statement cache size to an appropriate value based on runtime application characteristics and available memory resources.

  Note that for auto tuning OCI Statement Cache, the application must be programmed to use `OCIStatementPrepare2()` and `OCIStatementRelease()` calls (and not the older `OCISatementPrepare()` and `OCIHandleFree()` equivalents for getting and disposing of statement handles.

- `<fan_subscription_failure_action>` - Used to determine how OCI responds to a failure to subscribe for FAN notifications.

  A value of `trace` records any failure to subscribe for FAN notifications (if FAN is enabled) in the trace file and OCI proceeds ignoring the failure. A value of `error` makes OCI return an error if an attempt to subscribe for FAN notifications fails.

      <fan>
        <!--only possible values are "trace" and "error" -->
        <subscription_failure_action>
          trace
        </subscription_failure_action>
      </fan>

- `<ons>` - Sets up Oracle Notification Service (ONS) parameters.

  You can specify the following connection parameters:

  - `<subscription_wait_timeout>` - Length of time in seconds the client waits for its subscription to the ONS server.

  - `<auto_config>` - true or false. If true, the configuration specified in this section will augment the auto configuration information that the client receives from the database. If false, it will override the same.

  - `<thread_stack_size>` - Size in bytes of the event notification thread stack.

  - `<debug>` - true or false. Whether debug mode is on (true) or off (false).

  - `<wallet_location>` - Directory that contains an auto logon wallet file for a secure ONS subscription.

  - `<servers>` - Host list with ports and connection distribution.

  <!-- -->

      <ons>
        <!--values or in seconds -->
        <subscription_wait_timeout>
          5
        </subscription_wait_timeout>
        <auto_config>true</auto_config> <!--boolean -->
        <threadstacksize>100k</threadstacksize>
        <debug>true</debug>
        <wallet_location>/etc/oracle/wallets/</wallet_location>
        <servers>
          <address_list>
             <name>pacific</name>
             <max_connections> 3 <\max_connections>
             <hosts>
               10.228.215.121:25293,
               10.228.215.122:25293
             </hosts>
          </address_list>
          <address_list>
             <name>Europe</name>
             <max_connections>3<\max_connections>
             <hosts>
               myhost1.mydomain.com:25273,
               myhost2.mydomain.com:25298,
               myhost3.mydomain.com:30004
             </hosts>
          </address_list>
        </servers>
      </ons>

**See Also:**

- [\<auto_tune\>](performance-topics.md)

- [\<ram_threshold\>](performance-topics.md)

- [\<memory_target\>](performance-topics.md)

#### 3.6.6 Overriding Connection Parameters at the Connection-String Level

Using the `oraaccess.xml` file also allows you to override the very same set of connection-specific parameters at the connection-string level as well.

This allows for overriding those connection-specific parameters based on requirements of individual applications.

Using the `<config_descriptions>` tag, you can specify a set of connection-specific parameters (`<parameters>`) to be associated with a configuration alias (`<config_alias>`, which creates a named group of connection-specific parameters). Thereafter, using the `<connection_configs>` tag, you can associate one or more connection-strings (specified using the `<connection-string>` tag) with a `<config_alias>`. This permits a level of indirection that allows multiple `<connection_string>` elements to share the same set of `<parameters>`.

##### Example 1

This example shows a very simple `oraaccess.xml` file configuration that highlights defaulting of global and connection parameters applicable across all connections.

    <?xml version="1.0" encoding="ASCII" ?>
    <!--
         Here is a sample oraaccess.xml.
         This shows defaulting of global and connection parameters
         across all connections.
    -->
     <oraaccess xmlns="http://xmlns.oracle.com/oci/oraaccess"
      xmlns:oci="http://xmlns.oracle.com/oci/oraaccess"
      schemaLocation="http://xmlns.oracle.com/oci/oraaccess
      http://xmlns.oracle.com/oci/oraaccess.xsd">
      <default_parameters>
        <prefetch>
          <rows>50</rows>
        </prefetch>
        <statement_cache>
          <size>100</size>
        </statement_cache>
        <result_cache>
          <max_rset_rows>100</max_rset_rows>
          <max_rset_size>10K</max_rset_size>
          <max_size>64M</max_size>
        </result_cache>
      </default_parameters>
    </oraaccess>

##### Example 2

This example shows connection parameters being overridden at the connection level.

    <?xml version="1.0" encoding="ASCII" ?>
    <!--
            Here is a sample oraaccess.xml.
            This highlights some connection parameters being
            overridden at the connection level
         -->
     <oraaccess xmlns="http://xmlns.oracle.com/oci/oraaccess"
      xmlns:oci="http://xmlns.oracle.com/oci/oraaccess"
      schemaLocation="http://xmlns.oracle.com/oci/oraaccess
      http://xmlns.oracle.com/oci/oraaccess.xsd">
      <default_parameters>
        <prefetch>
          <rows>50</rows>
        </prefetch>
        <statement_cache>
          <size>100</size>
        </statement_cache>
        <auto_tune>
          <enable>true</enable>
          <ram_threshold>2.67</ram_threshold>
          <memory_target>204800</memory_target>
        </auto_tune>
        <result_cache>
          <max_rset_rows>100</max_rset_rows>
          <max_rset_size>10K</max_rset_size>
          <max_size>64M</max_size>
        </result_cache>
      </default_parameters>
        <!--
             Create configuration descriptions, which are
             groups of connection parameters associated with
             a config_alias.
        -->
      <config_descriptions>
        <config_description>
          <config_alias>bar</config_alias>
          <parameters>
            <prefetch>
              <rows>20</rows>
            </prefetch>
          </parameters>
        </config_description>
        <config_description>
          <config_alias>foo</config_alias>
          <parameters>
            <statement_cache>
              <size>15</size>
            </statement_cache>
          </parameters>
        </config_description>
      </config_descriptions>
      <!--
             Now map the connection string used by the application
             with a config_alias.
      -->
      <connection_configs>
        <connection_config>
          <connection_string>hr_db</connection_string>
          <config_alias>foo</config_alias>
        </connection_config>
        <connection_config>
          <connection_string>finance_db</connection_string>
          <config_alias>bar</config_alias>
        </connection_config>
      </connection_configs>
    </oraaccess>

##### Example 3

This example highlights setup for FAN notifications.

    <?xml version="1.0" encoding="ASCII" ?>
       <!--
        Here is a sample for oraaccess.xml for
        setting up for FAN notifications.
       -->
      <oraaccess xmlns="http://xmlns.oracle.com/oci/oraaccess"
        xmlns:oci="http://xmlns.oracle.com/oci/oraaccess"
        schemaLocation="http://xmlns.oracle.com/oci/oraaccess
        http://xmlns.oracle.com/oci/oraaccess.xsd">
        <default_parameters>
          <fan>
            <!-- only possible values are "trace" or "error" -->
            <subscription_failure_action>
              error
            </subscription_failure_action>
          </fan>
          <ons>
            <subscription_wait_timeout>
              5
            </subscription_wait_timeout>
            <auto_config>true</auto_config>
          </ons>
        <events>true</events>
        </default_parameters>
      </oraaccess>

##### Example 4

This example highlights an advanced `oraaccess.xml` file configuration usage with manual ONS settings. Manual ONS settings should be used rarely.

      <?xml version="1.0" encoding="ASCII" ?>
        <!--
           Here is a sample for oraaccess.xml that highlights
           manual ONS settings.
        -->
      <oraaccess xmlns="http://xmlns.oracle.com/oci/oraaccess"
        xmlns:oci="http://xmlns.oracle.com/oci/oraaccess"
        schemaLocation="http://xmlns.oracle.com/oci/oraaccess
        http://xmlns.oracle.com/oci/oraaccess.xsd">
        <default_parameters>
          <fan>
           <!-- only possible values are "trace" or "error"  -->
            <subscription_failure_action>
              error
            </subscription_failure_action>
          </fan>
          <ons>
            <subscription_wait_timeout>
              5
            </subscription_wait_timeout>
            <auto_config>true</auto_config>
            <!--This provides the manual configuration for ONS.
                Note that this functionality should not need to be used
                as auto_config can normally discover this
                information. -->
            <servers>
              <address_list>
                <name>pacific</name>
                <max_connections>3</max_connections>
                <hosts>10.228.215.121:25293, 10.228.215.122:25293</hosts>
              </address_list>
              <address_list>
                <name>Europe</name>
                <max_connections>3</max_connections>
                <hosts>myhost1.mydomain.com:25273,
                  myhost2.mydomain.com:25298,
                  myhost3.mydomain.com:30004</hosts>
              </address_list>
            </servers>
          </ons>
          <events>true</events>
        </default_parameters>
      </oraaccess>

**See Also:**

About Specifying Defaults for Connection Parameters about overriding the very same set of connection-specific parameters at the connection-string level

#### 3.6.7 About OCI Session Pool Configuration in oraaccess.xml

Beginning with Oracle Database release 18c, version 18.1, the OCI session pool configuration can be set up using the oraaccess.xml client-side configuration file.

The OCI session pool is configured by specifying the following set of parameters in the `oraaccess.xml` configuration file. These parameters can be specified in the default parameters section or in the configuration descriptions section. If specified in the default parameters section, then it applies to all the session pools in the application. These settings can benefit any OCI Session Pool allowing OCI Session Pool settings to be overridden.

- `<session_pool>` — Sets up session pool parameters.

  - `<enable>` — Setting this to true makes the session pool configuration effective. This is a mandatory parameter, that means, if the `<session_pool>` parameter is configured, then `<enable>` parameter must also be configured.

- `<min_size>` — Minimum number of connections in the pool. The default is 0.

- `<max_size>` — Maximum number of connections in the pool. This is a mandatory parameter, that means, if the `<session_pool>` parameter is configured, then `<max_size>` parameter must also be configured.

- `<increment>` — Amount of increase in the number of connections in the pool as the pool expands. The default is 1.

- `<inactivity_timeout>` — Maximum time in seconds for which a connection stays idle in the pool, after which it is terminated. The default is 0, that means, there is no limit for which a connection stays idle in the pool.

- `<max_use_session>` — Maximum number of times a connection can be taken and released to the pool. The default is 0, that means, there is no limit to take a connection and release to the pool.

- `<max_life_time_session>` — Time, in seconds, a connection will stay after it has been created in the pool. The default is 0, that means, there is no limit for a connection to stay after it has been created in the pool.

Using the `oraaccess.xml` file allows you to configure an OCI session pool for each needed connection service. The following example shows two groups of connection parameters associated with its respective config alias, the `sales_config` and the `hr_config`, where each connection string that the application uses is mapped with its respective config alias, thus providing two OCI session pools.

    <oraaccess xmlns="http://xmlns.oracle.com/oci/oraaccess"
                xmlns:oci="http://xmlns.oracle.com/oci/oraaccess"
                schemaLocation="http://xmlns.oracle.com/oci/oraaccess
                http://xmlns.oracle.com/oci/oraaccess.xsd">
      <default_parameters>
      </default_parameters>
        <!--
             Create configuration descriptions, which are
             groups of connection parameters associated with
             a config_alias.
        -->
      <config_descriptions>
        <config_description>
          <config_alias> sales_config </config_alias>
          <parameters>
             <session_pool>
                <enable>true</enable>
                <min_size> 10 </min_size>
                <max_size> 100 </max_size>
                <increment> 5 </increment>
             </session_pool>
          </parameters>
        </config_description>
        <config_description>
          <config_alias> hr_config </config_alias>
          <parameters>
             <session_pool>
                <enable>true</enable>
                <max_size> 10 </max_size>
             </session_pool>
          </parameters>
        </config_description>
      </config_descriptions>
      <!--
             Now map the connection string used by the application
             with a config_alias.
      -->
      <connection_configs>
        <connection_config>
          <connection_string>sales.us.acme.com</connection_string>
          <config_alias>sales_config</config_alias>
        </connection_config>
        <connection_config>
          <connection_string>hr.us.acme.com</connection_string>
          <config_alias>hr_config</config_alias>
        </connection_config>
      </connection_configs>
    </oraaccess>

#### 3.6.8 File (oraaccess.xml) Properties

Lists some high level rules with regards to the `oraaccess.xml` file syntax stated here for simplicity.

The XML schema specified in the `oraaccess.xsd` file is the ultimate formal reference for oraaccess syntax:

- The contents of the file are case sensitive, and all elements (tags, parameter names) are in lower case.

- Comments are allowed between parameters (nodes); for example, Comment "\<!-- comments --\>".

- For the syntax with respect to the order of the parameters, see the XML Schema: `oraaccess.xsd` file (see information about the `oraaccess.xsd` file later in this list).

- For memory size, valid values and formats are 100, 100k, 100K, 1000M, and 1121m. This means only suffixes 'M', 'm', 'K', 'k', or no suffix are allowed. 'K' or 'k' means kilobytes and 'M' or 'm' means megabytes. No suffix means the size is in bytes.

- \<ram_threshold\> should be a decimal number between 0 and 100 and indicates a percentage value.

- Where a number is expected, only positive unsigned integers are allowed; no sign is allowed. An example of a valid number usage is `<statement_cache> <size>100</size> </statement_cache>`).

- Configuration alias names (`<config_alias>foo</config_alias>`) are not case-sensitive

- String parameters (such as `<config_alias>`) are not expected to be quoted.

- These rules are all encapsulated in the schema definition.

- OCI will report an error if OCI is provided an invalid `oraaccess.xml` file.

- Before deploying an `oraaccess.xml` file, Oracle recommends that you validate it with the Oracle supplied XML schema file: `oraaccess.xsd`. The schema file is installed under `ORACLE_HOME/rdbms/admin` in a regular client and under `instantclient_12_2/sdk/admin` in an instant client SDK. Customers can use their own favorite XML validation tools to perform the validation after modifying the `oraaccess.xml` file.

- Sample `oraaccess.xml` files can be found in the `ORACLE_HOME/rdbms/demo` directory in a regular client and in the `instantclient_12_2/sdk/demo` in an instant client. The parameters in these files are for demonstration purpose only and should be modified and tested as per the application's requirement before deploying it.

### 3.7 About Compatibility and Upgrading

The following sections discuss issues concerning compatibility between different releases of OCI client and server, changes in the OCI library routines, and upgrading an application from the release 7.x OCI to the current release of OCI:

- Oracle Client and Server Cross Version Compatibility

- Version Compatibility of Statically Linked and Dynamically Linked Applications

- About Upgrading of Existing OCI Release 7 Applications

- Unsupported OCI Routines

- OCI Routines Not Supported

#### 3.7.1 Oracle Client and Server Cross Version Compatibility

As a general guide, Oracle client and server versions are cross version compatible with a number versions.

This means that you can connect to some older and newer versions of the database and do not always have to upgrade both the client and server at the same time.

However, certain products or utilities may impose additional restrictions on supported combinations specific to the product or utility.

**See Also:**

My Oracle Support [Document 207303.1](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=mos_doc_207303_1) for information about client and server interoperability support matrix for different Oracle versions.

#### 3.7.2 Version Compatibility of Statically Linked and Dynamically Linked Applications

Here are the rules for relinking for a new release.

- Statically linked OCI applications:

  Statically linked OCI applications must be relinked for both major and minor releases, because the statically linked Oracle Database client-side library code may be incompatible with the error messages in the upgraded Oracle home. For example, if an error message was updated with additional parameters then it is no longer compatible with the statically linked code.

- Dynamically linked OCI applications:

  Dynamically linked OCI applications from Oracle Database 10g and later releases need not be relinked. That is, the Oracle Database client-side dynamic library is upwardly compatible with the previous version of the library. Oracle Universal Installer creates a symbolic link for the previous version of the library that resolves to the current version. Therefore, an application that is dynamically linked with the previous version of the Oracle Database client-side dynamic library does not need to be relinked to operate with the current version of the Oracle Database client-side library.

  **Note:**

  If the application is linked with a runtime library search path (such as `-rpath` on Linux), then the application may still run with the version of Oracle Database client-side library it is linked with. To run with the current version of Oracle Database client-side library, it must be relinked.

  **See Also:**

  - [Oracle Database Upgrade Guide](../upgrd/compatibility-interoperability-between-database-releases.md) for information about compatibility and upgrading

  - The server versions supported currently are found on My Oracle Support [Document 207303.1](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=mos_doc_207303_1)

#### 3.7.3 About Upgrading of Existing OCI Release 7 Applications

OCI has been significantly improved with many features since OCI release 7.

Applications that use the OCI release 7.3 API work unchanged against the current release of Oracle Database. They do need to be linked with the current client library. However, OCI release 7.3 API has been deprecated and this option will not be available in future Oracle releases.

OCI release 7 and the OCI calls of this release can be mixed in the same application and in the same transaction provided they are not mixed within the same statement execution. As a result, when migrating an existing OCI version 7 application you have the following two alternatives:

- Upgrade to the current OCI client but do not modify the application: If you choose to upgrade from an Oracle release 7 OCI client to the current release OCI client, you need only link the new version of the OCI library and need not recompile your application. The relinked Oracle Database release 7 OCI applications work unchanged against a current Oracle Database. This option is deprecated and will not be available in future Oracle releases.

- Upgrade to the current OCI client and modify the application: To use the performance and scalability benefits provided by the current OCI, however, you must modify your existing applications to use the current OCI programming paradigm, rebuild and relink them with the current OCI library, and run them against the current release of the Oracle database.

If you want to use any of the object capabilities of the current Oracle Database release, you must upgrade your client to the current release of OCI.

**Note:**

Applications using version 7 API will not be able to connect to Oracle Database 12c by default. Such applications willing to connect to Oracle Database 12c must set `sqlnet.allowed_logon_version` to `8`.

In Oracle Database 12c Release 2 (12.2), identifier length supported by Oracle Database has been increased from 30 bytes to 128 bytes. With this database change, OCI applications using deprecated V7 API `odessp()` may need to be changed. In `odessp()` for the argument `argnam`, an application needs to pass the two dimensional array, which can accommodate identifiers of length 128 bytes, which was previously 30 bytes.

Applications using UPI API `upidpr()` may also need to be changed with long identifiers in Oracle Database 12c Release 2 (12.2). In `upidpr()` for the argument `argument_name`, an application needs to pass the two dimensional array, which can accommodate identifiers of length 128 bytes, which was previously 30 bytes.

**See Also:**

Programmer's Guide to the Oracle7 Server Call Interface in [Oracle 7 Documentation](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=oracle7_documentation).

#### 3.7.4 Unsupported OCI Routines

The release 7.3 OCI calls are not supported. Table 3-3 lists the 7.x OCI calls with their supported equivalents.

Table 3-3 Unsupported OCI Functions

| 7.x OCI Routine                           | Equivalent or Similar Later OCI Routine                                                                                                                                                         |
|:------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `obindps(), obndra(), obndrn(), obndrv()` | `OCIBindByName()` or `OCIBindByName2()`, `OCIBindByPos()` or `OCIBindByPos2()` (Note: additional bind calls may be necessary for some data types)                                               |
| `obreak()`                                | `OCIBreak()`                                                                                                                                                                                    |
| `ocan()`                                  | none                                                                                                                                                                                            |
| `oclose()`                                | Note: cursors are not used in release 8.x or later                                                                                                                                              |
| `ocof(), ocon()`                          | `OCIStmtExecute() `with `OCI_COMMIT_ON_SUCCESS` mode                                                                                                                                            |
| `ocom()`                                  | `OCITransCommit()`                                                                                                                                                                              |
| `odefin(), odefinps()`                    | `OCIDefineByPos()` or `OCIDefineByPos2()` (Note: additional define calls may be necessary for some data types)                                                                                  |
| `odescr()`                                | Note: schema objects are described with OCIDescribeAny(). A describe, as used in release 7.x, most often be done by calling OCIAttrGet() on the statement handle after SQL statement execution. |
| `odessp()`                                | `OCIDescribeAny()`                                                                                                                                                                              |
| `oerhms()`                                | `OCIErrorGet()`                                                                                                                                                                                 |
| `oexec(), oexn()`                         | `OCIStmtExecute()`                                                                                                                                                                              |
| `oexfet()`                                | `OCIStmtExecute()`, `OCIStmtFetch2()` (Note: result set rows can be implicitly prefetched)                                                                                                      |
| `ofen()`, `ofetch()`                      | `OCIStmtFetch2()`                                                                                                                                                                               |
| `oflng()`                                 | none                                                                                                                                                                                            |
| `ogetpi()`                                | `OCIStmtGetPieceInfo()`                                                                                                                                                                         |
| `olog()`                                  | `OCILogon()` or `OCILogon2()`                                                                                                                                                                   |
| `ologof()`                                | `OCILogoff()`                                                                                                                                                                                   |
| `onbclr(), onbset(), onbtst()`            | Note: nonblocking mode can be set or checked by calling `OCIAttrSet()` or `OCIAttrGet()` on the server context handle or service context handle                                                 |
| `oopen()`                                 | Note: cursors are not used in release 8.x or later                                                                                                                                              |
| `oopt()`                                  | none                                                                                                                                                                                            |
| `oparse()`                                | `OCIStmtPrepare2()`; however, it is all local                                                                                                                                                   |
| `opinit()`                                | `OCIEnvCreate()`                                                                                                                                                                                |
| `orol()`                                  | `OCITransRollback()`                                                                                                                                                                            |
| `osetpi()`                                | `OCIStmtSetPieceInfo()`                                                                                                                                                                         |
| `sqlld2()`                                | `SQLSvcCtxGet or SQLEnvGet`                                                                                                                                                                     |
| `sqllda()`                                | `SQLSvcCtxGet or SQLEnvGet`                                                                                                                                                                     |
| `odsc()`                                  | Note: see odescr() preceding                                                                                                                                                                    |
| `oermsg()`                                | `OCIErrorGet()`                                                                                                                                                                                 |
| `olon()`                                  | `OCISessionGet()`                                                                                                                                                                               |
| `orlon()`                                 | `OCISessionGet()`                                                                                                                                                                               |
| `oname()`                                 | Note: see `odescr()` preceding                                                                                                                                                                  |
| `osql3()`                                 | Note: see `oparse()` preceding                                                                                                                                                                  |
| `obind()`                                 | `OCIBindByName()`, `OCIBindByPos()` (Note: additional bind calls may be necessary for some data types)                                                                                          |
| `obindn()`                                | `OCIBindByName()`, `OCIBindByPos() `(Note: additional bind calls may be necessary for some data types)                                                                                          |
| `odfinn()`                                | `OCIDefineByPos()` (Note: additional define calls may be necessary for some data types)                                                                                                         |
| `odsrbn()`                                | Note: see `odescr()` in Table 3-3                                                                                                                                                               |
| `ologon()`                                | `OCISessionget()`                                                                                                                                                                               |
| `osql()`                                  | Note: see `oparse()` Table 3-3                                                                                                                                                                  |

**See Also:**

- [OCI Programming Basics](oci-programming-basics.md) for information about what additional program logic may be required before or after the new or current call is made.

#### 3.7.5 OCI Routines Not Supported

Some OCI routines that were available in previous versions of OCI are not supported in the current release.

They are listed in Table 3-4.

Table 3-4 OCI Functions Not Supported

| OCI Routine | Equivalent or Similar Later OCI Routine                                                                |
|:------------|:-------------------------------------------------------------------------------------------------------|
| `obind()`   | `OCIBindByName()`, `OCIBindByPos()` (Note: additional bind calls may be necessary for some data types) |
| `obindn()`  | `OCIBindByName()`, `OCIBindByPos() `(Note: additional bind calls may be necessary for some data types) |
| `odfinn()`  | `OCIDefineByPos()` (Note: additional define calls may be necessary for some data types)                |
| `odsrbn()`  | Note: see `odescr()` in Table 3-3                                                                      |
| `ologon()`  | `OCILogon()`                                                                                           |
| `osql()`    | Note: see `oparse()` Table 3-3                                                                         |

### 3.8 Fault Diagnosability in OCI

This section describes the following topics:

- About Fault Diagnosability in OCI

- ADR Base Location

- Using ADRCI

- Controlling ADR Creation and Disabling Fault Diagnosability Using sqlnet.ora

#### 3.8.1 About Fault Diagnosability in OCI

Fault diagnosability was introduced into OCI in Oracle Database 11g Release 1 (11.1).

An incident (an occurrence of a problem) on the OCI client is captured without user intervention in the form of diagnostic data: dump files or core dump files. Up to Release 11.2.0.1, the diagnostic data was stored in an Automatic Diagnostic Repository (ADR) subdirectory created for the incident. For example, if a Linux or UNIX application fails with a `NULL` pointer reference, then the core file is written in the ADR home directory (if it exists) instead of the operating system directory. The ADR subdirectory structure and a utility to deal with the output, ADR Command Interpreter (ADRCI), are discussed in the following sections. However, beginning with Release 11.2.0.2, the diagnostic data is stored in the current directory.

An ADR home is the root directory for all diagnostic data for an instance of a particular product such as OCI and a particular operating system user. ADR homes are grouped under the same root directory, the ADR base.

Fault diagnosability and the ADR structure for Oracle Database are described in detail in the discussion of managing diagnostic data in Oracle Database Administrator's Guide.

#### 3.8.2 ADR Base Location

Describes how the location of the ADR base is determined.

The location of the ADR base is determined by OCI in the following order:

1.  For all diagnosability parameters, OCI first looks in the file `oraaccess.xml`. If these parameters are not set there, then OCI looks next in `sqlnet.ora` (if it exists) for a statement such as (Linux or UNIX):

        ADR_BASE=/foo/adr

    `adr` (the name of a directory) must exist and be writable by all operating system users who execute OCI applications and want to share the same ADR base. `foo` stands for a path name. The location of `sqlnet.ora` is given in the directory `$TNS_ADMIN` (`%TNS_ADMIN%` on Windows). If there is no `$TNS_ADMIN` then the current directory is used. If `ADR_BASE` is set and one `sqlnet.ora` is shared by all users, then OCI stops searching when directory `adr` does not exist or is not writable by the user. If `ADR_BASE` is not set, then OCI continues the search, testing for the existence of certain directories.

    For example, if `sqlnet.ora` contains the entry `ADR_BASE=/home/chuck/test` then the ADR base is `/home/chuck/test/oradiag_chuck` and the ADR home could be something like `/home/chuck/test/oradiag_chuck/diag/clients/user_chuck/host_4144260688_11`.

2.  `$ORACLE_BASE` (`%ORACLE_BASE%` on Windows) exists. In this case, the client subdirectory exists because it was created during installation of the database using Oracle Universal Installer.

    For example, if `$ORACLE_BASE` is `/home/chuck/obase` then the ADR base is `/home/chuck/obase` and the ADR home could be similar to `/home/chuck/obase/diag/clients/user_chuck/host_4144260688_11`.

3.  `$ORACLE_HOME` `(%ORACLE_BASE%` on Windows) exists. In this case, the client subdirectory exists because it was created during installation of the database using Oracle Universal Installer.

    For example, if `$ORACLE_HOME` is `/ade/chuck_l1/oracle` then the ADR base is `/ade/chuck_l1/oracle/log` and the ADR home could be similar to `/ade/chuck_l1/oracle/log/diag/clients/user_chuck/host_4144260688_11`.

4.  Operating system home directory: `$HOME` on Linux or UNIX, or `%USERPROFILE%` on Windows. On Linux or UNIX the location could be something like this for user `chuck`: `/home/chuck/oradiag_chuck`. On Windows, a folder named `Oracle` is created under `C:\Documents and Settings\chuck`.

    For example, in an Instant Client, if `$HOME` is `/home/chuck` then the ADR base is `/home/chuck/oradiag_chuck` and the ADR home could be `/home/chuck/oradiag_chuck/diag/clients/user_chuck/host_4144260688_11`.

5.  On Windows, if the application is run as a service, the home directory option is skipped.

6.  Temporary directory in the Linux or UNIX operating system: `/var/tmp`.

    For example, in an Instant Client, if `$HOME` is not writable, then the ADR base is `/var/tmp/oradiag_chuck` and the ADR home could be `/var/tmp/oradiag_chuck/diag/clients/user_chuck/host_4144260688_11`.

    Temporary directories in the Windows operating system, searched in this order:

    1.  `%TMP%`

    2.  `%TEMP%`

    3.  `%USERPROFILE%`

    4.  Windows system directory

If none of these directory choices are available and writable, or the ADR base is not created and there are no diagnostics.

**See Also:**

- [About Oracle Instant Client](instant-client.md)

- [Oracle Database Net Services Reference](../netrf/index.md)

#### 3.8.3 Using ADRCI

ADRCI is a command-line tool that enables you to view diagnostic data within the ADR and to package incident and problem information into a zip file for Oracle Support to use.

You can use ADRCI interactively and from a script. A problem is a critical error in OCI or the client. Each problem has a problem key. An incident is a single occurrence of a problem and is identified by a unique numeric incident ID. Each incident has a problem key that is a set of attributes: the `ORA` error number, error parameter values, and other information. Two incidents have the same root cause if their problem keys match.

What follows is a launch of ADRCI in a Linux system, a use of the `HELP` command for the `SHOW` `BASE` command, and then the use of the `SHOW` `BASE` command with the option `-PRODUCT` `CLIENT`, which is necessary for OCI applications. The ADRCI commands are case-insensitive. User input is shown in bold.

    % adrci

    ADRCI: Release 12.2.0.0.0 - Development on Wed Dec 2 18:26:29 2015
    Copyright (c) 1982, 2015, Oracle.  All rights reserved. ADR base = "/u01/app/oracle/log"


    adrci> help show base

      Usage: SHOW BASE [-product <product_name>]

      Purpose: Show the current ADR base setting.

      Options:
        [-product <product_name>]: This option allows users to show the
        given product's ADR Base location. The current registered products are
        "CLIENT" and "ADRCI".

      Examples:
        show base -product client
        show base

    adrci> show base -product client
    ADR base = "/u01/app/oracle/log"

Next, the `SET` `BASE` command is described:

    adrci> help set base

      Usage:  SET BASE <base_str> | -product <product_name>

      Purpose: Set the ADR base to use in the current ADRCI session.
               If there are valid ADR homes under the base, all homes will
               will be added to the current ADRCI session.

      Arguments:
        <base_str>: It is the ADR base directory, which is a system-dependent
        directory path string.
        -product <product_name>: This option allows users to set the
        given product's ADR Base location. The current registered products are
        "CLIENT" and "ADRCI".

      Notes:
        On platforms that use "." to signify current working directory,
        it can be used as base_str.

      Example:
        set base /net/sttttd1/scratch/someone/view_storage/someone_v1/log
        set base -product client
        set base .

    adrci> quit

When `ADRCI` is started, the default ADR base is for the `rdbms` server. `$ORACLE_HOME` is set to `"/u01/app/oracle/"`:

    % adrci

    ADRCI: Release 12.2.0.0.0 - Development on Wed Dec 2 18:26:29 2015

    Copyright (c) 1982, 2015, Oracle.  All rights reserved.

    ADR base = "/u01/app/oracle/log"
     adrci>

For OCI application incidents you must check and set the base:

    adrci> show base -product client
    ADR base is "/u01/app/oracle/log"
    adrci> set base /home/chuck_13/oradiag_chuck

For Instant Client there is no `$ORACLE_HOME`, so the default base is the user's home directory:

    adrci> show base -product client
    ADR base is "/home/chuck_13/oradiag_chuck"
    adrci> set base /home/chuck/oradiag_chuck
    adrci> show incidents

    ADR Home = /home/chuck/oradiag_chuck/diag/clients/user_chuck/host_4144260688_11:
    *************************************************************************
    INCIDENT_ID    PROBLEM_KEY           CREATE_TIME
    -------------------------------------------------------------------------
    1                     oci 24550 [6]              2015-12-02 17:20:02.803697 -07:00
    1 rows fetched

    adrci>

**See Also:**

[About Oracle Instant Client](instant-client.md)

[Oracle Database Utilities](../sutil/oracle-adr-command-interpreter-adrci.md) for an introduction to ADRCI

#### 3.8.4 Controlling ADR Creation and Disabling Fault Diagnosability Using sqlnet.ora

Describes how to control ADR creation and disabling fault diagnosability using sqlnet.ora.

To disable diagnosability, turn off diagnostics by setting the following parameters in `sqlnet.ora` (the default is `TRUE`):

    DIAG_ADR_ENABLED=FALSE
    DIAG_DDE_ENABLED=FALSE

To turn off the OCI signal handler and reenable standard operating system failure processing, place the following parameter setting in `sqlnet.ora`:

    DIAG_SIGHANDLER_ENABLED=FALSE

As noted previously, `ADR_BASE` is used in `sqlnet.ora` to set the location of the ADR base.

Oracle Database client contains advanced features for diagnosing issues, including the ability to dump diagnostic information when important errors are detected. By default, these dumps are restricted to a small subset of available information, to ensure that application data is not dumped. However, in many installations, secure locations for dump files may be configured, ensuring the privacy of such logs. In such cases, it is recommended to turn on full dumps; this can greatly speed resolution of issues. Full dumps can be enabled by adding the following line to the `sqlnet.ora` file used by your Oracle Database client installation:

    DIAG_RESTRICTED=FALSE

To verify that diagnosability features are working correctly:

1.  Upgrade your application to use the latest client libraries.
2.  Start your application.
3.  Check the file `sqlnet.log` in your application's `TNS_ADMIN` directory for error messages indicating that diagnosability could not be started (normally this is due to invalid directory names or permissions).

**See Also:**

- [Oracle Database Net Services Reference](../netrf/index.md) for the ADR parameter settings in `sqlnet.ora`

- [Oracle Database Net Services Administrator's Guide](../netag/troubleshooting-oracle-net-services.md) for more information about the structure of ADR

------------------------------------------------------------------------



Footnote Legend

Footnote 1:

Returns an `ORA-01805` error when timezone files on the client and server do not match (regions are not synchronized); returns `OCI_SUCCESS` when region time zone values are the same (represent the same instant in UTC), though the `TIME ZONE` offsets are different.
