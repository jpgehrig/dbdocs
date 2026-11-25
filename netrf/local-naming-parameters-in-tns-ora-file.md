## 6 Local Naming Parameters in the tnsnames.ora File

Learn about the Oracle Net service names local naming parameters that you specify in the `tnsnames.ora` configuration file.

- Overview of Local Naming Parameters
  The `tnsnames.ora` file is a configuration file that contains network service names that are mapped to connect descriptors for the Local Naming method.
- General Syntax of tnsnames.ora
  In this example, you can see the general `tnsnames.ora` file syntax.
- Using Multiple Descriptions in tnsnames.ora Files
  In this example, you can see two connect descriptors with multiple addresses.
- Multiple Address Lists in tnsnames.ora Files
  The `tnsnames.ora` file supports connect descriptors with multiple lists of addresses, each with its own characteristics. Learn how to configure multiple address lists in `tnsnames.ora` files.
- Connect-Time Failover and Client Load Balancing with Oracle Connection Managers
  When `tnsnames.ora` connect descriptors have at least two protocol addresses for Oracle Connection Manager, you can also include parameters for connect-time failover and load balancing in the file.
- Connect Descriptor Descriptions
  Specify connect descriptors using the `DESCRIPTION` parameter. Identify multiple connect descriptors with the `DESCRIPTION_LIST` parameter.
- Protocol Addresses
  The protocol address section of a `tnsnames.ora` file specifies listener protocol addresses.
- Optional Parameters for Description
  Use these parameters to configure connect descriptor containers under the `DESCRIPTION` parameter.
- Connection Data Section
  Learn how to configure network connections with protocol addresses.
- Security Section
  The security section of the `tnsnames.ora` file specifies these security-related parameters for use with Oracle security features.
- Timeout Parameters
  The timeout section of the `tnsnames.or`a file provides the ability to specify timeout and retry configuration through the TNS connect string.
- Compression Parameters
  The compression section of the `tnsnames.ora` file provides the ability to enable compression and specify compression levels. These parameters can be set at the `DESCRIPTION` level of a connect string.

### 6.1 Overview of Local Naming Parameters

The `tnsnames.ora` file is a configuration file that contains network service names that are mapped to connect descriptors for the Local Naming method.

A net service name is an alias that is mapped to a database network address that is contained in a connect descriptor. A connect descriptor contains the location of the listener that is accessed through a protocol address and the service name of the database to which to connect. Clients and database servers that are clients of other database servers use the net service name when connecting with applications.

Typically, tools such as Oracle Database Configuration Assistant (DBCA) and Oracle Net Configuration Assistant (NETCA) create the `tnsnames.ora` file in the `ORACLE_HOME``/network/admin` directory for Oracle Database installations, the `GRID_HOME``/network/admin` directory for Oracle Grid Infrastructure installations, or the corresponding `ORACLE_BASE_HOME``/network/admin` directory for a read-only Oracle home. Note that if you have installed multiple databases, then the file is created in the Oracle home or Grid home where DBCA or NETCA is run (or the Oracle base home for read-only instances).

The order for checking the `tnsnames.ora` file is:

1.  The directory specified by the `TNS_ADMIN` environment variable

2.  If the `TNS_ADMIN` environment variable is not set or the file is not found in the `TNS_ADMIN` directory:

    - On Linux and UNIX: The `ORACLE_HOME``/network/admin` directory (or its `ORACLE_BASE_HOME``/network/admin` directory for a read-only Oracle home)

    - On Windows: The `ORACLE_HOME``\network\admin` directory (or its `ORACLE_BASE_HOME``\network\admin` directory for a read-only Oracle home)

3.  For a read-only Oracle home, if the file is not found in the Oracle base home:

    - On Linux and UNIX: The `ORACLE_HOME``/network/admin` directory

    - On Windows: The `ORACLE_HOME``\network\admin` directory

**Note:**

- On Windows, the `ORACLE_HOME` location is determined by the `ORACLE_HOME``\bin\oracle.key` file (which contains the name of the Windows Registry key where `ORACLE_HOME` is defined). Also, the `TNS_ADMIN` environment variable is used if it is set in the environment of the process. If you do not define the `TNS_ADMIN` environment variable in the environment or if the process is a service that does not have an environment, then Windows scans the registry for a `TNS_ADMIN` parameter.

- With Oracle Instant Client, `tnsnames.ora` is located in the subdirectory of the Oracle Instant Client software. For example, in the `/opt/oracle/instantclient_``release_number``/network/admin` directory.

**Related Topics**

