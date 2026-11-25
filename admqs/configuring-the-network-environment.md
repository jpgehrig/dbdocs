After installing Oracle Database, you have a fully functional database with a client/server network environment that has been minimally configured. This chapter helps you configure your client/server network.

These sections help you completely configure your client/server network:

- Understanding Network Configuration

- Viewing Listener Configuration

- Starting and Stopping the Listener

- Connecting to an Oracle Database from a Client Computer

- Configuring the Network Environment: Oracle by Example Series

### 4.1 Understanding Network Configuration

A client is any application that connects to Oracle Database to send or retrieve data. An Oracle Database client application can reside on any computer that has Oracle Database client software installed. Oracle Net is a software layer that resides on the client computer and on the Oracle Database host computer. It establishes and maintains the connection between the client application and the database over a network, and exchanges messages between them using industry standard protocols.

For a client application and a database to communicate, the client application must be able to identify the database it wants to connect to, and the database must provide an identification. You can use a service name to connect to a database. A service name is a logical representation of a database, which is the way a database is presented to clients. A single database can be presented as multiple services.

Service names can provide location transparency so that the client application does not have to know the server's location. If the database is moved to another location, then you must reconfigure only Oracle Net. No changes are necessary to client applications.

This section contains these topics:

- Oracle Net Listener Configuration

- Client Connections

- Tools for Network Configuration

#### 4.1.1 Oracle Net Listener Configuration

On the database host, the Oracle Net listener (the listener), is a process that listens for client connection requests. It receives incoming client connection requests and manages the traffic of these requests to the database server.

The default listener configuration file is called `listener.ora`, and it is located in the `network/admin` subdirectory of the Oracle home directory. For example, if your Oracle home directory is `/u01/app/oracle/product/11.2.0/dbhome_1`, then the `listener.ora` file is created by default in the `/u01/app/oracle/product/11.2.0/dbhome_1/network/admin` directory.

The file contains a protocol address that identifies the database. This address defines the protocol the listener is listening on and any other protocol-specific information. For example, the listener could be configured to listen at the following protocol address:

    (DESCRIPTION=
       (ADDRESS=(PROTOCOL=tcp)(HOST=dbhost.example.com) (PORT=1521)))

This example shows a TCP/IP protocol address that specifies the host computer of the listener and a port number. The listener can listen for connection requests on network interfaces with either IP version 4 (IPv4) or IP version 6 (IPv6) addresses.

The `listener.ora` file is automatically configured during installation.

Because the configuration parameters have default values, you can start and use a listener without configuring it. This default listener is named `LISTENER`, supports no service names on startup, and listens on the following TCP/IP protocol address:

    (ADDRESS=(PROTOCOL=tcp)(HOST=host_name)(PORT=1521))

An Oracle database registers with the listener within a minute or so of starting up. The service names, or the databases that they represent, to which the listener forwards client requests, can be configured in the `listener.ora` file. This information can also be dynamically registered with the listener. Dynamic registration of services and databases with the listener is called service registration.

Service registration is performed by the listener registration (LREG) process—an instance background process—of each database instance. Dynamic service registration does not require modification of the `listener.ora` file.

**See Also:**

- [Oracle Database Concepts](../cncpt/application-and-networking-architecture.md) for more information about listeners and service names

