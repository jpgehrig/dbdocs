## 8 Oracle Connection Manager Parameters

This chapter provides a complete listing of the `cman.ora` file configuration parameters.

- Overview of Oracle Connection Manager Configuration File
  Oracle Connection Manager configuration information is stored in the `cman.ora` file.
- Oracle Connection Manager Parameters
  This section lists and describes the following `cman.ora` file parameters:
- Oracle Connection Manager in Traffic Director Mode Parameters
  This section lists and describes the `cman.ora` file parameters.
- ADR Diagnostic Parameters for Oracle Connection Manager
  The diagnostic data for critical errors is quickly captured and stored in the ADR for Oracle Connection Manager.
- Non-ADR Diagnostic Parameters for Oracle Connection Manager
  This section lists the parameters used when ADR is disabled:

### 8.1 Overview of Oracle Connection Manager Configuration File

Oracle Connection Manager configuration information is stored in the `cman.ora` file.

#### Oracle Connection Manager Configuration File

Oracle Connection Manager configuration information consists of the following elements:

- Protocol address of the Oracle Connection Manager listener

- Access control parameters

- Performance parameters

By default, the `cman.ora` file is located in the `ORACLE_HOME``/network/admin` directory. You can also store the `cman.ora` file in the following locations:

- The directory specified by the `TNS_ADMIN` environment variable or registry value.
- On Linux and UNIX operating systems, the global configuration directory. For example, on the Oracle Solaris operating system, this directory is `/var/opt/oracle`.
- `ORACLE_BASE_HOME``/network/admin` directory.
- `ORACLE_HOME``/network/admin` directory.

Example 8-1 Sample cman.ora File

    CMAN=
      (CONFIGURATION=
        (ADDRESS=(PROTOCOL=tcp)(HOST=proxysvr)(PORT=1521))
        (RULE_LIST=
          (RULE=(SRC=192.0.2.32/27)(DST=sales-server)(SRV=*)(ACT=accept))
            (ACTION_LIST=(AUT=on)(MCT=120)(MIT=30)))
          (RULE=(SRC=foo)(DST=hr-server)(SRV=cmon)(ACT=accept)))
        (PARAMETER_LIST=
          (MAX_GATEWAY_PROCESSES=8)
          (MIN_GATEWAY_PRCESSSES=3)
          (DIAG_ADR_ENABLED=ON)
          (ADR_BASE=/oracle/log)))

#### cman.ora File Sections

- Listening address: Preceded by `ADDRESS=`, this section contains information pertinent to the listener. The `ADDRESS` parameter is required.

- Rule list: Preceded by `RULE_LIST=`, this section contains rule information. The`RULE` parameter is listed in the rule list section of the file. The `RULE` parameter is required.

- Rule Group: Preceded by `RULE_GROUP=`, this section contains` rule_list` grouped by service names. You can use either the `rule_group` syntax or the `rule_list` syntax.

- Parameter list: Preceded by `PARAMETER_LIST=`, this section contains all other parameters including those listed in " ADR Diagnostic Parameters for Oracle Connection Manager", and "Non-ADR Diagnostic Parameters for Oracle Connection Manager".

  The following parameters are allowed in the parameter list section of the `cman.ora` file. The default values are bold. To override the default setting for a parameter, enter the parameter and a nondefault value.

  `ASO_AUTHENTICATION_FILTER={``off` `| on}`

  `ADMIN_GROUP=``user_group`

  `CONNECTION_STATISTICS={``no` `| yes}`

  `EVENT_GROUP={init_and_term | memory_ops | conn_hdlg | proc_mgmt | reg_and_load | wake_up | timer | cmd_proc | relay}`

  `IDLE_TIMEOUT=``0` or greater

  `INBOUND_CONNECT_TIMEOUT=0` or greater. The default value is 60.

  `LOG_DIRECTORY=``log_directory`. The default value is `ORACLE_HOME/network/log`.

  `LOG_LEVEL={off | user | admin |` `support``}`

  `MAX_CMCTL_SESSIONS= `Any positive number. The default value is 4.

  `MAX_CONNECTIONS=` A value between 1 and 1024. The default value is 256.

  `MAX_GATEWAY_PROCESSES=` Any number greater than the minimum number of gateway processes up to 64. The default value is 16.

  `MIN_GATEWAY_PROCESSES=` Any positive number less than or equal to 64. Must be less than or equal to the maximum number of gateway processes. The default value is 2.

  `OUTBOUND_CONNECT_TIMEOUT=``0` or greater

  `PASSWORD_``instance_name``=` Value is the encrypted instance password, if one has been set. The default value is no value.

  `SESSION_TIMEOUT=``0` or greater

  `TRACE_DIRECTORY=``trace_directory`. The default value is `ORACLE_HOME/network/trace`.

  `TRACE_FILELEN= `Any positive number. The default value is 0 (zero).

  `TRACE_FILENO= `Any positive number. The default value is 0 (zero).

  `TRACE_LEVEL={``off` `| user | admin | support}`

  `TRACE_TIMESTAMP={``off`` | on}`

  **Note:**

  You cannot add the parameter `PASSWORD_``instance_name` directly to the `cman.ora` file. The parameter is added using the `SAVE_PASSWD` command.

Parameter List Section of a cman.ora File

    (PARAMETER_LIST=
          (ASO_AUTHENTICATION_FILTER=ON)
          (ADMIN_GROUP=dba)
          (CONNECTION_STATISTICS=NO)
          (EVENT_GROUP=INIT_AND_TERM,MEMORY_OPS,PROCESS_MGMT)
          (IDLE_TIMEOUT=30)
          (INBOUND_CONNECT_TIMEOUT=30)
          (LOG_DIRECTORY=/home/user/network/admin/log)
          (LOG_LEVEL=SUPPORT)
          (MAX_CMCTL_SESSIONS=6)
          (MAX_CONNECTIONS=512)
          (MAX_GATEWAY_PROCESSES=10)
          (MIN_GATEWAY_PROCESSES=4)
          (OUTBOUND_CONNECT_TIMEOUT=30)
          (SESSION_TIMEOUT=60)
          (TRACE_DIRECTORY=/home/user/network/admin/trace)
          (TRACE_FILELEN=100)
          (TRACE_FILENO=2)
          (TRACE_LEVEL=SUPPORT)
          (TRACE_TIMESTAMP=ON)
          (VALID_NODE_CHECKING_REGISTRATION=ON)
          (REGISTRATION_EXCLUDED_NODES = 10.1.26.*)
          (REGISTRATION_INVITED_NODES = 10.1.35.*)
    )

**Parent topic:** Oracle Connection Manager Parameters

### 8.2 Oracle Connection Manager Parameters

This section lists and describes the following `cman.ora` file parameters:

- ADDRESS
  The `ADDRESS` networking parameter specifies the protocol address of Oracle Connection Manager.
- ADMIN_GROUP
  The `ADMIN_GROUP` parameter of the `cman.ora` file specifies the user group that can perform the Oracle Connection Manager (CMAN) administration.
- ASO_AUTHENTICATION_FILTER
  It is a networking parameter for Oracle Connection Manager. It instructs Oracle Connection Manager to check the connection requests for Secure Network Services (SNS).
- COMPRESSION
  The `COMPRESSION` parameter of the `cman.ora` file enables or disables data compression.
