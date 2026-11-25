The gateway architecture involves multiple systems, database servers, and communications facilities, each having distinct security capabilities and limitations. To effectively plan and implement your security scheme, you must understand these capabilities and limitations, in addition to knowing your installation's security requirements.

Read the following topics to learn about the capabilities and limitations of the Oracle Database Gateway for APPC:

- Overview of Security Requirements

- Authenticating Application Logons

- Defining and Controlling Database Links

- Using SNA Security Validation

- TCP/IP Security

- Passwords in the Gateway Initialization File

### Overview of Security Requirements

Before implementing the security scheme, you must understand the existing security requirements and expectations in the environment. Because you are enabling application access to different databases on different systems, you must merge multiple security cultures. When developing your security scheme, the most stringent security requirements prevail. When you connect different systems into an operating whole, the system with the strictest security requirements generally dictates what the other systems can and cannot do.

Gateway security includes two main concerns:

- users and applications that are permitted access to a particular gateway instance and OLTP

- OLTP transactions that users and applications are able to execute

You can control access at several points in the gateway architecture. The primary options are discussed in the following sections. Control over remote transaction program (RTP) access is provided by each OLTP with native authorization mechanisms based on user ID. These facilities are described in the product documentation for your OLTP. Information in the following topics include how the gateway facilities determine the user ID that is in effect for a particular OLTP connection.

When the gateway is involved in an RPC request, security mechanisms are in effect for each system component encountered by the gateway. The first system component that is encountered is the application tool or 3GL program. The last system component that is encountered is the OLTP.

Each of the following sections identifies the component and the type of security processing that is available in that component. Each section offers a summary of key features and parameters. Refer to product-specific documentation for detailed information about the non-gateway components for Oracle and non-Oracle products.

### Authenticating Application Logons

An application must connect to an Oracle database before using that gateway. The type of logon authentication that you use determines the resulting Oracle user ID and can affect gateway operation.

Two basic types of authentication are available:

- Oracle authentication.

  With Oracle authentication, each Oracle user ID has an associated password that is known to Oracle. When an application connects to the server, it supplies a user ID and password. Oracle confirms that the user ID exists and that the password matches the one stored in the database.

