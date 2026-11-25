This chapter describes Oracle Net Services and its implementation in the BS2000 and POSIX program environment. It supplements the [Oracle Database Net Services Administrator's Guide](../netag/introducing-oracle-net-services.md) with BS2000-specific information about the following topics:

- Oracle Net Protocol Support

- Oracle Network Security

- Shared Server Architecture

- Configuring the Network

- Troubleshooting Oracle Net Services

### 13.1 Oracle Net Protocol Support

Oracle Net Services supports network communication between a client application and a remote or a local database running on a variety of operating systems.

Oracle Net Services allows the database servers and the client applications, or servers acting as clients, to run on separate systems and provides a means for moving data between the nodes on a network. For example, a UNIX or Windows user can run applications that access and manipulate data in a remote Oracle database running on a BS2000 system.

Oracle Net Services is also used for inter-process communication, if a client and the requested database service are running on the same machine.

As mentioned in the [Concepts and Architecture](concepts-and-architecture.md) chapter, Oracle programs can run in both the BS2000 and the POSIX program environment. Depending on the program environment, the Oracle protocol adapter uses different socket implementations, such as, the BS2000 sockets and the POSIX sockets. This causes differences in the protocols used for the local inter-process communication.

Oracle Net Services supports the following network protocols:

- TCP/IP (version 4 and version 6)
- TCP/IP with SSL
- ISO Domain (in the BS2000 program environment only)
- Unix Domain (in the POSIX program environment and optionally in the BS2000 program environment)

Oracle Net Services automatically detects the program environment and uses the appropriate sockets implementation. You can also specify Oracle Net Services to use the POSIX sockets instead of the BS2000 sockets. Use the variable `NT_IPC_PROTOCOL_UNIX` to switch to the POSIX sockets with the Unix Domain protocol for local communication:

`NT_IPC_PROTOCOL_UNIX={TRUE|FALSE} Default: FALSE`

The POSIX sockets provide a smarter handling of the hand-off mechanism, which is required for the support of the Database Resident Connection Pooling (DRCP) feature. To ensure the use of the correct protocol for inter-process communication in both program environments, you must set the variable to the same value in both the POSIX and the BS2000 program environment.

This section contains the following topics:

- About Bequeath Protocol

- About IPC Protocol Support

- About TCP/IP Protocol Support

- About TCP/IP with SSL Protocol

**Note:**

The InterProcess Communication (IPC) protocol requires the same socket implementation for both the client and the server.

#### 13.1.1 About Bequeath Protocol

The Bequeath technique enables clients to connect to a database without using the network listener. Oracle's Bequeath protocol internally spawns a server process for each client application. It does the same operation that a remote network listener does for the connection locally.

The Bequeath (BEQ) protocol is available in both program environments so that a client running in the POSIX shell can connect via the BEQ protocol to a server running in the BS2000 program environment. Ensure that the environment variable `NT_IPC_PROTOCOL_UNIX` has the same value in both program environments.

You can also use the POSIX sockets in the BS2000 program environment. In this case Oracle Net Services uses the protocol `PF_UNIX` for local connections and for handing off a connection.

By default, Oracle Net Services uses the BS2000 sockets in the BS2000 program environment, which is, `NT_IPC_PROTOCOL_UNIX=FALSE`. If you configure Oracle Net Services to use POSIX sockets in the BS2000 program environment, that is if `NT_IPC_PROTOCOL_UNIX=TRUE`, then ensure that the environment variable `NT_IPC_PROTOCOL_UNIX` is set to the same value for both the client and the local server.

##### 13.1.1.1 Overview of the Bequeath Protocol

The Bequeath protocol:

- Does not use a network listener. Therefore, listener configuration is not required.

- Automatically spawns a dedicated server.

- Is used for local connections where an Oracle Database client application, such as SQL\*Plus, communicates with an Oracle Database instance running on the same computer.

- Only works in the Dedicated Server mode. It cannot be used in the Shared Server mode.

**Note:**

If clients are running in a user ID that is different from the `DBA` user ID, then Oracle recommends using a net service name to connect through a listener to the destination database.

#### 13.1.2 About IPC Protocol Support

This section introduces Oracle's Inter Process Communication (IPC) protocol support for inter-process calls. It is used to map the functionality of IPC to Oracle's Protocol Support Layer. Oracle Utilities and products running in the POSIX shell cannot use the IPC protocol if the variable `NT_IPC_PROTOCOL_UNIX` is set to `FALSE`.

It includes the following topics:

- Overview of IPC

- Using the IPC Protocol

##### 13.1.2.1 Overview of IPC

On BS2000 systems, the IPC protocol is used for local inter-process communication. The Oracle Protocol Support for IPC uses the ISO functionality of the BS2000 sockets if `NT_IPC_PROTOCOL_UNIX=FALSE`. If POSIX sockets are also used in the BS2000 program environment, that is, if `NT_IPC_PROTOCOL_UNIX=TRUE`, then the Oracle Protocol Support for IPC uses the UNIX protocol family.

The client process initiates its IPC connection with the remote process by specifying a `KEY` that describes the listening process. Once the connection is established, the two communicating processes send and receive data through a continuous byte stream.

##### 13.1.2.2 Using the IPC Protocol

The IPC protocol enables applications to integrate with the Inter Process Communication method on a local host. The following is the syntax for using IPC protocol:

    (DESCRIPTION=
       (ADDRESS=
                (PROTOCOL=IPC)
                (KEY=alphanumeric)
                )
    )

where:

`PROTOCOL` specifies the supported protocol. For IPC, the value is `IPC`.

`KEY` specifies the listen endpoint. A string of at most 32 characters: \[a...z\], \[A...Z\], \[0...9\], '.', '-', '\_', '\$'

The following is an example of an IPC ADDRESS that specifies a server on a local host:

    (DESCRIPTION=
      (ADDRESS=
           (PROTOCOL=IPC)
           (KEY=ORCL)
       )
    )

**Note:**

If the IPC protocol is specified by a utility or user application running in the POSIX shell and if `NT_IPC_PROTOCOL_UNIX=FALSE`, then Oracle Net Services fails to use the IPC protocol. The following error message is displayed:

    TNS-12557: TNS:protocol adapter not loadable

#### 13.1.3 About TCP/IP Protocol Support

This section introduces Oracle's TCP/IP (Transmission Control Protocol/Internet Protocol) protocol support, which is used to map the functionality within TCP/IP to Oracle's Protocol Support Layer.

The specific TCP/IP connection parameters are part of the `ADDRESS` keyword-value pair. The three TCP/IP–specific parameters can be entered in any order within the `ADDRESS` construct. The syntax used by Oracle's TCP/IP protocol support is:

    (DESCRIPTION=
     (ADDRESS=
         (PROTOCOL=TCP)
         (HOST=hostname)
         (PORT=port#)
     )
    )

where:

`PROTOCOL` specifies the supported protocol. For TCP/IP, the value is `TCP`.

`HOST` specifies the host name or the host's IP address.

`PORT` specifies the TCP/IP port number.

The following is an example of the TCP/IP ADDRESS specifying a client on the `sales-server` host:

    (DESCRIPTION=
     (ADDRESS=
         (PROTOCOL=TCP)
         (HOST=sales-server)
         (PORT=1521)
     )
    )

**Related Topics**

- [Oracle Database Net Services Administrator's Guide](../netag/understanding-communication-layers.md)

#### 13.1.4 About TCP/IP with SSL Protocol

The TCP/IP with Secure Socket Layer (SSL) protocol is supported in this release. SSL provides authentication, encryption, and data integrity using public key infrastructure (PKI). SSL stores authentication data, such as certificates and private keys, in an Oracle Wallet.

The connection parameters for TCP/IP with SSL protocol are the same as TCP/IP except for the protocol, which is TCPS:

    (DESCRIPTION=
     (ADDRESS=
         (PROTOCOL=TCPS)
         (HOST=hostname)
         (PORT=port#)
     )
    )

where:

- `PROTOCOL` specifies the supported protocol. For TCP/IP with SSL protocol, the value is TCPS.

- `HOST` specifies the host name or the host's IP address.

- `PORT` specifies the TCP/IP with SSL protocol port number.

The following is an example of the TCP/IP with SSL protocol ADDRESS specifying a client on the sales-server host:

    (DESCRIPTION=
     (ADDRESS=
         (PROTOCOL=TCPS)
         (HOST=sales-server)
         (PORT=2484)
     )
    )

**Related Topics**

- [Oracle Database Net Services Administrator's Guide](../netag/understanding-communication-layers.md)

### 13.2 Oracle Network Security

This section describes how to configure the data integrity and the cryptographic services of Oracle Network Security for Fujitsu BS2000.

For using either the data integrity, or the cryptographic services, or both, you must specify the appropriate parameters in the `SQLNET.ORA` file.

Use the following parameters to specify whether a service (example: crypto-checksumming or encryption) should be active:

    SQLNET.CRYPTO_CHECKSUM_CLIENT
    SQLNET.CRYPTO_CHECKSUM_SERVER
    SQLNET.ENCRYPTION_CLIENT
    SQLNET.ENCRYPTION_SERVER

Each of the preceding parameters defaults to `REJECTED`.

Each of the preceding parameters can have one of the following values:

| Value       | Meaning                                                                                                                                                                                         |
|:------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `ACCEPTED`  | Enables the security service if the other side of the connection specifies `REQUESTED` or `REQUIRED` and there is a compatible algorithm available on the other side. It is inactive otherwise. |
| `REJECTED`  | Disables the security service, and the connection fails if the other side specifies `REQUIRED`.                                                                                                 |
| `REQUESTED` | Enables the security service if the other side specifies `ACCEPTED`, `REQUESTED`, or `REQUIRED` and there is a compatible algorithm available on the other side. It is inactive otherwise.      |
| `REQUIRED`  | Enables the security service, and the connection fails if the other side specifies `REJECTED` or if there is no compatible algorithm on the other side.                                         |

Use the following parameters to control the algorithms that are made available for each service on each end of a connection:

    SQLNET.CRYPTO_CHECKSUM_TYPES_CLIENT
    SQLNET.CRYPTO_CHECKSUM_TYPES_SERVER
    SQLNET.ENCRYPTION_TYPES_CLIENT
    SQLNET.ENCRYPTION_TYPES_SERVER

The value of each of these parameters can be either a list of algorithm names in parenthesis separated by commas or a single algorithm name.

| Type                  | Values                                                                                                       |
|:----------------------|:-------------------------------------------------------------------------------------------------------------|
| Crypto checksum types | `MD5`, `SHA1`,`SHA256`, `SHA384`, `SHA512`                                                                   |
| Encryption types      | `3DES112`, `3DES168`, `AES128`, `AES192`, `AES256`, `DES`, `DES40`, `RC4_40`, `RC4_56`, `RC4_128`, `RC4_256` |

**Related Topics**

- [Oracle Database Net Services Administrator's Guide](../netag/understanding-communication-layers.md)
- [Oracle Database Net Services Reference](../netrf/parameters-for-the-sqlnet.ora.md)
- [Oracle Database Security Guide](../dbseg/data-encryption-and-integrity-parameters.md)

### 13.3 Shared Server Architecture

The initialization parameters that control the shared server architecture are as follows:

- `LOCAL_LISTENER`

- `DISPATCHERS`

- `MAX_DISPATCHERS`

- `SHARED_SERVERS`

- `MAX_SHARED_SERVERS`

- `SHARED_SERVER_SESSIONS`

- `CIRCUITS`

The shared server architecture and the dedicated server architecture can work concurrently in an instance. Provide information in the connect descriptor to indicate whether a connecting application should use the shared server or the dedicated server architecture. By default, the listener process uses the shared server architecture. If you want the application to use the dedicated server architecture, then you must set `USE_DEDICATED_SERVER=ON` in the `SQLNET.ORA` file or specify a net service name with the parameter `SERVER` in the used naming method. The `SQLNET.ORA` parameter `USE_DEDICATED_SERVER=ON` overwrites the `SERVER` parameter.

The following example shows how to reference a dedicated server in a shared server configuration by using a specially defined net service name:

    FINANCE_DED=(DESCRIPTION=
                         (ADDRESS=
                              (PROTOCOL=TCP)
                              (HOST=sales-server)
                              (PORT=1521))
                         (CONNECT_DATA=
                              (SERVICE_NAME=sales.us.example.com)
                              (SERVER=dedicated)))

To choose between using the shared server and the dedicated server architecture, you must consider the CPU overhead versus resource allocation, such as, tasks, memory, and so on. Use the shared server architecture if many clients work only occasionally with an Oracle database. Use the dedicated server architecture if only a few clients work intensively with an Oracle database. Before you decide, consider using the information in the following shared server dynamic tables:

- `V$DISPATCHER`

- `V$QUEUE`

- `V$SHARED_SERVERS`

- `V$SHARED_SERVER_MONITOR`

**See Also:**

- [Oracle Database Net Services Administrator's Guide](../netag/introducing-oracle-net-services.md) and [Oracle Database Administrator’s Guide](../admin/managing-processes.md) for detailed information about the shared server architecture

- [Oracle Database Net Services Reference](../netrf/parameters-for-the-sqlnet.ora.md) for more information on how to reference a dedicated server in a shared server configuration

- [Oracle Database Administrator’s Guide](../admin/managing-processes.md) for more information about shared server dynamic tables

### 13.4 Configuring the Network

You can either use the Easy Connect Naming Method to connect to the database or the Local Naming Method. When you use the Local Naming Method, Oracle recommends to configure clients for the use of service names that are easy to remember aliases for database addresses and match the address preconfigured in each system's `LISTENER.ORA` file. The client uses these addresses to connect to the network listener, which routes the connection request to the required service. During a connection, a client passes the service name to which it wants to connect.

The `LISTENER.ORA` file identifies and controls the behavior of the network listener that listens for services on the system. This file includes:

- Network listener descriptors and addresses

- Services the listener is listening for

- Various control parameters

Client configuration is accomplished by creating a list of net service names with addresses of network destinations through the local naming parameter file `TNSNAMES.ORA` or an LDAP compliant directory server.

- About Using Easy Connect Naming Method

- About Using the Local Naming Method

- About Using the Directory Naming Method

- Customizing Oracle Net Listener Configuration

- Configuration of the Client

- Testing the Configuration of the Client

#### 13.4.1 About Using Easy Connect Naming Method

The Easy Connect naming method, can be used to connect to a database without the need to configure service names in the `TNSNAMES.ORA` configuration file. For using the Easy Connect naming method, ensure that `EZCONNECT` is listed in the client's configuration file parameter for naming adaptors `NAMES.DIRECTORY_PATH`.

Easy Connect naming is suitable for small and simple environments.

**See Also:**

[Oracle Database Net Services Administrator's Guide](../netag/configuring-naming-methods.md) for more information about the Easy Connect naming method

#### 13.4.2 About Using the Local Naming Method

Local naming refers to the method of resolving a service name to a network address by using information configured on each individual client in a `TNSNAMES.ORA` configuration file. For using the local naming, ensure that `TNSNAMES` is listed in the client's configuration file parameter for naming adaptors `NAMES.DIRECTORY_PATH`.

Local naming is most appropriate for simple distributed networks with a small number of services that change infrequently.

#### 13.4.3 About Using the Directory Naming Method

Directory Naming refers to the method of resolving a service name to a network address by using a directory server. For using a directory server, ensure that `LDAP` is listed in the client's configuration file parameter for naming adaptors `NAMES.DIRECTORY_PATH` and that the target address of the directory server is configured in the `LDAP.ORA` parameter file. For example:

    # LDAP.ORA Network Configuration File: network.admin.ldap.ora
    DEFAULT_ADMIN_CONTEXT = ""
    DIRECTORY_SERVERS= (ldap_server:389:636)
    DIRECTORY_SERVER_TYPE = Your Internet Directory Type

Where `DIRECTORY_SERVER_TYPE` specifies the type of the directory server that is being used. It can have the following values:

- `oid` for Oracle Internet Directory
- `ad` for Microsoft Active Directory

**See Also:**

[Oracle Database Net Services Administrator's Guide](../netag/configuring-naming-methods.md) and [Oracle Database Net Services Reference](../netrf/index.md) for more information

#### 13.4.4 Customizing Oracle Net Listener Configuration

Before starting the listener, you must set up the configuration file `LISTENER.ORA`. This file includes the address of the listener and various control parameters used by the listener. When a listener accepts a connection request of a client, it routes the connection to a database server. In case of a dedicated server, the listener starts the server using the bequeath protocol and inherits the connection. Therefore, the listener should run in the DBA user ID of the Oracle database.

Usually the listener runs in the same DBA user ID as the Oracle database instance. If you have Oracle database instances running in different DBA user IDs, then you can configure a single listener to support all database services. In this case the listener must know the LOGON authorization parameters, `USER-ID`, `ACCOUNT`, and `PASSWORD` of the foreign DBA user ID where Oracle database server tasks must be started. Use the Oracle environment variables `sid``_USER`, `user``_ACCOUNT`, and `user``_PASSWORD` as described in the following table to specify the required LOGON authorization parameters:

| Parameter         | Meaning                                         |
|:------------------|:------------------------------------------------|
| `BGJPAR`          | Parameters for `ENTER` jobs                     |
| `sid``_BGJPAR`    | Parameters for `ENTER` jobs identified by `SID` |
| `sid``_USER`      | The user ID under which the job should run      |
| `user``_ACCOUNT`  | Account of the target user ID                   |
| `user``_PASSWORD` | Password of the target user ID                  |

**Note:**

In order to avoid storing a password in the `ORAENV` file, you can use SECOS, which is Fujitsu's Security Control System for BS2000. SECOS supports the facility to grant the listener’s user ID the right to start batch jobs in the DBA user ID. Thus the environment variable `sid``_USER` is the only variable that must be set.

The following example of an `ORAENV` file configured for a central listener process shows how the parameters work. The listener can share this `ORAENV` file with an instance, which runs under the same user ID. For a better understanding, we assume that the listener and the instances `DEM0` and `DEM1` are running under the user ID `ORACDEM1` while the instance `DEM2` is running under the user ID `ORACDEM2`. Define the following parameters:

    BGJPAR=J-C=JCBORA,START=IMME,CPU-LIMIT=NO,LOGGING=*NO
    DEM1_BGJPAR=J-C=JCBDEM1,START=IMME,CPU-LIMIT=NO
    DEM2_USER=ORACDEM2
    ORACDEM2_ACCOUNT=01234
    ORACDEM2_PASSWORD=ORACLE

The listener always runs the same sequence to look up the parameters `sid``_BGJPAR` and `sid``_USER`. If the value for `sid``_BGJPAR` is not found, then the listener uses the value given by the parameter `BGJPAR`. If a user ID is given by `sid``_USER`, then the listener tries to get the processing admission from the parameters `user_ACCOUNT` and `user_PASSWORD`. For the given `ORAENV`, you get the following scenarios for the listener:

- The listener should start a server for the instance `DEM0`. Because the parameters `DEM0_BGJPAR` and `DEM0_USER` are not defined the listener starts the server for the instance `DEM0` under the user ID `ORACDEM1` with the start parameters defined by `BGJPAR`.

- If a server for the instance `DEM1` must be started, then the listener looks for the parameters `DEM1_BGJPAR` and `DEM1_USER`. In this case the parameter `DEM1_BGJPAR` can be evaluated, whereas, the evaluation of `DEM1_USER` failed because this parameter is not defined. Therefore, the listener adds the start parameters "`J-C=JCBDEM1,START=IMME,CPU-LIMIT=NO`" to the `ENTER-PROCEDURE` command and starts the job under the user ID `ORACDEM1`.

- Now a server for instance `DEM2` must be started. The listener looks for the parameters `DEM2_BGJPAR` and `DEM2_USER`. The parameter `DEM2_BGJPAR` is not defined so that the listener uses the start parameters defined by `BGJPAR`. On the other hand the parameter `DEM2_USER` can be evaluated successfully and returns the value `ORACDEM2`. Now the listener tries to get the processing admission by evaluating the parameters `ORACDEM2_ACCOUNT` and `ORACDEM2_PASSWORD`. The listener starts the server job under the user ID `ORACDEM2` with the `ENTER-PROCEDURE` parameters "`J-C=JCBORA,START=IMME,CPU-LIMIT=NO,LOGGING=*NO`".

Start the listener using the Listener Control Utility `LSNRCTL`:

    /CALL-PROCEDURE sid.P.ORAENV
    /START-EXECUTABLE (*LINK(ORALOAD),LSNRCTL)

When the `enter options` prompt is displayed, press ENTER to get to the `LSNRCTL` prompt. Enter the following command to start the listener:

    LSNRCTL> START listener-name

**See Also:**

[Oracle Database Net Services Administrator's Guide](../netag/configuring-and-administering-oracle-net-listener.md)

#### 13.4.5 Configuration of the Client

Configuration of network clients involves adding or editing parameters in the client configuration file `SQLNET.ORA` and, depending on the used naming method, in the configuration file `LDAP.ORA` or `TNSNAMES.ORA`.

**See Also:**

[Oracle Database Net Services Reference](../netrf/syntax-rules-configuration-files.md) for more information about the configuration parameters

#### 13.4.6 Testing the Configuration of the Client

After you have verified the network connections, verify the connections to the desired Oracle Database systems using the `TNSPING` utility:

    /CALL-PROCEDURE sid.P.ORAENV
    /START-EXECUTABLE (*LINK(ORALOAD),TNSPING)

When the `enter options` prompt displays, enter the net service name for the database service that you have specified in the naming service. If everything works fine, then a message similar to the following is returned:

    TNS Ping Utility for BS2000: Version 19.0.0.0 -
    Production on 11-MAR-2020 10:28:12
    Used parameter files: network.admin.sqlnet.ora
    Used TNSNAMES adapter to resolve the alias
    Attempting to contact (DESCRIPTION = (ADDRESS_LIST =
    (ADDRESS = (PROTOCOL = TCP)(HOST = sales-server)(PORT = 3055)))
    (CONNECT_DATA = (SERVICE_NAME = sales.us.example.com)))
    OK (30 msec)

**Related Topics**

- [Oracle Database Net Services Administrator's Guide](../netag/testing-connections.md)

### 13.5 Troubleshooting Oracle Net Services

The following is a list of error messages and steps to fix the errors:

1.  Listener could not be started. `LSNRCTL` returns the following error message:
        LSNRCTL> start
        Starting /BS2/$ORACINST.tnslsnr: please wait...

        TNS-12547: TNS:lost contact
        TNS-12560: TNS:protocol adapter error
        TNS-00517: Lost contact
        BS2000 Error: 145: Connection timed out
        LSNRCTL>

    - Ensure that the subsystem `POSIX` is up and running.

    - Ensure that the `BCAM` Light Weight Resolver `LWRESD` is properly configured and running.
2.  Listener could not open the log file.
    - Check the `listener.log` file in the ADR subdirectory for ` tnslsnr`. For example:

      `/u01/app/oracle/diag/tnslsnr/hostname/listener/trace/listener.log`

    - If ADR is disabled, then check if the `listener.log` file in the BS2000 file system, for example, `NETWORK.LOG.LISTENER.LOG`, is accessible and readable.

    - Verify the listener log file in the BS2000 file system using the BS2000 SDF command `REPAIR-DISK-FILES`.

    - If you are not able to fix the listener log file, then delete the file.
3.  A client reports ORA-12545: Connect failed because target host or object does not exist
    - Check the naming service, if the host name is well known in the TCP/IP network.

    - Use a Fully Qualified Domain Name (`hostname.domain`)

    - Ensure that the `BCAM` Light Weight Resolver `LWRESD` is properly configured and running.
4.  A client reports ORA-12535: TNS operation timed out
    - If you use the IPC protocol, then check the Connection Timeout parameter of `BCAM` (use the `BCSHOW` command). This parameter should be set to at least 600 seconds.
5.  A client reports ORA-03113: end-of-file on communication channel
    - Check if the `SQLNET.EXPIRE_TIME` parameter is set for the server. If the parameter is set, then check the `BCAM LETTER-TIMER` using the `BCSHOW` command. If the `LETTER-TIME` is less than the `SQLNET.EXPIRE_TIME`, then the data that is sent by the server to see if the client is running may not be read during their lifetime, which is limited by the `LETTER-TIME`. As a result, the client logs a broken pipe in the `SQLNET.LOG` file:

          ns main err code: 12547
          ns (2)  err code: 12560
          nt main err code: 517
          nt (2)  err code: 32
          nt OS   err code: 0x0040002c

      You can solve this problem by setting the `LETTER-TIMER` to infinite.
