## 14 Optimizing Performance

Learn how to optimize connection performance.

- Understanding the Benefits of Network Data Compression
- Configuring Session Data Unit
  Under typical database configuration, Oracle Net encapsulates data into buffers the size of the Session Data Unit (SDU) before sending the data across the network.
- Determining the Bandwidth-Delay Product
- Configuring I/O Buffer Space
  Reliable network protocols, such as TCP/IP, buffer data into send and receive buffers while sending and receiving to or from lower and upper layer protocols. The sizes of these buffers affect network performance by influencing flow control decisions.
- Configuring SDP Support for InfiniBand Connections
- Configuring Exadirect Support for InfiniBand Connections
  Oracle Net Services provides support for the Exadirect for InfiniBand high-speed networks.. Use the new transport to improve latency and throughput by leveraging Remote Direct Memory Access (RDMA) in an InfiniBand environment
- Limiting Resource Consumption by Unauthorized Users
- Configuring Key-Based Routing for Client-Server Connections
  Learn how to establish client-server connections in a sharded database by using key-based (or direct) routing. In key-based routing to a shard, a connection is established to a single, relevant shard that contains the data pertinent to the required transaction using a sharding key.

**Parent topic:** [Configuration and Administration of Oracle Net Services](part-II-config-and-admin-of-oracle-net-services.md)

### 14.1 Understanding the Benefits of Network Data Compression

Network data compression reduces the size of the [session data unit (SDU)](glossary.md) transmitted over a data connection. Reducing the size of data reduces the time required to transmit a SQL query and result across the network. In addition, compressed data uses less bandwidth which allows transmission of larger data in less time. The data compression process is transparent to the application layer.

The following are some of the benefits of using data compression:

- Increased network throughput means constrained bandwidth environments can utilize compression to reduce query response time.

- Reduced bandwidth utilization allows other applications to use the bandwidth.

- Reduction in the amount of data transferred between sites.

**Parent topic:** Optimizing Performance

### 14.2 Configuring Session Data Unit

Under typical database configuration, Oracle Net encapsulates data into buffers the size of the Session Data Unit (SDU) before sending the data across the network.

Oracle Net sends each buffer when it is filled, flushed, or when an application tries to read data. Adjusting the size of the SDU buffers relative to the amount of data provided to Oracle Net to send at any one time can improve performance, network utilization, and memory consumption. When large amounts of data are being transmitted, increasing the SDU size can improve performance and network throughput. SDU size can be adjusted lower or higher to achieve higher throughput for a specific deployment.

The amount of data provided to Oracle Net to send at any one time is referred to as the message size.

The SDU size can range from `512` bytes to `2` MB. The wide range of sizes allows the network administrator to tune the SDU size for optimal network performance for a given deployment. A high SDU size value requires more memory. The default SDU size for the client and a dedicated server is `8192` bytes. The default SDU size for a shared server is `65535` bytes.

The actual SDU size used is negotiated between the client and the server at connect time and is the smaller of the client and server values. Configuring an SDU size different from the default requires configuring the SDU on both the client and server computers, unless you are using shared servers.

You should consider changing the SDU size when the predominant message size is smaller or larger than `8192`. The SDU size should be `70` bytes more than the predominant message size. If the predominant message size plus `70` bytes exceeds the maximum SDU, then the SDU should be set such that the message size is divided into the smallest number of equal parts where each part is `70` bytes less than the SDU size. To change the default, change the `DEFAULT_SDU_SIZE` parameter in the `sqlnet.ora` file.

For example, if the majority of the messages sent and received by the application are smaller than `8` KB, taking into account the `70` bytes for overhead, then setting the SDU to `8` KB will likely produce good results. If sufficient memory is available, then using the maximum value for the SDU minimizes the number of system calls and overhead for Oracle Net Services.

- Setting the SDU Size for the Database
- Setting the SDU Size for the Client

**Related Topics**

