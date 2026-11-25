## Glossary

### access control list (ACL)

The group of access directives that you define. The directives grant levels of access to specific data for specific clients or groups of clients.

**Parent topic:** Glossary

### ACL

See access control list (ACL).

**Parent topic:** Glossary

### access control

A feature of Oracle Connection Manager that sets rules for denying or allowing certain clients to access designated servers.

**Parent topic:** Glossary

### address

See protocol address.

**Parent topic:** Glossary

### ADR

See Automatic Diagnostic Repository (ADR).

**Parent topic:** Glossary

### alias

An alternative name for a network object in a server. An alias stores the name of the object it is referencing. When a client requests a lookup of an alias, Oracle completes the lookup as if it is the referenced object.

**Parent topic:** Glossary

### application gateway

A host computer that runs the Oracle Net Firewall Proxy. An application gateway looks and acts like a real server from the client's point of view, and a real client from the server's point of view. An application gateway sits between the Internet and company's internal network and provides middleman services (or proxy services) to users on either side.

**Parent topic:** Glossary

### ASCII character set

American Standard Code for Information Interchange character set, a convention for representing alphanumeric information using digital data. The collation sequence used by most computers with the exception of IBM and IBM-compatible computers.

**Parent topic:** Glossary

### attribute

A piece of information that describes an aspect of a directory entry. An entry comprises a set of attributes, each of which belongs to an object class. Moreover, each attribute has both a type, which describes the kind of information in the attribute, and a value which contains the actual data.

**Parent topic:** Glossary

### authentication method

A security method that enables you to have high confidence in the identity of users, clients, and servers in distributed environments. Network authentication methods can also provide the benefit of single sign-on for users. The following authentication methods are supported:

- Kerberos

- Microsoft Azure Active Directory (Azure AD) user authentication and authorization for Oracle Autonomous Cloud Databases (See [Oracle Database Security Guide](../dbseg/authenticating-and-authorizing-microsoft-entra-id-ms-ei-users-oracle-databases-oracle-exadata.md))

- Microsoft Windows NT native authentication

- Oracle Cloud Infrastructure (OCI) Identity and Access Management (IAM) user authentication and authorization for Oracle Autonomous Cloud Databases (See [Oracle Database Security Guide](../dbseg/authenticating-and-authorizing-iam-users-oracle-dbaas-databases.md))

- RADIUS

- Transport Layer Security (TLS)

**Parent topic:** Glossary

### Automatic Diagnostic Repository (ADR)

Automatic Diagnostic Repository is a systemwide central repository for tracing and logging files. The repository is a file-based hierarchical data store for depositing diagnostic information.

**Parent topic:** Glossary

### cache

Memory that stores recently-accessed data to so that subsequent requests to access the same data can be processed quickly.

**Parent topic:** Glossary

### CIDR

Classless Inter-Domain Routing. In CIDR notation, an IPv6 subnet is denoted by the subnet prefix and the size in bits of the prefix (in decimal), separated by the slash (`/`) character. For example, `2001:0db8:0000:0000::/64` denotes a subnet with addresses `2001:0db8:000:0000:0000:0000:0000:0000` through `2001:0db8:000:0000:FFFF:FFFF:FFFF:FFFF`. The CIDR notation includes support for IPv4 addresses. For example, `192.0.2.1/24` denotes the subnet with addresses `192.0.2.1` through `192.0.2.255`.

**Parent topic:** Glossary

### Classless Inter-Domain Routing (CIDR)

See CIDR.

**Parent topic:** Glossary

### client

A user, software application, or computer that requests the services, data, or processing from another application or computer. The client is the user process. In a network environment, the client is the local user process and the server may be local or remote.

**Parent topic:** Glossary

### client load balancing

Load balancing, whereby if more than one listener services a single database, a client can randomly choose between the listeners for its connect requests. This randomization enables all listeners to share the burden of servicing incoming connect requests.

**Parent topic:** Glossary

### client profile

The properties of a client, which may include the preferred order of naming methods, client and server logging and tracing, the domain from which to request names, and other client options.

**Parent topic:** Glossary

### client/server architecture

Software architecture based on a separation of processing between two CPUs. One CPU acts as the client in the transaction, requesting and receiving services. The other acts as the server that provides service for the requests.

**Parent topic:** Glossary

### cman.ora file

An Oracle Connection Manager configuration file that specifies protocol addresses for incoming requests and administrative commands, as well as Oracle Connection Manager parameters and access control rules.

**Parent topic:** Glossary

### CMADMIN (Connection Manager Administration)

An Oracle Connection Manager process that monitors the health of the listener and Oracle Connection Manager gateway processes, shutting down and starting processes as needed. CMADMIN registers information about gateway processes with the listener and processes commands run with the Oracle Connection Manager Control utility.

**Parent topic:** Glossary

### CMGW (Connection Manager gateway)

An Oracle Connection Manager process that receives client connections screened and forwarded by the listener located at the Oracle Connection Manager instance. The gateway process forwards the requests to the database server. In addition, it can multiplex or process multiple client connections through a single protocol connection.

**Parent topic:** Glossary

### connect data