- [Oracle Database Net Services Administrator's Guide](../netag/configuring-and-administering-oracle-net-listener.md) for more information about configuring listeners

- "Viewing Listener Configuration"

- "Starting and Stopping the Listener"

- "[About Background Processes](managing-the-oracle-instance.md)" for more information about database processes

#### 4.1.2 Client Connections

This section describes the elements involved in client connections to the database. For example:

- Connect Descriptors

- Connection Requests

- Naming Methods

##### Connect Descriptors

The client uses a connect descriptor to specify the database to which it wants to connect. This connect descriptor contains a protocol and a database service name. A database can have multiple service names defined, so a specific service name must be specified for the connect descriptor. In a preconfigured database, there is only one service name, which defaults to the global database name.

The following example shows a connect descriptor that enables clients to connect to a database with service name `mydb.us.example.com`:

    DESCRIPTION=
       (ADDRESS=(PROTOCOL=tcp)(HOST=my-server)(PORT=1521))
       (CONNECT_DATA=
          (SERVICE_NAME=mydb.us.example.com))

##### Connection Requests

Users initiate a connection request by providing a connect string. A connect string includes a user name and password, and a connect identifier. This connect identifier can be the connect descriptor itself, or a name that resolves to the connect descriptor using mapping information stored in one or more repositories accessed with the naming methods described in "Naming Methods". This name is referred to as a net service name.

##### Naming Methods

A naming method is a resolution method used by a client application to resolve a connect identifier to a connect descriptor when attempting to connect to a database service.

Oracle Net provides support for the following naming methods:

- Easy Connect Naming

  The easy connect naming method enables clients to connect to an Oracle database by using only a TCP/IP connect string consisting of a host name and service name. The easy connect naming method requires no configuration. See "Connecting to an Oracle Database from a Client Computer" for an example of easy connect naming.

- Local Naming

  The local naming method stores connect descriptors, identified by their net service names, in a client configuration file named `tnsnames.ora`. This file is located in the `ORACLE_HOME``/network/admin` directory. When you create a database using Oracle Database Configuration Assistant (DBCA), local naming is configured automatically. You must then use the Net Configuration Assistant to create connect descriptors and their corresponding net service names.

- Directory Naming

  Directory naming resolves a database service, net service name, or net service alias to a connect descriptor stored in an LDAP-compliant directory server.

**See Also:**

- [Oracle Database Net Services Administrator's Guide](../netag/configuring-naming-methods.md)

- [Oracle Database Administrator’s Guide](../admin/creating-and-configuring-an-oracle-database.md) for more information about database services

#### 4.1.3 Tools for Network Configuration

Oracle Database provides tools to enable you to manage your network configuration. For example:

- Net Configuration Assistant

- Oracle Net Manager

##### Net Configuration Assistant

During a typical database installation, Net Configuration Assistant automatically configures a listener called `LISTENER` that has a TCP/IP listening protocol address for the database. If you do a custom installation, then Net Configuration Assistant prompts you to configure a listener name and protocol address of your choice.

Use Net Configuration Assistant for initial network configuration after database installation. Thereafter, you can use Oracle Net Manager to configure and administer your networks.

##### Oracle Net Manager

Oracle Net Manager provides various network configuration features, including the ability to configure profiles.

**Note:**

On Microsoft Windows operating systems only, if a non-administrator, low privileged Windows User Account was specified as the Oracle Home User during database installation, you are prompted for the Oracle Home User password when you access the Net Configuration Assistant and Oracle Net Manager.

**See Also:**

- "Viewing Listener Configuration"

- [Oracle Database Net Services Administrator's Guide](../netag/managing-oracle-net-services.md)

- [Oracle Database Administrator’s Reference for Microsoft Windows](../ntqrf/supporting-oracle-home-user-on-windows.md) for more information about the Oracle Home Users on Windows feature

### 4.2 Viewing Listener Configuration

The Oracle Net listener (the listener) runs on your database host and handles incoming client requests. You can view the listener status at the command line.

#### To view information about the listener at the command line:

1.  Open a command window.
2.  Follow the steps listed in "[Configuring the Operating System Environment Variables](getting-started-with-database-administration.md)."
3.  Enter the following command:
        lsnrctl status

### 4.3 Starting and Stopping the Listener

The Oracle listener is set to start automatically whenever the host is restarted. However, when your system encounters unforeseen circumstances, or when you have manually stopped the listener, you can restart it at the command line.

#### To start or stop the listener at the command line:

1.  Open a command window.
2.  Follow the steps listed in "[Configuring the Operating System Environment Variables](getting-started-with-database-administration.md)."
3.  Enter either of the following commands, depending on whether you want to start or stop the listener:
        lsnrctl start
        lsnrctl stop

### 4.4 Connecting to an Oracle Database from a Client Computer

This section describes how to use SQL\*Plus and the easy connect naming method to connect to an Oracle database from a client computer. SQL\*Plus is typically installed when you install Oracle Database client software. The easy connect naming method provides TCP/IP connectivity to databases without requiring you to configure Oracle Net Services.

You can use the instructions in this section to test your network configuration.

#### To connect to an Oracle database from a client computer using easy connect naming:

1.  Complete the steps in "[Configuring the Operating System Environment Variables](getting-started-with-database-administration.md)".
2.  Do one of the following to start SQL\*Plus:
    - (UNIX, Linux, or Windows systems) Open a command window and enter the following command:

          sqlplus

    - (Windows systems only) Click Start, select Programs (or All Programs), then Oracle - HOME_NAME, then Application Development, and then SQL\*Plus.
3.  When prompted, enter the user name followed by an at sign (@) and a connect identifier, where the connect identifier has the following format:
        "host[:port][/[service_name][:server][/instance_name]]"

    The place holders used in the connect identifier format represent:

    - `host` — the name or IP address of the Oracle database host computer.

      Both IPv4 and IPv6 addresses are supported. IPv6 addresses must be enclosed in square brackets. See [Oracle Database Net Services Administrator's Guide](../netag/understanding-communication-layers.md) for information about IPv6 addressing.

    - `port` (optional) — the TCP port number on which the Oracle Net listener listens for connections.

      If `port` is excluded, then the standard port number 1521 is assumed.

    - `service_name` — a database service name.

      If no database service names are defined, then you can use the name of the default service that is created for the database. This service name consists of the global database name, which is made up of the `DB_NAME` and `DB_DOMAIN` initialization parameters as follows:

          DB_NAME.DB_DOMAIN

      If `DB_DOMAIN` is null, then the standard service name is just `DB_NAME`.

    - `server` — the type of service handler. Acceptable values are `dedicated`, `shared`, and `pooled`. If omitted, then the default type of server is chosen by the listener: shared server if configured, otherwise dedicated server.

    - `instance_name` — the instance to which to connect. When you specify only instance name, you connect to the default database service. If there is no default service configured in the `listener.ora` file, then an error is generated.You can obtain the instance name from the `INSTANCE_NAME` initialization parameter.

    For example, to connect as user `NICK` to the database service `orcl.example.com` on the host `dbhost.example.com`, enter the following at the user name prompt:

        nick@"dbhost.example.com/orcl.example.com"

    The following examples substitute IPv4 and IPv6 addresses for the host name:

        nick@"192.0.2.1/orcl.example.com"
        nick@"[2001:0DB8:0:0::200C:417A]/orcl.example.com"
4.  When prompted, enter the user password.

**Note:**

Starting with Oracle Database Release 19c, the easy connect naming syntax has been extended. See About Easy Connect Plus for more information.

**See Also:**

- [Oracle Database Administrator’s Guide](../admin/index.md) for more examples of connecting with SQL\*Plus and for a discussion of environment variables

- [Oracle Database Net Services Administrator's Guide](../netag/quick-start-oracle-net-services.md) for information about easy connect, connect identifiers, and other naming methods

- [Oracle Database Net Services Reference](../netrf/index.md) for information about how to define the default service in `listener.ora`

- [SQL\*Plus User's Guide and Reference](../sqpug/configuring-SQL-Plus.md)

#### 4.4.1 About Easy Connect Plus

Starting with Oracle Database Release 19c, the easy connect naming syntax has been extended.

The connect identifier has the following format:

    "[[protocol:]//]host1{,host12}[:port1]{,host2:port2}[/[service_name][:server]
    [/instance_name]][?parameter_name=value{&parameter_name=value}]"

The place holders used in the connect identifier format represent:

- `protocol` — the transport protocol that must be used to connect to the Oracle database host computer. The supported values are `TCP` and `TCPS`. The default value is `TCP`.

- `host1{,host12}[:port1]{,host2:port2}`

  Starting with Oracle Database Release 19c, you can use multiple hosts or ports in the connect identifier. This helps in load balancing the client connections.

  For example, `salesserver1:1521,salesserver2,salesserver3:1522/sales.us.example.com` translates to the following connect descriptor:

      (DESCRIPTION=(LOAD_BALANCE=ON)
              (ADDRESS=(PROTOCOL=tcp)(HOST=salesserver1)(PORT=1521))
              (ADDRESS=(PROTOCOL=tcp)(HOST=salesserver2)(PORT=1522))
              (ADDRESS=(PROTOCOL=tcp)(HOST=salesserver3)(PORT=1522))
          (CONNECT_DATA=(SERVICE_NAME=sales.us.example.com)))

- `parameter_name=value` (optional) — the name-value pairs and their values. The question mark (?) indicates the start of name-value pairs and the ampersand (&) is the delimiter between the name-value pairs.

  For example, `tcps://salesserver1:1521/sales?ssl_server_cert_dn="cn=sales,cn=OracleContext,dc=us,dc=example,dc=com"&wallet_location="\tmp\oracle"` translates to the following:
      (DESCRIPTION=
           (ADDRESS=(PROTOCOL=tcps)(HOST=salesserver1)(PORT=1521))
           (SECURITY=
           (SSL_SERVER_DN_MATCH=TRUE) (MY_WALLET_DIRECTORY=/tmp/oracle)
           (SSL_SERVER_CERT_DN=cn=sales,cn=OracleContext,dc=us,dc=example,dc=com))
           (CONNECT_DATA=(SERVICE_NAME=sales)))

  In addition to `wallet_location` and `ssl_server_cert_dn` name-value pairs, other name-value pairs are also accepted by the connect identifier. See [Oracle Database Net Services Administrator's Guide](../netag/configuring-naming-methods.md) for more information.

For the descriptions of `server`, `service_name`, and `instance_name`, see Connecting to an Oracle Database from a Client Computer.

### 4.5 Configuring the Network Environment: Oracle by Example Series

Oracle By Example (OBE) has a series on the Oracle Database 2 Day DBA guide. This OBE series steps you through the tasks in this chapter and includes annotated screenshots.

The series consists of the following tutorials:

1.  Manage Listener Using the Listener Control Utility

2.  Connect to an Oracle Database from a Client Computer

The above tutorials can be accessed in two ways:

- To see a clickable list of the above tutorials, go to [Configure the Network Environment Series](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/admqs&id=twodaydba_obe_network).

- For seamless navigation through the tutorial series, access the following link:

  [Configure the Network Environment](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/admqs&id=twodaydba_lp_network)

  You can navigate across the tutorials by clicking the \> button at the bottom of the pane.