- [Session Data Unit Size for Data Transfer Optimization](introducing-oracle-net-services.md)
- [Statistics Example](troubleshooting-oracle-net-services.md)

**Parent topic:** Optimizing Performance

#### 14.2.1 Setting the SDU Size for the Database

To set the SDU size for the database server, configure the following files:

- `sqlnet.ora`

  Configure the DEFAULT_SDU_SIZE parameter in the `sqlnet.ora` file, such as the following:

      DEFAULT_SDU_SIZE=32767

- Initialization parameter file

  If using shared server processes, then set the SDU size in the DISPATCHERS parameter in the initialization parameter file, as follows:

      DISPATCHERS="(DESCRIPTION=(ADDRESS=(PROTOCOL=tcp))(SDU=8192))"

- `listener.ora`

  If the listener was configured with a list of targets in the `listener.ora` file, then the value for SDU in the SID_LIST parameter overrides the current setting in the `sqlnet.ora` file when using dedicated server processes.

**Parent topic:** Configuring Session Data Unit

#### 14.2.2 Setting the SDU Size for the Client

To set the SDU size for the client, configure the following files:

- `sqlnet.ora`

  For global configuration on the client side, configure the DEFAULT_SDU_SIZE parameter in the `sqlnet.ora` file, such as the following:

      DEFAULT_SDU_SIZE=32767

- `tnsnames.ora`

  For a particular connect descriptor, you can specify the SDU parameter in the DESCRIPTION parameter.

      sales.us.example.com=
      (DESCRIPTION=
          (SDU=11280)
            (ADDRESS=(PROTOCOL=tcp)(HOST=sales-server)(PORT=1521))
          (CONNECT_DATA=
           (SERVICE_NAME=sales.us.example.com))
      )

<!-- -->

The SDU size applies to all Oracle Net protocols for the particular connect descriptor.

**Parent topic:** Configuring Session Data Unit

### 14.3 Determining the Bandwidth-Delay Product

Bandwidth-delay product is the product of network bandwidth and the round trip time of data going over the network. A simple way to determine the round trip time, is to use a command such as `ping` from one host to another and use the response times returned by `ping`.

For example, if a network has a bandwidth of 100 Mbps and a round trip time of 5ms, then the send and receive buffers should be at least (100\*10ˆ6) \* (5/10ˆ3) bits or approximately 62.5 Kilobytes.

The following equation shows the relationships between the units and factors involved:

    100,000,000 bits   1 byte   5 seconds
    ---------------- x ------ x --------- = 62,500 bytes
     1 second          8 bits     1000

Setting the SEND_BUF_SIZE and RECV_BUF_SIZE parameters to at least the bandwidth-delay product insures that when large amounts of data are being sent that the network bandwidth will be optimally utilized.

Based on the preceding equation, the bandwidth-delay product of this network link is approximately 64 KB. If the largest message used to transfer redo data between a primary database and a standby database is 1 MB, then the value for the SEND_BUF_SIZE and RECV_BUF_SIZE parameters could be 1 MB. However, if the average message is less, then a setting of 64 KB should be sufficient to optimize use of the available bandwidth.

For most network protocols, ensure that the RECV_BUF_SIZE parameter at one end of the network connection, typically at the client, equals the value of the SEND_BUF_SIZE parameter at the other end, typically at the server.

**See Also:**

"[Statistics Example](troubleshooting-oracle-net-services.md)" for additional information about determining messages sizes

**Parent topic:** Optimizing Performance

### 14.4 Configuring I/O Buffer Space

Reliable network protocols, such as TCP/IP, buffer data into send and receive buffers while sending and receiving to or from lower and upper layer protocols. The sizes of these buffers affect network performance by influencing flow control decisions.

The `RECV_BUF_SIZE` and `SEND_BUF_SIZE` parameters specify sizes of socket buffers associated with an Oracle Net connection. To ensure the continuous flow of data and better utilization of network bandwidth, specify the I/O buffer space limit for receive and send operations of sessions with the `RECV_BUF_SIZE` and `SEND_BUF_SIZE` parameters. The `RECV_BUF_SIZE` and `SEND_BUF_SIZE` parameter values do not have to match, but should be set according to your environment.