A portion of the connect descriptor that defines the destination database service name or Oracle system identifier (SID). In the following example, `SERVICE_NAME` defines a database service called `sales.us.example.com`:

    (DESCRIPTION=
      (ADDRESS=(PROTOCOL=tcp)(HOST=sales-server)(PORT=1521)
      (CONNECT_DATA=
         (SERVICE_NAME=sales.us.example.com)))

**Parent topic:** Glossary

### connect descriptor

A specially-formatted description of the destination for a network connection. A connect descriptor contains destination service and network route information.

The destination service is indicated by using its service name. The network route provides, at a minimum, the location of the listener through use of a network address.

**Parent topic:** Glossary

### connect identifier

A connect descriptor or a name that maps to a connect descriptor. A connect identifier can be a network service name, database service name, or network service alias. Users initiate a connect request by passing a user name and password along with a connect identifier in a connect string for the service to which they want to connect:

    CONNECT username@connect_identifier

**Parent topic:** Glossary

### connect string

Information the user passes to a service to connect, such as user name, and connect identifier:

    CONNECT username@net_service_name

**Parent topic:** Glossary

### connect-time failover

A client connect request is forwarded to a another listener if a listener is not responding. Connect-time failover is enabled by service registration, because the listener knows if an instance is running to attempt a connection.

**Parent topic:** Glossary

### connection

An interaction between two processes on a network. Connections are originated by an initiator (client) that requests a connection with a destination (server).

**Parent topic:** Glossary

### connection load balancing

The method for balancing the number of active connections for the same service across the instances and dispatchers. Connection load balancing enables listeners to make routing decisions based on how many connections for each dispatcher and the load on the nodes.

**Parent topic:** Glossary

### connection pooling

A resource utilization and user scalability feature used to maximize the number of sessions over a limited number of protocol connections to a shared server.

**Parent topic:** Glossary

### connection request

A notification sent by an initiator and received by a listener that indicates that the initiator wants to start a connection.

**Parent topic:** Glossary

### data packet

See packet.

**Parent topic:** Glossary

### database link

A pointer that defines a one-way communication path from an Oracle database server to another database server. Public and private database links are a defined entries in a data dictionary table. Global database links are stored in an LDAP directory and can be accessed by all users on the network. To access public and private links, the user must be connected to the local database that contains the data dictionary entry.

A client connected to local database A can use a public or private link stored in database A to access information in remote database B. However, users connected to database B cannot use the same link to access data in database A. If local users on database B want to access data on database A, then a link must be defined and stored in the data dictionary of database B. Global links may be used between any clients and database on the network.

The following database links are supported:

- A private database link in a specific schema of a database. Only the owner of a private database link can use it.

- A public database link for a database. All users in the database can use it.

- A global database link is a database link stored in the LDAP directory.

**Parent topic:** Glossary

### dedicated connection

A dedicated server with a database session.

**Parent topic:** Glossary

### dedicated server

A server process that is dedicated to one client connection. Contrast with shared server.

**Parent topic:** Glossary

### default domain

The domain within which most client requests take place. It could be the domain where the client resides, or it could be a domain from which the client requests network services often. Default domain is also the client configuration parameter that determines what domain should be appended to unqualified network name requests. A name request is unqualified if it does not have a period (.) character within it.

**Parent topic:** Glossary

### directory information tree (DIT)

A hierarchical tree-like structure in a directory server of the distinguished names (DNs) of the entries. This structure is specific to x500 and LDAP.

**Parent topic:** Glossary

### directory naming

A naming method that resolves a database service, network service name, or network service alias to a connect descriptor stored in a central directory server. A directory server provides central administration of directory naming objects, reducing the work effort associated with adding or relocating services.

**Parent topic:** Glossary

### directory server

A directory server that is accessed with the Lightweight Directory Access Protocol (LDAP). Support of LDAP-compliant directory servers provides a centralized method for managing and configuring a distributed Oracle network. The directory server can replace client-side and server-side localized `tnsnames.ora` files.

**Parent topic:** Glossary

### dispatcher

A process that enables many clients to connect to the same server without the need for a dedicated server process for each client. A dispatcher handles and directs multiple incoming network session requests to shared server processes.

**Parent topic:** Glossary

### distinguished name (DN)

Name of entry in a directory server. The DN specifies where the entry resides in the LDAP directory hierarchy, similar to the way a directory path specifies the exact location of a file.

**Parent topic:** Glossary

### distributed processing

Division of front-end and back-end processing to different computers. Oracle Net Services supports distributed processing by transparently connecting applications to remote databases.

**Parent topic:** Glossary

### domain

Any tree or subtree within the Domain Name System (DNS) namespace. Domain most commonly refers to a group of computers whose host names share a common suffix, the domain name.

**Parent topic:** Glossary

### Domain Name System (DNS)

A system for naming computers and network services that is organized into a hierarchy of domains. DNS is used in TCP/IP networks to locate computers through user-friendly names. DNS resolves a friendly name into an IP address, which is understood by computers.

For Oracle Net Services, DNS translates the host name in a TCP/IP address into an IP address.

**Parent topic:** Glossary

### DNS

See Domain Name System (DNS).

**Parent topic:** Glossary

### enterprise role

An enterprise role is analogous to a regular database role, except that it spans authorization on multiple databases. An enterprise role is a category of roles that define privileges on a particular database. An enterprise role is created by the database administrator of a particular database. An enterprise role can be granted to or revoked from one or more enterprise users. The information for granting and revoking these roles is stored in the directory server.

**Parent topic:** Glossary

### enterprise user

A user that has a unique identity across an enterprise. Enterprise users connect to individual databases through a schema. Enterprise users are assigned enterprise roles that determine their access privileges on databases.

**Parent topic:** Glossary

### entry

The building block of a directory server, it contains information about an object of interest to directory users.

**Parent topic:** Glossary

### external naming

A naming method that uses a third-party naming service, such as Network Information Service (NIS).

**Parent topic:** Glossary

### external procedure

Function or procedure written in a third-generation language (3GL) that can be called from PL/SQL code. Only C is supported for external procedures.

**Parent topic:** Glossary

### failover

See connect-time failover.

**Parent topic:** Glossary

### firewall support

See access control.

**Parent topic:** Glossary

### FTP

File Transfer Protocol. A client/server protocol which allows a user on one computer to transfer files to and from another computer over a TCP/IP network.

**Parent topic:** Glossary

### global database link

A database link definition stored in an LDAP directory which can be accessed by all users on the network. This definition is the same as the one used for client connections to the database (name/connect-descriptor).

Global database links cannot include user or password clauses. They only work when the database initiating the link uses the identity of the existing client to establish the link.

**Parent topic:** Glossary

### global database name

The full name of the database which uniquely identifies it from any other database. The global database name is of the form "`database_name``.``database_domain`," for example, `sales.us.example.com`.

The database name portion, `sales`, is a simple name to call a database. The database domain portion, `us.example.com`, specifies the database domain which the database is located, making the global database name unique. When possible, Oracle recommends that your database domain mirror the network domain.

The global database name is the default service name of the database, as specified by the `SERVICE_NAMES` parameter in the initialization parameter file.

**Parent topic:** Glossary

### Heterogeneous Services

An integrated component that provides the generic technology for accessing non-Oracle systems from the Oracle database server. Heterogeneous Services enables you to:

- Use Oracle SQL to transparently access data stored in non-Oracle systems as if the data resides within an Oracle server.

- Use Oracle procedure calls to transparently access non-Oracle systems, services, or application programming interfaces (APIs), from your Oracle distributed environment.

**Parent topic:** Glossary

### hierarchical naming model

An infrastructure in which names are divided into multiple hierarchically-related domains.

**Parent topic:** Glossary

### host naming

A naming method resolution that enables users in a TCP/IP environment to resolve names through their existing name resolution service. This name resolution service might be Domain Name System (DNS), Network Information Service (NIS), or simply a centrally-maintained set of `/etc/hosts` files. Host naming enables users to connect to an Oracle database server by simply providing the server computer's host name or host name alias. No client configuration is required to take advantage of this feature. This method is recommended for simple TCP/IP environments.

**Parent topic:** Glossary

### HTTP

Hypertext Transfer Protocol. A protocol that provides the language that enables Web browsers and application Web servers to communicate.

**Parent topic:** Glossary

### identity management realm

A collection of identities, all of which are governed by the same administrative policies. In an enterprise, all employees having access to the intranet may belong to one realm, while all external users who access the public applications of the enterprise may belong to another realm. An identity management realm is represented in the directory by a specific entry with a special object class associated with it.

**Parent topic:** Glossary

### instance

The combination of the System Global Area (SGA) and the Oracle background processes. When a database is started on a database server (regardless of the type of computer), Oracle allocates a memory area called the SGA, and starts one or more Oracle processes. The memory and processes of an instance efficiently manage the associated database data and serve the database users. You can connect to any instance to access information within a cluster database.

**Parent topic:** Glossary

### instance name

A name of an Oracle database instance. The instance name is identified by the INSTANCE_NAME parameter in the database initialization parameter file. INSTANCE_NAME corresponds to the Oracle system identifier (SID) of the instance. Clients can connect to a specific instance by specifying the INSTANCE_NAME parameter in the connect descriptor.

The instance name is included in the connect data part of the connect descriptor.

**Parent topic:** Glossary

### IP address

Used to identify a node on a network. Each computer on the network is assigned a unique Internet Protocol (IP) address, which is made up of the network ID, and a unique host ID. This address is typically represented in dotted-decimal notation, with the decimal value of each octet separated by a period, for example `192.0.2.22`.

**Parent topic:** Glossary

### IPC

Interprocess Communication is a protocol used by client applications that resides on the same node as the listener to communicate with the database. IPC can provide a faster local connection than TCP/IP.

**Parent topic:** Glossary

### IPv4

Internet Protocol Version 4. IPv4 is the current standard for the IP protocol. IPv4 uses 32-bit (four-byte) addresses, which are typically represented in dotted-decimal notation. The decimal value of each octet is separated by a period, as in `192.0.2.22`.

**Parent topic:** Glossary

### IPv6

Internet Protocol Version 6. The protocol designed to replace IPv4. In IPv6, an IP address is typically represented in eight fields of hexadecimal values separated by colons, as in `2001:0db8:0000:0000:0000:0000:1428:57AB`. In some cases, fields with `0` values can be compressed, as in `2001:DB8::1428:57AB`.

**Parent topic:** Glossary

### IP Version 4 (IPv4)

See IPv4.

**Parent topic:** Glossary

### IP Version 6 (IPv6)

See IPv6.

**Parent topic:** Glossary

### Java Database Connectivity (JDBC) Driver

A driver that provides Java applications and applets access to an Oracle database.

**Parent topic:** Glossary

### JDBC OCI Driver

A Type II driver for use with client/server Java applications. This driver requires an Oracle client installation.

**Parent topic:** Glossary

### JDBC Thin Driver

A Type IV driver for Oracle JDBC applets and applications. Because it is written entirely in Java, this driver is platform-independent. It does not require any additional Oracle software on the client side. The Thin driver communicates with the server using Two-Task Common (TTC), a protocol developed by Oracle to access the database server.

**Parent topic:** Glossary

### Kerberos

A network authentication service that strengthens security in distributed environments. Kerberos is a trusted third-party authentication system that relies on shared secrets and assumes that the third party is secure. It provides single sign-on capabilities and database link authentication (MIT Kerberos only) for users, provides centralized password storage, and enhances PC security.

**Parent topic:** Glossary

### keyword-value pair

The combination of a keyword and a value, used as the standard unit of information in connect descriptors and many configuration files. Keyword-value pairs may be nested; that is, a keyword may have another keyword-value pair as its value.

**Parent topic:** Glossary

### latency

The amount of time it takes to send a request and receive an answer.

**Parent topic:** Glossary

### LDAP Data Interchange Format (LDIF)

See LDIF

**Parent topic:** Glossary

### ldap.ora file

A file created by Oracle Internet Directory Configuration Assistant or Oracle Net Configuration Assistant that contains the following directory server access information:

- Type of directory server

- Location of the directory server

- Default Oracle Context that the client or server use to look up or configure connect identifiers for connections to database services

When created with Oracle Internet Directory Configuration Assistant, the `ldap.ora` file is located in the `ORACLE_HOME/ldap/admin` directory. When created with Oracle Net Configuration Assistant, the `ldap.ora` file is located in the `ORACLE_HOME/network/admin` directory.

**Parent topic:** Glossary

### LDIF

LDAP Data Interchange Format (LDIF) is the set of standards for formatting an input file for any of the LDAP command line utilities.

**Parent topic:** Glossary

### Lightweight Directory Access Protocol (LDAP)

A standard, extensible directory access protocol. It is a common language that LDAP clients and servers use to communicate. The framework of design conventions supporting industry-standard directory servers.

**Parent topic:** Glossary

### link qualifier

An extension to the database link name which specifies the connect name used to connect to the database. It provides alternate settings for the database user name and password credentials. For example, a link qualifier of `fieldrep` can be appended to a global database link of `sales.us.example.com`.

    SQL> SELECT * FROM emp@sales.us.example.com@fieldrep

**Parent topic:** Glossary

### listener

See Oracle Net Listener.

**Parent topic:** Glossary

### Listener Control utility

A utility included with Oracle Net Services to control listener functions, such as starting, stopping, and getting the status of the listener.

**Parent topic:** Glossary

### listener.ora file

A configuration file for the listener that identifies the following for a listener:

- Unique name

- Protocol addresses that it is accepting connection requests on

- Services it is listening for

The `listener.ora` file typically resides in the `ORACLE_HOME/network/admin` directory.

Oracle does not require identification of the database service because of service registration. However, static service configuration is required if you plan to use Oracle Enterprise Manager Cloud Control.

**Parent topic:** Glossary

### Listener Registration (LREG)

As a part of service registration, LREG registers instance information with the listener. LREG is an instance background process of each database instance that is configured in the database initialization parameter file.

**Parent topic:** Glossary

### load balancing

A feature by which client connections are distributed evenly among multiple listeners, dispatchers, instances, and nodes so that no single component is overloaded.

Oracle Net Services support client load balancing and connection load balancing.

**Parent topic:** Glossary

### local naming

A naming method that locates network addresses by using information configured and stored on each individual client's tnsnames.ora file. Local naming is most appropriate for simple distributed networks with a small number of services that change infrequently.

**Parent topic:** Glossary

### location transparency

A distributed database characteristic that enables applications to access data tables without knowing where they reside. All data tables appear to be in a single database, and the system determines the actual data location based on the table name. The user can reference data on multiple nodes in a single statement, and the system automatically and transparently routes (parts of) SQL statements to remote nodes for execution if needed. The data can move among nodes with no impact on the user or application.

**Parent topic:** Glossary

### logging

A feature in which errors, service activity, and statistics are written to a log file. The log file provides additional information for an administrator when the error message on the screen is inadequate to understand the failure. The log file, by way of the error stack, shows the state of the software at various layers.

See also tracing.

**Parent topic:** Glossary

### loopback test

A connection from the server back to itself. Performing a successful loopback verifies that Oracle Net is functioning on the database server.

**Parent topic:** Glossary

### map

Files used by the Network Information Service (NIS) ypserv program to handle name requests.

**Parent topic:** Glossary

### Microsoft Active Directory

An LDAP-compliant directory server included with Microsoft Windows 2000 Server. It stores information about objects on the network, and makes this information available to users and network administrators. Active Directory also provides access to resources on the network using a single logon process.

Microsoft Active Directory can be configured as a directory naming method to store service information that clients can access.

**Parent topic:** Glossary

### Microsoft Windows NT native authentication

An authentication method that enables a client single login access to a Microsoft Windows NT server and a database running on the server.

**Parent topic:** Glossary

### Named Pipes protocol

A high-level interface protocol providing interprocess communications between clients and servers using distributed applications. Named Pipes enables client/server conversation over a network using Named Pipes protocol.

**Parent topic:** Glossary

### naming context

A subtree that resides entirely on one directory server. It is a contiguous subtree, that is, it must begin at an entry that serves as the top of the subtree, and extend downward to either leaf entries or references to subordinate naming contexts. It can range in size from a single entry to the entire directory information tree (DIT).

Oracle Context can be created under a naming context.

**Parent topic:** Glossary

### naming method

The resolution method used by a client application to resolve a connect identifier to a connect descriptor when attempting to connect to a database service. Oracle Net provides four naming methods:

- Domain Name System (DNS)

- directory naming

- Easy Connect naming

- external naming

**Parent topic:** Glossary

### network service alias

An alternative name for a directory naming object in a directory server. A directory server stores network service aliases for any defined network service name or database service. A network service alias entry does not have connect descriptor information. Instead, it only references the location of the object for which it is an alias. When a client requests a directory lookup of a network service alias, the directory determines that the entry is a network service alias and completes the lookup as if it was actually the entry it is referencing.

**Parent topic:** Glossary

### network service name

A simple name for a service that resolves to a connect descriptor. Users initiate a connect request by passing a user name and password along with a network service name in a connect string for the service to which they want to connect:

    CONNECT username/password@net_service_name

Depending on your needs, network service names can be stored in a variety of places, including:

- Local configuration file, `tnsnames.ora`, on each client

- Directory server

- External naming service, such as NIS

**Parent topic:** Glossary

### network

A group of two or more computers linked through hardware and software to allow the sharing of data and peripherals.

**Parent topic:** Glossary

### network administrator

The person who performs network management tasks such as installing, configuring, and testing network components. The administrator typically maintains the configuration files, connect descriptors and service names, aliases, and public and global database links.

**Parent topic:** Glossary

### network character set

As defined by Oracle, the set of characters acceptable for use as values in keyword-value pairs (that is, in connect descriptors and configuration files). The set includes alphanumeric uppercase, and lowercase, and some special characters.

**Parent topic:** Glossary

### Network Information Service (NIS)

The client/server protocol for distributing system configuration data such as user and host names between computers on a network. This service was formerly known as "Sun Microsystems Yellow Pages (yp)."

**Parent topic:** Glossary

### Network Interface (NI)

A network layer that provides a generic interface for Oracle clients, servers, or external processes to access Oracle Net functions. The network interface layer handles the break and reset requests for a connection.

**Parent topic:** Glossary

### network listener

See listener.

**Parent topic:** Glossary

### network object

Any service that can be directly addressed on a network, such as a listener.

**Parent topic:** Glossary

### network protocol

See Oracle protocol support.

**Parent topic:** Glossary

### Network Program Interface

An interface for server-to-server interactions that performs all of the functions that the Oracle Call Interface (OCI) does for clients, allowing a coordinating server to construct SQL requests for additional servers.

**Parent topic:** Glossary

### Network Session (NS)

A session layer that is used in typical Oracle Net connections to establish and maintain the connection between a client application and a database server.

**Parent topic:** Glossary

### NIS

See Network Information Service (NIS).

**Parent topic:** Glossary

### node

A computer or terminal that is part of a network

**Parent topic:** Glossary

### object class

In a directory server, a named group of attributes. To assign attributes to an entry, do so by assigning the object classes that hold those attributes to that entry.

All objects associated with the same object class share the attributes of that object class.

**Parent topic:** Glossary

### OCI

See Oracle Call Interface (OCI).

**Parent topic:** Glossary

### OPI

See Oracle Program Interface (OPI).

**Parent topic:** Glossary

### Open Systems Interconnection (OSI)

Open Systems Interconnection is a network architecture model developed by ISO as a framework for international standards in heterogeneous computer network architecture.

The OSI architecture has seven layers, from lowest to highest:

1.  Physical layer

2.  Data link layer

3.  Network layer

4.  Transport layer

5.  Session layer

6.  Presentation layer

7.  Application layer

**Parent topic:** Glossary

### Oracle Advanced Security

An Oracle product that provides Transparent Data Encryption (TDE) and data redaction.

**Parent topic:** Glossary

### Oracle Call Interface (OCI)

An application programming interface (API) that enables creation of applications that use the native procedures or function calls of a third-generation language to access an Oracle database server and control all phases of SQL statement execution. OCI supports the data types, calling conventions, syntax, and semantics of a number of third-generation languages including C, C++, COBOL and FORTRAN.

**Parent topic:** Glossary

### Oracle Connection Manager

A router through which a client connection request may be sent either to its next hop or directly to the database server. Clients who route their connection requests through Oracle Connection Manager can then take advantage of the session multiplexing, access control, or protocol conversion features configured for that Oracle Connection Manager.

**Parent topic:** Glossary

### Oracle Connection Manager Control utility

A utility included with Oracle Net Services to control various functions, such as starting, stopping, and getting the status of Oracle Connection Manager.

**Parent topic:** Glossary

### Oracle Context

An entry in an LDAP-compliant Internet directory called `cn=OracleContext`, under which all Oracle software relevant information is kept, including entries for Oracle Net Services directory naming and checksumming security. There may be one or more than one Oracle Context in a directory. An Oracle Context entry can be associated with a directory naming context.

Oracle Internet Directory automatically creates an Oracle Context at the root of the DIT structure. This root Oracle Context has a DN of `dn:cn=OracleContext`.

**Parent topic:** Glossary

### Oracle Enterprise Manager Cloud Control

A separate Oracle product that combines a graphical console, agents, common services, and tools to provide an integrated and comprehensive systems management platform for managing Oracle products.

**Parent topic:** Glossary

### Oracle Identity Management

An infrastructure enabling deployments to manage centrally and securely all enterprise identities and their access to various applications in the enterprise.

**Parent topic:** Glossary

### Oracle Internet Directory

A directory server implemented as an application on the Oracle database. It enables retrieval of information about dispersed users and network resources. It combines Lightweight Directory Access Protocol (LDAP) Version 3, the open Internet standard directory server access protocol, with the high performance, scalability, robustness, and availability of the Oracle database.

**Parent topic:** Glossary

### Oracle Net

Communication software that enables a network session from a client application to an Oracle database server. After a network session is established, Oracle Net acts as a data courier for the client application and the database server. It is responsible for establishing and maintaining the connection between the client application and database server, as well as exchanging messages between them. Oracle Net can perform these jobs because it is located on each computer in the network.

**Parent topic:** Glossary

### Oracle Net Configuration Assistant

A postinstallation tool that configures basic network components after installation, including:

- Listener names and protocol addresses

- Naming methods the client uses to resolve connect identifiers

- Net service names in a `tnsnames.ora` file

- Directory server usage

**Parent topic:** Glossary

### Oracle Net Firewall Proxy

Product offered by some firewall vendors that supplies Oracle Connection Manager functionality.

**Parent topic:** Glossary

### Oracle Net foundation layer

A networking communication layer that is responsible for establishing and maintaining the connection between the client application and server, as well as exchanging messages between them.

**Parent topic:** Glossary

### Oracle Net Listener

A process that resides on the server whose responsibility is to listen for incoming client connection requests and manage the traffic to the server.

When a client requests a network session with a database server, a listener receives the actual request. If the client information matches the listener information, then the listener grants a connection to the database server.

**Parent topic:** Glossary

### Oracle Net Manager

A tool that combines configuration abilities with component control to provide an integrated environment for configuring and managing Oracle Net Services.

You can use Oracle Net Manager to configure the following network components:

- Naming

  Define connect identifiers and map them to connect descriptors to identify the network location and identification of a service. Oracle Net Manager supports configuration of connect descriptors in a local `tnsnames.ora` file or directory server.

- Naming Methods

  Configure the ways in which connect identifiers are resolved into connect descriptors.

- Listeners

  Create and configure listeners to receive client connections.

**Parent topic:** Glossary

### Oracle Net Services

A suite of networking components that provide enterprise-wide connectivity solutions in distributed, heterogeneous computing environments. Oracle Net Services is comprised of Oracle Net, listener, Oracle Connection Manager, Oracle Net Configuration Assistant, and Oracle Net Manager.

**Parent topic:** Glossary

### Oracle Program Interface (OPI)

Oracle Program Interface is the networking layer responsible for responding to each of the possible messages sent by OCI. For example, an OCI request to fetch 25 rows would have an OPI response to return the 25 rows after they have been fetched.

**Parent topic:** Glossary

### Oracle protocol support

A software layer responsible for mapping Transparent Network Substrate (TNS) functionality to industry-standard protocols used in the client/server connection.

**Parent topic:** Glossary

### Oracle Real Application Clusters (Oracle RAC)

An architecture that allows multiple instances to access a shared database of data files. Oracle RAC is also a software component that provides the necessary cluster database scripts, initialization files, and data files needed for Oracle Enterprise Edition and Oracle RAC.

**Parent topic:** Glossary

### Oracle Rdb

A database for Digital's 64-bit platforms. Because Oracle Rdb has its own listener, the client interacts with Rdb in the same manner as it does with an Oracle database.

**Parent topic:** Glossary

### Oracle schema

A set of rules that determine what can be stored in a directory server. Oracle has its own schema that is applied to many types of Oracle entries, including Oracle Net Services entries. The Oracle schema for Oracle Net Services entries includes the attributes the entries may contain.

**Parent topic:** Glossary

### Oracle system identifier (SID)

A name that identifies a specific instance of an Oracle database. For any database, there is at least one instance referencing the database.

For Oracle databases earlier than release 8.1, a SID is used to identify the database. The SID is included in the connect descriptor of a tnsnames.ora file and in the definition of the listener in the listener.ora file.

**Parent topic:** Glossary

### Oracle XML DB

A high-performance XML storage and retrieval technology provided with Oracle database server. It is based on the W3C XML data model.

**Parent topic:** Glossary

### ORACLE_HOME

An alternate name for the top directory in the Oracle directory hierarchy on some directory-based operating systems.

**Parent topic:** Glossary

### OSI

See Open Systems Interconnection (OSI).

**Parent topic:** Glossary

### packet

A block of information sent over the network each time a connection or data transfer is requested. The information contained in packets depends on the type of packet, such as connect, accept, redirect, data, and so on. Packet information can be useful in troubleshooting.

**Parent topic:** Glossary

### PMON process

A process monitor (PMON) database process that performs process recovery when a user process fails. PMON is responsible for cleaning the cache and freeing resources that the process was using. PMON also checks on dispatcher and server processes and restarts them if they have failed.

**Parent topic:** Glossary

### SHOW

#### Purpose

To display a list of parameters that may be used as arguments for this command. Entering one of these parameters with the command displays the parameter value or values.

#### Prerequisites

None

#### Syntax

From the operating system:

    cmctl SHOW [-c instance_name]

From the Oracle Connection Manager Control utility:

    CMCTL> SHOW

#### Example

    CMCTL> SHOW
    The following operations are available after show
    An asterisk (*) denotes a modifier or extended command:

    all             gateways        status
    connections     parameters      version
    defaults        rules
    events          services

- TRACE_UNIQUE_CLIENT

**Parent topic:** Glossary

#### TRACE_UNIQUE_CLIENT

##### Purpose

To specify whether a unique trace file is created for each client trace session.

##### Usage Notes

When the value is set to `on`, a process identifier is appended to the name of each trace file, enabling several files to coexist. For example, trace files named `sqlnet``pid``.trc` are created if default trace file name `sqlnet.trc` is used. When the value is set to `off`, data from a new client trace session overwrites the existing file. Use this parameter when ADR is not enabled.

##### Default

on

##### Values

`on` or `off`

##### Example

    TRACE_UNIQUE_CLIENT=on

**Parent topic:** SHOW

### presentation layer

A networking communication layer that manages the representation of information that application layer entities either communicate or reference in their communication. Two-Task Common (TTC) is an example of presentation layer.

**Parent topic:** Glossary

### private database link

A database link created by one user for exclusive use.

See also database link and public database link.

**Parent topic:** Glossary

### profile

A collection of parameters that specifies preferences for enabling and configuring Oracle Net Services features on the client or server. A profile is stored and implemented through the `sqlnet.ora` file.

**Parent topic:** Glossary

### protocol

A set of rules that defines how data is transported across the network.

**Parent topic:** Glossary

### protocol address

An address that identifies the network address of a network object.

When a connection is made, the client and the receiver of the request, such as the listener or Oracle Connection Manager, are configured with identical protocol addresses. The client uses this address to send the connection request to a particular network object location, and the recipient listens for requests on this address. It is important to install the same protocols for the client and the connection recipient, as well as configure the same addresses.

**Parent topic:** Glossary

### protocol conversion

A feature of Oracle Connection Manager that enables a client and server with different networking protocols to communicate with each other. This feature replaces functionality previously provided by the Oracle Multi-Protocol Interchange with SQL\*Net version 2.

**Parent topic:** Glossary

### protocol stack

Designates a particular presentation layer and session layer combination.

**Parent topic:** Glossary

### SQLNET.RADIUS_ALTERNATE_RETRIES

#### Purpose

To specify the number of times the database server should resend messages to the alternate RADIUS server.

#### Default

3

#### Example

    SQLNET.RADIUS_ALTERNATE_RETRIES=4

**See Also:**

[Oracle Database Security Guide](../dbseg/kerberos-ssl-and-radius-authentication-parameters.md)

**Parent topic:** Glossary

### proxy server

A server that substitutes for a real server, forwarding client connection requests to the real server or to other proxy servers. Proxy servers provide access control, data and system security, monitoring, and caching.

**Parent topic:** Glossary

### public database link

A database link created by a DBA on a local database that is accessible to all users on that database.

See also database link and private database link.

**Parent topic:** Glossary

### RADIUS

Remote Authentication Dial-In User Service (RADIUS) is a client-server protocol and software that enables remote access servers to communicate with a central server. This helps in authenticating dial-in users and authorizing their access to the requested system or service.

**Parent topic:** Glossary

### realm Oracle Context

An Oracle Context contained in each identity management realm. It stores the following information:

- User naming policy of the identity management realm, that is, how users are named and located

- Mandatory authentication attributes

- Location of groups in the identity management realm

- Privilege assignments for the identity management realm, for example, who has privileges to add more users to the realm

- Application specific data for that realm including authorizations

**Parent topic:** Glossary

### RDBMS

Relational Database Management System.

**Parent topic:** Glossary

### RDN

See relative distinguished name (RDN).

**Parent topic:** Glossary

### relative distinguished name (RDN)

The local, most granular level entry name. It has no other qualifying entry names that would serve to address the entry uniquely. It is a fully-qualified X.500 name. For example, `cn=sales,dc=us,dc=example,dc=com`, `cn=sales` is a RDN.

**Parent topic:** Glossary

### root Oracle Context

In the Oracle Identity Management infrastructure, the root Oracle Context is an entry in Oracle Net Services containing a pointer to the default identity management realm in the infrastructure. It also contains information about how to locate an identity management realm given the simple name of the realm.

**Parent topic:** Glossary

### RPC

Remote procedure call.

**Parent topic:** Glossary

### SDP

Sockets Direct Protocol.

**Parent topic:** Glossary

### Secure Sockets Layer (SSL)

An industry standard protocol for securing network connections. SSL provides authentication, encryption, and data integrity using public key infrastructure (PKI). The Transport Layer Security (TLS) protocol is a successor to the SSL protocol.

See [The Difference Between Transport Layer Security and Secure Sockets Layer](../dbseg/configuring-secure-sockets-layer-authentication.md).

**Parent topic:** Glossary

### server parameter file

A binary file containing initialization parameter settings that is maintained on the Oracle Database host. You cannot manually edit this file with a text editor. A server parameter file is initially built from a text initialization parameter file by means of the `CREATE SPFILE` statement or created directly.

**Parent topic:** Glossary

### server process

Database processes that handle a client request on behalf of a database.

**Parent topic:** Glossary

### service

A program that responds to requests from various clients or performs some operation. The database is a service that stores and retrieves data for clients.

**Parent topic:** Glossary

### service handler

A process that acts a connection point from the listener to the database server. A service handler can be a dispatcher or dedicated server.

**Parent topic:** Glossary

### service name

A logical representation of a database, which is the way a database is presented to clients. The service name is a string that is the global database name, that is, a name comprised of the database name and domain name, entered during installation or database creation. If you are not sure what the global database name is, then you can obtain it from the value of the SERVICE_NAMES parameter in the initialization parameter file.

The service name is included in the connect data part of the connect descriptor.

**Parent topic:** Glossary

### service registration

A feature by which the Listener Registration (LREG) automatically registers information with a listener. Because this information is registered with the listener, the `listener.ora` file does not need to be configured with this static information.

Service registration provides the listener with information about:

- Service names for each running instance of the database

- Instance names of the database

- Service handlers (dispatcher or dedicated server) available for each instance

  These enable the listener to direct a client request appropriately.

- Dispatcher, instance, and node load information

This load information enables the listener to determine which dispatcher can best handle a client connection request. If all dispatchers are blocked, then the listener can spawn a dedicated server for the connection.

**Parent topic:** Glossary

### session data unit (SDU)

A buffer that Oracle Net uses to place data before transmitting it across the network. Oracle Net sends the data in the buffer either when requested or when it is full.

**Parent topic:** Glossary

### session layer

A network layer that provides the services needed by the protocol address entities that enable them to organize and synchronize their dialog and manage their data exchange. This layer establishes, manages, and terminates network sessions between the client and server. An example of a session layer is Network Session (NS).

**Parent topic:** Glossary

### session multiplexing

Combining multiple sessions for transmission over a single network connection to conserve the operating system's resources.

**Parent topic:** Glossary

### shared server

A database server that is configured to allow many user processes to share very few server processes, so the number of users that can be supported is increased. With shared server configuration, many user processes connect to a dispatcher. The dispatcher directs multiple incoming network session requests to a common queue. An idle shared server process from a shared pool of server processes picks up a request from the queue. This means that a small pool of server processes can serve a large number of clients. Contrast with dedicated server.

**Parent topic:** Glossary

### shared server process

A process type used with shared server configuration.

**Parent topic:** Glossary

### SID

See Oracle system identifier (SID).

**Parent topic:** Glossary

### SID_LIST\_listener_name

A section of the `listener.ora` file that defines the Oracle system identifier (SID) of the database served by the listener. This section is valid only for Oracle databases release 8.0, as information for Oracle8i or later instances is automatically registered with the listener. Static configuration is also required for other services, such as external procedure calls and Heterogeneous Services.

**Parent topic:** Glossary

### single sign-on

The ability for a user to log in to different servers using a single password. This permits the user to authenticate to all servers the user is authorized to access.

**Parent topic:** Glossary

### sqlnet.ora file

A configuration file for the client or server that specifies:

- Client domain to append to unqualified service names or net service names

- Order of naming methods the client should use when resolving a name

- Logging and tracing features to use

- Route of connections

- External naming parameters

- Oracle Advanced Security parameters

The `sqlnet.ora` file typically resides in the `ORACLE_HOME/network/admin` directory.

**Parent topic:** Glossary

### SSL

See Secure Sockets Layer (SSL).

**Parent topic:** Glossary

### System Global Area (SGA)

A group of shared memory structures that contain data and control information for an Oracle instance.

**Parent topic:** Glossary

### TCP/IP

Transmission Control Protocol/Internet Protocol. The standard communication protocol used for client/server conversation over a network.

**Parent topic:** Glossary

### TCP/IP with TLS protocol

A protocol that enables an Oracle application on a client to communicate with remote Oracle databases through the TCP/IP and Transport Layer Security (TLS).

**Parent topic:** Glossary

### tick

The amount of time it takes for a message to be sent and processed from the client to the server or from the server to the client.

**Parent topic:** Glossary

### TNS

See Transparent Network Substrate (TNS).

**Parent topic:** Glossary

### tnsnames.ora file

A configuration file that maps network service names to connect descriptors. This file is used for the local naming method. The `tnsnames.ora` file typically resides in the `ORACLE_HOME/network/admin` directory.

**Parent topic:** Glossary

### tracing

A facility that writes detailed information about an operation to an output file. The trace facility produces a detailed sequence of statements that describe the events of an operation as they are run. Administrators use the trace facility for diagnosing an abnormal condition. It is not normally turned on.

See also logging.

**Parent topic:** Glossary

### Transparent Application Failover (TAF)

A runtime failover for high-availability environments, such as Oracle Real Application Clusters and Oracle Fail Safe, that refers to the failover and re-establishment of application-to-service connections. It enables client applications to automatically reconnect to the database if the connection fails, and, optionally, resume a `SELECT` statement that was in progress. This reconnect happens automatically from within the Oracle Call Interface (OCI) library.

**Parent topic:** Glossary

### Transparent Network Substrate (TNS)

A foundation technology, built into the Oracle Net foundation layer that works with any standard network transport protocol.

**Parent topic:** Glossary

### transport

A networking layer that maintains end-to-end reliability through data flow control and error recovery methods. The Oracle Net foundation layer uses Oracle protocol support for the transport layer.

**Parent topic:** Glossary

### Transport Layer Security (TLS)

An industry standard protocol for securing network connections. The TLS protocol is a successor to the Secure Sockets Layer (SSL) protocol. It provides authentication, encryption, and data integrity using public key infrastructure (PKI).

See [The Difference Between Transport Layer Security and Secure Sockets Layer](../dbseg/configuring-secure-sockets-layer-authentication.md).

**Parent topic:** Glossary

### TTC

See Two-Task Common (TTC).

**Parent topic:** Glossary

### Two-Task Common (TTC)

A presentation layer type that is used in a typical Oracle Net connection to provide character set and data type conversion between different character sets or formats on the client and server.

**Parent topic:** Glossary

### UPI

User Program Interface.

**Parent topic:** Glossary

### virtual circuit

A piece of shared memory used by the dispatcher for client database connection requests and replies. The dispatcher places a virtual circuit on a common queue when a request arrives. An idle shared server picks up the virtual circuit from the common queue, services the request, and relinquishes the virtual circuit before attempting to retrieve another virtual circuit from the common queue.

**Parent topic:** Glossary

### WebDAV protocol

World Wide Web Distributed Authoring and Versioning. A protocol with a set of extensions to HTTP which allows users to manage files on remote Web servers.

**Parent topic:** Glossary
