## 7 Oracle Net Listener Parameters in the listener.ora File

This chapter provides a complete listing of the `listener.ora` file configuration parameters.

- Overview of Oracle Net Listener Configuration File
  Oracle Net Listener configuration, stored in the `listener.ora` file, consists of these elements.
- Protocol Address Parameters
  This section describes the most common parameters used in protocol addresses. The `ADDRESS_LIST` parameter is also supported.
- Connection Rate Limiter Parameters
  The connection rate limiter feature in Oracle Net Listener enables a database administrator to limit the number of new connections handled by the listener. When this feature is enabled, Oracle Net Listener imposes a user-specified maximum limit on the number of new connections handled by the listener every second. Depending on the configuration, the rate can be applied to a collection of endpoints, or to a specific endpoint.
- Control Parameters
  This section describes the following parameters that control the behavior of the listener:
- ADR Diagnostic Parameters for Oracle Net Listener
  The diagnostic data for the critical errors is quickly captured and stored in the ADR for Oracle Net listener.
- Non-ADR Diagnostic Parameters for Oracle Net Listener
  This section lists the parameters used when ADR is disabled. The default value of `DIAG_ADR_ENABLED_``listener_name` is `on`. Therefore, the `DIAG_ADR_ENABLED_``listener_name` parameter must explicitly be set to `off` to use non-ADR tracing.
- Class of Secure Transports Parameters
  The class of secure transports (COST) parameters specify a list of transports that are considered secure for administration and registration of a particular listener.

### 7.1 Overview of Oracle Net Listener Configuration File

Oracle Net Listener configuration, stored in the `listener.ora` file, consists of these elements.

- Name of the listener

- Protocol addresses that the listener is accepting connection requests on

- Valid nodes that the listener allows to register with the database

- Database services

- Control parameters

