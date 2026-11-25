The Oracle Database Gateway for APPC (the "gateway") enables users to initiate transaction program execution on remote online transaction processors (OLTPs.) The Oracle Database Gateway for APPC can establish connection with OLTP using the SNA communication protocol. The gateway can also use TCP/IP for IMS Connect to establish communication with the OLTP through TCP/IP. The gateway provides Oracle applications with seamless access to IBM mainframe data and services through Remote Procedural Call (RPC) processing. The gateway can access any application capable of using the CPI-C API either directly or through a TP monitor such as CICS.

The following topics discuss the architecture, uses, and features of the gateway.

- Overview of the Gateway

- Features of the Gateway

- Terms

- Architecture of the Gateway

- Implementation of the Gateway

- Communication with the Gateway

- Remote Procedural Call Functions

- Transaction Types for Gateway Using SNA

- Transaction Types for Gateway Using TCP/IP

### Overview of the Gateway

The Oracle Database Gateway for APPC extends the Remote Procedural Call (RPC) facilities available with the Oracle database . The gateway enables any client application to use PL/SQL to request execution of a remote transaction program (RTP) residing on a host. The gateway provides RPC processing to systems using the SNA APPC (Advanced Program-to-Program Communication) protocol and to systems using TCP/IP for IMS Connect protocol. This architecture allows efficient access to data and transactions available on the IBM mainframe and IMS, respectively.

The gateway requires no Oracle software on the remote host system. Thus, the gateway uses existing transactions with little or no programming effort on the remote host.

#### For gateways using SNA:

The use of a generic and standard protocol, APPC, allows the gateway to access a multitude of systems. The gateway can communicate with virtually any APPC-enabled system, including IBM Corporation's CICS on any platform and IBM Corporation's IMS and APPC/MVS. These transaction monitors provide access to a broad range of systems, allowing the gateway to access many datastores, including VSAM, DB2 (static SQL), IMS, and others.

The gateway can access any application capable of using the CPI-C API either directly or through a TP monitor such as CICS.

### Features of the Gateway

The Oracle Database Gateway for APPC provides the following benefits:

- TCP/IP support for IMS Connect

  This release of the gateway includes TCP/IP support for IMS Connect, giving users a choice of whether to use the SNA or TCP/IP communication protocol. IMS Connect is an IBM product which allows TCP/IP clients to trigger execution of IMS transactions. The gateway can use a TCP/IP communication protocol to access IMS Connect, which triggers execution of IMS transactions. If you choose to use TCP/IP, then there is no SNA involvement with this configuration. Related to this new feature of the gateway is:

  - The `pg4tcpmap` tool. This release of the gateway includes a new tool whose purpose is to map the information from your side profile name to TCP/IP and IMS Connect. For more information about the gateway mapping tool, refer to Chapter 6, of the [Oracle Database Gateway for APPC User's Guide](../appug/pg4tcpmap-commands-tcpip.md), and to [Gateway Configuration Using TCP/IP Communication Protocol](configure-appc-gateway-using-tcp-ip.md) in this guide.

- Fast interface

  The gateway is optimized so that remote execution of a program is achieved with minimum network traffic. The interface to the gateway is an optimized PL/SQL stored procedure specification (called the TIP or transaction interface package) precompiled in the Oracle database . Because there are no additional software layers on the remote host system, overhead occurs only when the program processes.

- Location transparency

  Client applications need not be operating system-specific. For example, your application can call a program on a CICS Transaction Server for z/OS. If you move the program to a CICS region on pSeries, then you need not change the application.

- Application transparency

  Users calling applications that execute a remote transaction program are unaware that a request is sent to a host.

- Flexible interface

  You can use the gateway to interface with existing procedural logic or to integrate new procedural logic into an Oracle database environment.

- Oracle database integration

  The integration of the Oracle database with the gateway enables the gateway to benefit from existing and future Oracle features. For example, the gateway can be called from an Oracle stored procedure or database trigger.

- Transactional support

  The gateway and the Oracle database allow remote transfer updates and Oracle database updates to be performed in a coordinated fashion.

- Wide selection of tools

  The gateway supports any tool or application that supports PL/SQL.

- PL/SQL code generator

  The Oracle Database Gateway for APPC provides a powerful development environment, including:

  - a data dictionary to store information relevant to the remote transaction

  - a tool to generate the PL/SQL Transaction Interface Package, or TIP

  - a report utility to view the information stored in the gateway dictionary

  - a complete set of tracing and debugging facilities

  - a wide set of samples to demonstrate the use of the product against datastores such as DB2, IMS, and CICS.

- Site autonomy and security

  The gateway provides site autonomy, allowing you to do such things as authenticate users. It also provides role-based security compatible with any security package running on the mainframe computer.

- Automatic conversion

  Through the TIP, the following conversions are performed:

  - ASCII to and from EBCDIC

  - remote transaction program datatypes to and from PL/SQL datatypes

  - national language support for many languages

### Terms

The following terms and definitions are used throughout this guide. Refer to [Gateway Terminology](appc-gateway-terminology.md) for a more elaborate list of terms and definitions pertaining to the gateway, its components and functions.

#### Oracle Database

This is any Oracle database instance that communicates with the gateway for purposes of performing remote procedural calls to execute remote transaction programs (RTP). The Oracle database can be on the same system as the gateway or on a different system. If it is on a different system, then Oracle Net is required on both systems. Refer to Figure 1-2 for a view of the gateway architecture.

#### OLTP

Online Transaction Processor (OLTP) is any of a number of online transaction processors available from other vendors, including CICS Transaction Server for z/OS, IMS/TM, and z/OS

#### PGAU

Procedural Gateway Administration Utility (PGAU) is the tool that is used to define and generate PL/SQL Transaction Interface Packages (TIPs.) Refer to Chapter 2, "Procedural Gateway Administration Utility" in the [Oracle Database Gateway for APPC User's Guide](../appug/pga-utility-oracle-database-gateway-appc.md) for more information about PGAU.

#### PG DD

Procedural Gateway Data Dictionary (PG DD) is a repository of remote host transaction (RHT) definitions and data definitions. PGAU accesses definitions in the Data Dictionary (PG DD) when generating TIPs. The PG DD has datatype dependencies because it supports the PGAU and is not intended to be directly accessed by the customer. Refer to Appendix A, "Database Gateway for APPC Data Dictionary" in the [Oracle Database Gateway for APPC User's Guide](../appug/oracle-database-gateway-appc-data-dictionary.md) for a list of PG DD tables.

#### RPC

Remote Procedural Call (RPC) is a programming call that executes program logic on one system in response to a request from another system. Refer to [Gateway Terminology](appc-gateway-terminology.md)for more information, and refer to Appendix C, "Gateway RPC Interface" in the [Oracle Database Gateway for APPC User's Guide](../appug/oracle-database-gateway-appc-utl_pg-interface.md) as well.

#### RTP

A remote transaction program (RTP) is a customer-written transaction, running under the control of an OLTP, which the user invokes remotely using a PL/SQL procedure. To execute a RTP through the gateway, you must use RPC to execute a PL/SQL program to call the gateway functions.

#### TIP

A Transaction Interface Package (TIP) is an Oracle PL/SQL package that exists between your application and the remote transaction program. TIP is a set of PL/SQL stored procedures that invoke the remote transaction program through the gateway. TIPs perform the conversion and reformatting of remote host data using PL/SQL and `UTL_RAW` or `UTL_PG` functions.

Figure 1-1 illustrates where the terminology discussed in the preceding sections apply within the gateway's architecture.

Figure 1-1 Relationship of Gateway and Oracle Database on Windows

![Description of Figure 1-1 follows](img/g1_1trms.gif)
[Description of "Figure 1-1 Relationship of Gateway and Oracle Database on Windows"](img_text/g1_1trms.md)

### Architecture of the Gateway

The architecture of Oracle Database Gateway for APPC consists of several components:

- Oracle database

- The gateway

  Oracle Database Gateway for APPC must be installed on a server that can run the required version of the operating system.

- An OLTP

  The OLTP must be accessible from the gateway using the SNA or TCP/IP communication protocol. Multiple Oracle database s can access the same gateway. A single system gateway installation can be configured to access more than one OLTP.

<!-- -->

- For a gateway using TCP/IP support for IMS Connect: The only OLTP that is supported through TCP/IP is IMS through IMS Connect.

  The OLTP must be accessible to the system using the TCP/IP protocol. Multiple Oracle database s can access the same gateway. A single-system gateway installation can be configured to access more than one OLTP. Multiple IMS can be accessed from an IMS Connect. If you have a number of IMS Connect systems available, then any of these may be connected to one or more IMS systems.

Figure 1-2 illustrates the architecture of Oracle Database Gateway for APPC using either SNA or TCP/IP, as described in the preceding section.

Figure 1-2 Gateway Architecture

![Description of Figure 1-2 follows](img/g1_2arch.gif)
[Description of "Figure 1-2 Gateway Architecture"](img_text/g1_2arch.md)

### Implementation of the Gateway

The basic structure of the gateway is the same whether your communications protocol is SNA or TCP/IP support for IMS Connect. The gateway has some of the same components as an Oracle database instance on Microsoft Windows. It has the following components:

- a home directory, similar to the one associated with an Oracle instance's ` ORACLE_HOME` environment variable;

- a system identifier, identified as `sid` or `ORACLE_SID`;

- an initialization parameter file, similar to the Oracle database 's initsid.ora file.

The gateway does not have:

- control, redo log, or database files;

- the full set of subdirectories and ancillary files associated with an installed Oracle database .

Because the gateway has no background processes and does not need a management utility such as Oracle Enterprise Manager, you do not need to start the gateway product. Each Oracle database user session that accesses a particular gateway creates an independent process on Windows, which, in turn, runs the gateway server and executes either the SNA or TCP/IP functions to communicate with an OLTP.

### Communication with the Gateway

All of the communication between the user or client program and the gateway is handled through a TIP which executes on an Oracle database . The TIP is a standard PL/SQL package that provides the following functions:

- declares the PL/SQL variables that can be exchanged with a RTP;

- calls the gateway packages that handle the communications for starting the conversation, exchanging data, and terminating the conversation;

- handles all datatype conversions between PL/SQL datatypes and the target program datatypes.

The PGAU, provided with the gateway, automatically generates the TIP specification.

The gateway is identified to the Oracle database using a database link. The database link is the same construct used to identify other Oracle databases. The functions in the gateway are referenced in PL/SQL as:

    function_name@dblink_name

### Remote Procedural Call Functions

The Oracle Database Gateway for APPC provides a set of functions that are invoked by the client through remote procedural call (RPC). These functions direct the gateway to initiate, transfer data with, and terminate RTPs running under an OLTP on another system.

Table 1-1 lists the RPC functions and the correlating commands that are invoked in the gateway and remote host.

Table 1-1 RPC Functions and Commands in Oracle Database Gateway for APPC and Remote Host

| Applications    | Oracle TIP                           | Gateway   | Remote Host       |
|:----------------|:-------------------------------------|:----------|:------------------|
| `call tip_init` | `tip_init`<br>`call pgainit@gateway` | `PGAINIT` | Initiate program  |
| `call tip_main` | `tip_main`<br>`call pgaxfer@gateway` | `PGAXFER` | Exchange data     |
| `call tip_term` | `tip_term`<br>`call pgaterm@gateway` | `PGATERM` | Terminate program |

#### Description of RPC Functions

The following sections describe how the RPC functions perform on gateways using SNA or TCP/IP communication protocols.

##### Remote Transaction Initiation

The TIP initiates a connection to the remote host system, using one of the gateway functions, `PGAINIT`.

When the communication protocol is SNA: `PGAINIT` provides, as input, the required SNA parameters to start a conversation with the target transaction program. These parameters are sent across the SNA network, which returns a conversation identifier to `PGAINIT`. Any future calls to the target program use the conversation identifier as an `INPUT` parameter.

When the communication protocol is TCP/IP: `PGAINIT` provides, as input, the required TCP/IP parameters. Use the pg4tcpmap tool to map the parameters. These parameters are sent across the TCP/IP network to start the conversation with the target transaction program, the TCP/IP network returns a socket file descriptor to `PGAINIT`. Future calls to the target program made by `PGAXFER` and `PGATERM` use the socket file descriptor as an input parameter.

Refer to [Gateway Initialization Parameters for TCP/IP Communication Protocol](appc-gateway-initialization-parameters-tcp-ip.md) in this guide, and to Chapter 6 in the [Oracle Database Gateway for APPC User's Guide](../appug/pg4tcpmap-commands-tcpip.md), for more information about the function and use of the `pg4tcpmap` tool.

##### Data Exchange

After the conversation is established, a database gateway function called `PGAXFER` can exchange data in the form of input and output variables. `PGAXFER` sends and receives buffers to and from the target transaction program. The gateway sees a buffer as only a RAW stream of bytes. The TIP that is residing in the Oracle database is responsible for converting the application's PL/SQL datatypes to RAW before sending the buffer to the gateway. It is also responsible for converting RAW to the PL/SQL datatypes before returning the results to the application.

##### Remote Transaction Termination

When communication with the remote program is complete, the gateway function `PGATERM` terminates the conversation between the gateway and the remote host.

When the communication protocol is SNA:, `PGATERM` uses the conversation identifier as an `INPUT` parameter to request conversation termination.

When the communication protocol is TCP/IP:, `PGATERM` uses the socket file descriptor for TCP/IP as an `INPUT` parameter to request conversation termination.

### Transaction Types for Gateway Using SNA

The Oracle Database Gateway for APPC supports three types of transactions that read data from and write data to remote host systems:

- one-shot

  In a one-shot transaction, the application initializes the connection, exchanges data, and terminates the connection, all in a single call.

- persistent

  In a persistent transaction, multiple calls to exchange data with the remote transaction can be executed before terminating the conversation.

- multiconversational

  In a multiconversation transaction, the database gateway server can be used to exchange multiple records in one call to the RTP.

Refer to "Remote Host Transaction Types" in Chapter 4, "Client Application Development" of the [Oracle Database Gateway for APPC User's Guide](../appug/developing-appc-client-app-sna-only.md) for more information about transaction types.

The following list demonstrates the power of the Oracle Database Gateway for APPC:

- You can initiate a CICS transaction on the mainframe to retrieve data from a VSAM file for a PC application.

- You can modify and monitor the operation of a remote process control computer.

- You can initiate an IMS/TM transaction that executes static SQL in DB2.

- You can initiate a CICS transaction that returns a large number of records in a single call.

### Transaction Types for Gateway Using TCP/IP

The Oracle Database Gateway for APPC using TCP/IP for IMS Connect supports three types of transaction socket connections:

- transaction socket

  The socket connection lasts across a single transaction.

- persistent socket

  The socket connection lasts across multiple transactions.

- nonpersistent socket

  The socket connection lasts across a single exchange consisting of one input and one output.

  **Note:**

  Do not use the nonpersistent socket type if you plan on implementing conversational transactions because multiple connects and disconnects will occur.

  Refer to the section about `pg4tcpmap` commands in Chapter 6 of the [Oracle Database Gateway for APPC User's Guide](../appug/pg4tcpmap-commands-tcpip.md) and to [Gateway Configuration Using TCP/IP Communication Protocol](configure-appc-gateway-using-tcp-ip.md) in this guide for more information about how to enter these parameters.

  You can initiate an IMS/TM transaction that executes static SQL in DB2, this illustrates the power of the Oracle Database Gateway for APPC feature supporting TCP/IP for IMS Connect.