For best performance, the size of the send and receive buffers should be set large enough to hold all the data that may be sent concurrently on the network connection. For optimal network performance, these buffers should be set to at least the bandwidth-delay product.

Use these parameters with caution as they affect network and system performance. The default values for these parameters are operating system specific. The following are the defaults for the Linux operating system:

- `SEND_BUF_SIZE`: 131,072 bytes (128k)

- `RECV_BUF_SIZE`: 174,700 bytes

These parameters are supported for TCP, TCP/IP with TLS, and SDPs. Additional protocols may support these parameters on certain operating systems. The recommended values for these parameters are specified in the installation guide. Refer to operating system specific documentation for additional information.

**Note:**

- The actual value of the `SEND_BUF_SIZE` and `RECV_BUF_SIZE` parameters may be less than the value specified because of limitations in the host operating system or due to memory constraints.

- It is important to consider the total number of concurrent connections that your system must support and the available memory resources. The total amount of memory consumed by these connections depends on the number of concurrent connections and the size of their respective buffers.

<!-- -->

- Configuring I/O Buffer Size on the Server
- Configuring I/O Buffer Space on the Client

**Related Topics**

- [Oracle Call Interface Programmer's Guide](../lnoci/using-sql_statements-in-oci.md)

**Parent topic:** Optimizing Performance

#### 14.4.1 Configuring I/O Buffer Size on the Server

Because the database server writes data to clients, setting the SEND_BUF_SIZE parameter on the server-side is typically adequate. If the database server is receiving large requests, then also set the RECV_BUF_SIZE parameter.To configure the database server, set the buffer space size in the `listener.ora` and `sqlnet.ora` files.

In the `listener.ora` file, specify the buffer space parameters for a particular protocol address or for a description. The following is an example of the settings:

    LISTENER=
    (DESCRIPTION=
    (ADDRESS=(PROTOCOL=tcp)(HOST=sales-server)(PORT=1521)
    (SEND_BUF_SIZE=11784)
    (RECV_BUF_SIZE=11784))
    (ADDRESS=(PROTOCOL=ipc)(KEY=extproc)
    (SEND_BUF_SIZE=11784)
    (RECV_BUF_SIZE=11784)))
    LISTENER2=
    (DESCRIPTION=
    (SEND_BUF_SIZE=8192)
    (RECV_BUF_SIZE=16384)
    (ADDRESS=(PROTOCOL=tcp)(HOST=sales-server)(PORT=1521)))

Although the preceding example has multiple addresses, the `ADDRESS_LIST` parameter was not used. This is because the `ADDRESS_LIST` parameter is not mandatory.

The following is an example of the settings in the `sqlnet.ora` file:

    RECV_BUF_SIZE=65536
    SEND_BUF_SIZE=65536

- Setting the Buffer Size Parameter for Shared Server Processes

**Parent topic:** Configuring I/O Buffer Space

##### 14.4.1.1 Setting the Buffer Size Parameter for Shared Server Processes

If using shared server processes, then you can override the current settings obtained from the server `sqlnet.ora` file by setting the buffer space parameters in the DISPATCHERS initialization parameter as follows:

    DISPATCHERS="(ADDRESS=(PROTOCOL=tcp)(SEND_BUF_SIZE=65536))"

**Parent topic:** Configuring I/O Buffer Size on the Server

#### 14.4.2 Configuring I/O Buffer Space on the Client

To configure the client, set the buffer space size in the following locations in the specified file:

- Setting only the RECV_BUF_SIZE parameter is typically adequate. If the client is sending large requests, then also set the SEND_BUF_SIZE parameter. These parameters are set in the client's `sqlnet.ora` file.

- For a particular connect descriptor, you can override the current settings in the client `sqlnet.ora` file. You can specify the buffer space parameters for a particular protocol address or description in the `tnsnames.ora` file similar to the following:

      sales.us.example.com=
       (DESCRIPTION=
         (ADDRESS_LIST=
           (ADDRESS=(PROTOCOL=tcp)(HOST=sales1-server)(PORT=1521)
              (SEND_BUF_SIZE=11784)
              (RECV_BUF_SIZE=11784))
           (ADDRESS=(PROTOCOL=tcp)(HOST=sales2-server)(PORT=1521)
              (SEND_BUF_SIZE=11784)
              (RECV_BUF_SIZE=11784))
         (CONNECT_DATA=
           (SERVICE_NAME=sales.us.example.com)))
      hr.us.example.com=
       (DESCRIPTION=
         (SEND_BUF_SIZE=8192)
         (RECV_BUF_SIZE=8192)
           (ADDRESS=(PROTOCOL=tcp)(HOST=hr1-server)(PORT=1521))
         (CONNECT_DATA=
           (SERVICE_NAME=hr.us.example.com)))

**Parent topic:** Configuring I/O Buffer Space

### 14.5 Configuring SDP Support for InfiniBand Connections

Oracle Net Services provides support for the Sockets Direct Protocol ([SDP](glossary.md)) for InfiniBand high-speed networks.

SDP is a standard communication protocol for clustered server environments. SDP is an interface between a network interface card and the application. By using SDP, applications place most of the messaging burden upon the network interface card, freeing the CPU for other tasks. As a result, SDP decreases network [latency](glossary.md) and CPU utilization.

SDP is designed specifically for System Area Networks (SANs). A SAN is characterized by short-distance, high-performance communications between multiple server systems, such as Oracle WebLogic Server or any other third-party middle-tier client and database servers clustered on one switch.

**Note:**

Check with your individual vendor for their version compatibility with Oracle Database 12c.

Visit the Oracle Technology Network for additional information about SDP support at

[`http://www.oracle.com/technetwork/index.html`](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/netag&id=otn_index)

The following sections describe how to set up Oracle Net support of SDP for middle tier and database server communication. It contains the following topics:

- Prerequisites for Using SDP
- Configuring SDP on the Server
- Configuring SDP on the Client

**See Also:**

"[Understanding Performance](introducing-oracle-net-services.md) " for an overview of supported deployments

**Parent topic:** Optimizing Performance

#### 14.5.1 Prerequisites for Using SDP

Prior to configuring support for SDP, install the required hardware, and set up InfiniBand hardware and software compatible with OpenFabrics Enterprise Distribution (OFED) 1.4 or 1.5 from a designated vendor on both the application web server and database server.

During installation of the InfiniBand software, identify the constant that defines SDP or the address family for the system. This can be obtained from the operating system or OFED documentation.

**See Also:**

Vendor documentation for installation information

**Parent topic:** Configuring SDP Support for InfiniBand Connections

#### 14.5.2 Configuring SDP on the Server

To configure the database server, configure an SDP address in the `listener.ora` file on the database server.

**Note:**

If the SDP or address protocol family constant is not 27, the default value for Oracle Net Services, then define the constant in the SDP.PF_INET_SDP parameter in the `sqlnet.ora` file.

The following example shows an SDP endpoint that uses port number 1521 on the computer `sales-server`.

    LISTENER=
      (DESCRIPTION=
        (ADDRESS_LIST=
          (ADDRESS=(PROTOCOL=sdp)(HOST=sales-server)(PORT=1521))
          (ADDRESS=(PROTOCOL=tcp)(HOST=sales-server)(PORT=1521))
          (ADDRESS=(PROTOCOL=ipc)(KEY=extproc))))

**See Also:**

"[Creating a List of Listener Protocol Addresses](enabling-advanced-features.md)"

**Parent topic:** Configuring SDP Support for InfiniBand Connections

#### 14.5.3 Configuring SDP on the Client

**Note:**

If the SDP or address protocol family constant is not 27, the default value for Oracle Net Services, then define the constant in the SDP.PF_INET_SDP parameter in the `sqlnet.ora` file.

The following procedure describes how to configure the Oracle WebLogic Server servers or third-party middle-tier client:

1.  If configuring third-party middle-tier client, then upgrade the clients to use Oracle Database 12c client software, as follows:

    1.  Run Oracle Universal Installer.

    2.  Select Oracle Database 12c Client from the Available Products page.

2.  For both Oracle WebLogic Server servers and third-party middle-tier client, create a network service name to connect to the database server, as follows:

    - For Oracle WebLogic Server servers, specify a network service name that uses the same TCP/IP protocol address configured in the `tnsnames.ora` file. For example:

          sales=
           (DESCRIPTION=
             (ADDRESS=(PROTOCOL=tcp)(HOST=sales-server)))
             (CONNECT_DATA=
               (SERVICE_NAME=sales.us.example.com)))

    - For third-party middle-tier clients, specify a network service name that uses the same SDP address configured in the `tnsnames.ora` file.

      For example:

          sales=
           (DESCRIPTION=
             (ADDRESS=(PROTOCOL=sdp)(HOST=sales-server)))
             (CONNECT_DATA=
               (SERVICE_NAME=sales.us.example.com)))

      **See Also:**

      [Configuring Naming Methods](configuring-naming-methods.md) for additional information about creating connect descriptors