- [Oracle Database Net Services Administrator's Guide](../netag/configuring-naming-methods.md)

**Parent topic:** Local Naming Parameters in the tnsnames.ora File

### 6.2 General Syntax of tnsnames.ora

In this example, you can see the general `tnsnames.ora` file syntax.

Here, `DESCRIPTION` contains the connect descriptor, `ADDRESS` contains the protocol address, and `CONNECT_DATA` contains database service identification information.

Example 6-1 Basic Format of tnsnames.ora File

    net_service_name=
     (DESCRIPTION=
       (ADDRESS=(protocol_address_information))
       (CONNECT_DATA=
         (SERVICE_NAME=service_name)
        )
      )

**Parent topic:** Local Naming Parameters in the tnsnames.ora File

### 6.3 Using Multiple Descriptions in tnsnames.ora Files

In this example, you can see two connect descriptors with multiple addresses.

A `tnsnames.ora` file can contain net service names with one or more connect descriptors. Each connect descriptor can contain one or more protocol addresses.

Use the `tnsnames.ora` parameter `DESCRIPTION_LIST` to define the list of connect descriptors.

Example 6-2 Net Service Name with Multiple Connect Descriptors in tnsnames.ora

    net_service_name=
     (DESCRIPTION_LIST=
      (DESCRIPTION=

       (ADDRESS=(PROTOCOL=tcp)(HOST=sales1-svr)(PORT=1521))
       (ADDRESS=(PROTOCOL=tcp)(HOST=sales2-svr)(PORT=1521))
       (CONNECT_DATA=
         (SERVICE_NAME=sales.us.example.com)))
      (DESCRIPTION=

       (ADDRESS=(PROTOCOL=tcp)(HOST=hr1-svr)(PORT=1521))
       (ADDRESS=(PROTOCOL=tcp)(HOST=hr2-svr)(PORT=1521))
       (CONNECT_DATA=
         (SERVICE_NAME=hr.us.example.com))))

**Note:**

Oracle Net Manager does not support multiple connect descriptors for a net service name if you use Oracle Connection Manager.

**Parent topic:** Local Naming Parameters in the tnsnames.ora File

### 6.4 Multiple Address Lists in tnsnames.ora Files

The `tnsnames.ora` file supports connect descriptors with multiple lists of addresses, each with its own characteristics. Learn how to configure multiple address lists in `tnsnames.ora` files.

The following example shows two address lists. The first address list features client load balancing and no connect-time failover. These setting apply only to protocol addresses that are within its `ADDRESS_LIST`. The second protocol address list does not enable client load loading balancing, but the list does enable connect-time failover. These settings affect only protocol addresses that are included in its `ADDRESS_LIST`. The client first tries the first or second protocol address at random, then it tries protocol addresses number three and four, in that order, and so on.

Example 6-3 Multiple Address Lists in tnsnames.ora Files

    net_service_name=
     (DESCRIPTION=
      (ADDRESS_LIST=
       (LOAD_BALANCE=on)
       (FAILOVER=off)
       (ADDRESS=(protocol_address_information))
       (ADDRESS=(protocol_address_information)))
      (ADDRESS_LIST=
       (LOAD_BALANCE=off)
       (FAILOVER=on)
       (ADDRESS=(protocol_address_information))
       (ADDRESS=(protocol_address_information)))
      (CONNECT_DATA=
       (SERVICE_NAME=service_name)))

**Note:**

- Oracle Net Manager supports only the creation of one protocol address list for a connect descriptor.

- Oracle Net Services supports the IFILE parameter in the `tnsnames.ora` file, with up to three levels of nesting. You must add the parameter manually to the file. The following is an example of the syntax:

      IFILE=/tmp/listener_em.ora
      IFILE=/tmp/listener_cust1.ora
      IFILE=/tmp/listener_cust2.ora

**Parent topic:** Local Naming Parameters in the tnsnames.ora File

### 6.5 Connect-Time Failover and Client Load Balancing with Oracle Connection Managers

When `tnsnames.ora` connect descriptors have at least two protocol addresses for Oracle Connection Manager, you can also include parameters for connect-time failover and load balancing in the file.

Example 6-4 Multiple Oracle Connection Manager Addresses in tnsnames.ora

This example illustrates the failover of multiple Oracle Connection Manager protocol addresses.

    sample1=
     (DESCRIPTION=
       (SOURCE_ROUTE=yes)
       (ADDRESS_LIST=
         (ADDRESS=(PROTOCOL=tcp)(HOST=host1)(PORT=1630))    # 1
         (ADDRESS_LIST=
           (FAILOVER=on)
           (LOAD_BALANCE=off)                               #  2
           (ADDRESS=(PROTOCOL=tcp)(HOST=host2a)(PORT=1630))
           (ADDRESS=(PROTOCOL=tcp)(HOST=host2b)(PORT=1630)))
         (ADDRESS=(PROTOCOL=tcp)(HOST=host3)(PORT=1521)))    #  3
       (CONNECT_DATA=(SERVICE_NAME=sales.us.example.com)))

The previous syntax does the following:

1.  The client connects to the protocol address of the first Oracle Connection Manager as indicated by:

    `(ADDRESS=(PROTOCOL=tcp)(HOST=host1)(PORT=1630)) `

2.  Oracle Connection Manager connects to the first protocol address of another Oracle Connection Manager. If the first protocol address fails, then it tries to connect to the second protocol address. This sequence is specified with the following configuration:

        (ADDRESS_LIST=
          (FAILOVER=on)
          (LOAD_BALANCE=off)
          (ADDRESS=(PROTOCOL=tcp)(HOST=host2a)(PORT=1630))
          (ADDRESS=(PROTOCOL=tcp)(HOST=host2b)(PORT=1630)))

3.  Oracle Connection Manager connects to the database service using the following protocol address:

    `(ADDRESS=(PROTOCOL=tcp)(HOST=host3)(PORT=1521)) `

Example 6-5 Client Load Balancing in tnsnames.ora

This example illustrates client load balancing among two Oracle Connection Managers and two protocol addresses:

    sample2=
     (DESCRIPTION=
       (LOAD_BALANCE=on)                                    # 1
       (FAILOVER=on)
       (ADDRESS_LIST=
         (SOURCE_ROUTE=yes)
         (ADDRESS=(PROTOCOL=tcp)(HOST=host1)(PORT=1630))    # 2
         (ADDRESS=(PROTOCOL=tcp)(HOST=host2)(PORT=1521)))
      (ADDRESS_LIST=
         (SOURCE_ROUTE=yes)
         (ADDRESS=(PROTOCOL=tcp)(HOST=host3)(port=1630))
         (ADDRESS=(PROTOCOL=tcp)(HOST=host4)(port=1521)))
       (CONNECT_DATA=(SERVICE_NAME=sales.us.example.com)))  # 3

The previous syntax does the following:

1.  The client selects an `ADDRESS_LIST` at random and fails over to the other address if the chosen `ADDRESS_LIST` fails. This is indicated if you set the `LOAD_BALANCE` and `FAILOVER` parameters to `on`.

2.  When an `ADDRESS_LIST` is chosen, the client first connects to Oracle Connection Manager using the Oracle Connection Manager protocol address that uses port 1630 as is indicated for the `ADDRESS_LIST`.

3.  Oracle Connection Manager then connects to the database service using the protocol address that is indicated for the `ADDRESS_LIST`.

**Parent topic:** Local Naming Parameters in the tnsnames.ora File

### 6.6 Connect Descriptor Descriptions

Specify connect descriptors using the `DESCRIPTION` parameter. Identify multiple connect descriptors with the `DESCRIPTION_LIST` parameter.

- DESCRIPTION_LIST
  `DESCRIPTION_LIST` networking parameter of the `tnsnames.ora` file defines a list of connect descriptors for a particular net service name.
- DESCRIPTION
  DESCRIPTION networking parameter of the tnsnames.ora file specifies a container for a connect descriptor.

**Parent topic:** Local Naming Parameters in the tnsnames.ora File

#### 6.6.1 DESCRIPTION_LIST

`DESCRIPTION_LIST` networking parameter of the `tnsnames.ora` file defines a list of connect descriptors for a particular net service name.

##### Purpose

To define a list of connect descriptors for a particular net service name.

Example 6-6 Example

    net_service_name=
    (DESCRIPTION_LIST=
     (DESCRIPTION=
      (ADDRESS=...)
      (CONNECT_DATA=(SERVICE_NAME=sales.example.com)))
     (DESCRIPTION=

**Parent topic:** Connect Descriptor Descriptions

#### 6.6.2 DESCRIPTION

DESCRIPTION networking parameter of the tnsnames.ora file specifies a container for a connect descriptor.

##### Purpose

To specify a container for a connect descriptor.

##### Usage Notes

When using more than one `DESCRIPTION` parameter, put the parameters under the `DESCRIPTION_LIST` parameter.

Example 6-7 Example

    net_service_name=
    (DESCRIPTION=
      (ADDRESS=...)
      (CONNECT_DATA=(SERVICE_NAME=sales.us.example.com)))

**Parent topic:** Connect Descriptor Descriptions

### 6.7 Protocol Addresses

The protocol address section of a `tnsnames.ora` file specifies listener protocol addresses.

If there is only one listener protocol address, then use the `ADDRESS` parameter. If there is more than one address, then use the `ADDRESS_LIST` parameter.

- ADDRESS
  The `ADDRESS` networking parameter is in the `tnsnames.ora` file and it specifies the protocol address under the `ADDRESS_LIST` or the `DESCRIPTION` parameter for one listener.
- HTTPS_PROXY
  Learn to use the `tnsnames.ora` parameter `HTTPS_PROXY` to specify HTTP proxy host names to tunnel Transport Layer Security (TLS) client connections.
- HTTPS_PROXY_PORT
  Learn how to use the `tnsnames.ora` parameter `HTTPS_PROXY_PORT` to specify forward HTTP proxy host ports for tunneling Transport Layer Security (TLS) client connections.
- ADDRESS_LIST
  The `ADDRESS_LIST` networking parameter specifies the number of protocol addresses.

**Parent topic:** Local Naming Parameters in the tnsnames.ora File

#### 6.7.1 ADDRESS

The `ADDRESS` networking parameter is in the `tnsnames.ora` file and it specifies the protocol address under the `ADDRESS_LIST` or the `DESCRIPTION` parameter for one listener.

##### Purpose

To specify a single listener protocol address.

##### Usage Notes

Put this parameter under either the `ADDRESS_LIST` parameter or the `DESCRIPTION` parameter.

##### Example

    net_service_name=
    (DESCRIPTION=
     (ADDRESS=(PROTOCOL=tcp)(HOST=sales-svr)(PORT=1521))
     (CONNECT_DATA=(SERVICE_NAME=sales.us.example.com))

**Parent topic:** Protocol Addresses

#### 6.7.2 HTTPS_PROXY

Learn to use the `tnsnames.ora` parameter `HTTPS_PROXY` to specify HTTP proxy host names to tunnel Transport Layer Security (TLS) client connections.

##### Purpose

To specify HTTP proxy host name for tunneling TLS client connections.

##### Usage Notes

The clients can tunnel secure connections over forward HTTP proxy using HTTP CONNECT method. This helps in accessing the public cloud database service as it eliminates the requirement to open an outbound port on a client side firewall. This parameter is applicable only to the connect descriptors where `PROTOCOL=TCPS`. This is similar to the web browser setting for intranet users who want to connect to internet hosts. Increase the forward web proxy read timeout for requests to a higher value depending on client queries. Otherwise, the forward web proxy closes the connection assuming that no requests are made from the client.

Successful connection depends on specific proxy configurations. The performance of data transfers depends on proxy capacity. Oracle recommends not to use this feature in production environments where performance is critical.

Configuring `tnsnames.ora` for the HTTP proxy may not be enough depending your organization’s network configuration and security policies. For example, some networks require a user name and password for the HTTP proxy.

Oracle Client versions earlier than 18c does not support connections through HTTP proxy.

Contact your network administrator to open outbound connections to hosts in the `oraclecloud.com` domain using the relevant port, without going through an HTTP proxy. For example, port 1522.

##### Default

None

##### Values

HTTP proxy host name that can make an outbound connection to the internet hosts.

##### Example

`HTTPS_PROXY=www-proxy.example.com`

**Parent topic:** Protocol Addresses

#### 6.7.3 HTTPS_PROXY_PORT

Learn how to use the `tnsnames.ora` parameter `HTTPS_PROXY_PORT` to specify forward HTTP proxy host ports for tunneling Transport Layer Security (TLS) client connections.

##### Purpose

To specify forward HTTP proxy host port for tunneling TLS client connections.

##### Usage Notes

It forwards the HTTP proxy host port that receives HTTP CONNECT method. This parameter should be used along with `HTTPS_PROXY_PORT`. This value takes effect only when `SQLNET.USE_HTTPS_PROXY=1` is set in `sqlnet.ora`.

##### Default

none

##### Values

port number

##### Example

`HTTPS_PROXY_PORT=80`

**Parent topic:** Protocol Addresses

#### 6.7.4 ADDRESS_LIST

The `ADDRESS_LIST` networking parameter specifies the number of protocol addresses.

##### Purpose

To define a list of protocol addresses.

##### Usage Notes

If there is only one listener protocol address, then `ADDRESS_LIST` is not necessary.

Put this parameter either under the `DESCRIPTION` parameter or the `DESCRIPTION_LIST` parameter.

##### Example

    net_service_name=
     (DESCRIPTION=
      (ADDRESS_LIST=
       (ADDRESS=(PROTOCOL=tcp)(HOST=sales1-svr)(PORT=1521))
       (ADDRESS=(PROTOCOL=tcp)(HOST=sales2-svr)(PORT=1521)))
      (CONNECT_DATA=(SERVICE_NAME=sales.us.example.com)))

**Parent topic:** Protocol Addresses

### 6.8 Optional Parameters for Description

Use these parameters to configure connect descriptor containers under the `DESCRIPTION` parameter.

- ENABLE
  Use the `ENABLE` parameter to enable the keepalive feature on the supported TCP transports.
- FAILOVER
  Use the `FAILOVER` parameter to enable or disable connect-time failover for multiple protocol addresses.
- LOAD_BALANCE
  Use the `LOAD_BALANCE` parameter to enable or disable client load balancing for multiple protocol addresses.
- RECV_BUF_SIZE
  Use the `RECV_BUF_SIZE` parameter to specify buffer space for session receive operations.
- SDU
  Use the `SDU` parameter to configure the session data unit (SDU) size.
- SEND_BUF_SIZE
  Use the `SEND_BUF_SIZE` parameter to specify buffer space for session send operations.
- SOURCE_ROUTE
  Use the `SOURCE_ROUTE` parameter to enable routing through multiple protocol addresses.
- TYPE_OF_SERVICE
  Use the `TYPE_OF_SERVICE` parameter to specify the type of service to use for an Oracle Rdb database.

**Parent topic:** Local Naming Parameters in the tnsnames.ora File

#### 6.8.1 ENABLE

Use the `ENABLE` parameter to enable the keepalive feature on the supported TCP transports.

##### Purpose

To allow the caller to detect a terminated remote server; typically it takes 2 hours or more to notice.

##### Usage Notes

The keepalive feature on the supported TCP transports can be enabled for a net service client by putting `(ENABLE=broken)` under the `DESCRIPTION` parameter in the connect string. On the client side, the default for `tcp_keepalive` is `off`. Operating system TCP configurables, which vary by platform, define the actual keepalive timing details.

##### Values

    broken

##### Example

    net_service_name=
     (DESCRIPTION=
      (ENABLE=broken)
      (ADDRESS=(PROTOCOL=tcp)(HOST=sales1-svr)(PORT=1521))
      (ADDRESS=(PROTOCOL=tcp)(HOST=sales2-svr)(PORT=1521)))
      (CONNECT_DATA=(SERVICE_NAME=sales.us.example.com))

Although the preceding example has multiple addresses, the `ADDRESS_LIST` parameter was not used. This is because the `ADDRESS_LIST` parameter is not mandatory.

**Parent topic:** Optional Parameters for Description

#### 6.8.2 FAILOVER

Use the `FAILOVER` parameter to enable or disable connect-time failover for multiple protocol addresses.

##### Purpose

To enable or disable connect-time failover for multiple protocol addresses.

##### Usage Notes

When you set the parameter to `on`, `yes`, or `true`, Oracle Net fails over at connect time to a different address if the first protocol address fails. When you set the parameter to `off`, `no`, or `false`, Oracle Net tries one protocol address.

Put this parameter under the `DESCRIPTION_LIST` parameter, the `DESCRIPTION` parameter, or the `ADDRESS_LIST` parameter.

**Note:**

Do not set the `GLOBAL_DBNAME` parameter in the `SID_LIST_``listener_name` section of the `listener.ora`. A statically configured global database name disables connect-time failover.

##### Default

`on` for the `DESCRIPTION_LIST`, `DESCRIPTION`, and `ADDRESS_LIST` parameters

##### Values

- `yes` \| `on` \| `true`

- `no` \| `off` \| `false`

##### Example

    net_service_name=
     (DESCRIPTION=
      (FAILOVER=on)
      (ADDRESS_LIST=
        (ADDRESS=(PROTOCOL=tcp)(HOST=sales1-svr)(PORT=1521))
        (ADDRESS=(PROTOCOL=tcp)(HOST=sales2-svr)(PORT=1521)))
      (CONNECT_DATA=(SERVICE_NAME=sales.us.example.com)))

**Parent topic:** Optional Parameters for Description

#### 6.8.3 LOAD_BALANCE

Use the `LOAD_BALANCE` parameter to enable or disable client load balancing for multiple protocol addresses.

##### Purpose

To enable or disable client load balancing for multiple protocol addresses.

##### Usage Notes

When you set the parameter to `on`, `yes`, or `true`, Oracle Net goes through the list of addresses in a random sequence, balancing the load on the various listener or Oracle Connection Manager protocol addresses. When you set the parameter to `off`, `no`, or `false`, Oracle Net tries the protocol addresses sequentially until one succeeds.

Put this parameter under the `DESCRIPTION_LIST` parameter, the `DESCRIPTION` parameter, or the `ADDRESS_LIST` parameter.

##### Default

`on` for `DESCRIPTION_LIST`

##### Values

- `yes` \| `on` \| `true`

- `no` \| `off` \| `false`

##### Example

    net_service_name=
     (DESCRIPTION=
      (LOAD_BALANCE=on)
      (ADDRESS_LIST=
        (ADDRESS=(PROTOCOL=tcp)(HOST=sales1-svr)(PORT=1521))
        (ADDRESS=(PROTOCOL=tcp)(HOST=sales2-svr)(PORT=1521)))
      (CONNECT_DATA=(SERVICE_NAME=sales.us.example.com))

**Parent topic:** Optional Parameters for Description

#### 6.8.4 RECV_BUF_SIZE

Use the `RECV_BUF_SIZE` parameter to specify buffer space for session receive operations.

##### Purpose

To specify, in bytes, the buffer space for receive operations of sessions.

##### Usage Notes

This parameter is supported by the TCP/IP, TCP/IP with TLS, and SDP protocols.

Put this parameter under the `DESCRIPTION` parameter or at the end of the protocol address.

Setting this parameter in the connect descriptor for a client overrides the [RECV_BUF_SIZE](parameters-for-the-sqlnet.ora.md) parameter at the client-side `sqlnet.ora` file.

**Note:**

Additional protocols might support this parameter on certain operating systems. Refer to the operating system-specific documentation for additional information about additional protocols.

##### Default

The default value for this parameter is specific to the operating system. The default for the Linux 2.6 operating system is 87380 bytes.

##### Example

    net_service_name=
     (DESCRIPTION=
       (ADDRESS_LIST=
         (ADDRESS=(PROTOCOL=tcp)(HOST=sales1-server)(PORT=1521)
            (RECV_BUF_SIZE=11784))
         (ADDRESS=(PROTOCOL=tcp)(HOST=sales2-server)(PORT=1521)
            (RECV_BUF_SIZE=11784))
       (CONNECT_DATA=
         (SERVICE_NAME=sales.us.example.com)))
    net_service_name=
     (DESCRIPTION=
       (RECV_BUF_SIZE=11784)
       (ADDRESS_LIST=
         (ADDRESS=(PROTOCOL=tcp)(HOST=hr1-server)(PORT=1521))
         (ADDRESS=(PROTOCOL=tcp)(HOST=hr2-server)(PORT=1521)))
       (CONNECT_DATA=
         (SERVICE_NAME=hr.us.example.com)))

**Related Topics**

- [Oracle Database Net Services Administrator's Guide](../netag/optimizing-performance.md)

**Parent topic:** Optional Parameters for Description

#### 6.8.5 SDU

Use the `SDU` parameter to configure the session data unit (SDU) size.

##### Purpose

To instruct Oracle Net to optimize the transfer rate of data packets being sent across the network with a specified SDU size.

##### Usage Notes

Put this parameter under the `DESCRIPTION` parameter.

Setting this parameter in the connect descriptor for a client overrides the `DEFAULT_SDU_SIZE` parameter at client-side `sqlnet.ora` file.

##### Default

`8192` bytes (8 KB)

##### Values

`512` to `2097152` bytes

##### Example

    net_service_name=
     (DESCRIPTION=
      (SDU=8192)
       (ADDRESS_LIST=
         (ADDRESS=(PROTOCOL=tcp)(HOST=sales1-server)(PORT=1521))
         (ADDRESS=(PROTOCOL=tcp)(HOST=sales2-server)(PORT=1521)))
      (CONNECT_DATA=
        (SERVICE_NAME=sales.us.example.com))

**Related Topics**

- [Oracle Database Net Services Administrator's Guide](../netag/optimizing-performance.md)

**Parent topic:** Optional Parameters for Description

#### 6.8.6 SEND_BUF_SIZE

Use the `SEND_BUF_SIZE` parameter to specify buffer space for session send operations.

##### Purpose

To specify, in bytes, the buffer space for send operations of sessions.

##### Usage Notes

This parameter is supported by the TCP/IP, TCP/IP with TLS, and SDP protocols.

Put this parameter under the `DESCRIPTION` parameter or at the end of the protocol address.

Setting this parameter in the connect descriptor for a client overrides the [SEND_BUF_SIZE](parameters-for-the-sqlnet.ora.md) parameter at the client-side `sqlnet.ora` file.

**Note:**

Additional protocols might support this parameter on certain operating systems. Refer to the operating system-specific documentation for information about additional protocols.

##### Default

The default value for this parameter is operating system specific. The default for the Linux 2.6 operating system is 16 KB.

##### Example

    net_service_name=
     (DESCRIPTION=
       (ADDRESS_LIST=
         (ADDRESS=(PROTOCOL=tcp)(HOST=sales1-server)(PORT=1521)
            (SEND_BUF_SIZE=11784))
         (ADDRESS=(PROTOCOL=tcp)(HOST=sales2-server)(PORT=1521)
            (SEND_BUF_SIZE=11784)))
       (CONNECT_DATA=
         (SERVICE_NAME=sales.us.example.com)))
    net_service_name=
     (DESCRIPTION=
       (SEND_BUF_SIZE=11784)
       (ADDRESS_LIST=
         (ADDRESS=(PROTOCOL=tcp)(HOST=hr1-server)(PORT=1521)
         (ADDRESS=(PROTOCOL=tcp)(HOST=hr2-server)(PORT=1521)))
       (CONNECT_DATA=
         (SERVICE_NAME=hr.us.example.com)))

**Related Topics**

- [Oracle Database Net Services Administrator's Guide](../netag/optimizing-performance.md)

**Parent topic:** Optional Parameters for Description

#### 6.8.7 SOURCE_ROUTE

Use the `SOURCE_ROUTE` parameter to enable routing through multiple protocol addresses.

##### Purpose

To enable routing through multiple protocol addresses.

##### Usage Notes

When you set this parameter to `on` or `yes`, Oracle Net uses each address in order until the destination is reached.

To use Oracle Connection Manager, an initial connection from the client to Oracle Connection Manager is required, and a second connection from Oracle Connection Manager to the listener is required.

Put this parameter under either the `DESCRIPTION_LIST` parameter, the `DESCRIPTION` parameter, or the `ADDRESS_LIST` parameter.

##### Default

off

##### Values

- `yes` \| `on`

- `no` \| `off`

##### Example

    net_service_name=
     (DESCRIPTION=
      (SOURCE_ROUTE=on)
      (ADDRESS=(PROTOCOL=tcp)(HOST=cman-pc)(PORT=1630))
      (ADDRESS=(PROTOCOL=tcp)(HOST=sales1-svr)(PORT=1521))
      (CONNECT_DATA=(SERVICE_NAME=sales.us.example.com))

**Related Topics**

- [Oracle Database Net Services Administrator's Guide](../netag/enabling-advanced-features.md)

**Parent topic:** Optional Parameters for Description

#### 6.8.8 TYPE_OF_SERVICE

Use the `TYPE_OF_SERVICE` parameter to specify the type of service to use for an Oracle Rdb database.

##### Purpose

To specify the type of service to use for an Oracle Rdb database.

##### Usage Notes

This parameter should only be used if the application supports both an Oracle Rdb and Oracle database service, and you want the application to load balance between the two.

Put this parameter under the `DESCRIPTION` parameter.

##### Example

    net_service_name=
     (DESCRIPTION_LIST=
      (DESCRIPTION=
       (ADDRESS=...)
       (CONNECT_DATA=
        (SERVICE_NAME=generic)
        (RDB_DATABASE=[.mf]mf_personal.rdb)
        (GLOBAL_NAME=alpha5))
       (TYPE_OF_SERVICE=rdb_database))
      (DESCRIPTION=
       (ADDRESS=...)
       (CONNECT_DATA=
        (SERVICE_NAME=sales.us.example.com))
       (TYPE_OF_SERVICE=oracle11_database)))

**Related Topics**

- [Oracle Database Net Services Administrator's Guide](../netag/enabling-advanced-features.md)

**Parent topic:** Optional Parameters for Description

### 6.9 Connection Data Section

Learn how to configure network connections with protocol addresses.

A network object is identified by a protocol address. When a connection is made, the client and the receiver of the request (listener or Oracle Connection Manager) are configured with identical protocol addresses. The client uses this address to send the connection request to a particular network object location, and the recipient "listens" for requests on this address, and grants a connection based on its address information matching the client information.

- COLOCATION_TAG
- CONNECT_DATA
  Use the `CONNECT_DATA` parameter to define the connection service.
- FAILOVER_MODE
- GLOBAL_NAME
- HS
- INSTANCE_NAME
- KERBEROS5_PRINCIPAL
  Use the `KERBEROS5_PRINCIPAL` parameter to set the Kerberos principal name associated with the Kerberos credentials cache (CC) file.
- RDB_DATABASE
- SHARDING_KEY
  Use the `SHARDING_KEY` parameter to route the database connection request to an appropriate shard.
- SUPER_SHARDING_KEY
  Use the `SUPER_SHARDING_KEY` parameter in the case of composite sharding to route the database request to a collection of shards (shardspace).
- SERVER
- SERVICE_NAME

**Parent topic:** Local Naming Parameters in the tnsnames.ora File

#### 6.9.1 COLOCATION_TAG

##### Purpose

To direct the listener to route all connections with the same `colocation_tag` to the same database instance.

##### Usage Notes

Use this parameter with the `CONNECT_DATA` parameter.

The parameter value must be an alphanumeric string.

##### Example

    net_service_name=
     (DESCRIPTION=
       (ADDRESS_LIST=
        (ADDRESS=...)
        (ADDRESS=...))
     (CONNECT_DATA=
        (SERVICE_NAME=sales.us.example.com)
        (COLOCATION_TAG=abc)))

**Note:**

Under certain conditions, such as, when maximum load of an instance is reached or when new instances are added or deleted for a service, the colocation of client connections that have the same `colocation_tag` to the same database instance may not be consistent.

**Parent topic:** Connection Data Section

#### 6.9.2 CONNECT_DATA

Use the `CONNECT_DATA` parameter to define the connection service.

##### Purpose

To define the service to which you want to connect, such as `SERVICE_NAME`.

##### Usage Notes

Put this parameter under the `DESCRIPTION` parameter. `CONNECT_DATA` permits additional parameters as listed in Connection Data Section.

##### Example

    net_service_name=
     (DESCRIPTION=
      (ADDRESS_LIST=
        (ADDRESS=(PROTOCOL=tcp)(HOST=sales1-svr)(PORT=1521))
        (ADDRESS=(PROTOCOL=tcp)(HOST=sales2-svr)(PORT=1521)))
      (CONNECT_DATA=
        (SERVICE_NAME=sales.us.example.com)))

**Parent topic:** Connection Data Section

#### 6.9.3 FAILOVER_MODE

##### Purpose

To instruct Oracle Net to fail over to a different listener if the first listener fails during run time.

##### Usage Notes

Depending upon the configuration, the session or any `SELECT` statements which were in progress are automatically failed over.

This type of failover is called [Transparent Application Failover (TAF)](glossary.md) and should not be confused with the connect-time failover FAILOVER parameter.

Put this parameter under the `CONNECT_DATA` parameter.

##### Additional Parameters

`FAILOVER_MODE` supports the following parameters:

- `BACKUP`: Specifies the failover node by its net service name. A separate net service name must be created for the failover node.

- `TYPE`: Specifies the type of failover. Three types of Oracle Net failover functionality are available by default to [Oracle Call Interface (OCI)](glossary.md) applications:

  - `SESSION`: Fails over the session. For example, if a user's connection is lost, then a new session is automatically created for the user on the backup. This type of failover does not attempt to recover selects.

  - `SELECT`: Allows users with open cursors to continue fetching them after failure. However, this mode involves overhead on the client side in normal select operations.

  - `NONE`: This is the default, in which no failover functionality is used. This can also be explicitly specified to prevent failover from happening.

- `METHOD`: Specifies how fast failover is to occur from the primary node to the backup node:

  - `BASIC`: Establishes connections at failover time. This option requires almost no work on the backup database server until failover time.

  - `PRECONNECT`: Pre-establishes connections. This provides faster failover but requires that the backup instance be able to support all connections from every supported instance.

- `TRANSACTION`: Allows the database to complete the current database transaction following a recoverable error. This parameter is used with the `COMMIT_OUTCOME=TRUE` parameter.

- `RETRIES`: Specifies the number of times to attempt to connect after a failover. If `DELAY` is specified, then `RETRIES` defaults to five retry attempts.

- `DELAY`: Specifies the amount of time in seconds to wait between connect attempts. If `RETRIES` is specified, then `DELAY` defaults to one second.

**Note:**

If a callback function is registered, then `RETRIES` and `DELAY` parameters are ignored.

**See Also:**

[Oracle Database Net Services Administrator's Guide](../netag/enabling-advanced-features.md) for additional configuration information

**Parent topic:** Connection Data Section

#### 6.9.4 GLOBAL_NAME

##### Purpose

To identify the Oracle Rdb database.

##### Usage Notes

Put this parameter under the `CONNECT_DATA` parameter.

##### Example

    net_service_name=
     (DESCRIPTION=
       (ADDRESS_LIST=
        (ADDRESS=...)
        (ADDRESS=...))
       (CONNECT_DATA=
        (SERVICE_NAME=generic)
        (RDB_DATABASE=[.mf]mf_personal.rdb)
        (GLOBAL_NAME=alpha5)))

**Parent topic:** Connection Data Section

#### 6.9.5 HS

##### Purpose

To direct Oracle Net to connect to a non-Oracle system through [Heterogeneous Services](glossary.md).

##### Usage Notes

Put this parameter under the `CONNECT_DATA` parameter.

##### Default

None

##### Values

    ok

##### Example

    net_service_name=
     (DESCRIPTION=
       (ADDRESS_LIST=
         (ADDRESS=...)
         (ADDRESS=...))
       (CONNECT_DATA=
        (SID=sales6)
        )
    (HS=ok))

**See Also:**

[Oracle Database Net Services Administrator's Guide](../netag/enabling-advanced-features.md) for complete configuration information

**Parent topic:** Connection Data Section

#### 6.9.6 INSTANCE_NAME

##### Purpose

To identify the database instance to access.

##### Usage Notes

Set the value to the value specified by the `INSTANCE_NAME` parameter in the initialization parameter file.

Put this parameter under the `CONNECT_DATA` parameter.

##### Example

    net_service_name=
     (DESCRIPTION=
       (ADDRESS_LIST=
         (ADDRESS=...)
         (ADDRESS=...))
       (CONNECT_DATA=
         (SERVICE_NAME=sales.us.example.com)
         (INSTANCE_NAME=sales1)))

**See Also:**

[Oracle Database Net Services Administrator's Guide](../netag/configuring-profiles.md) for additional information about the use of `INSTANCE_NAME`

**Parent topic:** Connection Data Section

#### 6.9.7 KERBEROS5_PRINCIPAL

Use the `KERBEROS5_PRINCIPAL` parameter to set the Kerberos principal name associated with the Kerberos credentials cache (CC) file.

##### Purpose

When you configure Kerberos authentication for an Oracle Database client, you can specify multiple Kerberos principals with a single Oracle Database client.

This is an optional parameter. When specified, it is used to verify if the principal name in the credential cache (specified using `SQLNET.KERBEROS5_CC_NAME`) matches the parameter value.

##### Usage Notes

Use this parameter with the `CONNECT_DATA` parameter in the `tnsnames.ora` file. Alternatively, you can specify `KERBEROS5_CC_NAME` in the connect string along with the optional `KERBEROS5_PRINCIPAL` parameter to connect as a different Kerberos principal.

Each Kerberos principal must have a valid credential cache. Oracle Database checks `KERBEROS5_PRINCIPAL` against the value that is retrieved from the credential cache. If the two values do not match, then the user is not authenticated.

##### Example

For a user `krbuser1`, who is externally authenticated using the Kerberos principal `krbprinc1.example.com` and the credential cache for this principal is located at `/tmp/krbuser1/krb.cc`, the connect string is:

    net_service_name=
    (DESCRIPTION=
          (ADDRESS=(PROTOCOL=tcp)(HOST=sales-svr)(PORT=1521))
          (CONNECT_DATA=(SERVICE_NAME=sales.example.com))
          (SECURITY=
              (KERBEROS5_CC_NAME=/tmp/krbuser1/krb.cc)
              (KERBEROS5_PRINCIPAL=krbprinc1@example.com)))

**Note:**

The connection fails if the principal in the `/tmp/krbuser1/krb.cc` file does not contain the `krbprinc1@example.com` value.

Similarly, for a user `krbuser2`, who is externally authenticated using the Kerberos principal `krbprinc2.example.com` and the credential cache for this principal is located at `/tmp/krbuser2/krb.cc`, the connect string is:

    net_service_name=
    (DESCRIPTION=
          (ADDRESS=(PROTOCOL=tcp)(HOST=sales-svr)(PORT=1521))
          (CONNECT_DATA=(SERVICE_NAME=sales.example.com))
          (SECURITY=
              (KERBEROS5_CC_NAME=/tmp/krbuser2/krb.cc)
              (KERBEROS5_PRINCIPAL=krbprinc2@example.com)))

**Related Topics**

- [SQLNET.KERBEROS5_CC_NAME](parameters-for-the-sqlnet.ora.md)
- [Oracle Database Security Guide](../dbseg/configuring-kerberos-authentication.md)

**Parent topic:** Connection Data Section

#### 6.9.8 RDB_DATABASE

##### Purpose

To specify the file name of an Oracle Rdb database.

##### Usage Notes

Put this parameter under the `CONNECT_DATA` parameter.

##### Example

    net_service_name=
     (DESCRIPTION=
       (ADDRESS_LIST=
         (ADDRESS=...)
         (ADDRESS=...))
       (CONNECT_DATA=
         (SERVICE_NAME=sales.us.example.com)
         (RDB_DATABASE= [.mf]mf_personal.rdb)))

**Parent topic:** Connection Data Section

#### 6.9.9 SHARDING_KEY

Use the `SHARDING_KEY` parameter to route the database connection request to an appropriate shard.

##### Purpose

To specify the value of a sharding key. Based on the value specified during a database connection request, the request is directly routed to the appropriate shard.

##### Usage Notes

You specify this parameter under the `CONNECT_DATA` section of a connect string or `tnsnames.ora` file.

Use the `SHARDING_KEY` parameter to specify a sharding key in simplified text format. This parameter supports only ASCII character set and not special characters. The following data types are supported for a sharding key:

- `NUMBER`

- `INTEGER`

- `SMALLINT`

- `RAW`

- `NVARCHAR`

- `NVARCHAR2`

- `NCHAR`

- `DATE`

- `TIMESTAMP`

Use the `SHARDING_KEY_B64` parameter to specify the base64-encoded binary representation of a sharding key. This parameter supports these special characters: `"` quotation mark `,` comma `( )` close parenthesis `+` plus sign)

##### Values

The fields for base64-encoded values (`*_B64`) start with a header, which is a sequence of space-separated integer values:

    (CONNECT_DATA=
      (SHARDING_KEY_B64=
        [version][type][key column 1 type identifier][key column 2 type identifier] ... ,[base64 string],[base64 string],[base64 string],...))...

In the above syntax:

- Parts of the compound key are separated with a comma.

- `version` specifies the version number of base64 representation. Currently, only version 1 is supported, and thus the supported version value is `1`.

- `type` specifies the character set string and its encoding information. The supported `type` values are:

  | Value | Character Set String                | Encoding Scheme                                                                              |
  |:------|:------------------------------------|:---------------------------------------------------------------------------------------------|
  | `0`   | String contains hash value.         | Character values are encoded in `AL32UTF8` (for `VARCHAR`) and `AL16UTF16` (for `NVARCHAR`). |
  | `1`   | String does not contain hash value. |                                                                                              |
  | `2`   | String does not contain hash value. | Character values are encoded in database encoding, which may be specific for each column.    |
  | `3`   | String contains hash value.         |                                                                                              |
  | `4`   | String contains only hash value.    |                                                                                              |

- key column type identifier specifies the data types. The supported key column type identifier values are:

  | Value | Data Type                              |
  |:------|:---------------------------------------|
  | `1`   | `VARCHAR`, `NVARCHAR`, `CHAR`, `NCHAR` |
  | `2`   | `NUMBER`                               |
  | `6`   | `NUMBER` with length in first byte     |
  | `12`  | `DATE`                                 |
  | `23`  | `RAW`                                  |
  | `180` | `TIMESTAMP`                            |

- The header is terminated by a comma and is followed by base64 string. base64 string is a comma-separated list of the base64-encoded value string. The hash value, if available, is the last value in the list.

Example 6-8

In the following sample connect string, the `SHARDING_KEY` parameter value is specified in simplified text format:

    net_service_name=
     (DESCRIPTION=
      (ADDRESS_LIST=
        (ADDRESS=(host=sales-east1)(port=1522))
        (ADDRESS=(host=sales-east2)(port=1522))
      )
      (CONNECT_DATA=
        (SERVICE_NAME=sales.us.example.com)
        (SHARDING_KEY=40598230)
      )
     )

Example 6-9

In the following sample connect string, the `SHARDING_KEY_B64` parameter value is encoded to base64 binary representation:

    net_service_name=
     (DESCRIPTION=
      (ADDRESS_LIST=
        (ADDRESS=(host=sales-east1)(port=1522))
        (ADDRESS=(host=sales-east2)(port=1522))
      )
      (CONNECT_DATA=
        (SERVICE_NAME=sales.us.example.com)
        (SHARDING_KEY_B64=1 1 2,VVM=,OTQwMDI=)
      )
     )

**Related Topics**

- SUPER_SHARDING_KEY
- [Oracle Database Net Services Administrator's Guide](../netag/optimizing-performance.md)

**Parent topic:** Connection Data Section

#### 6.9.10 SUPER_SHARDING_KEY

Use the `SUPER_SHARDING_KEY` parameter in the case of composite sharding to route the database request to a collection of shards (shardspace).

##### Purpose

To specify a shardspace key for a collection of shards. A shardspace is set of shards that store data that corresponds to a range or list of key values. Based on the value specified during a database connection request, the request is directly routed to an appropriate shardspace.

##### Usage Notes

You specify this parameter under the `CONNECT_DATA` section of a connect string or `tnsnames.ora` file.

Use the `SUPER_SHARDING_KEY` parameter to specify a shardspace key for a collection of shards in simplified text format. This parameter supports only ASCII character set and not special characters. The supported data types for a super sharding key are the same as those for a sharding key.

Use the `SUPER_SHARDING_KEY_B64` parameter to specify the base64-encoded binary representation of a shardspace key. This parameter supports special characters (such as " quotation mark , comma ( ) close parenthesis + plus sign).

##### Values

The fields for base64-encoded values (`*_B64`) start with a header, which is a sequence of space-separated integer values:

    (CONNECT_DATA=(SUPER_SHARDING_KEY_B64=[version] [type] [integer literal] [integer literal] ... ,[base64 binary],[base64 binary],[base64 binary],...))...

For details on each of the base64-encoded header fields, see SHARDING_KEY.

Example 6-10

In the following sample connect string, the `SHARDING_KEY` and `SUPER_SHARDING_KEY` parameter values are specified in simplified text format:

    net_service_name=
     (DESCRIPTION=
      (ADDRESS_LIST=
        (ADDRESS=(host=sales-east1)(port=1522))
        (ADDRESS=(host=sales-east2)(port=1522))
      )
      (CONNECT_DATA=
        (SERVICE_NAME=sales.us.example.com)
        ((SHARDING_KEY=40598230)(SUPER_SHARDING_KEY=gold))
      )
     )

Example 6-11

In the following sample connect string, the `SHARDING_KEY_B64` and `SUPER_SHARDING_KEY_B64` parameter values are encoded to base64 binary representation:

    net_service_name=
     (DESCRIPTION=
      (ADDRESS_LIST=
        (ADDRESS=(host=sales-east1)(port=1522))
        (ADDRESS=(host=sales-east2)(port=1522))
      )
      (CONNECT_DATA=
        (SERVICE_NAME=sales.us.example.com)
        ((SHARDING_KEY_B64=1 1 2,VVM=,OTQwMDI=)(SUPER_SHARDING_KEY_B64=1 1,BBWEPGRBBDOEMGQW))
      )
     )

**Related Topics**

- SHARDING_KEY
- [Oracle Database Net Services Administrator's Guide](../netag/optimizing-performance.md)

**Parent topic:** Connection Data Section

#### 6.9.11 SERVER

##### Purpose

To direct the listener to connect the client to a specific type of [service handler](glossary.md).

##### Usage Notes

Put this parameter under the `CONNECT_DATA` parameter.

##### Values

- `dedicated` to specify whether client requests be served by [dedicated server](glossary.md).

- `shared` to specify whether client requests be served by a [dispatcher](glossary.md) or [shared server](glossary.md).

- `pooled` to get a connection from the connection pool if database resident connection pooling is enabled on the server.

**Note:**

- Shared server must be configured in the database initialization file in order for the client to connect to the database with a shared server process.

- The [USE_DEDICATED_SERVER](parameters-for-the-sqlnet.ora.md) parameter in the `sqlnet.ora` file overrides this parameter.

##### Example

    net_service_name=
     (DESCRIPTION=
       (ADDRESS_LIST=
         (ADDRESS=...)
         (ADDRESS=...))
       (CONNECT_DATA=
        (SERVICE_NAME=sales.us.example.com)
        (SERVER=dedicated)))

**Parent topic:** Connection Data Section

#### 6.9.12 SERVICE_NAME

##### Purpose

To identify the Oracle Database database service to access.

##### Usage Notes

Set the value to a value specified by the `SERVICE_NAMES` parameter in the initialization parameter file.

Put this parameter under the `CONNECT_DATA` parameter.

##### Example

    net_service_name=
     (DESCRIPTION=
       (ADDRESS_LIST=
         (ADDRESS=...)
         (ADDRESS=...))
       (CONNECT_DATA=
         (SERVICE_NAME=sales.us.example.com)))

**Related Topics**

- [Oracle Database Net Services Administrator's Guide](../netag/configuring-profiles.md)

**Parent topic:** Connection Data Section

### 6.10 Security Section

The security section of the `tnsnames.ora` file specifies these security-related parameters for use with Oracle security features.

- AUTHENTICATION_SERVICE
  Use the `tnsnames.ora` parameter `AUTHENTICATION_SERVICE` to enable an authentication service.
- IGNORE_ANO_ENCRYPTION_FOR_TCPS
  The `IGNORE_ANO_ENCRYPTION_FOR_TCPS` parameter specifies if the `SQLNET.ENCRYPTION_CLIENT` parameter should be ignored for this specific TNS alias.
- KERBEROS5_CC_NAME
  Use the `tnsnames.ora` parameter `KERBEROS5_CC_NAME` to specify the complete path name to the Kerberos credentials cache (CC) file.
- OCI_COMPARTMENT
  Use the `OCI_COMPARTMENT` parameter to specify Oracle Cloud Identifier (OCID) of the compartment that holds database instances for client connections.
- OCI_DATABASE
  Use the `OCI_DATABASE` parameter to specify Oracle Cloud Identifier (OCID) of the database that you want to access for the client connection.
- OCI_IAM_URL
  Use the `OCI_IAM_URL` parameter to specify an endpoint URL that the database client must connect with to get the database token for authenticating Oracle Cloud Infrastructure (OCI) Identity and Access Management (IAM) users on OCI Database as a Service (DBaaS).
- OCI_TENANCY
  Use the `OCI_TENANCY` parameter to specify Oracle Cloud Identifier (OCID) of the user’s tenancy.
- PASSWORD_AUTH
  With this setting, client connections use the IAM user name and IAM database password for logging in users to the database.
- SECURITY
  Use the `SECURITY` parameter to change the security properties of a connection.
- SSL_DISABLE_WEAK_EC_CURVES
  Use the `SSL_DISABLE_WEAK_EC_CURVES` parameter to disable the use of weak Elliptic Curve Cryptography (ECC) curves.
- SSL_SERVER_CERT_DN
  Use the `SSL_SERVER_CERT_DN` parameter to specify the distinguished name (DN) of the database server.
- SSL_SERVER_DN_MATCH
  Use the `SSL_SERVER_DN_MATCH` parameter to enforce server-side certificate validation through distinguished name (DN) matching.
- SSL_VERSION
  Use the `SSL_VERSION` parameter to define valid Transport Layer Security (TLS) versions to be used for connections.
- TOKEN_AUTH
  Use the `TOKEN_AUTH` parameter to configure token-based authentication for Oracle Cloud Infrastructure (OCI) Identity and Access Management (IAM) or Microsoft Azure users of Microsoft Entra ID (previously called Microsoft Azure Active Directory).
- TOKEN_LOCATION
  Use the `TOKEN_LOCATION` parameter to specify the directory location where token file is stored for token-based authentication.
- WALLET_LOCATION
  Use the `WALLET_LOCATION` parameter in the `tnsnames.ora` file to specify different locations where Oracle wallets are stored.

**Parent topic:** Local Naming Parameters in the tnsnames.ora File

#### 6.10.1 AUTHENTICATION_SERVICE

Use the `tnsnames.ora` parameter `AUTHENTICATION_SERVICE` to enable an authentication service.

##### Purpose

To enable an authentication service. If you have installed authentication, then Oracle recommends that you set `AUTHENTICATION_SERVICE` to either `NONE` or to one of the listed authentication methods.

##### Usage Notes

- Use this parameter in the `SECURITY` section of the `tnsnames.ora` file or directly as part of the connect string.

  You can also set this value in the `sqlnet.ora` file. The `AUTHENTICATION_SERVICE` parameter is equivalent to the `sqlnet.ora` parameter `SQLNET.AUTHENTICATION_SERVICES`. The parameter value specified in the connect string takes precedence.

  Note that the `AUTHENTICATION_SERVICE` parameter can take only a single authentication service, unlike the `SQLNET.AUTHENTICATION_SERVICES` parameter that can take multiple values.

- When using the `AUTHENTICATION_SERVICE=ALL`, the server attempts to authenticate using each of the following methods:

  1.  Authentication based on a service external to the database, such as a service on the network layer, Kerberos, or RADIUS.

  2.  Authentication based on the operating system user's membership in an administrative operating system group. Group names are platform-specific. This authentication applies to administrative connections only.

  3.  Authentication performed by the database.

  4.  Authentication based on credentials stored in a directory server.

  The server falls back to the authentication methods that appear further down on the list if attempts to use the authentication methods appearing higher on the list were unsuccessful.

- When using local database password authentication (no external authentication), set `AUTHENTICATION_SERVICE=NONE` for better client performance.

- Operating system authentication enables access to the database using any user name and any password when an administrative connection is attempted to the CDB root, such as using the `AS SYSDBA` clause when connecting using SQL\*Plus.

  An example of a connection to the CDB root is as follows.

      sqlplus ignored_username/ignored_password AS SYSDBA

  When the operating-system user who issued the preceding command is already a member of the appropriate administrative operating system group, then the connection is successful. This is because Oracle checks the group membership first, and thus the user name and password are ignored by the server.

##### Default

`ALL`

**Note:**

When installing Oracle Database with Database Configuration Assistant (DBCA), you can set this parameter to `NTS` in the `sqlnet.ora` file.

##### Values

Authentication methods that are available with Oracle Net Services:

- `NONE` for no authentication methods, including Microsoft Windows native operating system authentication. When you set `AUTHENTICATION_SERVICE` to `NONE`, then the user can use a valid user name and password to access the database.

- `ALL` for all authentication methods.

- `BEQ` for native operating system authentication for operating systems other than Microsoft Windows.

- `KERBEROS5` for Kerberos authentication.

- `RADIUS` for Remote Authentication Dial-In User Service (RADIUS) authentication.

- `TCPS` for TLS authentication.

- `NTS` for Microsoft Windows native operating system authentication. In this case, the user must authenticate to the database (CDB root) with OS credentials using Windows native authentication. No external password is needed. NTS checks the group membership for an OS user. For example, if an OS user is a member of the `ORA_DBA` group, then the user can log in to the database as `SYSDBA`.

  **Note:**

  With the `AUTHENTICATION_SERVICE=NTS` setting, if you try to connect through SQL\*Plus using NTS authentication and specify an external password (for example, `SQL*Plus SYSTEM/``password`), then the connection fails with an `ORA-12638: credential retrieval failed` error. For regular user name and password based authentication, set the value to `NONE`.

##### Example

    net_service_name=
        (DESCRIPTION=
            (ADDRESS=(PROTOCOL=tcps)(HOST=sales-svr)(PORT=1521))
            (SECURITY=(AUTHENTICATION_SERVICE=KERBEROS5))
            (CONNECT_DATA=(SERVICE_NAME=sales.us.example.com))
        )

**Related Topics**

- [Oracle Database Security Guide](../dbseg/configuring-authentication.md)
- [SQLNET.AUTHENTICATION_SERVICES](parameters-for-the-sqlnet.ora.md)

**Parent topic:** Security Section

#### 6.10.2 IGNORE_ANO_ENCRYPTION_FOR_TCPS

The `IGNORE_ANO_ENCRYPTION_FOR_TCPS` parameter specifies if the `SQLNET.ENCRYPTION_CLIENT` parameter should be ignored for this specific TNS alias.

##### Purpose

To specify if the `SQLNET.ENCRYPTION_CLIENT` parameter should be ignored for this specific TNS alias.

##### Usage Notes

If your requirements are that `SQLNET.ENCRYPTION_SERVER` be set to `required`, then you can set the `IGNORE_ANO_ENCRYPTION_FOR_TCPS` parameter in both `SQLNET.ENCRYPTION_CLIENT` and `SQLNET.ENCRYPTION_SERVER` to `TRUE`. This forces the client to ignore the value that is set for the `SQLNET.ENCRYPTION_CLIENT` parameter for all outgoing TCPS connections.

##### Default

`FALSE`

Example 6-12 Example

    test_ssl=
        (DESCRIPTION =
           (ADDRESS=(PROTOCOL=tcps)(HOST=)(PORT=1750))
           (CONNECT_DATA=(SID=^ORACLE_SID^))
           (SECURITY=(IGNORE_ANO_ENCRYPTION_FOR_TCPS=TRUE))
         )

**Parent topic:** Security Section

#### 6.10.3 KERBEROS5_CC_NAME

Use the `tnsnames.ora` parameter `KERBEROS5_CC_NAME` to specify the complete path name to the Kerberos credentials cache (CC) file.

##### Purpose

To specify the complete path name to the Kerberos CC file.

##### Usage Notes

Use this parameter in the `SECURITY` section of the `tnsnames.ora` file or directly as part of the connect string.

You can also set this value in the `sqlnet.ora` file. The `KERBEROS5_CC_NAME` parameter is equivalent to the `sqlnet.ora` parameter `SQLNET.KERBEROS5_CC_NAME`. The parameter value specified in the connect string takes precedence.

##### Values and Examples

You can use the following formats to specify a value for `KERBEROS5_CC_NAME`:

- If the Oracle database is using a directory cache:
  - `KERBEROS5_CC_NAME=``complete_path_to_cc_file`

    For example:

    `KERBEROS5_CC_NAME=/tmp/kcache`

    `KERBEROS5_CC_NAME=D:\tmp\kcache`

  - `KERBEROS5_CC_NAME=FILE:``complete_path_to_cc_ file`

    For example:

    `KERBEROS5_CC_NAME=FILE:/tmp/kcache`
- If the Oracle database is using the native Windows cache:
  - `KERBEROS5_CC_NAME=OSMSFT://`

  - `KERBEROS5_CC_NAME=MSLSA:`

  The `OSMSFT` and `MSLSA` options specify that the file is on Microsoft Windows and is running Microsoft Kerberos Key Distribution Center (KDC).

**Note:**

If you want to authenticate multiple Kerberos principals, then you can specify additional Kerberos principals either through the connect string directly or in the `tnsnames.ora` file.

##### Default

The default value is operating system-dependent, as follows:

- On Linux and UNIX operating systems: `/tmp/krb5cc_userid`

- On Microsoft Windows operating systems: `c:\tmp\krbcache`

**Related Topics**

- KERBEROS5_PRINCIPAL
- [SQLNET.KERBEROS5_CC_NAME](parameters-for-the-sqlnet.ora.md)
- [Oracle Database Security Guide](../dbseg/configuring-kerberos-authentication.md)

**Parent topic:** Security Section

#### 6.10.4 OCI_COMPARTMENT

Use the `OCI_COMPARTMENT` parameter to specify Oracle Cloud Identifier (OCID) of the compartment that holds database instances for client connections.

##### Purpose

To define the scope of your database token request. This value instructs the database client to initiate a token request to databases within the specified compartment only.

##### Usage Notes

You can use this parameter along with the `PASSWORD_AUTH`, `OCI_IAM_URL`, and `OCI_TENANCY` parameters while configuring token-based authentication for Oracle Cloud Infrastructure (OCI) Identity and Access Management (IAM) users on OCI Database as a Service (DBaaS). You can also use the optional `OCI_DATABASE` parameter to specify a database instance within the compartment for your connection.

With this configuration, the database client can only request an IAM database token using the IAM user name and IAM database password. The client cannot request an IAM database token for an API-key, delegation token, security token, resource principal, service principal, or instance principal.

The `OCI_COMPARTMENT` parameter is optional if `OCI_DATABASE` is not set. If you choose to set `OCI_DATABASE`, then you must also set `OCI_COMPARTMENT` so that your token request is for the specified database in that compartment.

If you do not set both `OCI_COMPARTMENT` and `OCI_DATABASE`, then the entire tenancy is the scope of your token request.

Use this parameter under the `SECURITY` section of the `tnsnames.ora` file, `sqlnet.ora` file, or directly as part of the command-line connect string. The parameter value specified in the connect string takes precedence over the other specified values.

##### Default

None

##### Value

OCID for the IAM compartment to allow access for the database token. You can get the OCID value for your compartment from the Compartments information page in the OCI console.

The compartment OCID uses this syntax:

`OCI_COMPARTMENT=``compartment_OCID`

For details on the syntax options, see [Oracle Cloud IDs (OCIDs)](https://docs.oracle.com/en-us/iaas/Content/GSG/Tasks/contactingsupport_topic-Finding_the_OCID_of_a_Compartment.htm).

##### Examples

In the `tnsnames.ora` file:

    net_service_name=
      (DESCRIPTION=
         (ADDRESS=(PROTOCOL=tcps)(HOST=salesserver1)(PORT=1522))
         (SECURITY=
            (SSL_SERVER_DN_MATCH=TRUE)
            (SSL_SERVER_CERT_DN="C=US,O=example,CN=OracleContext")
            (PASSWORD_AUTH=OCI_TOKEN)
            (OCI_IAM_URL=https://auth.us-region-1.example.com/v1/actions/generateScopedAccessBearerToken)
            (OCI_TENANCY=ocid1.tenancy..12345)
            (OCI_COMPARTMENT=ocid1.compartment..12345)
            (OCI_DATABASE=ocid1.autonomousdatabase.oc1.12345))
         (CONNECT_DATA=(SERVICE_NAME=sales.us.example.com))
      )

In the `sqlnet.ora` file:

    SSL_SERVER_DN_MATCH=TRUE
    PASSWORD_AUTH=OCI_TOKEN
    OCI_IAM_URL=https://auth.us-region-1.example.com/v1/actions/generateScopedAccessBearerToken
    OCI_TENANCY=ocid1.tenancy..12345
    OCI_COMPARTMENT=ocid1.compartment..12345
    OCI_DATABASE=ocid1.autonomousdatabase.oc1.12345

**Related Topics**

- [Oracle Database Security Guide](../dbseg/authenticating-and-authorizing-iam-users-oracle-dbaas-databases.md)
- PASSWORD_AUTH

**Parent topic:** Security Section

#### 6.10.5 OCI_DATABASE

Use the `OCI_DATABASE` parameter to specify Oracle Cloud Identifier (OCID) of the database that you want to access for the client connection.

##### Purpose

To define the scope of your database token request. The database OCID value instructs the database client to initiate a token request to the specified database within your compartment.

##### Usage Notes

This parameter is optional. You can use this parameter along with the `PASSWORD_AUTH`, `OCI_IAM_URL`, `OCI_TENANCY`, and `OCI_COMPARTMENT` parameters while configuring token-based authentication for Oracle Cloud Infrastructure (OCI) Identity and Access Management (IAM) users on OCI Database as a Service (DBaaS).

With this configuration, the database client can only request an IAM database token using the IAM user name and IAM database password. The client cannot request an IAM database token for an API-key, delegation token, security token, resource principal, service principal, or instance principal.

The `OCI_DATABASE` value limits your token request to the specified database only. If you set `OCI_DATABASE`, then you must also set `OCI_COMPARTMENT` so that your token request is for the specified database in that compartment.

Use this parameter under the `SECURITY` section of the `tnsnames.ora` file, `sqlnet.ora` file, or directly as part of the command-line connect string. The parameter value specified in the connect string takes precedence over the other specified values.

##### Default

None

##### Value

OCID of the database that you want to access for the client connection. You can get the OCID value for your database from the Database details page in the OCI console.

The database OCID uses this syntax:

`OCI_DATABASE=``database_OCID`

For details on the syntax options, see [Oracle Cloud IDs (OCIDs)](https://docs.oracle.com/en-us/iaas/autonomous-database/doc/view-list-acds-compartment.html).

##### Examples

In the `tnsnames.ora` file:

    net_service_name=
      (DESCRIPTION=
         (ADDRESS=(PROTOCOL=tcps)(HOST=salesserver1)(PORT=1522))
         (SECURITY=
            (SSL_SERVER_DN_MATCH=TRUE)
            (SSL_SERVER_CERT_DN="C=US,O=example,CN=OracleContext")
            (PASSWORD_AUTH=OCI_TOKEN)
            (OCI_IAM_URL=https://auth.us-region-1.example.com/v1/actions/generateScopedAccessBearerToken)
            (OCI_TENANCY=ocid1.tenancy..12345)
            (OCI_COMPARTMENT=ocid1.compartment..12345)
            (OCI_DATABASE=ocid1.autonomousdatabase.oc1.12345))
         (CONNECT_DATA=(SERVICE_NAME=sales.us.example.com))
      )

In the `sqlnet.ora` file:

    SSL_SERVER_DN_MATCH=TRUE
    PASSWORD_AUTH=OCI_TOKEN
    OCI_IAM_URL=https://auth.us-region-1.example.com/v1/actions/generateScopedAccessBearerToken
    OCI_TENANCY=ocid1.tenancy..12345
    OCI_COMPARTMENT=ocid1.compartment..12345
    OCI_DATABASE=ocid1.autonomousdatabase.oc1.12345

**Related Topics**

- [Oracle Database Security Guide](../dbseg/authenticating-and-authorizing-iam-users-oracle-dbaas-databases.md)
- PASSWORD_AUTH

**Parent topic:** Security Section

#### 6.10.6 OCI_IAM_URL

Use the `OCI_IAM_URL` parameter to specify an endpoint URL that the database client must connect with to get the database token for authenticating Oracle Cloud Infrastructure (OCI) Identity and Access Management (IAM) users on OCI Database as a Service (DBaaS).

##### Purpose

To specify the IAM URL for your REST API requests. The database client connects to this URL to retrieve the database token from IAM.

##### Usage Notes

You set the `OCI_IAM_URL` parameter along with the `PASSWORD_AUTH` and `OCI_TENANCY` parameters while configuring IAM token-based authentication (using the IAM user name and IAM database password to retrieve the database token). These parameters are mandatory.

With this configuration, the database client can only request an IAM database token using the IAM user name and IAM database password. The client cannot request an IAM database token for an API-key, delegation token, security token, resource principal, service principal, or instance principal.

You can also set the optional `OCI_COMPARTMENT` and `OCI_DATABASE` parameters to specify the scope of your token request.

Use this parameter under the `SECURITY` section of the `tnsnames.ora` file, `sqlnet.ora` file, or directly as part of the command-line connect string. The parameter value specified in the connect string takes precedence over the other specified values.

##### Default

None

##### Value

OCI IAM endpoint URL that the database client must connect with to get the database token. This URL is specific to your region and uses this syntax:

    <authentication_regional_endpoint>/v1/actions/generateScopedAccessBearerToken

You can derive this value by replacing \<authentication_regional_endpoint\> with the API endpoint URL for your region. To obtain the appropriate API endpoint URL, see [Identity and Access Management Data Plane API](https://docs.oracle.com/en-us/iaas/api/#/en/identity-dp/v1/).

For example, if you want to use the URL as `https://auth.us-region-1.example.com`, then your OCI_IAM_URL value is:

    https://auth.us-region-1.example.com/v1/actions/generateScopedAccessBearerToken

##### Examples

In the `tnsnames.ora` file:

    net_service_name=
      (DESCRIPTION=
         (ADDRESS=(PROTOCOL=tcps)(HOST=salesserver1)(PORT=1522))
         (SECURITY=
            (SSL_SERVER_DN_MATCH=TRUE)
            (SSL_SERVER_CERT_DN="C=US,O=example,CN=OracleContext")
            (PASSWORD_AUTH=OCI_TOKEN)
            (OCI_IAM_URL=https://auth.us-region-1.example.com/v1/actions/generateScopedAccessBearerToken)
            (OCI_TENANCY=ocid1.tenancy..12345))
         (CONNECT_DATA=(SERVICE_NAME=sales.us.example.com))
      )

In the `sqlnet.ora` file:

    SSL_SERVER_DN_MATCH=TRUE
    PASSWORD_AUTH=OCI_TOKEN
    OCI_IAM_URL=https://auth.us-region-1.example.com/v1/actions/generateScopedAccessBearerToken
    OCI_TENANCY=ocid1.tenancy..12345

In these examples, the optional `OCI_COMPARTMENT` and `OCI_DATABASE` parameters are not specified and thus the entire tenancy is set as the scope of the token request.

**Related Topics**

- [Oracle Database Security Guide](../dbseg/authenticating-and-authorizing-iam-users-oracle-dbaas-databases.md)
- PASSWORD_AUTH

**Parent topic:** Security Section

#### 6.10.7 OCI_TENANCY

Use the `OCI_TENANCY` parameter to specify Oracle Cloud Identifier (OCID) of the user’s tenancy.

##### Purpose

To specify OCID of the user’s tenancy (root compartment).

##### Usage Notes

You set this parameter along with the mandatory `PASSWORD_AUTH` and `OCI_IAM_URL` parameters while configuring token-based authentication for Oracle Cloud Infrastructure (OCI) Identity and Access Management (IAM) users on OCI Database as a Service (DBaaS).

With this configuration, the database client can only request an IAM database token using the IAM user name and IAM database password. The client cannot request an IAM database token for an API-key, delegation token, security token, resource principal, service principal, or instance principal.

You can also set the optional `OCI_COMPARTMENT` and `OCI_DATABASE` parameters to specify the scope of your token request. If you do not set the `OCI_COMPARTMENT` and `OCI_DATABASE` parameter values, then the entire tenancy is the scope of your token request.

Use this parameter under the `SECURITY` section of the `tnsnames.ora` file, `sqlnet.ora` file, or directly as part of the command-line connect string. The parameter value specified in the connect string takes precedence over the other specified values.

##### Default

None

##### Value

OCID of the user’s tenancy. You can get the OCID value for your tenancy from the Tenancy information page in the OCI console.

The tenancy OCID uses this syntax:

`OCI_TENANCY=``tenancy_OCID`

For details on the syntax options, see [Oracle Cloud IDs (OCIDs)](https://docs.oracle.com/en-us/iaas/Content/General/Concepts/identifiers.htm#Resource_Identifiers).

##### Examples

In the `tnsnames.ora` file:

    net_service_name=
      (DESCRIPTION=
         (ADDRESS=(PROTOCOL=tcps)(HOST=salesserver1)(PORT=1522))
         (SECURITY=
            (SSL_SERVER_DN_MATCH=TRUE)
            (SSL_SERVER_CERT_DN="C=US,O=example,CN=OracleContext")
            (PASSWORD_AUTH=OCI_TOKEN)
            (OCI_IAM_URL=https://auth.us-region-1.example.com/v1/actions/generateScopedAccessBearerToken)
            (OCI_TENANCY=ocid1.tenancy..12345))
         (CONNECT_DATA=(SERVICE_NAME=sales.us.example.com))
      )

In the `sqlnet.ora` file:

    SSL_SERVER_DN_MATCH=TRUE
    PASSWORD_AUTH=OCI_TOKEN
    OCI_IAM_URL=https://auth.us-region-1.example.com/v1/actions/generateScopedAccessBearerToken
    OCI_TENANCY=ocid1.tenancy..12345

In these examples, the optional `OCI_COMPARTMENT` and `OCI_DATABASE` parameters are not specified and thus the entire tenancy is set as the scope of the token request.

**Related Topics**

- [Oracle Database Security Guide](../dbseg/authenticating-and-authorizing-iam-users-oracle-dbaas-databases.md)
- PASSWORD_AUTH

**Parent topic:** Security Section

#### 6.10.8 PASSWORD_AUTH

Use the `PASSWORD_AUTH` parameter to configure an authentication method for Oracle Cloud Infrastructure (OCI) Identity and Access Management (IAM) users on OCI Database as a Service (DBaaS). With this setting, client connections use the IAM user name and IAM database password for logging in users to the database.

##### Purpose

To configure either IAM database password verifier authentication or IAM token-based authentication, using the IAM user name and IAM database password for the access.

For password verifier authentication, the database server retrieves an IAM database password verifier from IAM. For token-based authentication, the database client requests a database token (`db-token`) from IAM.

##### Usage Notes

- Use this parameter under the `SECURITY` section of the `tnsnames.ora` file, `sqlnet.ora` file, or directly as part of the command-line connect string. The parameter value specified in the connect string takes precedence over the other specified values.

- This setting instructs the database client to either use the existing password login process with the database server (password verifier authentication) or to get a token with the IAM user name and IAM database password (token-based authentication). This IAM database password is different from the OCI console password. An IAM user can set this password from the OCI console.

  See [Create an OCI IAM password to use for Autonomous Databases User Authentication and Authorization](https://www.youtube.com/watch?v=Y0jYPPnO5Dwx).

- By default, this parameter is set to `PASSWORD_VERIFIER`. The `PASSWORD_AUTH=PASSWORD_VERIFIER` setting configures IAM database password verifier authentication. The database server retrieves an IAM database password verifier (an encrypted hash of password) from IAM to authenticate users.

  When an IAM user logs in with the IAM user name and IAM database password using `@connect_identifier`, the `PASSWORD_AUTH=PASSWORD_VERIFIER` setting along with `@connect_identifier` instructs the database client to follow the existing user name and password login process with the database server.

  You can use the `PASSWORD_AUTH` parameter to override the `tnsnames.ora` or `sqlnet.ora` setting by specifying a different value in the connect string.

- To configure IAM token-based authentication with the IAM user name and IAM database password, set `PASSWORD_AUTH=OCI_TOKEN`. The database client requests a database token (`db-token`) from IAM for the user to access the database.

  This `db-token` obtained by the client is a bearer token with an expiration time and scope, and does not come with a private key. These tokens are transmitted over secure channels. You must use only the TCP/IP with Transport Layer Security (TLS) protocol, otherwise an error message appears indicating that non-TLS connections are disallowed.

  When an IAM user logs in with the IAM user name and IAM database password using `/@connect_identifier`, the `PASSWORD_AUTH=OCI_TOKEN` setting along with `/@connect_identifier` instructs the database client to get the token directly from an OCI IAM endpoint using a REST API request. If the IAM user is mapped to a database schema (exclusively or shared), then the login is completed.

  For the database client to retrieve the token from IAM, you must set additional parameters so that the database client can find the IAM endpoint along with additional meta-data. The additional parameters are `OCI_IAM_URL` and `OCI_TENANCY` along with the optional `OCI_COMPARTMENT` and `OCI_DATABASE`. These values enable the database client to make appropriate calls to the specified endpoint.

  The `OCI_IAM_URL` parameter specifies the API endpoint URL that the database client must connect with. The `OCI_TENANCY` parameter specifies the OCID (Oracle Cloud Identifier) of the user’s tenancy. The optional `OCI_COMPARTMENT` and `OCI_DATABASE` parameters limit the scope of your request.

  This authentication method is more secure than using a password verifier because a password verifier is considered sensitive. Also, only the database client can retrieve the database token. Applications or tools cannot pass these types of tokens through the database client API.

**Note:**

You can also use other IAM user credentials (such as API-key, security token, resource principal, service principal, instance principal, or delegation token) to get the `db-token`. This `db-token` is a proof-of-possession (PoP) token. In this case, you use a different parameter setting (`TOKEN_AUTH=OCI_TOKEN`).

Unlike the IAM database password that can only be used by the database client to retrieve the token, these credentials require an application or tool to retrieve the token. See TOKEN_AUTH.

##### Default

`PASSWORD_VERIFIER`

##### Values and Examples

| Value                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | Example                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| For IAM database password verifier authentication:<br>`PASSWORD_AUTH=PASSWORD_VERIFIER`<br>Note: Use of IAM user name and IAM database password with the IAM database password verifier is the default configuration, and you do not need to set any additional parameters for the client.<br>However, if `PASSWORD_AUTH` is set to `OCI_TOKEN` in the client-side `sqlnet.ora` file, then the client tries to connect with OCI IAM to retrieve a database token using the IAM user name and IAM database password. In this case, you can override this setting for a particular connection using `PASSWORD_AUTH=PASSWORD_VERIFIER`. | In the `tnsnames.ora` file:<br>`net_service_name=`<br>`  (DESCRIPTION =`<br>`     (ADDRESS=(PROTOCOL=tcps)(HOST=sales-svr)(PORT=1521))`<br>`     (SECURITY=`<br>`        (SSL_SERVER_DN_MATCH=TRUE)`<br>`        (SSL_SERVER_CERT_DN="C=US,O=example,CN=OracleContext")`<br>`        (PASSWORD_AUTH=PASSWORD_VERIFIER))`<br>`     (CONNECT_DATA=(SERVICE_NAME=sales.us.example.com))`<br>`  ) `<br>In the `sqlnet.ora` file:<br>`PASSWORD_AUTH=PASSWORD_VERIFIER`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| For IAM token-based authentication with the IAM user name and IAM database password:<br>`PASSWORD_AUTH=OCI_TOKEN`<br>Note: You must configure the TCPS protocol (`PROTOCOL=tcps`) and set the `SSL_SERVER_DN_MATCH` parameter to `TRUE` for token-based authentication.                                                                                                                                                                                                                                                                                                                                                              | In the `tnsnames.ora` file:<br>`net_service_name=`<br>`  (DESCRIPTION=`<br>`     (ADDRESS=(PROTOCOL=tcps)(HOST=salesserver1)(PORT=1522))`<br>`     (SECURITY=`<br>`        (SSL_SERVER_DN_MATCH=TRUE)`<br>`        (SSL_SERVER_CERT_DN="C=US,O=example,CN=OracleContext")`<br>`        (PASSWORD_AUTH=OCI_TOKEN)`<br>`        (OCI_IAM_URL=https://auth.us-region-1.example.com/v1/actions/generateScopedAccessBearerToken)`<br>`        (OCI_TENANCY=ocid1.tenancy..12345))`<br>`     (CONNECT_DATA=(SERVICE_NAME=sales.us.example.com))  `<br>`  )`<br>In the `sqlnet.ora` file:<br>`SSL_SERVER_DN_MATCH=TRUE`<br>`PASSWORD_AUTH=OCI_TOKEN`<br>`OCI_IAM_URL=https://auth.us-region-1.example.com/v1/actions/generateScopedAccessBearerToken`<br>`OCI_TENANCY=ocid1.tenancy..12345`<br>In these examples, the optional `OCI_COMPARTMENT` and `OCI_DATABASE` parameters are not specified and thus the entire tenancy is set as the scope of the token request. |

**Related Topics**

- [Oracle Database Security Guide](../dbseg/authenticating-and-authorizing-iam-users-oracle-dbaas-databases.md)
- OCI_IAM_URL
- OCI_TENANCY
- OCI_COMPARTMENT
- OCI_DATABASE

**Parent topic:** Security Section

#### 6.10.9 SECURITY

Use the `SECURITY` parameter to change the security properties of a connection.

##### Purpose

To change the security properties of a connection.

##### Usage Notes

Put this parameter under the `DESCRIPTION` parameter. `SECURITY` permits additional parameters as listed in Security Section.

##### Example

    net_service_name=
     (DESCRIPTION=
      (ADDRESS_LIST=
        (ADDRESS=(PROTOCOL=tcp)(HOST=sales1-svr)(PORT=1521))
        (ADDRESS=(PROTOCOL=tcp)(HOST=sales2-svr)(PORT=1521)))
      (CONNECT_DATA=
        (SERVICE_NAME=sales.us.example.com))
        (SECURITY=
          (SSL_SERVER_CERT_DN="cn=sales,cn=OracleContext,dc=us,dc=acme,dc=com")))

**Parent topic:** Security Section

#### 6.10.10 SSL_DISABLE_WEAK_EC_CURVES

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

**Parent topic:** Security Section

#### 6.10.11 SSL_SERVER_CERT_DN

Use the `SSL_SERVER_CERT_DN` parameter to specify the distinguished name (DN) of the database server.

##### Purpose

To specify the [distinguished name (DN)](glossary.md) of the database server.

##### Usage Notes

The server DN must be known by the client ahead of time. Otherwise, the client cannot specify the server's DN in` SSL_SERVER_CERT_DN`. The client uses this information to obtain the list of DNs it expects for each of the servers, enforcing the database server DN to match its service name. This parameter must be set to the server DN (for example, `SSL_SERVER_CERT_DN="finance, cn=OracleContext,c=us,o=example"`) to use full DN matching. For partial DN matching, do not include this parameter.

Use this parameter with the `sqlnet.ora` parameter SSL_SERVER_DN_MATCH to enable full DN matching.

##### Example

    finance=
     (DESCRIPTION=
       (ADDRESS_LIST=
         (ADDRESS=(PROTOCOL = tcps) (HOST = finance)
         (PORT = 1575)))
       (CONNECT_DATA=
         (SERVICE_NAME=finance.us.example.com))
       (SECURITY=
         (SSL_SERVER_CERT_DN="cn=finance,cn=OracleContext,c=us,o=example")))

**See Also:**

[Oracle Database Security Guide](../dbseg/configuring-secure-sockets-layer-authentication.md)

**Parent topic:** Security Section

#### 6.10.12 SSL_SERVER_DN_MATCH

Use the `SSL_SERVER_DN_MATCH` parameter to enforce server-side certificate validation through distinguished name (DN) matching.

##### Purpose

To enforce server-side certification validation through [distinguished name (DN)](glossary.md) matching.

##### Usage Notes

If you enforce the DN matching, in addition to verifying the server's certificate chain, the client performs another check through DN matching.

You can configure either partial DN matching or full DN matching. Partial DN matching occurs if the server's CN contains its host name. Full DN matching occurs against the server's complete DN. Not enforcing the match allows the server to potentially fake its identity.

In addition to the `sqlnet.ora` file, configure the `tnsnames.ora` parameter SSL_SERVER_CERT_DN to enable full DN matching.

##### Default

`NO`

##### Values

- `YES` \| `ON` \| `TRUE` \| `1`:

  To enforce partial or full DN matching. If the DN matches the service name, then the connection succeeds. If the DN does not match the service name, then the connection fails.

- `NO` \| `OFF` \| `FALSE` \| `0`:

  To not enforce DN matching. If the DN does not match the service name, then the connection is successful, but an error is logged to the `sqlnet.log` file.

##### Example

    SSL_SERVER_DN_MATCH=YES

**Related Topics**

- [Oracle Database Security Guide](../dbseg/kerberos-ssl-and-radius-authentication-parameters.md)

**Parent topic:** Security Section

#### 6.10.13 SSL_VERSION

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

**Parent topic:** Security Section

#### 6.10.14 TOKEN_AUTH

Use the `TOKEN_AUTH` parameter to configure token-based authentication for Oracle Cloud Infrastructure (OCI) Identity and Access Management (IAM) or Microsoft Azure users of Microsoft Entra ID (previously called Microsoft Azure Active Directory).

##### Purpose

Token-based access enforces strong authentication, which enables a more secure access to the database. IAM users can connect to OCI Database as a Service (DBaaS) databases, and Azure users can connect to Oracle Databases (cloud or on-premises).

With this setting, the database client looks for a token file when a `/` (slash) login is used.

Use this parameter under the `SECURITY` section of the `tnsnames.ora` file, `sqlnet.ora` file, or directly as part of the command-line connect string. The parameter value specified in the connect string takes precedence over the other specified values.

##### Usage Notes for IAM

- OCI IAM token:

  An OCI IAM token (`db-token`), which is obtained from IAM using Oracle Cloud Infrastructure (OCI) Command Line Interface (CLI) or programmatically from the OCI Software Development Kit (SDK), is a proof-of-possession (PoP) token with an expiration time and scope.

  You can use one of the IAM user credentials, such as API-key, security token, resource principal, instance principal, or delegation token to retrieve the `db-token` and private key from IAM.

  These tokens are transmitted over secure channels. You must use only the TCP/IP with Transport Layer Security (TLS) protocol, otherwise an error message appears indicating that non-TLS connections are disallowed.

- Required setting for token-based authentication:

  You must configure the TCPS protocol (`PROTOCOL=tcps`) and set the `SSL_SERVER_DN_MATCH` parameter to `TRUE` for token-based authentication.

- Use a file location to send the token to Oracle Database:

  When an IAM user logs in using `/@``connect_identifier` (and `TOKEN_AUTH` is set to `OCI_TOKEN`), the `TOKEN_AUTH=OCI_TOKEN` setting along with `/@``connect_identifier` instructs the database client to get the `db-token` and private key from either the default directory or the location specified by `TOKEN_LOCATION` (using IAM token-based authentication).

- Use the client API to send the token to Oracle Database:

  If your client application is updated to retrieve tokens from IAM, then you can override the `TOKEN_AUTH=OCI_TOKEN` setting. The client application gets the `db-token` and private key from IAM and sends as attributes to the database client using the client API. In this case, you do not need to specify the `TOKEN_AUTH` and `TOKEN_LOCATION` parameters.

- General IAM token-based authentication process:

  1.  An IAM user or application in OCI first requests the `db-token` from IAM by using API-key, security token, resource principal, service principal, instance principal, or delegation token (delegation token is available only in the Cloud Shell).

      To use a security token, you need to generate it by completing the browser authentication process and then request the `db-token` using that security token. If the IAM policy that authorizes you to be issued the `db-token` exists, then the `db-token` is returned.

      You request the `db-token` using OCI CLI (or OCI SDK for applications). For example, run the following OCI CLI command to request the `db-token` by using an API-key (`apikey`):

          $ oci iam db-token get --profile scott

      The `profile` option specifies the profile for which you want to access the IAM user credentials and retrieve the `db-token`.

      For more information on using OCI CLI, see the `get` command details in [Oracle Cloud Infrastructure CLI Command Reference](https://docs.oracle.com/en-us/iaas/tools/oci-cli/latest/oci_cli_docs/cmdref/iam/db-token/get.html).

  2.  OCI CLI references the `config` file (that stores your IAM user credentials as part of the profile) and makes a call to IAM to get the `db-token`. The `db-token` and private key files are written at the default or specified token location.

  3.  You can specify the `TOKEN_LOCATION` parameter to override the default directory where the `db-token` and private key files are stored.

      The database client gets the `db-token` and private key from the default token location or the location specified by `TOKEN_LOCATION`, signs the `db-token` with the private key and sends it to the database server. The database server verifies the `db-token` and gets the group membership information for the user. If the IAM user is mapped to a database schema (exclusively or shared), then the login is completed.

**Note:**

You can also use another IAM credential, IAM database password, to request the `db-token` from IAM. This `db-token` is a bearer token and does not come with a private key. You can configure the database client to request this token using your IAM user name and IAM database password. An application cannot pass this type of `db-token` to the client. In this case, you use a different parameter setting (`PASSWORD_AUTH=OCI_TOKEN`).

Unlike the API-key, security token, resource principal, service principal, instance principal, and delegation token that require an application or tool to get a token, the IAM database password can only be used by the database client to retrieve the token. See PASSWORD_AUTH.

Table 6-1 Values and Examples for IAM

| Default | Value                  | Example                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|:--------|:-----------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| None    | `TOKEN_AUTH=OCI_TOKEN` | In the `tnsnames.ora` file:<br>`net_service_name=`<br>`    (DESCRIPTION =`<br>`       (ADDRESS=(PROTOCOL=tcps)(HOST=sales-svr)(PORT=1521))`<br>`       (SECURITY=`<br>`          (SSL_SERVER_DN_MATCH=TRUE)`<br>`          (SSL_SERVER_CERT_DN="C=US,O=example,CN=OracleContext")`<br>`          (TOKEN_AUTH=OCI_TOKEN))`<br>`       (CONNECT_DATA=(SERVICE_NAME=sales.us.example.com))`<br>`     ) `<br>In the `sqlnet.ora` file:<br>`SSL_SERVER_DN_MATCH=TRUE`<br>`TOKEN_AUTH=OCI_TOKEN`<br>In these examples, the optional `TOKEN_LOCATION` parameter is not specified. Thus, the client automatically gets the `db-token` and private key from the default token location. |

##### Usage Notes for Entra ID

- Entra ID access token:

  An Entra ID OAuth2 access token is a bearer token with an expiration time and scope. This token follows the OAuth2.0 standard with Entra ID extensions. You can request these tokens from tools and scripts run on Linux, Microsoft PowerShell, or other environments. You can also request these tokens programmatically using the Microsoft SDKs.

  These tokens are transmitted over secure channels. You must use only the TCP/IP with Transport Layer Security (TLS) protocol, otherwise an error message appears indicating that non-TLS connections are disallowed.

- Required setting for token-based authentication:

  You must configure the TCPS protocol (`PROTOCOL=tcps`) and set the `SSL_SERVER_DN_MATCH` parameter to `TRUE` for token-based authentication.

- Use a file location to send the token to Oracle Database:

  When an Azure user logs in using `/@``connect_identifier`, then the `TOKEN_AUTH=OAUTH` setting instructs the database client to get the access token from the directory location specified by `TOKEN_LOCATION` if the token file is named `token`. If the token file name is different from `token`, then you must use the file name along with the directory location while specifying the `TOKEN_LOCATION` parameter.

  The `TOKEN_LOCATION` parameter is mandatory for Azure token-based authentication. The database client gets the token from this location and sends it to the database server.

- Use the client API to send the token to Oracle Database:

  If your client application is updated to retrieve tokens from Entra ID, then you can override the `TOKEN_AUTH=OAUTH` setting. Entra ID directly passes the `db-token` as an attribute to the database client using the client API. When the client receives this request, the client sends it to the database server.

  In this case, you do no need to specify the `TOKEN_AUTH` and `TOKEN_LOCATION` parameters.

- General Azure token-based authentication process:

  1.  An Azure user or application first requests the access token from Entra ID using one of the supported authentication flows (resource owner password credentials, authorization code, on-behalf-of (OBO) flow, or client credentials).

      An Azure user can connect using any supported utility to retrieve the token and store it in a local file directory.

      You can request the token from tools and scripts run on Linux, Microsoft PowerShell, or other environments. You can also request programmatically using the Microsoft SDKs.

      For detailed examples on how to retrieve an Entra ID OAuth2 access token, see [Oracle Database Security Guide](../dbseg/authenticating-and-authorizing-microsoft-entra-id-ms-ei-users-oracle-databases-oracle-exadata.md).

  2.  The database client then sends the token to the database server. The database server verifies the token (using the Entra ID public key) and extracts various claims from the token, including user name, app roles, and audience. If the Entra ID principal is mapped to a database schema (exclusively or shared), then the login is completed.

Table 6-2 Values and Examples for Entra ID

| Default                                                                                                                                | Value                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | Example                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:---------------------------------------------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| None                                                                                                                                   | If the token file is named `token`:<br>`TOKEN_AUTH=OAUTH` `TOKEN_LOCATION="``token_file_directory``"`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | In the `tnsnames.ora` file:<br>`net_service_name=`<br>`    (DESCRIPTION=`<br>`      (ADDRESS=(PROTOCOL=tcps)(HOST=salesserver1)(PORT=1522))`<br>`      (SECURITY=`<br>`          (SSL_SERVER_DN_MATCH=TRUE)`<br>`          (SSL_SERVER_CERT_DN="C=US,O=example,CN=OracleContext")`<br>`          (TOKEN_AUTH=OAUTH)`<br>`          (TOKEN_LOCATION="/home/dbuser1/access-token"))`<br>`      (CONNECT_DATA=(SERVICE_NAME=sales.us.example.com))`<br>`    )`<br>In the `sqlnet.ora` file:<br>`SSL_SERVER_DN_MATCH=TRUE`<br>`TOKEN_AUTH=OAUTH `<br>`TOKEN_LOCATION="/home/dbuser1/access-token"`<br>In these examples, the token file name is `token`. Thus, only the directory path (`/home/dbuser1/access-token`) is specified. The client automatically looks for the `token` file in the specified path and gets the access token. |
| If the token file name is different from `token`:<br>`TOKEN_AUTH=OAUTH` `TOKEN_LOCATION="``token_file_directory``/``token_filename``"` | In the `tnsnames.ora` file:<br>`net_service_name=`<br>`    (DESCRIPTION=`<br>`      (ADDRESS=(PROTOCOL=tcps)(HOST=salesserver1)(PORT=1522))`<br>`      (SECURITY=`<br>`          (SSL_SERVER_DN_MATCH=TRUE)`<br>`          (SSL_SERVER_CERT_DN="C=US,O=example,CN=OracleContext")`<br>`          (TOKEN_AUTH=OAUTH)`<br>`          (TOKEN_LOCATION="/home/dbuser1/access-token/mytoken"))`<br>`      (CONNECT_DATA=(SERVICE_NAME=sales.us.example.com))`<br>`    )`<br>In the `sqlnet.ora` file:<br>`SSL_SERVER_DN_MATCH=TRUE`<br>`TOKEN_AUTH=OAUTH `<br>`TOKEN_LOCATION="/home/dbuser1/access-token/mytoken"`<br>In these examples, the token file name is `mytoken`. Thus, both the file name and directory path (`/home/dbuser1/access-token`) are specified. The client gets the access token from the `mytoken` file in the specified path. |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |

**Related Topics**

- [Authenticating and Authorizing IAM Users for Oracle DBaaS Databases](../dbseg/authenticating-and-authorizing-iam-users-oracle-dbaas-databases.md)
- [Authenticating and Authorizing Microsoft Azure Users for Oracle Databases](../dbseg/authenticating-and-authorizing-microsoft-entra-id-ms-ei-users-oracle-databases-oracle-exadata.md)
- TOKEN_LOCATION

**Parent topic:** Security Section

#### 6.10.15 TOKEN_LOCATION

Use the `TOKEN_LOCATION` parameter to specify the directory location where token file is stored for token-based authentication.

##### Purpose

To specify the token file directory location. You use this parameter while configuring token-based authentication for Oracle Cloud Infrastructure (OCI) Identity and Access Management (IAM) or Microsoft Azure users of Microsoft Entra ID. The database client gets the token from this location and sends it to the database server. For Entra ID, you can also specify the token file name along with the directory location.

Use this parameter along with the `TOKEN_AUTH` parameter in the `tnsnames.ora` file, `sqlnet.ora` file, or directly as part of the command-line connect string. The parameter values specified in the connect string take precedence over the other specified values.

##### Usage Notes for IAM

The `TOKEN_LOCATION` parameter is optional for IAM token-based authentication. You can use this parameter along with the `TOKEN_AUTH` parameter to override the default directory where the `db-token` and private key are stored. This location is used by the database client to retrieve the `db-token` and private key.

When an IAM user initiates a connection using `/@``connect_identifier` (and `TOKEN_AUTH` is set to `OCI_TOKEN`), the database client retrieves the `db-token` and private key from either the default directory or the location specified by `TOKEN_LOCATION`. The client then signs the `db-token` using the private key and sends the `db-token` to the database server.

##### Default Setting for IAM

- On Linux:

  `/home/``username``/.oci/db-token`

- On Windows:

  The database client searches for the default directory in this order:

  If the `USERPROFILE` environment variable is set, then the client searches in the `USERPROFILE` directory (for example, `C:\Users\``username`).

  If `USERPROFILE` is not set, then the client searches in `HOMEDRIVE` directory (for example, `C:`) with `HOMEPATH` (for example, `\Users\``username`).

  For example, the default token location directory on Windows is:

  `C:\Users\``username``\.oci\db-token`

##### Values and Examples for IAM

| Value                                       | Example                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|:--------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `TOKEN_LOCATION="``token_file_directory``"` | In the `tnsnames.ora` file:<br>`net_service_name=`<br>`    (DESCRIPTION =`<br>`       (ADDRESS=(PROTOCOL=tcps)(HOST=sales-svr)(PORT=1521))`<br>`       (SECURITY=`<br>`          (SSL_SERVER_DN_MATCH=TRUE)`<br>`          (SSL_SERVER_CERT_DN="C=US,O=example,CN=OracleContext")`<br>`          (TOKEN_AUTH=OCI_TOKEN)`<br>`          (TOKEN_LOCATION="/home/oracle/.oci/db-token"))`<br>`       (CONNECT_DATA=(SERVICE_NAME=sales.us.example.com))`<br>`     ) `<br>In the `sqlnet.ora` file:<br>`SSL_SERVER_DN_MATCH=TRUE`<br>`TOKEN_AUTH=OCI_TOKEN`<br>`TOKEN_LOCATION="/home/oracle/.oci/db-token"` |

##### Usage Notes for Entra ID

The `TOKEN_LOCATION` parameter is mandatory for Azure token-based authentication. You must use this parameter along with the `TOKEN_AUTH` parameter to specify the directory location where the Entra ID OAuth2 access token is stored. This location is used by the database client to get the access token.

If your token file is named `token`, then specify only the directory path. If the token file name is different from `token`, then you must use the file name along with the directory path.

When an Azure user initiates a connection using `/@``connect_identifier`, the database client retrieves the access token from the location specified by `TOKEN_LOCATION` and sends the token to the database server.

##### Default Setting for Entra ID

None

##### Values and Examples for Entra ID

| Value                                                                                                               | Example                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|:--------------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| If the token file is named `token`:<br>`TOKEN_LOCATION="``token_file_directory``"`                                  | In the `tnsnames.ora` file:<br>`net_service_name=`<br>`    (DESCRIPTION=`<br>`      (ADDRESS=(PROTOCOL=tcps)(HOST=salesserver1)(PORT=1522))`<br>`      (SECURITY=`<br>`          (SSL_SERVER_DN_MATCH=TRUE)`<br>`          (SSL_SERVER_CERT_DN="C=US,O=example,CN=OracleContext")`<br>`          (TOKEN_AUTH=OAUTH)(TOKEN_LOCATION="/home/dbuser1/access-token"))`<br>`      (CONNECT_DATA=(SERVICE_NAME=sales.us.example.com))`<br>`    )`<br>In the `sqlnet.ora` file:<br>`SSL_SERVER_DN_MATCH=TRUE`<br>`TOKEN_AUTH=OAUTH `<br>`TOKEN_LOCATION="/home/dbuser1/access-token"`<br>In these examples, the token file name is `token`. Thus, only the directory path (`/home/dbuser1/access-token`) is specified. The client automatically looks for the `token` file in the specified path and gets the access token.                           |
| If the token file name is different from `token`:<br>`TOKEN_LOCATION="``token_file_directory``/``token_filename``"` | In the `tnsnames.ora` file:<br>`net_service_name=`<br>`    (DESCRIPTION=`<br>`      (ADDRESS=(PROTOCOL=tcps)(HOST=salesserver1)(PORT=1522))`<br>`      (SECURITY=`<br>`          (SSL_SERVER_DN_MATCH=ON)`<br>`          (SSL_SERVER_CERT_DN="C=US,O=example,CN=OracleContext")`<br>`          (TOKEN_AUTH=OAUTH)`<br>`          (TOKEN_LOCATION="/home/dbuser1/access-token/mytoken"))`<br>`      (CONNECT_DATA=(SERVICE_NAME=sales.us.example.com))`<br>`    )`<br>In the `sqlnet.ora` file:<br>`SSL_SERVER_DN_MATCH=TRUE`<br>`TOKEN_AUTH=OAUTH `<br>`TOKEN_LOCATION="/home/dbuser1/access-token/mytoken"`<br>In these examples, the token file name is `mytoken`. Thus, both the file name and directory path (`/home/dbuser1/access-token`) are specified. The client gets the access token from the `mytoken` file in the specified path. |

**Related Topics**

- [Authenticating and Authorizing IAM Users for Oracle DBaaS Databases](../dbseg/authenticating-and-authorizing-iam-users-oracle-dbaas-databases.md)
- [Authenticating and Authorizing Microsoft Azure Users for Oracle Databases](../dbseg/authenticating-and-authorizing-microsoft-entra-id-ms-ei-users-oracle-databases-oracle-exadata.md)
- TOKEN_AUTH

**Parent topic:** Security Section

#### 6.10.16 WALLET_LOCATION

Use the `WALLET_LOCATION` parameter in the `tnsnames.ora` file to specify different locations where Oracle wallets are stored.

##### Purpose

This parameter denotes a connection specific wallet. You can use this parameter when different connections need to use different wallets on the client side.

##### Usage Notes

You can use `WALLET_LOCATION` in both the `sqlnet.ora` file and `tnsnames.ora` file. Use of `WALLET_LOCATION` in `tnsnames.ora` overrides the `WALLET_LOCATION` in `sqlnet.ora` for the specific `tnsnames.ora` service.

`WALLET_LOCATION` enables a client connection to have distinct TLS connections that use certificates. This means that the clients will initiate multiple TLS connections using different TLS certificates, in the same client process.

Use this parameter if you have a single client that must rely on more than one TLS session. An example would be for a client that requires access to multiple pluggable databases (PDBs), each with its own identity (certificate). This feature enables you to configure the client to connect to the correct identity for each PDB. After the configuration is complete, multi-threaded clients are able to access more than one wallet with different certificates in simultaneous TLS sessions.

##### Examples

    net_service_name=
     (DESCRIPTION=
       (ADDRESS_LIST=
         (ADDRESS=(PROTOCOL=tcp)(HOST=sales1-svr)(PORT=1521))
         (ADDRESS=(PROTOCOL=tcp)(HOST=sales2-svr)(PORT=1521)))
       (CONNECT_DATA=
         (SERVICE_NAME=sales.us.example.com))
          (SECURITY=(wallet_location=/home/oracle/wallets/databases)))

    ssl_certs1 =
        (DESCRIPTION =
           (ADDRESS=(PROTOCOL=tcps)(HOST=shobeen.us.example.com) (PORT=1750))
           (CONNECT_DATA=(SID=sales_pdb))
           (SECURITY=(WALLET_LOCATION=/oracle/wallets/certificates/sales_cert))
         )
    ssl_certs2 =
        (DESCRIPTION =
           (ADDRESS=(PROTOCOL=tcps)(HOST=shobeen.us.example.com) (PORT=1750))
           (CONNECT_DATA=(SID=marketing_pdb))
           (SECURITY=(WALLET_LOCATION=/oracle/wallets/certificates/marketing_cert))
         )

**Related Topics**

- [Oracle Database Security Guide](../dbseg/index.md)
- [Oracle Database Net Services Reference](parameters-for-the-sqlnet.ora.md)

**Parent topic:** Security Section

### 6.11 Timeout Parameters

The timeout section of the `tnsnames.or`a file provides the ability to specify timeout and retry configuration through the TNS connect string.

The following parameters can be set at the `DESCRIPTION` level of a connect string:

- CONNECT_TIMEOUT
  Use the `tnsnames.ora` parameter `CONNECT_TIMEOUT` to specify the amount of time, in milliseconds, seconds, or minutes, in which clients must establish Oracle Net connections to database instances.
- RETRY_COUNT
  Use the `tnsnames.ora` parameter `RETRY_COUNT` to specify the number of times an `ADDRESS` list is traversed before terminating the connection attempt.
- RETRY_DELAY
  Use the `tnsnames.ora` parameter `RETRY_DELAY` to specify the delay in seconds between connection retries.
- TRANSPORT_CONNECT_TIMEOUT
  Use the `tnsnames.ora` parameter `TRANSPORT_CONNECT_TIMEOUT` to specify the transport connect timeout duration, in milliseconds, seconds, or minutes.
- RECV_TIMEOUT
  Use the `tnsnames.ora` parameter `RECV_TIMEOUT` to specify the duration of time that a database client or server should wait for data from a peer after establishing a connection.

**Parent topic:** Local Naming Parameters in the tnsnames.ora File

#### 6.11.1 CONNECT_TIMEOUT

Use the `tnsnames.ora` parameter `CONNECT_TIMEOUT` to specify the amount of time, in milliseconds, seconds, or minutes, in which clients must establish Oracle Net connections to database instances.

##### Purpose

To specify the timeout duration in `ms` or `msec` (milliseconds), `sec` (seconds), or `min` (minutes) for a client to establish an Oracle Net connection to Oracle Database.

##### Usage Notes

- Put this parameter under the `DESCRIPTION` parameter.

- In case, no unit is mentioned, the default unit is `sec`.

  It accepts different timeouts with or without space between the value and the unit. For example:

      CONNECT_TIMEOUT=10 ms

  or

      CONNECT_TIMEOUT=10ms

- The timeout interval specified by `CONNECT_TIMEOUT` is a superset of the TCP connect timeout interval. It includes the time to be connected to the database instance providing the requested service, not just the duration of the TCP connection.

  The timeout interval is applicable to each `ADDRESS` in an `ADDRESS_LIST`, and each IP address to which a host name is mapped.

- The `CONNECT_TIMEOUT` parameter is equivalent to the `sqlnet.ora` parameter `SQLNET.OUTBOUND_CONNECT_TIMEOUT`, and overrides it.

##### Examples

    net_service_name=
     (DESCRIPTION=
      (CONNECT_TIMEOUT=10 ms)(RETRY_COUNT=3)
      (ADDRESS_LIST=
       (ADDRESS=(PROTOCOL=tcp)(HOST=sales1-svr)(PORT=1521))
       (ADDRESS=(PROTOCOL=tcp)(HOST=sales2-svr)(PORT=1521)))
      (CONNECT_DATA=
       (SERVICE_NAME=sales.us.example.com)))

**Related Topics**

- [SQLNET.OUTBOUND_CONNECT_TIMEOUT](parameters-for-the-sqlnet.ora.md)

**Parent topic:** Timeout Parameters

#### 6.11.2 RETRY_COUNT

Use the `tnsnames.ora` parameter `RETRY_COUNT` to specify the number of times an `ADDRESS` list is traversed before terminating the connection attempt.

##### Purpose

To specify the number of times an `ADDRESS` list is traversed before the connection attempt is terminated.

##### Usage Notes

Put this parameter under the `DESCRIPTION` parameter.

When a `DESCRIPTION_LIST` is specified, each `DESCRIPTION` is traversed multiple times based on the specified number of retries.

##### Example

    net_service_name=
    (DESCRIPTION_LIST=
     (DESCRIPTION=
      (CONNECT_TIMEOUT=10)(RETRY_COUNT=3)
      (ADDRESS_LIST=
       (ADDRESS=(PROTOCOL=tcp)(HOST=sales1a-svr)(PORT=1521))
       (ADDRESS=(PROTOCOL=tcp)(HOST=sales1b-svr)(PORT=1521)))
      (CONNECT_DATA=(SERVICE_NAME=sales1.example.com)))
     (DESCRIPTION=
      (CONNECT_TIMEOUT=60)(RETRY_COUNT=1)
      (ADDRESS_LIST=
       (ADDRESS=(PROTOCOL=tcp)(HOST=sales2a-svr)(PORT=1521))
       (ADDRESS=(PROTOCOL=tcp)(HOST=sales2b-svr)(PORT=1521)))
      (CONNECT_DATA=(SERVICE_NAME=sales2.us.example.com))))

**Parent topic:** Timeout Parameters

#### 6.11.3 RETRY_DELAY

Use the `tnsnames.ora` parameter `RETRY_DELAY` to specify the delay in seconds between connection retries.

##### Purpose

To specify the delay in seconds between subsequent retries for a connection. This parameter works in conjunction with `RETRY_COUNT` parameter.

##### Usage Notes

Put this parameter under the `DESCRIPTION` parameter.

When a `DESCRIPTION_LIST` is specified, each `DESCRIPTION` is traversed multiple times based on the specified number of retries, and the specific delay for the description.

##### Example

    net_service_name=
    (DESCRIPTION_LIST=
     (DESCRIPTION=
      (CONNECT_TIMEOUT=10)(RETRY_COUNT=3)(RETRY_DELAY=2)
      (ADDRESS_LIST=
       (ADDRESS=(PROTOCOL=tcp)(HOST=sales1a-svr)(PORT=1521))
       (ADDRESS=(PROTOCOL=tcp)(HOST=sales1b-svr)(PORT=1521)))
      (CONNECT_DATA=(SERVICE_NAME=sales1.example.com)))
     (DESCRIPTION=
      (CONNECT_TIMEOUT=60)(RETRY_COUNT=2)(RETRY_DELAY=1)
      (ADDRESS_LIST=
       (ADDRESS=(PROTOCOL=tcp)(HOST=sales2a-svr)(PORT=1521))
       (ADDRESS=(PROTOCOL=tcp)(HOST=sales2b-svr)(PORT=1521)))
      (CONNECT_DATA=(SERVICE_NAME=sales2.us.example.com))))

**Parent topic:** Timeout Parameters

#### 6.11.4 TRANSPORT_CONNECT_TIMEOUT

Use the `tnsnames.ora` parameter `TRANSPORT_CONNECT_TIMEOUT` to specify the transport connect timeout duration, in milliseconds, seconds, or minutes.

##### Purpose

To specify the transport connect timeout duration in `ms` or `msec` (milliseconds), `sec` (seconds), or `min` (minutes) for a client to establish an Oracle Net connection to Oracle Database.

##### Usage Notes

- This parameter is put under the `DESCRIPTION` parameter.

- The default value is 60 `sec`. In case, no unit is mentioned, the default unit is `sec`.

  It accepts different timeouts with or without space between the value and the unit.

      TRANSPORT_CONNECT_TIMEOUT=10 ms

  or

      TRANSPORT_CONNECT_TIMEOUT=10ms

- The timeout interval is applicable for each `ADDRESS` in an `ADDRESS_LIST` description, and each IP address that a host name is mapped. The `TRANSPORT_CONNECT_TIMEOUT` parameter is equivalent to the `sqlnet.ora` parameter `TCP.CONNECT_TIMEOUT`, and overrides it.

##### Example

    net_service_name =
      (DESCRIPTION=
        (TRANSPORT_CONNECT_TIMEOUT=10 ms)
        (ADDRESS_LIST=
          (ADDRESS=(PROTOCOL=tcp)(HOST=sales1-svr)(PORT=1521))
          (ADDRESS=(PROTOCOL=tcp)(HOST=sales2-svr)(PORT=1521)))
        (CONNECT_DATA=
          (SERVICE_NAME=sales.us.example.com)))

**Related Topics**

- [TCP.CONNECT_TIMEOUT](parameters-for-the-sqlnet.ora.md)

**Parent topic:** Timeout Parameters

#### 6.11.5 RECV_TIMEOUT

Use the `tnsnames.ora` parameter `RECV_TIMEOUT` to specify the duration of time that a database client or server should wait for data from a peer after establishing a connection.

##### Purpose

To specify the time duration in `ms` or `msec` (milliseconds), `sec` (seconds), `min` (minutes), or `hr` (hours) for a database client or server to wait for data from the peer after establishing a connection. The peer must send data within the time interval that you specify.

##### Usage Notes

- This parameter is put under the `DESCRIPTION` parameter.

- If you do not specify a unit of measurement, then the default unit is `sec`.

  It accepts time duration with or without space between the value and the unit. For example:

      RECV_TIMEOUT=10 ms

  or

      RECV_TIMEOUT=10ms

- Setting this parameter for clients ensures that receive operations are not left in a wait state indefinitely or for a long period due to server host being down, server busy state, or network connectivity issues.

  If a client does not receive response data in the time specified, then the client logs `ORA-12535: TNS:operation timed out` and `ORA-12609: TNS: Receive timeout occurred` messages to the `sqlnet.log` file.

##### Default Value

None

##### Minimum Value

`1 ms`

##### Allowed Range

Any number greater than the minimum value of `1 ms` up to `4294967295 ms`.

##### Examples

    net_service_name=
     (DESCRIPTION=
      (CONNECT_TIMEOUT=10ms)(RETRY_COUNT=3)(RECV_TIMEOUT=10ms)
      (ADDRESS_LIST=
       (ADDRESS=(PROTOCOL=tcp)(HOST=sales1-svr)(PORT=1521))
       (ADDRESS=(PROTOCOL=tcp)(HOST=sales2-svr)(PORT=1521)))
      (CONNECT_DATA=
       (SERVICE_NAME=sales.us.example.com)))

**Related Topics**

- [Oracle Database Net Services Administrator's Guide](../netag/index.md)

**Parent topic:** Timeout Parameters

### 6.12 Compression Parameters

The compression section of the `tnsnames.ora` file provides the ability to enable compression and specify compression levels. These parameters can be set at the `DESCRIPTION` level of a connect string.

- COMPRESSION
  The `tnsnames.ora` file’s compression parameter enables or disables the data compression.
- COMPRESSION_LEVELS
  The `COMPRESSION_LEVELS` parameter of the `tnsnames.ora` file specifies the compression level.

**Parent topic:** Local Naming Parameters in the tnsnames.ora File

#### 6.12.1 COMPRESSION

The `tnsnames.ora` file’s compression parameter enables or disables the data compression.

##### Purpose

To enable or disable data compression.

##### Usage Notes

Put this parameter under the `DESCRIPTION` parameter.

Setting this parameter in the connect descriptor for a client overrides the `SQLNET.COMPRESSION` parameter in the client-side `sqlnet.ora` file.

##### Default

`off`

##### Values

- `on` to enable data compression.

- `off` to disable data compression.

##### Example

    net_service_name=
     (DESCRIPTION=
       (COMPRESSION=on)
          (ADDRESS_LIST=
             (ADDRESS= (PROTOCOL=tcp) (HOST=sales1-server) (PORT=1521))
             (ADDRESS= (PROTOCOL=tcp) (HOST=sales2-server) (PORT=1521)))
       (CONNECT_DATA=
           (SERVICE_NAME=sales.us.example.com)))

**Related Topics**

- [SQLNET.COMPRESSION](parameters-for-the-sqlnet.ora.md)

**Parent topic:** Compression Parameters

#### 6.12.2 COMPRESSION_LEVELS

The `COMPRESSION_LEVELS` parameter of the `tnsnames.ora` file specifies the compression level.

##### Purpose

To specify the compression level.

##### Usage Notes

The compression levels are used at the time of negotiation to verify which levels are used at both ends, and select one level. Put this parameter under the `DESCRIPTION` parameter.

This parameter is used with the `COMPRESSION` parameter. Setting this parameter in the connect descriptor for a client overrides the `SQLNET.COMPRESSION_LEVELS` parameter in the client-side `sqlnet.ora` file.

##### Default

`low`

##### Values

- `low` for low CPU usage and a low compression ratio.

- `high` for high CPU usage and a high compression ratio.

##### Example

    net_service_name=
     (DESCRIPTION=
      (COMPRESSION=on)
      (COMPRESSION_LEVELS=(LEVEL=low)(LEVEL=high))
       (ADDRESS_LIST=
         (ADDRESS=(PROTOCOL=tcp)(HOST=sales1-server)(PORT=1521))
         (ADDRESS=(PROTOCOL=tcp)(HOST=sales2-server)(PORT=1521)))
      (CONNECT_DATA=
        (SERVICE_NAME=sales.us.example.com)))

**Related Topics**

- [SQLNET.COMPRESSION_LEVELS](parameters-for-the-sqlnet.ora.md)

**Parent topic:** Compression Parameters
