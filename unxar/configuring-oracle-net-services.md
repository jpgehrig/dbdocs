This chapter describes how to configure Oracle Net Services. It contains the following sections:

- Locating Oracle Net Services Configuration Files

- Using Adapters Utility

- Using Oracle Protocol Support

- Setting Up the Listener for TCP/IP or TCP/IP with Secure Sockets Layer

**Related Topics**

- [Oracle Database Net Services Administrator's Guide](../netag/introducing-oracle-net-services.md)

### 5.1 Locating Oracle Net Services Configuration Files

Oracle Net Services configuration files are typically, but not always, located in the `$ORACLE_HOME/network/admin` directory. Depending on the type of file, Oracle Net uses a different search order to locate the file.

The search order for the `sqlnet.ora` and `ldap.ora` files is as follows:

1.  The directory specified by the `TNS_ADMIN` environment variable, if this environment variable is set

2.  The `$ORACLE_HOME/network/admin` directory

The search order for the `cman.ora`, `listener.ora`, and `tnsnames.ora` files is as follows:

1.  The directory specified by the `TNS_ADMIN` environment variable, if this environment variable is set
2.  One of the following directories:
    - On Oracle Solaris:

          /var/opt/oracle

    - On other platforms:

          /etc
3.  The `$ORACLE_HOME/network/admin` directory

For some system-level configuration files, users may have a corresponding user-level configuration file stored in their home directory. The settings in the user-level file override the settings in the system-level file. The following table lists the system-level configuration files and the corresponding user-level configuration files:

| System-Level Configuration File | User-Level Configuration File |
|:--------------------------------|:------------------------------|
| `sqlnet.ora`                    | `$HOME/.sqlnet.ora`           |
| `tnsnames.ora`                  | `$HOME/.tnsnames.ora`         |

Example 5-1 Sample Configuration Files

The `$ORACLE_HOME/network/admin/samples` directory contains samples of the `cman.ora`, `listener.ora`, `sqlnet.ora`, and `tnsnames.ora` configuration files.

**Note:**

- The `cman.ora` file is installed only if you select Connection Manager as part of a custom option during a client custom installation.
- In a Read-only Oracle Home, the configuration files are located in the `$ORACLE_BASE_HOME/network/admin` directory.

### 5.2 Using Adapters Utility

The `adapters` utility displays the transport protocols, naming methods, and Oracle Advanced Security options that Oracle Database supports on the system.

**See Also:**

[Oracle Database Net Services Administrator's Guide](../netag/troubleshooting-oracle-net-services.md) for more information about the `adapters` utility

### 5.3 Using Oracle Protocol Support

Oracle protocol support is a component of Oracle Net. It includes the following:

- IPC Protocol Support

- TCP/IP Protocol Support

- TCP/IP with Secure Sockets Layer Protocol Support

Each of the IPC, TCP/IP, and TCP/IP with Secure Sockets Layer protocol support have an address specification that is used in the Oracle Net Services configuration files and in the `DISPATCHER` initialization parameter. The following sections describe the address specifications for each of the protocol supports.

**Related Topics**

- [Oracle Database Net Services Administrator's Guide](../netag/introducing-oracle-net-services.md)

#### 5.3.1 IPC Protocol Support

The IPC protocol support can be used only when the client program and Oracle Database are installed on the same system. This protocol support requires a listener. It is installed and linked to all client tools and the `oracle` executable.

The IPC protocol support requires an address specification in the following format:

    (ADDRESS = (PROTOCOL=IPC)(KEY=key))

The following table describes the parameters used in this address specification:

| Parameter | Description                                                                            |
|:----------|:---------------------------------------------------------------------------------------|
| PROTOCOL  | The protocol to be used. The value is IPC. It is not case-sensitive.                   |
| KEY       | Any name that is different from any other name used for an IPC KEY on the same system. |

The following is a sample IPC protocol address:

    (ADDRESS= (PROTOCOL=IPC)(KEY=EXTPROC))

#### 5.3.2 TCP/IP Protocol Support

TCP/IP is the standard communication protocol used for client/server communication over a network. The TCP/IP protocol support enables communication between client programs and Oracle Database, whether they are installed on the same or different systems. If the TCP/IP protocol is installed on the system, then the TCP/IP protocol support is installed and linked to all client tools and to the `oracle` executable.

The TCP/IP protocol support requires an address specification in the following format:

    (ADDRESS = (PROTOCOL=TCP)(HOST=hostname)(PORT=port))

The following table describes the parameters used in this address specification:

| Parameter | Description                                                                                                                                               |
|:----------|:----------------------------------------------------------------------------------------------------------------------------------------------------------|
| PROTOCOL  | The protocol support to be used. The value is TCP. It is not case-sensitive.                                                                              |
| HOST      | The host name or the host IP address.                                                                                                                     |
| PORT      | The TCP/IP port. Specify the port as either a number or the alias name mapped to the port in the `/etc/services` file. Oracle recommends a value of 1521. |

The following is a sample TCP/IP protocol address:

    (ADDRESS= (PROTOCOL=TCP)(HOST=MADRID)(PORT=1521))

#### 5.3.3 TCP/IP with Secure Sockets Layer Protocol Support

The TCP/IP with Secure Sockets Layer protocol support enables an Oracle application on a client to communicate with remote Oracle Database instances through TCP/IP and Secure Sockets Layer.

The TCP/IP with Secure Sockets Layer protocol support requires an address specification in the following format:

    (ADDRESS = (PROTOCOL=TCPS)(HOST=hostname)(PORT=port))

The following table describes the parameters used in this address specification:

| Parameter | Description                                                                                                                                                                         |
|:----------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| PROTOCOL  | The protocol to be used. The value is TCPS. It is not case-sensitive.                                                                                                               |
| HOST      | The host name or the host IP address.                                                                                                                                               |
| PORT      | The TCP/IP with Secure Sockets Layer port. Specify the port as either a number or the alias name mapped to the port in the `/etc/services` file. Oracle recommends a value of 2484. |

The following is a sample TCP/IP with Secure Sockets Layer protocol address:

    (ADDRESS= (PROTOCOL=TCPS)(HOST=MADRID)(PORT=2484))

### 5.4 Setting Up the Listener for TCP/IP or TCP/IP with Secure Sockets Layer

Oracle recommends that you reserve a port for the listener in the `/etc/services` file of each Oracle Net Services node on the network. The default port is 1521. The entry lists the listener name and the port number. For example:

    oraclelistener    1521/tcp

In this example, `oraclelistener` is the name of the listener as defined in the `listener.ora` file. Reserve multiple ports if you intend to start multiple listeners.

If you intend to use Secure Sockets Layer, then you should define a port for TCP/IP with Secure Sockets Layer in the `/etc/services` file. Oracle recommends a value of 2484. For example:

    oraclelistenerssl     2484/tcps

In this example, `oraclelistenerssl` is the name of the listener as defined in the `listener.ora` file. Reserve multiple ports if you intend to start multiple listeners.