- COMPRESSION_LEVELS
  The `COMPRESSION_LEVELS` networking parameter of the `cman.ora` file specifies the CPU usage and compression ratio.
- COMPRESSION_THRESHOLD
  The `COMPRESSION_THRESHOLD` parameter of the `cman.ora` file specifies the minimum data size for which compression is required.
- CONNECTION_STATISTICS
  `CONNECTION_STATISTICS` networking parameter of the `cman.ora` file specifies whether the `SHOW_CONNECTIONS` command displays connection statistics.
- EVENT_GROUP
  `EVENT_GROUP` networking parameter of the `cman.ora` file specifies which event groups are logged.
- EXPIRE_TIME
  The `EXPIRE_TIME` networking parameter of `cman.ora` file specifies a time interval, in minutes, to send a check to verify that client/gateway connections are active.
- IDLE_TIMEOUT
- INBOUND_CONNECT_TIMEOUT
  The `INBOUND_CONNECT_TIMEOUT` parameter of the `cman.ora` file specifies the time limit that the Oracle Connection Manager listener waits for a valid connection before timing out.
- LOG_FILE_NUM
  The `LOG_FILE_NUM` networking parameter of the `cman.ora` file specifies the number of log file segments.
- LOG_FILE_SIZE
  `LOG_FILE_SIZE` networking parameter of the`cman.ora` file specifies the size of each log file segment.
- MAX_ALL_CONNECTIONS
- MAX_CMCTL_SESSIONS
  The `MAX_CMCTL_SESSIONS` parameter of the `cman.ora` file specifies the maximum number of concurrent local or remote sessions.
- MAX_CONNECTIONS
  The `MAX_CONNECTIONS` parameter of the `cman.ora` file specifies the maximum number of connection slots that a gateway process can handle.
- MAX_GATEWAY_PROCESSES
- MAX_REG_CONNECTIONS
- MIN_GATEWAY_PROCESSES
- OUTBOUND_CONNECT_TIMEOUT
- PASSWORD_instance_name
- REGISTRATION_EXCLUDED_NODES
  The Oracle Connection Manager parameter file (`cman.ora`) REGISTRATION_EXCLUDED_NODES specifies the list of nodes that cannot register with the listener.
- REGISTRATION_INVITED_NODES
  The Oracle Connection Manager parameter file (`cman.ora`) `REGISTRATION_EXCLUDED_NODES` parameter specifies the list of node that can register with the listener.
- RULE
  The `RULE` parameter of the `cman.ora` file specifies an access control rule list to filter incoming connections.
- SDU
  Use the `SDU` parameter to specify the session data unit (SDU) size for connections.
- SERVICE_RATE
  The SERVICE_RATE parameter of cman.ora file specifies incoming connection rate that is allowed per service for an instance.
- SESSION_TIMEOUT
  The `SESSION_TIMEOUT` parameter of the `cman.ora` file specifies the maximum time in seconds allowed for a user session.
- SSL_CIPHER_SUITES
  Use the `SSL_CIPHER_SUITES` parameter to control the combination of authentication, encryption, and data integrity algorithms used by Transport Layer Security (TLS).
- SSL_CLIENT_AUTHENTICATION
  Use the `SSL_CLIENT_AUTHENTICATION` parameter to specify whether a client is authenticated using Transport Layer Security (TLS).
- SSL_VERSION
  Use the `SSL_VERSION` parameter to define valid Transport Layer Security (TLS) versions to be used for connections.
- TRACE_FILE
- USE_SID_AS_SERVICE
  The `USE_SID_AS_SERVICE` Oracle Connection Manager parameter enables the system identifier (SID) in the connect descriptor to be interpreted as a service name when a user attempts a database connection.
- VALID_NODE_CHECKING_REGISTRATION
  The `VALID_NODE_CHECKING_REGISTRATION` parameter of the `cman.ora` file specifies whether valid node checking registration is performed.
- WALLET_LOCATION

**Parent topic:** Oracle Connection Manager Parameters

#### 8.2.1 ADDRESS

The `ADDRESS` networking parameter specifies the protocol address of Oracle Connection Manager.

##### Purpose

To specify the protocol address of Oracle Connection Manager.

##### Syntax

`(ADDRESS=(PROTOCOL=``protocol``)(HOST=``host_name``)(PORT=``port_number``)`