- Operating system authentication

  With operating system authentication, the server's underlying operating system is responsible for authentication. An Oracle user ID that is created with the `IDENTIFIED EXTERNALLY` attribute (instead of a password) is accessed with operating system authentication. To log on to such a user ID, the application supplies a slash ( / ) for a user ID and does not supply a password.

  To perform operating system authentication, the server determines the requester's operating system user ID, optionally adds a fixed prefix to it, and uses the result as the Oracle user ID. The server confirms that the user ID exists and is identified externally, but no password checking is done. The underlying assumption is that users were authenticated when they logged on to the operating system.

  Operating system authentication is not available on all platforms and is not available in some Oracle Net (client-server) and multi-threaded server configurations. Refer to your Windows Oracle database documentation and [Oracle Database Net Services Administrator's Guide](../netag/index.md) to determine the availability of this feature in your configuration.

For more information about authenticating application logons, refer to the [Oracle Database Administrator's Guide](../admin/getting-started-with-database-administration.md).

### Defining and Controlling Database Links

These topics discuss database links for users of the gateway employing either TCP/IP or SNA communications protocols.

- Link Accessibility

- Links and CONNECT Clauses

#### Link Accessibility

The first point of control for a database link is whether it is accessible to a given user. A public database link can be used by any user ID. A private database link can be used only by the user who created it. Database link usability is determined by its ability to open a session to the gateway. The Oracle database makes no distinction as to the type of use (such as read-only and update or write) or which remote objects can be accessed. These distinctions are the responsibility of the OLTP that is accessed.

#### Links and CONNECT Clauses

The `CONNECT` clause is another security-related attribute of a database link. You can use the `CONNECT` clause to specify an explicit user ID and password, which can differ from the user's Oracle user ID and password. This `CONNECT` user ID and password combination is sent to the gateway when the database link connection is first opened. Depending on gateway-specific options, the gateway might send that user ID and password to the OLTP to be validated.

If a database link is created without a `CONNECT` clause using Oracle authentication, then the user's Oracle user ID and password are sent to the gateway when the connection is opened. If the user logs on to the Oracle database with operating system authentication, then the gateway receives no user ID or password from the Oracle database . It is impossible for operating system-authenticated Oracle users to use a gateway database link defined without a `CONNECT` clause. However, if your OLTP provides user ID mapping facilities based on the gateway LU name from which the user is connecting, then such a connection is possible if all users on the same gateway instance can use the same OLTP user ID.

For more information about database links, refer to the [Oracle Database Administrator’s Guide](../admin/distributed-database-concepts.md).

### Using SNA Security Validation

The information in this section applies only to the security needs of gateway users employing the SNA communications protocol. When an RPC request to start a remote transaction program is received by the gateway, the gateway attempts to start an APPC conversation with the OLTP. Before the conversation can begin, a session must start between Windows' Logical Unit (LU) and the OLTP LU.

APPC support for the Windows platform is provided by the SNA Server (Microsoft Host Integration Server or IBM Communication Server v6.1.1 or higher).

SNA and its various access method implementations, including VTAM and the SNA Server, provide security validation at session initiation time, allowing each LU to authenticate its partner. This validation is carried out entirely by network software before the gateway and OLTP application programs begin their conversation and process conversation-level security data. If session-level security is used, then correct password information must be established in Microsoft Windows' SNA profiles and in similar parameter structures in the OLTP to be accessed. Refer to the suitable communications software product documentation for detailed information about this subject.

#### Specifying SNA Conversation Security

The `PGA_SECURITY_TYPE` parameter of the gateway initialization file allows you to specify one of three options that determine the security conduct of the LU6.2 conversation that is allocated with the OLTP. These options are part of the SNA LU6.2 architecture, but their precise behavior might vary depending on the particular OLTP system.

##### SNA Security Option SECURITY=NONE

If you specify `PGA_SECURITY_TYPE=NONE`, then the gateway performs no processing of the client user ID and password. The conversation is allocated with SNA option `SECURITY=NONE`.

##### SNA Security Option SECURITY=PROGRAM

If you specify `PGA_SECURITY_TYPE=PROGRAM`, then the gateway allocates the conversation with SNA option `SECURITY=PROGRAM`, and the following information is sent to the OLTP:

- If the TIP user ID and password overrides are used, then the specified user ID and password are sent regardless of the database link specification.

- If the database link has explicit `CONNECT` information, then the specified user ID and password are sent.

- If the database link has no `CONNECT` clause, and if the application logged on to Oracle with an explicit user ID and password, then the Oracle user ID and password are sent.

- If the application logs on to Oracle with operating system authentication, and if the database link lacks explicit `CONNECT` information, then no user ID and password are sent. If no user ID and password are sent, and if the OLTP is not configured to assign a default user ID, then the connection fails.

In general, SNA option `SECURITY=PROGRAM` tells the OLTP to authenticate the user ID/password combination using whatever authentication mechanisms are available. For example, if CICS Transaction Server for z/OS is the OLTP, then RACF can be used. This is not always the case, however, because each OLTP can be configured to process inbound user IDs in other ways.

### TCP/IP Security

The security information in this section applies only to users of the Oracle Database Gateway for APPC using the TCP/IP for IMS Connect feature. When an RPC request to start a RTP is received by the gateway, the gateway attempts to start the TCP/IP conversation with IMS Connect. IMS Connect would contact the OLTP (IMS) through OTMA and XCF. Refer to the IBM IMS Connect Guide and Reference for more information. The conversation between the gateway and IMS Connect occurs when the network uses the TCP/IP address or host name and port number to connect from the gateway to IMS Connect.

**Note:**

Because the gateway is using PGAU to generate TIPs, the TIPs contain SNA information. When using the Oracle Database Gateway for APPC with TCP/IP support for IMS Connect, you need to map the SNA names to the TCP/IP host name and port number in order for the gateway to communicate with IMS Connect. Use the `pg4tcpmap` tool to map the information from SNA to TCP/IP. Refer to Chapter 6, "pg4tcpmap Commands," of the [Oracle Database Gateway for APPC User's Guide](../appug/pg4tcpmap-commands-tcpip.md) for more information.

IMS Connect provides validation at session initiation time, allowing each connection to authenticate its partner. This validation is carried out entirely by network software before the gateway and OLTP application programs at IMS begin their conversation and process conversation-level security data. If session-level security is used, then correct password information must be established in Microsoft Windows and in similar parameter structures in the OLTP to be accessed.

#### Specifying TCP/IP Conversation Security

The `PGA_SECURITY_TYPE` parameter of the gateway initialization file allows you to specify the security conduct for the conversation that is allocated by the gateway for OLTP. Refer to [Gateway Initialization Parameters for TCP/IP Communication Protocol](appc-gateway-initialization-parameters-tcp-ip.md) .

##### TCP/IP Security Option SECURITY=NONE

If you specify `PGA_SECURITY_TYPE=NONE`, then the gateway performs no processing of the client user ID and password.

##### TCP/IP Security Option SECURITY=PROGRAM

If you specify `PGA_SECURITY_TYPE=PROGRAM`, then the following information is sent to the OLTP:

- If the TIP user ID and password overrides are used, then the specified user ID and password are sent regardless of the database link specification.

- If the database link has explicit `CONNECT` information, then the specified user ID and password are sent.

- If the database link has no `CONNECT` clause, and if the application logged on to Oracle with an explicit user ID and password, then the Oracle user ID and password are sent.

- If the application logs on to Oracle with operating system authentication, and if the database link lacks explicit `CONNECT` information, then no user ID and password are sent. If no user ID and password are sent, and if the OLTP is not configured to assign a default user ID, then the connection fails.

RACF is the only authentication mechanism available when the Oracle Database Gateway for APPC using TCP/IP for IMS Connect communicates with IMS Connect.

**Note:**

You must specify your RACF group name through the `pg4tcpmap` tool if you have set your PGA security option to `SECURITY=PROGRAM`. For more information about this issue, refer to the [Oracle Database Gateway for APPC User's Guide](../appug/pga-utility-oracle-database-gateway-appc.md).

### Passwords in the Gateway Initialization File

Initialization parameters may contain sensitive information, such as user IDs or passwords. Initialization parameters are stored in plain text files and may be deemed insecure. An encryption feature has been added to Heterogenous Services making it possible to encrypt parameters values. This is done through the `dg4pwd` utility.

**See Also:**

Refer to [Oracle Database Heterogeneous Connectivity User's Guide](../heter/initialization-parameters.md) for more information about this utility