**Parent topic:** Configuring SDP Support for InfiniBand Connections

### 14.6 Configuring Exadirect Support for InfiniBand Connections

Oracle Net Services provides support for the Exadirect for InfiniBand high-speed networks.. Use the new transport to improve latency and throughput by leveraging Remote Direct Memory Access (RDMA) in an InfiniBand environment

Exadirect protocol uses TCP for control communication and IB RC transport for data. The Exadirect protocol adapter is supported only on Oracle Linux in this release.

**Note:**

In Oracle Database 12c release 2 (12.2), Exadirect supports a single Exadirect endpoint configuration. It does not support DRCP.

The following sections describe how to set up Oracle Net support of Exadirect for middle tier and database server communication.

- Prerequisites for Using Exadirect
- Configuring Exadirect on the Server
  To configure the database server, configure an Exadirect address in the `listener.ora` file on the database server.
- Configuring Exadirect on the Client
  Specify a network service name that uses the same Exadirect address that is configured in the `tnsnames.ora` file.

**Parent topic:** Optimizing Performance

#### 14.6.1 Prerequisites for Using Exadirect

Exadirect can be used as a transport protocol between Exadata nodes. The Exadata version must be 12.1.2.3.3 or higher for Exadirect to work.

**Parent topic:** Configuring Exadirect Support for InfiniBand Connections