##### Example

    (ADDRESS=(PROTOCOL=tcp)(HOST=sales-server)(PORT=1521)

**Parent topic:** Oracle Connection Manager Parameters

#### 8.2.2 ADMIN_GROUP

The `ADMIN_GROUP` parameter of the `cman.ora` file specifies the user group that can perform the Oracle Connection Manager (CMAN) administration.

##### Purpose

To allow users of the specified group to perform CMAN administration operations. Users of the group are allowed to run Oracle Connection Manager control utility commands, such as show status, show services, show gateways, show rules, and so on.

##### Usage Notes

You can include `ADMIN_GROUP` parameter in the `PARAMETER_LIST` section of the `cman.ora` file to specify the group that can run CMAN control utility commands and carry out administration operations.

##### Default

By default, only `CMAN` user can perform the connection manager administration operations.

##### Example

`ADMIN_GROUP=dba`

**Related Topics**

- [Oracle Connection Manager Control Utility Commands](oracle-connection-manager-control-utility.md)

**Parent topic:** Oracle Connection Manager Parameters

#### 8.2.3 ASO_AUTHENTICATION_FILTER

It is a networking parameter for Oracle Connection Manager. It instructs Oracle Connection Manager to check the connection requests for Secure Network Services (SNS).

##### Purpose

To specify whether Oracle Database security authentication settings must be used by the client.

##### Usage Notes

The global setting can be overridden by a rule-level setting in `ACTION_LIST`.

##### Values

- `on` to instruct Oracle Connection Manager to reject connection requests that are not using Secure Network Services (SNS). SNS is part of Oracle Database security.

- `off` to instruct Oracle Connection Manager not to check for SNS between the client and server. This is the default.

**Parent topic:** Oracle Connection Manager Parameters

#### 8.2.4 COMPRESSION

The `COMPRESSION` parameter of the `cman.ora` file enables or disables data compression.

##### Purpose

To enable or disable data compression. If both the Oracle Connection Manager and the other end (server or client or Oracle Connection Manager) have this parameter set to `ON`, then compression is used for the connection.

##### Default

`off`

##### Values

- `on` to enable data compression.

- `off` to disable data compression.

##### Example

`COMPRESSION=on`

**Parent topic:** Oracle Connection Manager Parameters

#### 8.2.5 COMPRESSION_LEVELS

The `COMPRESSION_LEVELS` networking parameter of the `cman.ora` file specifies the CPU usage and compression ratio.

##### Purpose

To specify the compression level.

##### Usage Notes

The compression levels are used at the time of negotiation to verify which levels are used at both ends, and select one level.

##### Default

`low`

##### Values

- `low` for low CPU usage and a low compression ratio.

- `high` for high CPU usage and a high compression ratio.

Example 8-2 Example

`COMPRESSION_LEVELS=high,low`

**Parent topic:** Oracle Connection Manager Parameters

#### 8.2.6 COMPRESSION_THRESHOLD

The `COMPRESSION_THRESHOLD` parameter of the `cman.ora` file specifies the minimum data size for which compression is required.

##### Purpose

To specify the minimum data size, in bytes, for which compression is required.

##### Usage Notes

Compression is not be done if the size of the data to be sent is less than this value.

##### Default

`1024 bytes`

##### Example

`COMPRESSION_THRESHOLD=1024`

**Parent topic:** Oracle Connection Manager Parameters

#### 8.2.7 CONNECTION_STATISTICS

`CONNECTION_STATISTICS` networking parameter of the `cman.ora` file specifies whether the `SHOW_CONNECTIONS` command displays connection statistics.

##### Purpose

To specify whether the `SHOW_CONNECTIONS` command displays connection statistics.

##### Usage Notes

The global setting can be overridden by a rule-level setting in `ACTION_LIST`.

##### Values

- `yes` to display statistics.

- `no` to not display statistics. This is the default.

**Parent topic:** Oracle Connection Manager Parameters

#### 8.2.8 EVENT_GROUP

`EVENT_GROUP` networking parameter of the `cman.ora` file specifies which event groups are logged.

##### Purpose

To specify which event groups are logged.

##### Usage Notes

Multiple events may be designated using a comma-delimited list.

##### Values

- `alert` for alert notifications.

- `cmd_proc` for command processing.

- `conn_hdlg` for connection handling.

- `init_and_term` for initialization and termination.

- `memory_ops` for memory operations.

- `proc_mgmt` for process management.

- `reg_and_load` for registration and load update.

- `relay` for events associated with connection control blocks.

- `timer` for gateway timeouts.

- `wake_up` for events related to Connection Manager Administration (CMADMIN) wake-up queue.

**Note:**

The event group `ALERT` cannot be turned off.

**Parent topic:** Oracle Connection Manager Parameters

#### 8.2.9 EXPIRE_TIME

The `EXPIRE_TIME` networking parameter of `cman.ora` file specifies a time interval, in minutes, to send a check to verify that client/gateway connections are active.

##### Purpose

To specify a time interval, in minutes, to send a check to verify that client/server connections are active.

##### Usage Notes

Setting a value greater than `0` ensures that connections are not left open indefinitely, due to an unusual client termination. If the system supports TCP keepalive tuning, then Oracle Net Services automatically uses the enhanced detection model, and tunes the TCP keepalive parameters

If the probe finds a terminated connection, or a connection that is no longer in use, then it returns an error, causing the server process to exit.

This parameter is primarily intended for the database server, which typically handles multiple connections at any one time.

Limitations on using this terminated connection detection feature are:

- It is not allowed on bequeathed connections.

- Though very small, a probe packet generates additional traffic that may downgrade network performance.

- Depending on which operating system is in use, the server may need to perform additional processing to distinguish the connection probing event from other events that occur. This can also result in degraded network performance.

##### Values

- `0`: To disable terminated connection detection.

- Any number greater than `0`: To enable terminated connection detection. The number equals the time interval in minutes.

##### Default

`0`

Example 8-3 Example

`EXPIRE_TIME=10`

**Parent topic:** Oracle Connection Manager Parameters

#### 8.2.10 IDLE_TIMEOUT

##### Purpose

To specify the amount of time that an established connection can remain active without transmitting data.

##### Usage Notes

The global setting can be overridden by a rule-level setting in `ACTION_LIST`.

##### Values

- `0` to disable the timeout. This is the default.

- Any number greater than 0 to enable the timeout. The number equals the timeout period in seconds.

**Parent topic:** Oracle Connection Manager Parameters

#### 8.2.11 INBOUND_CONNECT_TIMEOUT

The `INBOUND_CONNECT_TIMEOUT` parameter of the `cman.ora` file specifies the time limit that the Oracle Connection Manager listener waits for a valid connection before timing out.

##### Purpose

To specify how long, in seconds, the Oracle Connection Manager listener waits for a valid connection from a client or another instance of Oracle Connection Manager.

##### Values

- `60 sec` is the default. Use value `0` to disable timeout.

- Any number greater than `0` to enable the timeout. The number equals the timeout period in seconds.

##### Example

    INBOUND_CONNECT_TIMEOUT=30

**Parent topic:** Oracle Connection Manager Parameters

#### 8.2.12 LOG_FILE_NUM

The `LOG_FILE_NUM` networking parameter of the `cman.ora` file specifies the number of log file segments.

##### Purpose

To specify the number of log file segments. At any point of time there can be only `n` log file segments where `n` is `LOG_FILE_NUM` and if the log grows beyond this number, then the older segments are deleted.

##### Default

No default. Number of segments grow indefinitely, if not specified or set to zero.

##### Value

Any integer value up to the maximum integer.

##### Example

    LOG_FILE_NUM=3

**Parent topic:** Oracle Connection Manager Parameters

#### 8.2.13 LOG_FILE_SIZE

`LOG_FILE_SIZE` networking parameter of the`cman.ora` file specifies the size of each log file segment.

##### Purpose

To specify the size of each log file segment. The size is in `MB`.

##### Default

`300 MB`

##### Values

Any integer value.

Example 8-4 Example

`LOG_FILE_SIZE=10`

**Parent topic:** Oracle Connection Manager Parameters

#### 8.2.14 MAX_ALL_CONNECTIONS

##### Purpose

To specify the maximum number of concurrent registration and client connection sessions that can be supported by Oracle Connection Manager.

##### Usage Notes

This number includes registration connections from databases, and ongoing client connection establishment requests. After a connection is established, the clients do not maintain a connection to the listener. This limit only applies to client connections that are in the initial connection establishment phase from a listener perspective.

##### Default

Operating system-specific

##### Example

    MAX_ALL_CONNECTIONS=40

**Parent topic:** Oracle Connection Manager Parameters

#### 8.2.15 MAX_CMCTL_SESSIONS

The `MAX_CMCTL_SESSIONS` parameter of the `cman.ora` file specifies the maximum number of concurrent local or remote sessions.

##### Purpose

To specify the maximum number of concurrent local or remote sessions of the Oracle Connection Manager control utility allowable for a given instance.

##### Usage Notes

One of the sessions must be a local session.

##### Value

Any number of sessions can be designated.

##### Example

    MAX_CMCTL_SESSIONS=6

**Parent topic:** Oracle Connection Manager Parameters

#### 8.2.16 MAX_CONNECTIONS

The `MAX_CONNECTIONS` parameter of the `cman.ora` file specifies the maximum number of connection slots that a gateway process can handle.

##### Purpose

To specify the maximum number of connection slots that a gateway process can handle.

##### Values

Any number in the range of `1` to `1024`.

##### Default

The default value is `256`.

##### Example

    MAX_CONNECTIONS=100

**Parent topic:** Oracle Connection Manager Parameters

#### 8.2.17 MAX_GATEWAY_PROCESSES

##### Purpose

To specify the maximum number of gateway processes that an instance of Oracle Connection Manager supports.

##### Values

The number designated must be greater than the minimum number of gateway processes. The maximum is 64.

**Parent topic:** Oracle Connection Manager Parameters

#### 8.2.18 MAX_REG_CONNECTIONS

##### Purpose

To specify the maximum number of concurrent registration connection sessions that can be supported by Oracle Connection Manager.

##### Default

512

##### Example

    MAX_REG_CONNECTIONS=20

**Parent topic:** Oracle Connection Manager Parameters

#### 8.2.19 MIN_GATEWAY_PROCESSES

##### Purpose

To specify the minimum number of gateway processes that an instance of Oracle Connection Manager supports.

##### Values

Any number of sessions can be designated up to 64.

**Parent topic:** Oracle Connection Manager Parameters

#### 8.2.20 OUTBOUND_CONNECT_TIMEOUT

##### Purpose

To specify the length of time in seconds that the Oracle Connection Manager instance waits for a valid connection to be established with the database server or with another Oracle Connection Manager instance.

##### Values

- `60` to disable the timeout. This is the default.

- Any number greater than 0 to enable the timeout. The number equals the timeout period in seconds.

**Parent topic:** Oracle Connection Manager Parameters

#### 8.2.21 PASSWORD\_instance_name

##### Purpose

To specify the encrypted instance password, if one has been set.

**Parent topic:** Oracle Connection Manager Parameters

#### 8.2.22 REGISTRATION_EXCLUDED_NODES

The Oracle Connection Manager parameter file (`cman.ora`) REGISTRATION_EXCLUDED_NODES specifies the list of nodes that cannot register with the listener.

##### Purpose

To specify the list of nodes that cannot register with the listener.

##### Usage Notes

The list can include host names or CIDR notation for IPv4 and IPv6 addresses. The wildcard format (`*`) is supported for IPv4 addresses. The presence of a host name in the list results in the inclusion of all IP addresses mapped to the host name. The host name should be consistent with the public network interface.

If the `REGISTRATION_INVITED_NODES` parameter and the `REGISTRATION_EXCLUDED_NODES` parameter are set, then the `REGISTRATION_EXCLUDED_NODES` parameter is ignored.

##### Values

Valid nodes and subnet IP addresses or names.

##### Example

    REGISTRATION_EXCLUDED_NODES = 10.1.26.*, 10.16.40.0/24, \
                                           2001:DB8:3eff:fe38, node2

**Parent topic:** Oracle Connection Manager Parameters

#### 8.2.23 REGISTRATION_INVITED_NODES

The Oracle Connection Manager parameter file (`cman.ora`) `REGISTRATION_EXCLUDED_NODES` parameter specifies the list of node that can register with the listener.

##### Purpose

To specify the list of node that can register with the listener.

##### Usage Notes

The list can include host names or CIDR notation for IPv4 and IPv6 addresses. The wildcard format (`*`) is supported for IPv4 addresses. The presence of a host name in the list results in the inclusion of all IP addresses mapped to the host name. The host name should be consistent with the public network interface.

If the `REGISTRATION_INVITED_NODES` parameter and the `REGISTRATION_EXCLUDED_NODES` parameter are set, then the `REGISTRATION_EXCLUDED_NODES` parameter is ignored.

##### Values

Valid nodes and subnet IP addresses or names.

##### Example

    REGISTRATION_INVITED_NODES = 10.1.35.*, 10.1.34.0/24, \
                                          2001:DB8:fe38:7303, node1

**Parent topic:** Oracle Connection Manager Parameters

#### 8.2.24 RULE

The `RULE` parameter of the `cman.ora` file specifies an access control rule list to filter incoming connections.

##### Purpose

To specify an access control rule list to filter incoming connections.

##### Usage Notes

A rule list specifies which connections are accepted, rejected, or dropped.

If no rules are specified, then all connections are rejected.

The source and destination can be a host name, IP address, or subnet mask.

There must be at least one rule for client connections and one rule for CMCTL connections. Omitting one or the other results in the rejection of all connections for the rule type omitted. The last rule in the example that follows is a CMCTL rule.

Oracle Connection Manager does not support wildcards for partial IP addresses. If you use a wildcard, then use it in place of a full IP address. The IP address of the client may, for example, be (SRC=\*).

Oracle Connection Manager supports only the `/nn` notation for subnet addresses. In the first rule in Example “Sample cman.ora File”, /27 represents a subnet mask that comprises 27 left-most bits.

##### Values

This parameter is listed in the rule list section of the `cman.ora` file preceded by `RULE_LIST=`.

##### Syntax

    (RULE_LIST=
      (RULE=
        (SRC=host)
        (DST=host)
        (SRV=service_name)
        (ACT={accept|reject|drop})
        (ACTION_LIST=AUT={on|off}
        ((CONN_STATS={yes|no})(MCT=time)(MIT=time)(MOCT=time)))
      (RULE= ...))

##### Additional Parameters

The `RULE` parameter filters a connection or group of connections using the following parameters:

`SRC`: The source host name or IP address of the client.

`DST`: The destination server host name or IP address of the database server.

`SRV`: The database service name of Oracle Database obtained from the `SERVICE_NAME` parameter in the initialization parameter file.

`ACT`: The action for the connection request. Use `accept` to accept incoming requests, `reject` to reject incoming requests, or `drop` to reject incoming requests without sending an error message.

`ACTION_LIST`: The rule-level parameter settings for some parameters. These parameters are as follows:

- `AUT`: Oracle Database security authentication on client side.

- `CONN_STATS`: Log input and output statistics.

- `MCT`: Maximum connect time.

- `MIT`: Maximum idle timeout.

- `MOCT`: Maximum outbound connect time.

Rule-level parameters override their global counterparts.

##### Example

    (RULE_LIST=
      (RULE=
        (SRC=client1-pc)
        (DST=sales-server)
        (SRV=sales.us.example.com)
        (ACT=reject))
      (RULE=
        (SRC=192.0.2.45)
        (DST=192.0.2.200)
        (SRV=db1)
        (ACT=accept))
      (RULE=
        (SRC=sale-rep)
        (DST=sales1-server)
        (SRV=cmon)
        (ACT=accept)))

**Parent topic:** Oracle Connection Manager Parameters

#### 8.2.25 SDU

Use the `SDU` parameter to specify the session data unit (SDU) size for connections.

##### Purpose

To specify the SDU size, in bytes, for connections

##### Usage Notes

Oracle Connection Manager can negotiate large SDU with client and server when configured. When the configured values of client, database server, and Oracle Connection Manager do not match for a session, the least value of all the three values is used.

##### Default

`8192` bytes (8 KB)

##### Value

`512` to `2097152` bytes

##### Example

`SDU=32768`

**Parent topic:** Oracle Connection Manager Parameters

#### 8.2.26 SERVICE_RATE

The SERVICE_RATE parameter of cman.ora file specifies incoming connection rate that is allowed per service for an instance.

##### Purpose

To specify incoming connection rate that is allowed per service for an instance.

##### Usage Notes

Any user-specified value greater than `0` sets the maximum limit on the number of new connections per service-instance handled by the proxy listener every second. Listener rejects connections after it reaches the maximum limit. Client side connection failure is reported with “TNS:listener: rate limit reached”.

##### Values

- `0` to disable service rate limit. This is the default.

- Any number greater than 0 to enable service rate limit.

Example 8-5 Example

`SERVICE_RATE=10`

**Parent topic:** Oracle Connection Manager Parameters

#### 8.2.27 SESSION_TIMEOUT

The `SESSION_TIMEOUT` parameter of the `cman.ora` file specifies the maximum time in seconds allowed for a user session.

##### Purpose

To specify the maximum time in seconds allowed for a user session.

##### Usage Notes

The global setting can be overridden by a rule-level setting in `ACTION_LIST`.

##### Values

- `0` to disable the timeout. This is the default.

- Any number greater than `0` to enable the timeout. The number equals the timeout period in seconds.

##### Example

    SESSION_TIMEOUT=60

**Parent topic:** Oracle Connection Manager Parameters

#### 8.2.28 SSL_CIPHER_SUITES

Use the `SSL_CIPHER_SUITES` parameter to control the combination of authentication, encryption, and data integrity algorithms used by Transport Layer Security (TLS).

##### Purpose

To control the combination of authentication, encryption, and data integrity algorithms used by [Transport Layer Security (TLS)](glossary.md). By default, the strongest protocol and cipher are negotiated between the database client and server. Setting this parameter will override the default behavior. You must use this parameter only if you have internal security controls that dictate the usage of certain protocol versions.

##### Usage Notes

Enclose the `SSL_CIPHER_SUITES` parameter value in parentheses. Otherwise, the cipher suite setting does not parse correctly.

##### Default

None

##### Values

Approved ciphers compatible with TLS 1.2:

- `TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384`
- `TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256`
- `TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384`
- `TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256`
- `TLS_DHE_RSA_WITH_AES_256_GCM_SHA384`
- `TLS_DHE_RSA_WITH_AES_128_GCM_SHA256`

Deprecated ciphers compatible with TLS 1.2:

- `TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384`
- `TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256`
- `TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA384`
- `TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA256`
- `TLS_RSA_WITH_AES_256_GCM_SHA384`
- `TLS_RSA_WITH_AES_256_CBC_SHA256`
- `TLS_RSA_WITH_AES_128_GCM_SHA256`
- `TLS_RSA_WITH_AES_128_CBC_SHA256`
- `TLS_ECDH_RSA_WITH_AES_256_GCM_SHA384`
- `TLS_ECDH_RSA_WITH_AES_128_GCM_SHA256`
- `TLS_ECDH_RSA_WITH_AES_256_CBC_SHA384`
- `TLS_ECDH_RSA_WITH_AES_128_CBC_SHA256`
- `TLS_ECDH_ECDSA_WITH_AES_256_GCM_SHA384`
- `TLS_ECDH_ECDSA_WITH_AES_128_GCM_SHA256`
- `TLS_ECDH_ECDSA_WITH_AES_256_CBC_SHA384`
- `TLS_ECDH_ECDSA_WITH_AES_128_CBC_SHA256`
- `TLS_DHE_RSA_WITH_AES_256_CBC_SHA256`
- `TLS_DHE_RSA_WITH_AES_128_CBC_SHA256`
- `TLS_DH_anon_WITH_AES_256_GCM_SHA384`
- `TLS_DH_anon_WITH_AES_128_GCM_SHA256 `

Deprecated ciphers compatible with TLS 1.0, TLS 1.1, and TLS 1.2:

- `TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA`
- `TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA`
- `TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA`
- `TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA`
- `TLS_RSA_WITH_AES_256_CBC_SHA`
- `TLS_RSA_WITH_AES_128_CBC_SHA`
- `TLS_ECDH_RSA_WITH_AES_256_CBC_SHA`
- `TLS_ECDH_RSA_WITH_AES_128_CBC_SHA`
- `TLS_ECDH_ECDSA_WITH_AES_256_CBC_SHA`
- `TLS_ECDH_ECDSA_WITH_AES_128_CBC_SHA`
- `TLS_DHE_RSA_WITH_AES_256_CBC_SHA`
- `TLS_DHE_RSA_WITH_AES_128_CBC_SHA`
- `TLS_ECDHE_RSA_WITH_RC4_128_SHA`
- `TLS_ECDHE_ECDSA_WITH_RC4_128_SHA`
- `TLS_ECDH_RSA_WITH_RC4_128_SHA`
- `TLS_ECDH_ECDSA_WITH_RC4_128_SHA`
- `SSL_RSA_WITH_RC4_128_SHA`
- `SSL_RSA_WITH_RC4_128_MD5`
- `TLS_ECDHE_ECDSA_WITH_NULL_SHA`
- `TLS_ECDHE_RSA_WITH_NULL_SHA`
- `TLS_ECDH_ECDSA_WITH_NULL_SHA`
- `TLS_ECDH_RSA_WITH_NULL_SHA`
- `SSL_RSA_WITH_NULL_SHA`
- `SSL_RSA_WITH_NULL_MD5`
- `SSL_DH_anon_WITH_RC4_128_MD5`

Deprecated ciphers compatible with TLS 1.0 and TLS 1.1:

- `TLS_ECDHE_RSA_WITH_3DES_EDE_CBC_SHA`
- `TLS_ECDHE_ECDSA_WITH_3DES_EDE_CBC_SHA`
- `TLS_ECDH_ECDSA_WITH_3DES_EDE_CBC_SHA`
- `TLS_ECDH_RSA_WITH_3DES_EDE_CBC_SHA`
- `SSL_RSA_WITH_3DES_EDE_CBC_SHA`
- `SSL_DH_anon_WITH_3DES_EDE_CBC_SHA`

**Note:**

The `DH_anon` cipher suites do not provide authentication of the communicating parties, and can be vulnerable to man-in-the-middle attacks. Oracle recommends that you do not use these cipher suites to protect sensitive data.

##### Examples

    SSL_CIPHER_SUITES=(TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384)

    SSL_CIPHER_SUITES=(TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384, TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256)

**Related Topics**

- [Set the TLS Cipher Suites on the Server](../dbseg/configuring-secure-sockets-layer-authentication.md)
- [Set the TLS Cipher Suites on the Client](../dbseg/configuring-secure-sockets-layer-authentication.md)

**Parent topic:** Oracle Connection Manager Parameters

#### 8.2.29 SSL_CLIENT_AUTHENTICATION

Use the `SSL_CLIENT_AUTHENTICATION` parameter to specify whether a client is authenticated using Transport Layer Security (TLS).

##### Purpose

To specify whether a client is authenticated using [Transport Layer Security (TLS)](glossary.md).

##### Usage Notes

The database server authenticates the client. Therefore, this value should be set to `false`. If this parameter is set to `true`, then the listener attempts to authenticate the client, which can result in a failure.

##### Default

true

##### Values

    true | false

##### Example

    SSL_CLIENT_AUTHENTICATION=false

**See Also:**

[Oracle Database Security Guide](../dbseg/kerberos-ssl-and-radius-authentication-parameters.md)

**Parent topic:** Oracle Connection Manager Parameters

#### 8.2.30 SSL_VERSION

Use the `SSL_VERSION` parameter to define valid Transport Layer Security (TLS) versions to be used for connections.

##### Purpose

To define the version of TLS that must run on the systems with which the database server communicates. By default, the database server and client negotiate the strongest security protocol. Oracle does not recommend modifying this parameter, unless your security requirements mandate the usage of certain protocol versions.

##### Usage Notes

Clients, listeners, and database servers must use compatible versions. Modify this parameter only when necessary to enforce the use of the more secure TLS protocol and not allow clients that only work with the older TLS protocols. If you need to specify TLS 1.0 or TLS 1.1, then also include TLS 1.2 to allow more secure connections. The current default uses TLS 1.2, which is the version required for multiple security compliance requirements.

If you set `SSL_VERSION` to `undetermined`, then the most secure TLS protocol version is used. You can use the `SSL_VERSION=undetermined` setting in the connect string for a specific connection to override the `SSL_VERSION` value configured in the `sqlnet.ora` file.

If you do not set `SSL_VERSION` to any value, then all the supported TLS protocol versions are tried starting with the most secure version. This is typically the most common configuration, ensuring that the strongest protocol is chosen during TLS negotiation.

##### Default

`undetermined`

##### Values

`undetermined` \| `1.0` \| `1.1` \| `1.2`

The version numbers correspond to the TLS versions, such as TLSv1.0, TLSv1.1, and TLSv1.2.

**Note:**

The `sqlnet.ora` parameter `ADD_SSLV3_TO_DEFAULT` has no impact on this parameter.

##### Syntax and Examples

- To specify a single TLS version:
      SSL_VERSION=TLS_protocol_version

  For example:
      SSL_VERSION=1.2

- To specify multiple TLS versions, use the `or` operator as follows:

      SSL_VERSION=TLS_protocol_version1 or TLS_protocol_version2

  For example:
      SSL_VERSION=1.1 or 1.2

      SSL_VERSION=1.0 or 1.1 or 1.2

**Related Topics**

- [Set the Required TLS Version on the Server](../dbseg/configuring-secure-sockets-layer-authentication.md)
- [Set the Required TLS Version on the Client](../dbseg/configuring-secure-sockets-layer-authentication.md)

**Parent topic:** Oracle Connection Manager Parameters

#### 8.2.31 TRACE_FILE

##### Purpose

To specify the directory for Oracle Connection Manager trace files.

**Parent topic:** Oracle Connection Manager Parameters

#### 8.2.32 USE_SID_AS_SERVICE

The `USE_SID_AS_SERVICE` Oracle Connection Manager parameter enables the system identifier (SID) in the connect descriptor to be interpreted as a service name when a user attempts a database connection.

##### Purpose

To enable the system identifier (SID) in the connect descriptor to be interpreted as a service name when a user attempts a database connection.

##### Usage Notes

Database clients with earlier releases of Oracle Database that have hard-coded connect descriptors can use this parameter to connect to a container or pluggable database.

For an Oracle container database, the client must specify a service name in order to connect to it. Setting this parameter to `on` instructs the Oracle Connection Manager listener to use the SID in the connect descriptor as a service name and connect the client to the specified database.

##### Values

- `off` (default value)

- `on`

Example 8-6 Example

`USE_SID_AS_SERVICE=on`

**Parent topic:** Oracle Connection Manager Parameters

#### 8.2.33 VALID_NODE_CHECKING_REGISTRATION

The `VALID_NODE_CHECKING_REGISTRATION` parameter of the `cman.ora` file specifies whether valid node checking registration is performed.

##### Purpose

To determine whether valid node checking registration is performed, and if the subnet is allowed.

##### Usage Notes

When set to `on`, valid node checking registration is performed at the listener for any incoming registration request, and only local IP addresses are allowed.

##### Default

`on`

##### Values

- `off | 0` to specify valid node checking registration is off, and no checking is performed.

- `on | 1 | local` to specify valid node checking registration is on, and all local IP addresses can register. If a list of invited nodes is set, then all IP addresses, host names, or subnets in the list as well as local IP addresses are allowed.

- `subnet | 2` to specify valid node checking registration is on, and all machines in the local subnets are allowed to register. If a list of invited nodes is set, then all nodes in the local subnets as well as all IP addresses, host names and subnets in the list are allowed.

##### Example

    VALID_NODE_CHECKING_REGISTRATION=on

**Parent topic:** Oracle Connection Manager Parameters

#### 8.2.34 WALLET_LOCATION

##### Purpose

To specify the location of wallets. Wallets are certificates, keys, and trustpoints processed by SSL.

##### Usage Notes

The key/value pair for Microsoft certificate store (MCS) omits the `METHOD_DATA` parameter because MCS does not use wallets. Instead, Oracle PKI (public key infrastructure) applications obtain certificates, trustpoints and private keys directly from the user's profile.

If an Oracle wallet is stored in the Microsoft Windows registry and the wallet's key (`KEY)` is `SALESAPP`, then the storage location of the encrypted wallet is `HKEY_CURRENT_USER\SOFTWARE\ORACLE\WALLETS\SALESAPP\EWALLET.P12`. The storage location of the decrypted wallet is `HKEY_CURRENT_USER\SOFTWARE\ORACLE\WALLETS\SALESAPP\CWALLET.SSO.`

**Note:**

This parameter must be specified outside Oracle Connection Manager alias

##### Syntax

The syntax depends on the wallet, as follows:

- Oracle wallets on the file system:

      WALLET_LOCATION=
        (SOURCE=
          (METHOD=file)
          (METHOD_DATA=
             (DIRECTORY=directory)
             [(PKCS11=TRUE/FALSE)]))

- Microsoft certificate store:

      WALLET_LOCATION=
        (SOURCE=
           (METHOD=mcs))

- Oracle wallets in the Microsoft Windows registry:

      WALLET_LOCATION=
         (SOURCE=
            (METHOD=reg)
            (METHOD_DATA=
               (KEY=registry_key)))

- Entrust wallets:

      WALLET_LOCATION=
         (SOURCE=
            (METHOD=entr)
            (METHOD_DATA=
               (PROFILE=file.epf)
               (INIFILE=file.ini)))

##### Additional Parameters

`WALLET_LOCATION` supports the following parameters:

- `SOURCE`: The type of storage for wallets, and storage location.

- `METHOD`: The type of storage.

- `METHOD_DATA`: The storage location.

- `DIRECTORY`: The location of Oracle wallets on file system.

- `KEY`: The wallet type and location in the Microsoft Windows registry.

- `PROFILE`: The Entrust profile file (`.epf`).

- `INIFILE`: The Entrust initialization file (`.ini`).

##### Default

None

##### Values

    true | false

##### Examples

Oracle wallets on file system:

    WALLET_LOCATION=
      (SOURCE=
          (METHOD=file)
          (METHOD_DATA=
             (DIRECTORY=/etc/oracle/wallets/databases)))

Microsoft certificate store:

    WALLET_LOCATION=
       (SOURCE=
         (METHOD=mcs))


Oracle Wallets in the Microsoft Windows registry:

    WALLET_LOCATION=
       (SOURCE=
         (METHOD=REG)
         (METHOD_DATA=
            (KEY=SALESAPP)))

Entrust Wallets:

    WALLET_LOCATION=
       (SOURCE=
         (METHOD=entr)
         (METHOD_DATA=
           (PROFILE=/etc/oracle/wallets/test.epf)
           (INIFILE=/etc/oracle/wallets/test.ini)))

**Parent topic:** Oracle Connection Manager Parameters

### 8.3 Oracle Connection Manager in Traffic Director Mode Parameters

This section lists and describes the `cman.ora` file parameters.

- SERVICE_AFFINITY
  Use the `cman.ora` parameter `SERVICE_AFFINITY` to modify the default load distribution mechanism for Oracle Connection Manager in Traffic Director Mode.
- TDM
- TDM_BIND_THREAD
- TDM_DATATYPE_CHECK
- TDM_PRCP_MAX_CALL_WAIT_TIME
- TDM_PRCP_MAX_TXN_CALL_WAIT_TIME
- TDM_SHARED_THREADS_MAX
- TDM_SHARED_THREADS_MIN
- TDM_THREADING_MODE

**Parent topic:** Oracle Connection Manager Parameters

#### 8.3.1 SERVICE_AFFINITY

Use the `cman.ora` parameter `SERVICE_AFFINITY` to modify the default load distribution mechanism for Oracle Connection Manager in Traffic Director Mode.

##### Purpose

To configure load distribution mechanism for Oracle Connection Manager in Traffic Director Mode. By default, Oracle Connection Manager in Traffic Director Mode uses service affinity to select a gateway for routing incoming connection requests. All new connection requests are routed to the gateways associated with database services.

##### Usage Notes

If you set this parameter to `ON`, then all new connection requests are routed to the gateways associated with database services.

If you set this parameter to `OFF`, then all new connection requests are routed to the least-loaded gateways.

When using Proxy Resident Connection Pooling (PRCP), Oracle recommends that you set the `SERVICE_AFFINITY` parameter to `OFF` for better performance and resource utilization of gateway processes.

##### Values

`ON` \| `OFF`

##### Default

`ON`

##### Example

    SERVICE_AFFINITY = {ON | OFF}

**Related Topics**

- [Oracle Database Net Services Administrator's Guide](../netag/configuring-oracle-connection-manager.md)
- [Oracle Multitenant Administrator's Guide](../admin/creating-and-configuring-an-oracle-database.md)

**Parent topic:** Oracle Connection Manager in Traffic Director Mode Parameters

#### 8.3.2 TDM

##### Purpose

To configure Oracle Connection Manager to act as Oracle Connection Manager in Traffic Director Mode.

##### Default

`FALSE`

##### Values

- `TRUE`

- `FALSE`

##### Example

`tdm = TRUE`

**Parent topic:** Oracle Connection Manager in Traffic Director Mode Parameters

#### 8.3.3 TDM_BIND_THREAD

##### Purpose

To make the application connection hold on to the TDM thread and has different implications with and without PRCP. This parameter only applies when `TDM_THREADING_MODE` is set to `SHARED`.

##### Usage Notes

Without PRCP, setting this parameter to `yes` makes the application connection hold on the TDM worker thread as long as there is a transaction in progress.

With PRCP, setting this parameter to `yes` makes the application connection hold on to the TDM thread from the time `OCISessionGet` is done by the application till it does an `OCISessionRelease`.

##### Default

`no`

##### Values

- `yes`

- `no`

##### Example

`TDM_BIND_THREAD = yes`

**Parent topic:** Oracle Connection Manager in Traffic Director Mode Parameters

#### 8.3.4 TDM_DATATYPE_CHECK

##### Purpose

To validate all the inbound data to the database, of the data type `NUMBER, DATE, TIMESTAMP, TIMESTAMP WITH LOCAL TIMEZONE, TIMESTAMP WITH TIMEZONE, BLOB, CLOB, BFILE, UROWID` and `REF`. The following error is received by the application if there is any problem with the data sent to the Oracle Connection Manager in Traffic Director Mode.

`ORA-03137: malformed TTC packet from client rejected: [3101]`

##### Usage Notes

Turning `ON/OFF` this parameter enables or disables the data validation.

##### Default

`OFF`

##### Values

- `ON`

- `OFF`

##### Example

`tdm_datatype_check={ON | OFF}`

**Parent topic:** Oracle Connection Manager in Traffic Director Mode Parameters

#### 8.3.5 TDM_PRCP_MAX_CALL_WAIT_TIME

##### Purpose

To record the maximum time of inactivity, in seconds, for a client after obtaining a session from the PRCP pool. This parameter is applicable when the Oracle Connection Manager in Traffic Director Mode is configured to have Proxy Resident Connection Pool.

##### Usage Notes

After obtaining a session from the PRCP pool, if the client application does not issue a database call for the time specified by `TDM_PRCP_MAX_CALL_WAIT_TIME` parameter, then the PRCP session is freed and the client connection is terminated. As a result, if the client application attempts a round trip call on such a connection, then it receives an `ORA-3113` or `ORA-3115` error.

##### Default

30 seconds

##### Values

Any non negative value. However, Oracle recommends not to use a value of `0` as that implies that a connection can acquire a PRCP session for an indefinite amount of time

**Parent topic:** Oracle Connection Manager in Traffic Director Mode Parameters

#### 8.3.6 TDM_PRCP_MAX_TXN_CALL_WAIT_TIME

##### Purpose

To record the maximum time of inactivity, in seconds, for a client after it obtains a session from the Proxy Resident Connection Pool and starts a transaction. This parameter is applicable when the Oracle Connection Manager in Traffic Director Mode is configured to have PRCP.

##### Usage Notes

If the client application does not issue a database call for the time specified by `TDM_PRCP_MAX_TXN_CALL_WAIT_TIME` parameter while in a transaction, the PRCP session is freed, the transaction is rolled back, and the client connection is terminated. As a result, if the client application attempts a round trip call on such a connection, then it receives an `ORA-3113` or `ORA-3115` error.

##### Default

`0`

##### Values

Any nonnegative value. However, it is recommended not to use a value of`0` as it implies that a connection can acquire a PRCP session for an indefinite amount of time.

**Parent topic:** Oracle Connection Manager in Traffic Director Mode Parameters

#### 8.3.7 TDM_SHARED_THREADS_MAX

##### Purpose

To configure the maximum number of threads that an Oracle Connection Manager process in Traffic Director Mode should have, when `tdm_threading_mode` is set to `SHARED`.

##### Values

Any number can be designated for the maximum number of threads. For `DEDICATED` mode, the maximum number of threads is same as the maximum number of connections. In `SHARED` mode, though there is no fixed upper bound, it should ideally be proportional to the load.

**Parent topic:** Oracle Connection Manager in Traffic Director Mode Parameters

#### 8.3.8 TDM_SHARED_THREADS_MIN

##### Purpose

To configure the minimum number of threads that an Oracle Connection Manager process in Traffic Director Mode should have, when `tdm_threading_mode` is set to `SHARED`.

##### Values

Any number can be designated for the minimum number of threads. For `SHARED` mode, there is no limit enforced. However, the number of threads should be proportional to the load.

**Parent topic:** Oracle Connection Manager in Traffic Director Mode Parameters

#### 8.3.9 TDM_THREADING_MODE

##### Purpose

To configure the usage of threads by the Oracle Connection Manager in Traffic Director Mode.

##### Usage Notes

If this parameter is set to `DEDICATED`, then a worker thread is spawned for each inbound connection and the maximum number of threads is determined by the` max_connections` parameter

If this parameter is set to `SHARED`, then a shared pool of worker threads handle all inbound connections. The minimum number of worker threads is specified by the `tdm_shared_threads_min` setting and the maximum number of worker threads is specified by the `tdm_shared_threads_max` setting. The thread pool is internally managed within these bounds.

##### Default

`DEDICATED`

##### Values

- `DEDICATED`

- `SHARED`

##### Example

`tdm_threading_mode={DEDICATED | SHARED}`

`tdm_shared_threads_min = 4`

`tdm_shared_threads_max = 5`

**Parent topic:** Oracle Connection Manager in Traffic Director Mode Parameters

### 8.4 ADR Diagnostic Parameters for Oracle Connection Manager

The diagnostic data for critical errors is quickly captured and stored in the ADR for Oracle Connection Manager.

Since Oracle Database 11g, Oracle Database includes an advanced fault diagnosability infrastructure for preventing, detecting, diagnosing, and resolving problems. The problems are critical errors such as those caused by database code bugs, metadata corruption, and customer data corruption.

When a critical error occurs, it is assigned an incident number, and diagnostic data for the error, such as traces and dumps, are immediately captured and tagged with the incident number. The data is then stored in the [Automatic Diagnostic Repository (ADR)](glossary.md), a file-based repository outside the database.

This section describes the parameters used when ADR is enabled. ADR is enabled by default. Non-ADR parameters listed in the `cman.ora` file are ignored when ADR is enabled.

- ADR_BASE
  It is a diagnostic parameter in the `cman.ora` file and it specifies the base directory to store tracing and logging incidents when ADR is enabled.
- DIAG_ADR_ENABLED
  `DIAG_ADR_ENABLED` diagnostic parameter of the `cman.ora` file indicates whether ADR tracing is enabled.
- LOG_LEVEL
- TRACE_LEVEL
- TRACE_TIMESTAMP

**Parent topic:** Oracle Connection Manager Parameters

#### 8.4.1 ADR_BASE

It is a diagnostic parameter in the `cman.ora` file and it specifies the base directory to store tracing and logging incidents when ADR is enabled.

##### Purpose

To specify the base directory to store tracing and logging incidents when ADR is enabled.

##### Default

The default is `ORACLE_BASE`, or `ORACLE_HOME/log` if `ORACLE_BASE` is not defined.

##### Values

Any valid directory path to a directory with write permission.

Example 8-7 Example

`ADR_BASE=/oracle/network/trace`

**Parent topic:** ADR Diagnostic Parameters for Oracle Connection Manager

#### 8.4.2 DIAG_ADR_ENABLED

`DIAG_ADR_ENABLED` diagnostic parameter of the `cman.ora` file indicates whether ADR tracing is enabled.

##### Purpose

To indicate whether ADR tracing is enabled.

##### Usage Notes

When the `DIAG_ADR_ENABLED` parameter is set to `OFF`, then non-ADR file tracing is used.

##### Values

`on` \| `off`

Example 8-8 Example

`DIAG_ADR_ENABLED=on`

**Parent topic:** ADR Diagnostic Parameters for Oracle Connection Manager

#### 8.4.3 LOG_LEVEL

##### Purpose

To specify the level of logging performed by Oracle Connection Manager.

##### Usage Notes

This parameter is also applicable when non-ADR logging is used.

The following log files are used with Oracle Connection Manager:

- `instance-name_pid``.log` for the listener.

- `instance-name_``cmadmin``_pid``.log` for CMADMIN.

- `instance-name_``cmgw``_pid``.log` for the gateway processes.

The log files are located in the `ORACLE_HOME/network/log` directory.

##### Default

off or 0

##### Values

- `off` or `0` for no log output.

- `user` or `4` for user log information.

- `admin` or `10` for administration log information.

- `support` or `16` for Oracle Support Services log information.

##### Example

    LOG_LEVEL=admin

**Parent topic:** ADR Diagnostic Parameters for Oracle Connection Manager

#### 8.4.4 TRACE_LEVEL

##### Purpose

To specify the trace level for the Oracle Connection Manager instance.

##### Usage Notes

This parameter is also applicable when non-ADR tracing is used.

The following trace files are used with Oracle Connection Manager:

- `instance-name_pid``.trc` for the listener.

- `instance-name_``cmadmin``_pid``.trc` for CMADMIN.

- `instance-name_``cmgw``_pid``.trc` for the gateway processes.

The log files are located in the `ORACLE_HOME/network/log` directory.

##### Default

off

##### Values

- `off` for no trace output.

- `user` for user trace information.

- `admin` for administration trace information.

- `support` for Oracle Support Services trace information.

##### Example

    TRACE_LEVEL=admin

**Parent topic:** ADR Diagnostic Parameters for Oracle Connection Manager

#### 8.4.5 TRACE_TIMESTAMP

##### Purpose

To add a time stamp in the form of `dd-mmm-yyyy hh:mi:ss:mil` to every trace event in the trace file for the listener.

##### Usage Notes

This parameter is used with the TRACE_LEVEL parameter. This parameter is also applicable when non-ADR tracing is used.

##### Default

on

##### Values

- `on` or `true`

- `off` or `false`

##### Example

    TRACE_TIMESTAMP=true

**Parent topic:** ADR Diagnostic Parameters for Oracle Connection Manager

### 8.5 Non-ADR Diagnostic Parameters for Oracle Connection Manager

This section lists the parameters used when ADR is disabled:

- LOG_DIRECTORY
- TRACE_DIRECTORY
- TRACE_FILELEN
- TRACE_FILENO

**Parent topic:** Oracle Connection Manager Parameters

#### 8.5.1 LOG_DIRECTORY

##### Purpose

To specify the location of Oracle Connection Manager log files.

##### Usage Notes

Use this parameter when ADR is not enabled.

##### Default

    ORACLE_BASE_HOME/network/log

##### Values

Any valid directory path to a directory with write permission.

##### Example

    LOG_DIRECTORY=/oracle/network/log

**Parent topic:** Non-ADR Diagnostic Parameters for Oracle Connection Manager

#### 8.5.2 TRACE_DIRECTORY

##### Purpose

To specify the location of the Oracle Connection Manager trace files.

##### Usage Notes

Use this parameter when ADR is not enabled.

##### Default

    ORACLE_BASE_HOME/network/trace

##### Values

Any valid directory path to a directory with write permission.

##### Example

    TRACE_DIRECTORY=/oracle/network/admin/trace

**Parent topic:** Non-ADR Diagnostic Parameters for Oracle Connection Manager

#### 8.5.3 TRACE_FILELEN

##### Purpose

To specify the size, in KB, of the trace file.

##### Usage Notes

When the size is met, the trace information is written to the next file. The number of files is specified with the TRACE_FILENO parameter. Any size can be designated. Use this parameter when ADR is not enabled.

##### Default

Unlimited

##### Example

    TRACE_FILELEN=100

**Parent topic:** Non-ADR Diagnostic Parameters for Oracle Connection Manager

#### 8.5.4 TRACE_FILENO

##### Purpose

To specify the number of trace files for Oracle Connection Manager tracing.

##### Usage Notes

When this parameter is set along with the TRACE_FILELEN parameter, trace files are used in a cyclical fashion. The first file is filled first, then the second file, and so on. When the last file has been filled, the first file is reused, and so on. Any number of files can be designated.

The trace file names are distinguished from one another by their sequence number. For example, if this parameter is set to `3`, then the gateway trace files would be named `instance-name_``cmgw1``_pid``.trc`, `instance_name_``cmgw2``_pid``.trc` and `instance_name_``cmgw3``_pid``.trc`.

In addition, trace events in the trace files are preceded by the sequence number of the file. Use this parameter when ADR is not enabled.

##### Default

1

##### Example

    TRACE_FILENO=3

**Parent topic:** Non-ADR Diagnostic Parameters for Oracle Connection Manager