Dynamic [service registration](glossary.md), eliminates the need for static configuration of supported services. However, static service configuration is required if you plan to use Oracle Enterprise Manager Cloud Control. For information about static service configuration, see [Oracle Database Net Services Administrator's Guide](../netag/enabling-advanced-features.md).

By default, the `listener.ora` file is located in the `ORACLE_HOME/network/admin` directory. The `listener.ora` file can also be stored the following locations:

- The directory specified by the `TNS_ADMIN` environment variable or registry value.

- On Linux and UNIX operating systems, it is the global configuration directory. For example, on the Oracle Solaris operating system, the directory is `/var/opt/oracle`. See [Oracle Database Global Data Services Concepts and Administration Guide](../gsmug/global-data-services-admin.md) for information about management of global services. Also refer to Oracle operating system-specific documentation.

- In the read-only Oracle home mode, the `listener.ora` file default location is `ORACLE_BASE_HOME``/network/admin`.

- In the read-only Oracle home mode, the parameters that default to `ORACLE_HOME` location change to default to `ORACLE_BASE_HOME` location.

It is possible to configure multiple listeners, each with a unique name, in one `listener.ora` file. Multiple listener configurations are possible because each of the top-level configuration parameters has a suffix of the listener name or is the listener name itself.

**Note:**

- It is often useful to configure multiple listeners in one `listener.ora` file. However, Oracle recommends running only one listener for each node in most customer environments.

- Oracle Net Services supports the IFILE parameter in the `listener.ora` file, with up to three levels of nesting. The parameter is added manually to the file. The following is an example of the syntax:

      IFILE=/tmp/listener_em.ora
      IFILE=/tmp/listener_cust1.ora
      IFILE=/tmp/listener_cust2.ora

  Refer to [Oracle Database Reference](../refrn/IFILE.md) for additional information.

Example 7-1 shows a `listener.ora` file for a listener named `LISTENER`, which is the default name of the listener.

Example 7-1 listener.ora File

    LISTENER=
      (DESCRIPTION=
        (ADDRESS_LIST=
          (ADDRESS=(PROTOCOL=tcp)(HOST=sale-server)(PORT=1521))
          (ADDRESS=(PROTOCOL=ipc)(KEY=extproc))))

**Parent topic:** Oracle Net Listener Parameters in the listener.ora File

### 7.2 Protocol Address Parameters

The [protocol address](glossary.md) section of the `listener.ora` file defines the protocol addresses on which the listener is accepting connection requests. This section describes the most common parameters used in protocol addresses. The `ADDRESS_LIST` parameter is also supported.

This section lists and describes the following parameters:

- ADDRESS
  The protocol `ADDRESS` parameter’s networking parameter is in the `listener.ora` file. It specifies the protocol address under the `DESCRIPTION` parameter for one listener.
- DESCRIPTION
  `DESCRIPTION` networking parameter of the listener.ora file contains listener protocol addresses.
- Firewall
- IP
  The protocol address parameter `IP` determine which IP address the listener listens on when a host name is specified
- QUEUESIZE
- RECV_BUF_SIZE
  Use the `RECV_BUF_SIZE` parameter to specify buffer space for session receive operations.
- SEND_BUF_SIZE
  Use the `SEND_BUF_SIZE` parameter to specify buffer space for session send operations.

**Parent topic:** Oracle Net Listener Parameters in the listener.ora File

#### 7.2.1 ADDRESS

The protocol `ADDRESS` parameter’s networking parameter is in the `listener.ora` file. It specifies the protocol address under the `DESCRIPTION` parameter for one listener.

##### Purpose

Specifies a single listener protocol address in the `DESCRIPTION` parameter

##### Usage Notes

Use this parameter to define the protocol, the host, and the port number for the listener.

##### Example

    listener_name=
     (DESCRIPTION=
      (ADDRESS_LIST=
       (ADDRESS=(PROTOCOL=tcp)(HOST=hr-server)(PORT=1521))
       (ADDRESS=(PROTOCOL=tcp)(HOST=sales-server)(PORT=1521))))

**Parent topic:** Protocol Address Parameters

#### 7.2.2 DESCRIPTION

`DESCRIPTION` networking parameter of the listener.ora file contains listener protocol addresses.

##### Purpose

To contain listener protocol addresses.

Example 7-2 Example

listener_name= (DESCRIPTION= (ADDRESS_LIST= (ADDRESS=(PROTOCOL=tcp)(HOST=hr-server)(PORT=1521)) (ADDRESS=(PROTOCOL=tcp)(HOST=sales-server)(PORT=1521))))

**Parent topic:** Protocol Address Parameters

#### 7.2.3 Firewall

##### Purpose

It can be set in endpoint to enable firewall functionality.

**Related Topics**

- [Oracle Database Net Services Administrator's Guide](../netag/configuring-and-administering-oracle-net-listener.md)

**Parent topic:** Protocol Address Parameters

#### 7.2.4 IP

The protocol address parameter `IP` determine which IP address the listener listens on when a host name is specified

##### Purpose

To determine which IP address the listener listens on when a host name is specified.

##### Usage Notes

This parameter is only applicable when the `HOST` parameter specifies a host name.

##### Values

- `first`

  Listen on the first IP address returned by the DNS resolution of the host name. If the user wants the listener to listen on the first IP to which the specified host name resolves, then the address must be qualified with `(IP=first)`.

- `v4_only`

  Listen only on IPv4 addresses.

- `v6_only`

  Listen only on IPv6 addresses.

##### Default

This feature is disabled by default.

##### Example

    listener_name=
     (DESCRIPTION=
      (ADDRESS=(PROTOCOL=tcp)(HOST=rancode1-vip)(PORT=1522)(IP=v6_only))

**Parent topic:** Protocol Address Parameters

#### 7.2.5 QUEUESIZE

##### Purpose

To specify the number of concurrent connection requests that the listener can accept on a TCP/IP or IPC listening endpoint (protocol address).

##### Usage Notes

The number of concurrent connection requests is dependent on the platform and listener usage scenarios. If the listener is heavily-loaded, then set the parameter to a higher number.

Put this parameter at the end of the protocol address with its value set to the expected number of concurrent connection requests.

##### Default

The default number of concurrent connection requests is operating system specific.

##### Example

    listener_name=
     (DESCRIPTION=
      (ADDRESS=(PROTOCOL=tcp)(HOST=hr-server)(PORT=1521)(QUEUESIZE=20)))

**See Also:**

[Oracle Database Net Services Administrator's Guide](../netag/configuring-and-administering-oracle-net-listener.md) for additional information about configuring this parameter

**Parent topic:** Protocol Address Parameters

#### 7.2.6 RECV_BUF_SIZE

Use the `RECV_BUF_SIZE` parameter to specify buffer space for session receive operations.

##### Purpose

To specify, in bytes, the buffer space for receive operations of sessions.

##### Usage Notes

Put this parameter under the `DESCRIPTION` parameter or at the end of the protocol address with its value set to the expected number of bytes.

This parameter is supported by the TCP/IP, TCP/IP with TLS, and SDP protocols.

**Note:**

Additional protocols might support this parameter on certain operating systems. Refer to the operating system-specific documentation for information about additional protocols that support this parameter.

##### Default

The default value for this parameter is operating system specific. The default for the Linux operating system is 87380 bytes.

##### Example

    listener_name=
      (DESCRIPTION=
        (ADDRESS_LIST=
          (ADDRESS=(PROTOCOL=tcp)(HOST=sales-server)(PORT=1521)
            (RECV_BUF_SIZE=11784))
          (ADDRESS=(PROTOCOL=ipc)(KEY=extproc)
            (RECV_BUF_SIZE=11784))))
    listener_name=
      (DESCRIPTION=
        (ADDRESS_LIST=
          (RECV_BUF_SIZE=11784))
          (ADDRESS=(PROTOCOL=tcp)(HOST=sales-server)(PORT=1521)
          (ADDRESS=(PROTOCOL=ipc)(KEY=extproc))))

**Related Topics**

- [Oracle Database Net Services Administrator's Guide](../netag/optimizing-performance.md)

**Parent topic:** Protocol Address Parameters

#### 7.2.7 SEND_BUF_SIZE

Use the `SEND_BUF_SIZE` parameter to specify buffer space for session send operations.

##### Purpose

To specify, in bytes, the buffer space for send operations of sessions.

##### Usage Notes

Put this parameter under the `DESCRIPTION` parameter or at the end of the protocol address.

This parameter is supported by the TCP/IP, TCP/IP with TLS, and SDP protocols.

**Note:**

Additional protocols might support this parameter on certain operating systems. Refer to operating system-specific documentation for additional information about additional protocols that support this parameter.

##### Default

The default value for this parameter is operating system specific. The default for the Linux operating system is 16 KB.

##### Example

    listener_name=
      (DESCRIPTION=
        (ADDRESS_LIST=
          (ADDRESS=(PROTOCOL=tcp)(HOST=sales-server)(PORT=1521)
           (SEND_BUF_SIZE=11280))
          (ADDRESS=(PROTOCOL=ipc)(KEY=extproc)
           (SEND_BUF_SIZE=11280))))
    listener_name=
      (DESCRIPTION=
        (SEND_BUF_SIZE=11280)
        (ADDRESS_LIST=
          (ADDRESS=(PROTOCOL=tcp)(HOST=sales-server)(PORT=1521)
          (ADDRESS=(PROTOCOL=ipc)(KEY=extproc))))

**Related Topics**

- [Oracle Database Net Services Administrator's Guide](../netag/optimizing-performance.md)

**Parent topic:** Protocol Address Parameters

### 7.3 Connection Rate Limiter Parameters

The connection rate limiter feature in Oracle Net Listener enables a database administrator to limit the number of new connections handled by the listener. When this feature is enabled, Oracle Net Listener imposes a user-specified maximum limit on the number of new connections handled by the listener every second. Depending on the configuration, the rate can be applied to a collection of endpoints, or to a specific endpoint.

This feature is controlled through the following `listener.ora` configuration parameters:

- CONNECTION_RATE_listener_name
  The `CONNECTION_RATE_``listener_name` configuration parameter of the`listener.ora` file specifies a global rate that is enforced across all listening endpoints that are rate-limited.
- RATE_LIMIT
  The `RATE_LIMIT` configuration parameter of the `listener.ora` file indicates that a particular listening endpoint is rate-limited.

**Parent topic:** Oracle Net Listener Parameters in the listener.ora File

#### 7.3.1 CONNECTION_RATE_listener_name

The `CONNECTION_RATE_``listener_name` configuration parameter of the`listener.ora` file specifies a global rate that is enforced across all listening endpoints that are rate-limited.

##### Purpose

To specify a global rate that is enforced across all listening endpoints that are rate-limited.

##### Usage Notes

When this parameter is specified, it overrides any endpoint-level numeric rate values that might be specified.

##### Syntax

`CONNECTION_RATE_``listener_name``=``number_of_connections_per_second`

**Parent topic:** Connection Rate Limiter Parameters

#### 7.3.2 RATE_LIMIT

The `RATE_LIMIT` configuration parameter of the `listener.ora` file indicates that a particular listening endpoint is rate-limited.

##### Purpose

To indicate that a particular listening endpoint is rate-limited.

##### Usage Notes

The parameter is specified in the `ADDRESS` section of the listener endpoint configuration.

##### Syntax

    LISTENER=
       (ADDRESS=(PROTOCOL=tcp)(HOST=)(PORT=1521)(RATE_LIMIT=yes))

- When the `RATE_LIMIT` parameter is set to `yes` for an endpoint, that endpoint is included in the enforcement of the global rate configured by the `CONNECTION_RATE_``listener_name` parameter. The global rate limit is enforced individually at each endpoint that has `RATE_LIMIT` set to `yes`.

- Dynamic endpoints for listeners managed by Oracle Clusterware have the `RATE_LIMIT` parameter set to `yes`.

- When the `RATE_LIMIT` parameter is set to a value greater than `0`, then the rate limit is enforced at that endpoint level.

##### Examples

The following examples use the `CONNECTION_RATE_``listener name` and `RATE_LIMIT` parameters.

Example 1

    CONNECTION_RATE_LISTENER=10

    LISTENER=
      (ADDRESS_LIST=
       (ADDRESS=(PROTOCOL=tcp)(HOST=)(PORT=1521)(RATE_LIMIT=yes))
       (ADDRESS=(PROTOCOL=tcp)(HOST=)(PORT=1522)(RATE_LIMIT=yes))
       (ADDRESS=(PROTOCOL=tcp)(HOST=)(PORT=1523)))

In the preceding example, the global rate of new connections is enforced separately for each endpoint. Connections through port 1521 are limited at 10 every second, and the connections through port 1522 are also separately limited at 10 every second. Connections through port 1523 are not limited.

Example 2

    LISTENER= (ADDRESS_LIST=
       (ADDRESS=(PROTOCOL=tcp)(HOST=)(PORT=1521)(RATE_LIMIT=5))
       (ADDRESS=(PROTOCOL=tcp)(HOST=)(PORT=1522)(RATE_LIMIT=10))
       (ADDRESS=(PROTOCOL=tcp)(HOST=)(PORT=1523))
       )

In the preceding example, the connection rates are enforced at the endpoint level. A maximum of 5 connections are processed through port 1521 every second. The limit for connections through port 1522 is 10 every second. Connections through port 1523 are not limited.

**Note:**

The global `CONNECTON_RATE_``listener_name` parameter is not specified in the preceding configuration. If it is specified, then the limits on ports 1521 and 1522 are ignored, and the global value is used instead.

**Parent topic:** Connection Rate Limiter Parameters

### 7.4 Control Parameters

This section describes the following parameters that control the behavior of the listener:

- ADMIN_RESTRICTIONS_listener_name
  The `listener.ora` control parameter `ADMIN_RESTRICTIONS_``listener_name` restricts runtime administration of the listener.
- ALLOW_MULTIPLE_REDIRECTS_listener_name
  The listener.ora control parameter `ALLOW_MULTIPLE_REDIRECTS_``listener_name` enables multiple redirects of the client.
- ENABLE_EXADIRECT_listener_name
- CRS_NOTIFICATION_listener_name
  `CRS_NOTIFICATION_``listener_name` control parameter of the `listener.ora` file sets notification to allow or disallow Cluster Ready Services (CRS) to manage the listener in an Oracle Real Application Clusters environment.
- DEDICATED_THROUGH_BROKER_LISTENER
  `DEDICATED_THROUGH_BROKER_LISTENER` networking parameter of the `listener.ora` file enables the server to spawn a thread or process when a connection to the database is requested through the listener.
- DEFAULT_SERVICE_listener_name
  `DEFAULT_SERVICE_``listener_name` control parameter of the `listener.ora` file enables users to connect to the database without having to specify a service name from the client side.
- INBOUND_CONNECT_TIMEOUT_listener_name
- LOCAL_REGISTRATION_ADDRESS_listener_name
- MAX_ALL_CONNECTIONS_listener_name
- MAX_REG_CONNECTIONS_listener_name
  Use the `MAX_REG_CONNECTIONS``_listener_name` parameter to specify the maximum number of concurrent registration connection sessions.
- REGISTRATION_EXCLUDED_NODES_listener_name
- REGISTRATION_INVITED_NODES_listener_name
- REMOTE_REGISTRATION_ADDRESS_listener_name
- SAVE_CONFIG_ON_STOP_listener_name
- SERVICE_RATE_listener_name
  The `SERVICE_RATE_listener_name` control parameter specifies incoming connection rate that is allowed per service for an instance.
- SSL_CIPHER_SUITES
  Use the `SSL_CIPHER_SUITES` parameter to control the combination of authentication, encryption, and data integrity algorithms used by Transport Layer Security (TLS).
- SSL_CLIENT_AUTHENTICATION
  Use the `SSL_CLIENT_AUTHENTICATION` parameter to specify whether a client is authenticated using Transport Layer Security (TLS).
- SSL_DISABLE_WEAK_EC_CURVES
  Use the `SSL_DISABLE_WEAK_EC_CURVES` parameter to disable the use of weak Elliptic Curve Cryptography (ECC) curves.
- SSL_VERSION
  Use the `SSL_VERSION` parameter to define valid Transport Layer Security (TLS) versions to be used for connections.
- SUBSCRIBE_FOR_NODE_DOWN_EVENT_listener_name
- USE_SID_AS_SERVICE_listener_name
- VALID_NODE_CHECKING_REGISTRATION_listener_name
  The listener.ora control parameter `VALID_NODE_CHECKING_REGISTRATION_``listener_name` determines if valid node checking registration is performed, or if the subnet is allowed.
- WALLET_LOCATION
  Use the `WALLET_LOCATION` parameter to specify the location of Oracle wallets.

**Parent topic:** Oracle Net Listener Parameters in the listener.ora File

#### 7.4.1 ADMIN_RESTRICTIONS\_listener_name

The `listener.ora` control parameter `ADMIN_RESTRICTIONS_``listener_name` restricts runtime administration of the listener.

##### Purpose

To restrict runtime administration of the listener.

##### Usage Notes

Setting `ADMIN_RESTRICTIONS_``listener_name``=on` disables the runtime modification of parameters in `listener.ora`. That is, the listener refuses to accept SET commands that alter its parameters. To change any of the parameters in `listener.ora`, including `ADMIN_RESTRICTIONS_``listener_name` itself, modify the `listener.ora` file manually and reload its parameters using the RELOAD command for the new changes to take effect without explicitly stopping and restarting the listener.

##### Default

`off`

##### Example

`ADMIN_RESTRICTIONS_listener=on`

[SET](listener-control-utility.md)

[RELOAD](listener-control-utility.md)

**Parent topic:** Control Parameters

#### 7.4.2 ALLOW_MULTIPLE_REDIRECTS\_listener_name

The listener.ora control parameter `ALLOW_MULTIPLE_REDIRECTS_``listener_name` enables multiple redirects of the client.

##### Purpose

To support multiple redirects of the client.

##### Usage Notes

This parameter should only be set on the SCAN listener on the Oracle Public Cloud. When set to `on`, multiple redirects of the client are allowed.

Do not set this parameter for a node listener if that is used as a SCAN listener.

##### Default

off

##### Values

`on | off`

##### Example

    ALLOW_MULTIPLE_REDIRECTS_listener=on

**Parent topic:** Control Parameters

#### 7.4.3 ENABLE_EXADIRECT\_listener_name

##### Purpose

To enable Exadirect protocol.

##### Usage Notes

The parameter enables Exadirect support.

##### Default

`Off`

##### Values

`on | off`

Example 7-3 Example

`ENABLE_EXADIRECT_listener=on`

**Parent topic:** Control Parameters

#### 7.4.4 CRS_NOTIFICATION_listener_name

`CRS_NOTIFICATION_``listener_name` control parameter of the `listener.ora` file sets notification to allow or disallow Cluster Ready Services (CRS) to manage the listener in an Oracle Real Application Clusters environment.

##### Purpose

To set notification.

##### Usage Notes

By default, the Oracle Net listener notifies Cluster Ready Services (CRS) when it is started or stopped. These notifications allow CRS to manage the listener in an Oracle Real Application Clusters environment. This behavior can be prevented by setting the `CRS_NOTIFICATION_``listener_name` parameter to `off`.

##### Default

`on`

##### Values

`on | off`

**Parent topic:** Control Parameters

#### 7.4.5 DEDICATED_THROUGH_BROKER_LISTENER

`DEDICATED_THROUGH_BROKER_LISTENER` networking parameter of the `listener.ora` file enables the server to spawn a thread or process when a connection to the database is requested through the listener.

##### Purpose

To enable the server to spawn a thread or process when a connection to the database is requested through the listener.

##### Default

`off`

##### Values

`on | off`

Example 7-4 Example

(Optional) Enter an example to illustrate your reference here.

**Parent topic:** Control Parameters

#### 7.4.6 DEFAULT_SERVICE_listener_name

`DEFAULT_SERVICE_``listener_name` control parameter of the `listener.ora` file enables users to connect to the database without having to specify a service name from the client side.

##### Purpose

To enable users to connect to the database without having to specify a service name from the client side.

##### Usage Notes

When a client tries to connect to the database, the connection request passes through the listener. The listener may be servicing several different databases. If a service name is configured in this parameter, then users may not necessarily need to specify a service name in the connect syntax. If a user specifies a service name, then the listener connects the user to that specific database, otherwise the listener connects to the service name specified by the `DEFAULT_SERVICE_``listener_name` parameter. For container databases, the client must explicitly specify the service name.

##### Default

There is no default value for the `DEFAULT_SERVICE_``listener_name` parameter. If this parameter is not configured and a user does not specify a fully-qualified service name in the connect syntax, then the connection attempt fails. This parameter only accepts one value.

Example 7-5 Example

`DEFAULT_SERVICE_listener=sales.us.example.com`

**Parent topic:** Control Parameters

#### 7.4.7 INBOUND_CONNECT_TIMEOUT\_listener_name

##### Purpose

To specify the time, in seconds, for the client to complete its connect request to the listener after the network connection had been established.

##### Usage Notes

If the listener does not receive the client request in the time specified, then it terminates the connection. In addition, the listener logs the IP address of the client and an `ORA-12525:TNS: listener has not received client's request in time allowed` error message to the `listener.log` file.

To protect both the listener and the database server, Oracle recommends setting this parameter in combination with the [SQLNET.INBOUND_CONNECT_TIMEOUT](parameters-for-the-sqlnet.ora.md) parameter in the `sqlnet.ora` file. When specifying values for these parameters, consider the following recommendations:

- Set both parameters to an initial low value.

- Set the value of the `INBOUND_CONNECT_TIMEOUT_``listener_name` parameter to a lower value than the `SQLNET.INBOUND_CONNECT_TIMEOUT` parameter.

For example, you can set the `INBOUND_CONNECT_TIMEOUT_``listener_name` parameter to 2 seconds and the `INBOUND_CONNECT_TIMEOUT` parameter to 3 seconds. If clients are unable to complete connections within the specified time due to system or network delays that are normal for the particular environment, then increment the time as needed.

##### Default

60 seconds

##### Example

    INBOUND_CONNECT_TIMEOUT_listener=2

**Parent topic:** Control Parameters

#### 7.4.8 LOCAL_REGISTRATION_ADDRESS_listener_name

##### Purpose

To secure registration requests through dedicated secure registration endpoints for local listeners. Service ACLs are accepted by listener only if `LOCAL_REGISTRATION_ADDRESS_`lsnr alias is configured. The parameter specifies the group that is allowed to send ACLs.

##### Usage Notes

The local registration endpoint accepts local registration connections from the specified group. All local registration requests coming on normal listening endpoints are redirected to the local registration endpoint. If the registrar is not a part of the group, then it cannot connect to the endpoint.

##### Default

`OFF`

##### Values

`ON, OFF, or IPC endpoint address with group`

When set to ON, listener defaults the group to `oinstall` on UNIX and `ORA_INSTALL` on Windows.

Example 7-6 Example

    LOCAL_REGISTRATION_ADDRESS_lsnr_alias = (address=(protocol=ipc)(group=xyz)) LOCAL_REGISTRATION_ADDRESS_lsnr_alias =ON

**Related Topics**

- Firewall
- [DBMS_SFW_ACL_ADMIN](../arpls/DBMS_SFW_ACL_ADMIN.md)

**Parent topic:** Control Parameters

#### 7.4.9 MAX_ALL_CONNECTIONS\_listener_name

##### Purpose

To specify the maximum number of concurrent registration and client connection sessions that can be supported by Oracle Net Listener.

##### Usage Notes

This number includes registration connections from databases, and ongoing client connection establishment requests. After a connection is established, the clients do not maintain a connection to the listener. This limit only applies to client connections that are in the initial connection establishment phase from a listener perspective.

##### Default

Operating system-specific

##### Example

    MAX_ALL_CONNECTIONS_listener=4096

**Parent topic:** Control Parameters

#### 7.4.10 MAX_REG_CONNECTIONS\_listener_name

Use the `MAX_REG_CONNECTIONS``_listener_name` parameter to specify the maximum number of concurrent registration connection sessions.

##### Purpose

To specify the maximum number of concurrent registration connection sessions that can be supported by Oracle Net Listener.

##### Default

`512`

##### Example

    MAX_REG_CONNECTIONS_listener=2048

**Parent topic:** Control Parameters

#### 7.4.11 REGISTRATION_EXCLUDED_NODES\_listener_name

##### Purpose

To specify the list of nodes that cannot register with the listener.

##### Usage Notes

The list can include host names or CIDR notation for IPv4 and IPv6 addresses. The wildcard format (`*`) is supported for IPv4 addresses. The presence of a host name in the list results in the inclusion of all IP addresses mapped to the host name. The host name should be consistent with the public network interface.

If the `REGISTRATION_INVITED_NODES_``listener_name` parameter and the `REGISTRATION_EXCLUDED_NODES_``listener_name` parameter are set, then the `REGISTRATION_EXCLUDED_NODES_``listener_name` parameter is ignored.

##### Values

Valid nodes and subnet IP addresses or names.

##### Example

    REGISTRATION_EXCLUDED_NODES_listener = (10.1.26.*, 10.16.40.0/24, \
                                           2001:DB8:3eff:fe38, node2)

**Parent topic:** Control Parameters

#### 7.4.12 REGISTRATION_INVITED_NODES\_listener_name

##### Purpose

To specify the list of node that can register with the listener.

##### Usage Notes

- The list can include host names or CIDR notation for IPv4 and IPv6 addresses. The wildcard format (`*`) is supported for IPv4 addresses. The presence of a host name in the list results in the inclusion of all IP addresses mapped to the host name. The host name should be consistent with the public network interface.

- If the `REGISTRATION_INVITED_NODES_``listener_name` parameter and the `REGISTRATION_EXCLUDED_NODES``_listener_name` parameter are set, then the `REGISTRATION_EXCLUDED_NODES_``listener_name` parameter is ignored.

- Starting with Oracle Grid Infrastructure 12c, for a SCAN listener, if the `VALID_NODE_CHECKING_REGISTRATION_``listener_name` and `REGISTRATION_INVITED_NODES_``listener_name` parameters are set in the `listener.ora` file, then the listener agent overwrites these parameters.

##### Values

Valid nodes and subnet IP addresses or names.

##### Example

    REGISTRATION_INVITED_NODES_listener = (10.1.35.*, 10.1.34.0/24, \
                                          2001:DB8:fe38:7303, node1)

**See Also:**

[Oracle Real Application Clusters Administration and Deployment Guide](../racad/introduction-to-oracle-rac.md) for information about valid node checking for registration

**Parent topic:** Control Parameters

#### 7.4.13 REMOTE_REGISTRATION_ADDRESS\_listener_name

##### Purpose

To secure registration requests through dedicated secure registration endpoints for SCAN listeners.

##### Usage Notes

The registration endpoint is on a private network within the cluster. All remote registration requests coming in on normal listening endpoints are redirected to the registration endpoint. Any system which is not a part of the cluster cannot connect to the endpoint. This feature is not supported when `ADMIN_RESTRICTIONS_``listener_name` is set to `ON` as the Cluster Ready Services agent configures the `remote_registration_address` dynamically at run time.

##### Default

This parameter is configured internally in listeners managed by Oracle Clusterware to restrict registrations to the private network. The value of this parameter should not be modified or specified explicitly. The only supported explicit setting is for turning this feature off by setting the value to `OFF`.

##### Values

`off`

##### Example

    REMOTE_REGISTRATION_ADDRESS_listener=off

**Parent topic:** Control Parameters

#### 7.4.14 SAVE_CONFIG_ON_STOP\_listener_name

##### Purpose

To specify whether runtime configuration changes are saved to the `listener.ora` file.

##### Usage Notes

When you set the parameter to `true`, any parameters that were modified while the listener was running using the Listener Control utility [SET](listener-control-utility.md) command are saved to the `listener.ora` file when the [STOP](listener-control-utility.md) command is issued. When you set the parameter to `false`, the Listener Control utility does not save the runtime configuration changes to the `listener.ora` file.

##### Default

false

##### Values

    true | false

##### Example

    SAVE_CONFIG_ON_STOP_listener=true

**Parent topic:** Control Parameters

#### 7.4.15 SERVICE_RATE_listener_name

The `SERVICE_RATE_listener_name` control parameter specifies incoming connection rate that is allowed per service for an instance.

##### Purpose

To specify incoming connection rate that is allowed per service for an instance.

##### Usage Notes

Any user-specified value greater than `0` sets the maximum limit on the number of new connections per service-instance handled by the proxy listener every second. Listener rejects connections after it reaches the maximum limit. Client side connection failure is reported with the “`TNS:listener: rate limit reached`” error.

##### Default

`0`

Example 7-7 Example

`SERVICE_RATE=10`

**Parent topic:** Control Parameters

#### 7.4.16 SSL_CIPHER_SUITES

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

**Parent topic:** Control Parameters

#### 7.4.17 SSL_CLIENT_AUTHENTICATION

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

**Parent topic:** Control Parameters

#### 7.4.18 SSL_DISABLE_WEAK_EC_CURVES

Use the `SSL_DISABLE_WEAK_EC_CURVES` parameter to disable the use of weak Elliptic Curve Cryptography (ECC) curves.

##### Purpose

To disable the use of weak ECC curves with key length less than 256 bits. You can set this parameter in the database server (`sqlnet.ora`), client (`sqlnet.ora` or `tnsnames.ora` connect string), or the listener (`listener.ora`).

##### Usage Notes

By default, this parameter is set to `FALSE` to enable the use of all ECC curves. If you want to enable the use of only Oracle approved curves with ECC curve key size of 256 bits or higher, then set this parameter to `TRUE`.

When set to `TRUE`, you can use only the following ECC curves:

- `secp256r1`

- `secp384r1`

- `secp521r1`

##### Values

- `TRUE` \| `ON` \| `YES` \| `1`: To enable only the Oracle approved ECC curves with minimum ECC curve key length of 256 bits

- `FALSE` \| `OFF` \| `NO` \| `0`: To enable all ECC curves

##### Default

`FALSE`

##### Examples

- In the `tnsnames.ora` file:

      net_service_name=
        (DESCRIPTION=
          (ADDRESS=(PROTOCOL=tcps)(HOST=sales-svr)(PORT=1521))
          (SECURITY=(SSL_DISABLE_WEAK_EC_CURVES=TRUE))
        )

- In the `sqlnet.ora` file or the `listener.ora` file:

      SSL_DISABLE_WEAK_EC_CURVES=TRUE

**Parent topic:** Control Parameters

#### 7.4.19 SSL_VERSION

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

**Parent topic:** Control Parameters

#### 7.4.20 SUBSCRIBE_FOR_NODE_DOWN_EVENT\_listener_name

##### Purpose

To subscribe to Oracle Notification Service (ONS) notifications for downed events.

##### Usage Notes

By default, the listener subscribes to the ONS node down event on startup, if ONS is available. This subscription enables the listener to remove the affected service when it receives node down event notification from ONS. The listener uses asynchronous subscription for the event notification. Alter this behavior by setting `SUBSCRIBE_FOR_NODE_DOWN_EVENT_``listener_name``=off` in `listener.ora`.

##### Default

on

##### Values

    on | off

**Parent topic:** Control Parameters

#### 7.4.21 USE_SID_AS_SERVICE\_listener_name

##### Purpose

To enable the system identifier (SID) in the connect descriptor to be interpreted as a service name when a user attempts a database connection.

##### Usage Notes

Database clients with earlier releases of Oracle Database that have hard-coded connect descriptors can use this parameter to connect to a container or pluggable database.

For an Oracle container database, the client must specify a service name in order to connect to it. Setting this parameter to `on` instructs the listener to use the SID in the connect descriptor as a service name and connect the client to the specified database.

##### Default

off

##### Example

    USE_SID_AS_SERVICE_listener=on

**Parent topic:** Control Parameters

#### 7.4.22 VALID_NODE_CHECKING_REGISTRATION\_listener_name

The listener.ora control parameter `VALID_NODE_CHECKING_REGISTRATION_``listener_name` determines if valid node checking registration is performed, or if the subnet is allowed.

##### Purpose

To determine whether valid node checking registration is performed, or the subnet is allowed.

##### Usage Notes

- When set to `on`, valid node checking registration is performed at the listener for any incoming registration request, and only local IP addresses are allowed.

- Starting with Oracle Grid Infrastructure 12c, for a SCAN listener, if the `VALID_NODE_CHECKING_REGISTRATION_``listener_name` and `REGISTRATION_INVITED_NODES_``listener_name` parameters are set in the `listener.ora` file, then the listener agent overwrites these parameters.

##### Default

on

##### Values

- `off | 0` to specify valid node checking registration is off, and no checking is performed.

- `on | 1 | local` to specify valid node checking registration is on, and all local IP addresses can register. If a list of invited nodes is set, then all IP addresses, host names, or subnets in the list as well as local IP addresses are allowed.

- `subnet | 2` to specify valid node checking registration is on, and all machines in the local subnets are allowed to register. If a list of invited nodes is set, then all nodes in the local subnets as well as all IP addresses, host names and subnets in the list are allowed.

##### Example

    VALID_NODE_CHECKING_REGISTRATION_listener=on

**See Also:**

[Oracle Real Application Clusters Administration and Deployment Guide](../racad/introduction-to-oracle-rac.md) for information about valid node checking for registration

**Parent topic:** Control Parameters

#### 7.4.23 WALLET_LOCATION

Use the `WALLET_LOCATION` parameter to specify the location of Oracle wallets.

##### Purpose

To specify the directory path where an Oracle wallet is stored. Wallets securely contain certificates, secrets, private keys, and trust points used by Oracle Database.

##### Usage Notes

- Where to set this parameter:

  You can set `WALLET_LOCATION` in the `listener.ora` file to specify a common wallet location for all listeners. You can also set `WALLET_LOCATION` as part of address string of the listener in `listener.ora` to specify a different wallet location for each listener. For example:
      net_service_name=
          (DESCRIPTION =
             (ADDRESS=(PROTOCOL=tcps)(HOST=sales-svr)(PORT=1234))
             (SECURITY=(WALLET_LOCATION=DIRECTORY))

- Storage of wallet files:

  The password-protected wallet is stored in an `ewallet.p12` file. The auto-login and local auto-login wallets are stored in a `cwallet.sso` file.

  For example, if an Oracle wallet is stored in the Microsoft Windows registry and the wallet's key `(KEY)` is `SALESAPP`, then the storage location of the password-protected wallet is `HKEY_CURRENT_USER\SOFTWARE\ORACLE\WALLETS\SALESAPP\EWALLET.P12`. The storage location of the auto-login and local auto-login wallets is `HKEY_CURRENT_USER\SOFTWARE\ORACLE\WALLETS\SALESAPP\CWALLET.SSO`.

##### Additional Parameters

Use `SOURCE` to specify the type of storage and storage location for wallets, as follows:

- `METHOD`: Type of storage

- `METHOD_DATA`: Storage location:
  - `DIRECTORY`: Location of wallet on the file system

  - `KEY`: Wallet type and location in the Microsoft Windows registry

##### Syntax and Examples

The syntax depends on the wallet as follows:

- Wallet on the file system:
      WALLET_LOCATION=
        (SOURCE=
          (METHOD=file)
          (METHOD_DATA=
             (DIRECTORY=directory)))

  For example:
      WALLET_LOCATION=
        (SOURCE=
            (METHOD=file)
            (METHOD_DATA=
               (DIRECTORY=/etc/oracle/wallets/databases)))
- Microsoft certificate store:
      WALLET_LOCATION=
        (SOURCE=
           (METHOD=mcs))

  The key-value pair for MCS omits the `METHOD_DATA` parameter because MCS does not use wallets. Instead, Oracle PKI (public key infrastructure) applications obtain certificates, trust points and private keys directly from a user's profile.
- Wallet in the Microsoft Windows registry:
      WALLET_LOCATION=
         (SOURCE=
            (METHOD=reg)
            (METHOD_DATA=
               (KEY=registry_key)))

  For example:
      WALLET_LOCATION=
         (SOURCE=
           (METHOD=reg)
           (METHOD_DATA=
              (KEY=SALESAPP)))

##### Default

None

**Parent topic:** Control Parameters

### 7.5 ADR Diagnostic Parameters for Oracle Net Listener

The diagnostic data for the critical errors is quickly captured and stored in the ADR for Oracle Net listener.

Since Oracle Database 11g, Oracle Database includes an advanced fault diagnosability infrastructure for preventing, detecting, diagnosing, and resolving problems. The problems are critical errors such as those caused by database code bugs, metadata corruption, and customer data corruption.

When a critical error occurs, it is assigned an incident number, and diagnostic data for the error, such as traces and dumps, are immediately captured and tagged with the incident number. The data is then stored in the Automatic Diagnostic Repository (ADR), a file-based repository outside the database.

This section includes the parameters used when ADR is enabled. ADR is enabled by default. Non-ADR parameters listed in the `listener.ora` file are ignored when ADR is enabled.

The following `listener.ora` parameters are used when ADR is enabled (when `DIAG_ADR_ENABLED` is set to `on`):

- ADR_BASE_listener_name
  The `ADR_BASE_``listener_name` parameter is a diagnostic parameter specifies the base directory that stores tracing and logging incidents when ADR is enabled.
- DIAG_ADR_ENABLED_listener_name
  The `DIAG_ADR_ENABLED_``listener_name` is a diagnostic parameter of the `listener.ora` file. It indicates whether ADR is enabled.
- LOG_FILE_NUM_listener_name
  The `LOG_FILE_NUM_``listener_name` is a diagnostic parameter of the `listener.ora` file that specifies the number of log file segments.
- LOG_FILE_SIZE_listener_name
  The `LOG_FILE_SIZE_``listener_name` diagnostic parameter of the`listener.ora` file specifies the size of each log file segment.
- LOGGING_listener_name
  The `LOGGING_``listener_name` diagnostic parameter of the `listener.ora` file turns logging on or off.
- TRACE_LEVEL_listener_name
  The `TRACE_LEVEL_``listener_name` diagnostic parameter of the` listener.ora` file turns listener tracing on, at a specific level, or turns it off.
- TRACE_TIMESTAMP_listener_name
  The `TRACE_TIMESTAMP_``listener_name` diagnostic parameter of the` listener.ora` file adds a time stamp to every trace event in the trace file for the listener.

**Parent topic:** Oracle Net Listener Parameters in the listener.ora File

#### 7.5.1 ADR_BASE\_listener_name

The `ADR_BASE_``listener_name` parameter is a diagnostic parameter specifies the base directory that stores tracing and logging incidents when ADR is enabled.

##### Purpose

To specify the base directory that stores tracing and logging incidents when ADR is enabled.

##### Default

The default is `ORACLE_BASE`, or `ORACLE_HOME/log` if `ORACLE_BASE` is not defined.

##### Values

Any valid directory path to a directory with write permission.

##### Example

    ADR_BASE_listener=/oracle/network/trace

**Parent topic:** ADR Diagnostic Parameters for Oracle Net Listener

#### 7.5.2 DIAG_ADR_ENABLED\_listener_name

The `DIAG_ADR_ENABLED_``listener_name` is a diagnostic parameter of the `listener.ora` file. It indicates whether ADR is enabled.

##### Purpose

To indicate whether ADR tracing is enabled.

##### Usage Notes

When the `DIAG_ADR_ENABLED_``listener_name` parameter is set to `on`, then ADR file tracing is used. When the `DIAG_ADR_ENABLED_``listener_name` parameter is set to `off`, then non-ADR file tracing is used.

##### Default

`on`

##### Values

`on|off`

Example 7-8 Example

`DIAG_ADR_ENABLED_listener=on`

**Parent topic:** ADR Diagnostic Parameters for Oracle Net Listener

#### 7.5.3 LOG_FILE_NUM\_listener_name

The `LOG_FILE_NUM_``listener_name` is a diagnostic parameter of the `listener.ora` file that specifies the number of log file segments.

##### Purpose

To specify the number of log file segments. At any point of time there can be only `n` log file segments where `n` is `LOG_FILE_NUM_``listener_name`. If the log grows beyond this number, then the older segments are deleted.

##### Default

No default. If you don't specify a value, or set the value to zero, then the number of segments grows indefinitely.

##### Values

Any integer value.

Example 7-9

`LOG_FILE_NUM_``listener``=3`

**Parent topic:** ADR Diagnostic Parameters for Oracle Net Listener

#### 7.5.4 LOG_FILE_SIZE\_listener_name

The `LOG_FILE_SIZE_``listener_name` diagnostic parameter of the`listener.ora` file specifies the size of each log file segment.

##### Purpose

To specify the size of each log file segment. The size is in `MB`.

##### Default

`300 MB`

##### Values

Any integer value.

Example 7-10 Example

`LOG_FILE_SIZE_listener=10`

**Parent topic:** ADR Diagnostic Parameters for Oracle Net Listener

#### 7.5.5 LOGGING\_listener_name

The `LOGGING_``listener_name` diagnostic parameter of the `listener.ora` file turns logging on or off.

##### Purpose

To turn logging on or off.

##### Usage Notes

This parameter is also applicable when non-ADR tracing is used.

##### Default

on

##### Values

`on` \| `off`

##### Example

    LOGGING_listener=on

**Parent topic:** ADR Diagnostic Parameters for Oracle Net Listener

#### 7.5.6 TRACE_LEVEL\_listener_name

The `TRACE_LEVEL_``listener_name` diagnostic parameter of the` listener.ora` file turns listener tracing on, at a specific level, or turns it off.

##### Purpose

To turn listener tracing on, at a specific level, or to turn it off.

##### Usage Notes

This parameter is also applicable when non-ADR tracing is used.

##### Default

    off | 0

##### Values

- `off` or `0` for no trace output

- `user` or `4` for user trace information

- `admin` or `10` for administration trace information

- `support` or `16` for Oracle Support Services trace information

##### Example

    TRACE_LEVEL_listener=admin

**Parent topic:** ADR Diagnostic Parameters for Oracle Net Listener

#### 7.5.7 TRACE_TIMESTAMP\_listener_name

The `TRACE_TIMESTAMP_``listener_name` diagnostic parameter of the` listener.ora` file adds a time stamp to every trace event in the trace file for the listener.

##### Purpose

To add a time stamp in the form of `dd-mmm-yyyy hh:mi:ss:mil` to every trace event in the trace file for the listener.

##### Usage Notes

This parameter is used with the TRACE_LEVEL_listener_name parameter. This parameter is also applicable when non-ADR tracing is used.

##### Default

on

##### Values

- `on` \| `true`

- `off` \| `false`

##### Example

    TRACE_TIMESTAMP_listener=true

**Parent topic:** ADR Diagnostic Parameters for Oracle Net Listener

### 7.6 Non-ADR Diagnostic Parameters for Oracle Net Listener

This section lists the parameters used when ADR is disabled. The default value of `DIAG_ADR_ENABLED_``listener_name` is `on`. Therefore, the `DIAG_ADR_ENABLED_``listener_name` parameter must explicitly be set to `off` to use non-ADR tracing.

- LOG_DIRECTORY_listener_name
- LOG_FILE_listener_name
- TRACE_DIRECTORY_listener_name
- TRACE_FILE_listener_name
- TRACE_FILEAGE_listener_name
- TRACE_FILELEN_listener_name
- TRACE_FILENO_listener_name

**Parent topic:** Oracle Net Listener Parameters in the listener.ora File

#### 7.6.1 LOG_DIRECTORY\_listener_name

##### Purpose

To specify the destination directory of the listener log file.

##### Usage Notes

Use this parameter when ADR is not enabled.

##### Default

    ORACLE_HOME/network/log

##### Example

    LOG_DIRECTORY_listener=/oracle/network/admin/log

**Parent topic:** Non-ADR Diagnostic Parameters for Oracle Net Listener

#### 7.6.2 LOG_FILE\_listener_name

##### Purpose

To specify the name of the log file for the listener.

##### Usage Notes

Use this parameter when ADR is not enabled.

##### Default

    listener.log

##### Example

    LOG_FILE_listener=list.log

**Parent topic:** Non-ADR Diagnostic Parameters for Oracle Net Listener

#### 7.6.3 TRACE_DIRECTORY\_listener_name

##### Purpose

To specify the destination directory of the listener trace file.

##### Usage Notes

Use this parameter when ADR is not enabled.

##### Default

    ORACLE_HOME/network/trace

##### Example

    TRACE_DIRECTORY_listener=/oracle/network/admin/trace

**Parent topic:** Non-ADR Diagnostic Parameters for Oracle Net Listener

#### 7.6.4 TRACE_FILE\_listener_name

##### Purpose

To specify the name of the trace file for the listener.

##### Usage Notes

Use this parameter when ADR is not enabled.

##### Default

    listener.trc

##### Example

    TRACE_FILE_listener=list.trc

**Parent topic:** Non-ADR Diagnostic Parameters for Oracle Net Listener

#### 7.6.5 TRACE_FILEAGE\_listener_name

##### Purpose

To specify the maximum age of listener trace files in minutes.

##### Usage Notes

When the age limit is reached, the trace information is written to the next file. The number of files is specified with the TRACE_FILENO_listener_name parameter. Use this parameter when ADR is not enabled.

##### Default

Unlimited

This is the same as setting the parameter to `0`.

Example 7-11 Example

`TRACE_FILEAGE_listener=60`

**Parent topic:** Non-ADR Diagnostic Parameters for Oracle Net Listener

#### 7.6.6 TRACE_FILELEN\_listener_name

##### Purpose

To specify the size of the listener trace files in kilobytes (KB).

##### Usage Notes

When the size is met, the trace information is written to the next file. The number of files is specified using the TRACE_FILENO_listener_name parameter. Use this parameter when ADR is not enabled.

##### Default

Unlimited

##### Example

    TRACE_FILELEN_listener=100

**Parent topic:** Non-ADR Diagnostic Parameters for Oracle Net Listener

#### 7.6.7 TRACE_FILENO\_listener_name

##### Purpose

To specify the number of trace files for listener tracing.

##### Usage Notes

When this parameter is set along with the TRACE_FILELEN_listener_name parameter, trace files are used in a cyclical fashion. The first file is filled first, then the second file, and so on. When the last file has been filled, the first file is re-used, and so on.

The trace file names are distinguished from one another by their sequence number. For example, if the default trace file of `listener.trc` is used, and this parameter is set to 3, then the trace files would be named `listener1.trc`, `listener2.trc` and `listener3.trc`.

In addition, trace events in the trace files are preceded by the sequence number of the file. Use this parameter when ADR is not enabled.

##### Default

1

##### Example

    TRACE_FILENO_listener=3

**Parent topic:** Non-ADR Diagnostic Parameters for Oracle Net Listener

### 7.7 Class of Secure Transports Parameters

The class of secure transports (COST) parameters specify a list of transports that are considered secure for administration and registration of a particular listener.

The COST parameters identify which transports are considered secure for that installation and whether the administration of a listener requires secure transports. Configuring these parameters is optional.

- SECURE_REGISTER_listener_name
- Using COST Parameters in Combination
- DYNAMIC_REGISTRATION_listener_name
  `DYNAMIC_REGISTRATION_``listener_name` is a class of secure transports (COST) parameter and it enables or disables dynamic registration of a listener.
- SECURE_PROTOCOL_listener_name
- SECURE_CONTROL_listener_name

**See Also:**

[Oracle Database Net Services Administrator's Guide](../netag/configuring-and-administering-oracle-net-listener.md) for additional information about COST parameters and listener security

**Parent topic:** Oracle Net Listener Parameters in the listener.ora File

#### 7.7.1 SECURE_REGISTER\_listener_name

##### Purpose

To specify the transports on which registration requests are to be accepted.

##### Usage Notes

If the `SECURE_REGISTER_``listener_name` parameter is configured with a list of transport names, then only the connections arriving on the specified transports are able to register the service with the listener. Connections arriving by other transport protocols are refused. The following is an example:

    SECURE_REGISTER_listener1 = (TCPS,IPC)

In the preceding example, registration requests are accepted only on TCPS and IPC transports.

If no values are entered for this parameter, then the listener accepts registration requests from any transport.

##### Syntax

    SECURE_REGISTER_listener_name =
    [(]transport1[,transport2, ....,transportn)]

In the preceding example, `transport1`, `transport2`, and `transport``n` are valid, installed transport protocol names.

If this parameter and SECURE_CONTROL_listener_name are configured, then they override the SECURE_PROTOCOL_listener_name parameter.

##### Example

    LISTENER1=
     (DESCRIPTION=
        (ADDRESS_LIST=
          (ADDRESS=(PROTOCOL=tcp)(HOST=sales-server)(PORT=1521))
          (ADDRESS=(PROTOCOL=ipc)(KEY=extproc))
          (ADDRESS=(PROTOCOL=tcps)(HOST=sales-server)(PORT=1522))))
      SECURE_REGISTER_listener1=tcps

**Parent topic:** Class of Secure Transports Parameters

#### 7.7.2 Using COST Parameters in Combination

COST parameters can also be used in combination to further control which transports accept service registration and control commands.

In Example 7-12, control commands are accepted only on the IPC channel and the TCPS transport, and service registrations are accepted only on an IPC channel.

Example 7-12 Combining COST Parameters

    LISTENER1=
     (DESCRIPTION=
       (ADDRESS_LIST=
         (ADDRESS=(PROTOCOL=tcp)(HOST=sales-server)(PORT=1521))
         (ADDRESS=(PROTOCOL=ipc)(KEY=extproc))
         (ADDRESS=(PROTOCOL=tcps)(HOST=sales-server)(PORT=1522))))
      SECURE_CONTROL_listener1=(tcps,ipc)
      SECURE_REGISTER_listener1=ipc

In Example 7-13, control commands are accepted only on the TCPS transport, and service registrations are accepted only on the IPC channel.

Example 7-13 Combining COST Parameters

    LISTENER1=
     (DESCRIPTION=
       (ADDRESS_LIST=
         (ADDRESS=(PROTOCOL=tcp)(HOST=sales-server)(PORT=1521))
         (ADDRESS=(PROTOCOL=ipc)(KEY=extproc))
         (ADDRESS=(PROTOCOL=tcps)(HOST=sales-server)(PORT=1522))))
      SECURE_CONTROL_listener1=tcps
      SECURE_PROTOCOL_listener1=ipc

**Parent topic:** Class of Secure Transports Parameters

#### 7.7.3 DYNAMIC_REGISTRATION_listener_name

`DYNAMIC_REGISTRATION_``listener_name` is a class of secure transports (COST) parameter and it enables or disables dynamic registration of a listener.

##### Purpose

To enable or disable dynamic registration.

##### Usage Notes

Static registrations are not affected by this parameter.

##### Default

The default value is `on`. Unless this parameter is explicitly set to `off`, all registration connections are accepted.

##### Values

- `on`: The listener accepts dynamic registration.

- `off`: The listener refuses dynamic registration.

Example 7-14 Example

`DYNAMIC_REGISTRATION_``listener_name``=on`

**Parent topic:** Class of Secure Transports Parameters

#### 7.7.4 SECURE_PROTOCOL\_listener_name

##### Purpose

To specify the transports on which administration and registration requests are accepted.

##### Usage Notes

If this parameter is configured with a list of transport names, then the control commands and service registration can happen only if the connection belongs to the list of transports.

If this parameter is not present and neither SECURE_CONTROL_listener_name or SECURE_REGISTER_listener_name are configured, then all supported transports accept control and registration requests.

If the SECURE_CONTROL_listener_name and SECURE_REGISTER_listener_name parameters are configured, then they override the `SECURE_PROTOCOL_``listener_name` parameter.

##### Syntax

    SECURE_PROTOCOL_listener_name =
    [(]transport1[,transport2, ....,transportn)]

In the preceding syntax, `transport1`, `transport2`, and `transport``n` are valid, installed transport protocol names.

##### Example

    LISTENER1=
     (DESCRIPTION=
        (ADDRESS_LIST=
          (ADDRESS=(PROTOCOL=tcp)(HOST=sales-server)(PORT=1521))
          (ADDRESS=(PROTOCOL=ipc)(KEY=extproc))
          (ADDRESS=(PROTOCOL=tcps)(HOST=sales-server)(PORT=1522))))
      SECURE_PROTOCOL_listener1=tcps

**Parent topic:** Class of Secure Transports Parameters

#### 7.7.5 SECURE_CONTROL\_listener_name

##### Purpose

To specify the transports on which control commands are to be serviced.

##### Usage Notes

If the `SECURE_CONTROL_``listener_name` parameter is configured with a list of transport names, then the control commands are serviced only if the connection is one of the listed transports. Connections arriving by other transport protocols are refused. The following is an example:

    SECURE_CONTROL_listener1 = (TCPS,IPC)

In the preceding example, administration requests are accepted only on TCPS and IPC transports.

If no values are entered for this parameter, then the listener accepts any connection on any endpoint.

##### Syntax

    SECURE_CONTROL_listener_name =
    [(]transport1[,transport2, ....,transportn)]

In the preceding syntax, `transport1`, `transport2`, and `transport``n` are valid, installed transport protocol names.

##### Example

    LISTENER1=
     (DESCRIPTION=
        (ADDRESS_LIST=
          (ADDRESS=(PROTOCOL=tcp)(HOST=sales-server)(PORT=1521))
          (ADDRESS=(PROTOCOL=ipc)(KEY=extproc))
          (ADDRESS=(PROTOCOL=tcps)(HOST=sales-server)(PORT=1522))))
      SECURE_CONTROL_LISTENER1=tcps

**Parent topic:** Class of Secure Transports Parameters