#### 14.6.2 Configuring Exadirect on the Server

To configure the database server, configure an Exadirect address in the `listener.ora` file on the database server.

Configure `enable_exadirect_listener_name=on` parameter in `listener.ora` file.

The following example shows an Exadirect endpoint that uses port number `1522` on the computer having IB interface as `192.168.10.1`.

    LISTENER
    =
    (DESCRIPTION=
    (ADDRESS_LIST=
    (ADDRESS=(PROTOCOL=exadirect)(HOST=192.168.10.1)(PORT=1522))
    (ADDRESS=(PROTOCOL=tcp)(HOST=sales-server)(PORT=1521))
    (ADDRESS=(PROTOCOL=ipc)(KEY=extproc))))

    ENABLE_EXADIRECT_LISTENER=on

**Note:**

To enable Exadirect flow control, set `exadirect_flow_control=on` in `sqlnet.ora` file. This is a negotiated parameter and should be set in both the server and the client `sqlnet.ora` file. `EXADIRECT_RECVPOLL` parameter specifies the time that a receiver polls for incoming data. Exadirect adapter uses HugePages.

**Parent topic:** Configuring Exadirect Support for InfiniBand Connections

#### 14.6.3 Configuring Exadirect on the Client

Specify a network service name that uses the same Exadirect address that is configured in the `tnsnames.ora` file.

Enable Exadirect flow control by setting `exadirect_flow_control=on` in `sqlnet.ora` file.

For example:

    (DESCRIPTION=
    (ADDRESS=(PROTOCOL=exadirect)(HOST=192.168.10.1)(port=1522))
    (CONNECT_DATA=
    (SERVICE_NAME=sales.us.example.com)))

**Parent topic:** Configuring Exadirect Support for InfiniBand Connections

### 14.7 Limiting Resource Consumption by Unauthorized Users

Unauthorized access to the listener or database server can result in denial-of-service attacks, whereby an unauthorized client attempts to block authorized users' ability to access and use the system when needed. Malicious clients may attempt to flood the listener or database server with connect requests that have the sole purpose of consuming resources, such as connections, processes, or threads. To mitigate these types of attacks, configure limits that constrain the time in which resources can be held prior to authentication. Client attempts to exceed the configured limits result in connection terminations and an audit trail containing the IP address of the client being logged.

To limit the resource consumption by unauthorized users and enable the audit trail, set time-limit values for the parameters described in Table 14-1. These parameters do not have default values.

Table 14-1 Connect-Timeout Parameters

| Parameter                              | File                                | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|:---------------------------------------|:------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| INBOUND_CONNECT_TIMEOUT\_listener_name | `listener.ora`                      | The time, in seconds, for the client to complete its connect request to the listener after the network connection had been established.<br>If the listener does not receive the client request in the time specified, then it terminates the connection. In addition, the listener logs the IP address of the client and an [ORA-12525: Listener Has Not Received Client's Request in Time Allowed](troubleshooting-oracle-net-services.md) error message to the `listener.log` file.                                                                                                                 |
| SQLNET.INBOUND_CONNECT_TIMEOUT         | `sqlnet.ora` on the database server | The time, in seconds, for a client to connect with the database server and provide the necessary authentication information.<br>If the client fails to establish a connection and complete authentication in the time specified, then the database server terminates the connection. In addition, the database server logs the IP address of the client and an [ORA-12170: Connect Timeout Occurred](troubleshooting-oracle-net-services.md) error message to the `sqlnet.log` file. The client receives either an ORA-12547: TNS:lost contact, or an ORA-12637: Packet receive failed error message. |

When specifying values for these parameters, consider the following recommendations:

- Set both parameters to an initial low value.

- Set the value of the INBOUND_CONNECT_TIMEOUT\_listener_name parameter to a lower value than the SQLNET.INBOUND_CONNECT_TIMEOUT parameter.

For example, you can set INBOUND_CONNECT_TIMEOUT\_listener_name to 2 seconds and INBOUND_CONNECT_TIMEOUT parameter to 3 seconds. If clients are unable to complete connections within the specified time due to system or network delays that are normal for the particular environment, then increment the time as needed.

**See Also:**

- "[Resolving the Most Common Error Messages for Oracle Net Services](troubleshooting-oracle-net-services.md)" for a description of error message workarounds

- "[Analyzing Listener Log Files](troubleshooting-oracle-net-services.md)" for additional information about entries in the `listener.log` file

- "[About Advanced Profile Information](configuring-profiles.md)" for additional information about configuring these parameters

**Parent topic:** Optimizing Performance

### 14.8 Configuring Key-Based Routing for Client-Server Connections

Learn how to establish client-server connections in a sharded database by using key-based (or direct) routing. In key-based routing to a shard, a connection is established to a single, relevant shard that contains the data pertinent to the required transaction using a sharding key.

- About Key-Based Routing
  With key-based or direct routing, a database connection is established directly from the client to a shard according to the value of the sharding key specified in the connect string.
- Specifying a Sharding Key in the Connect String
  You can directly connect to shards by specifying a sharding key in the `CONNECT_DATA` section of a connect string or `tnsnames.ora` file. You can also specify shard directors (as endpoints), global service name, and region name for your sharding deployment.

**Parent topic:** Optimizing Performance

#### 14.8.1 About Key-Based Routing

Oracle Sharding enables you to horizontally partition data across multiple, independent Oracle databases. Each physical database in such a configuration is called a shard. Sharded table partitions are distributed across shards at the tablespace level, based on a sharding key. Examples of keys include customer ID, account number, and country ID. With key-based or direct routing, a database connection is established directly from the client to a shard according to the value of the sharding key specified in the connect string.

A shard director is a specific implementation of a Global Service Manager (GSM) that acts as a regional listener for clients that connect to a sharded database. Based on the sharding key passed during a connection request, the shard director establishes a connection to an appropriate shard as follows:

- The shard director performs a lookup for the service and key value, and then redirects the client to a shard containing the data.
- The client runs a SQL statement and receives results directly from the shard.

Direct routing assumes that all the database requests that are issued within a connection are related to the data associated with the specified key value. If a client needs to access data with a different key value, then it must establish a new database connection.

The connect string contains a single sharding key if an Oracle Database is sharded by consistent hash, list, or range. Oracle Database also supports composite sharding that enables two levels of sharding. First the data is sharded by list or range and then it is further sharded by consistent hash. In composite sharding method, the connect string contains both a sharding key (for sharding by consistent hash) and a super sharding key (for sharding by list or range).

**Related Topics**

- [Using Oracle Sharding](../shard/sharding-overview.md)
- [Oracle Database Global Data Services Concepts and Administration Guide](../gsmug/intro-global-data-services.md)

**Parent topic:** Configuring Key-Based Routing for Client-Server Connections

#### 14.8.2 Specifying a Sharding Key in the Connect String

You can directly connect to shards by specifying a sharding key in the `CONNECT_DATA` section of a connect string or `tnsnames.ora` file. You can also specify shard directors (as endpoints), global service name, and region name for your sharding deployment.

Specify a shard (partition) key value using one of the following parameters:

- `SHARDING_KEY`: To specify a sharding key for a particular shard in simplified text format.

- `SUPER_SHARDING_KEY`: To specify a shardspace key for a collection of shards in simplified text format.

- `SHARDING_KEY_B64`: To specify a sharding key for a particular shard in base64-encoded binary format.

- `SUPER_SHARDING_KEY_B64`: To specify a shardspace key for a collection of shards in base64-encoded binary format.

The connect string must be in the format required to connect to a global service.

Here is an example of the connect string for a shard, where the `SHARDING_KEY` and `SUPER_SHARDING_KEY` parameter values are specified in simplified text format:

    (DESCRIPTION=
      (FAILOVER=on)
      (ADDRESS_LIST=
        (LOAD_BALANCE=ON)
        (ADDRESS=(host=sales-east1)(port=1522))
        (ADDRESS=(host=sales-east2)(port=1522))
        (ADDRESS=(host=sales-east3)(port=1522)))
      (ADDRESS_LIST=
        (LOAD_BALANCE=ON)
        (ADDRESS=(host=sales-west1)(port=1522))
        (ADDRESS=(host=sales-west2)(port=1522))
        (ADDRESS=(host=sales-west3)(port=1522)))
      (CONNECT_DATA=
       (SERVICE_NAME=sales)
       (SHARDING_KEY=40598230)(SUPER_SHARDING_KEY=gold)
       (REGION=east))
    )

**Related Topics**

- [Using Oracle Sharding](../shard/sharding-overview.md)
- [SHARDING_KEY](../netrf/local-naming-parameters-in-tns-ora-file.md)
- [SUPER_SHARDING_KEY](../netrf/local-naming-parameters-in-tns-ora-file.md)

**Parent topic:** Configuring Key-Based Routing for Client-Server Connections
