The following topics discuss how you will call a TIP and control a remote host transaction if your gateway uses TCP/IP support for IMS Connect. It also provides you with the steps for preparing and executing a gateway transaction.

The following assumptions are made:

- a remote host transaction (RHT) has already been written

- a TIP corresponding to the RHT has already been defined using the steps described in [Creating a TIP](creating-tip-oracle-database-gateway-appc.md).

- the `PGA_TCP_IMSC` mapping table has been populated, using the `pg4tcpmap` tool, with the `SIDE PROFILE` name, TCP/IP hostname, port number and other IMS Connect parameters.

Topics:

- Overview of Client Application

- Preparing the Client Application

- Ensuring TIP and Remote Transaction Program Correspondence

- Calling the TIP from the Client Application

- Exchanging Data

- Calling PG4TCPMAP

- Executing the Application

- Application Development with Multi-Byte Character Set Support

- Privileges Needed to Use TIPs

### Overview of Client Application

The Procedural Gateway Administration Utility (PGAU) generates a complete TIP using definitions you provide. The client application can then call the TIP to access the remote host transaction. [Procedural Gateway Administration Utility](pga-utility-oracle-database-gateway-appc.md) , discusses the use of PGAU in detail.

This overview explains what you must do in order to call a TIP and control a remote host transaction.

The gateway receives PL/SQL calls from the Oracle database and issues TCP/IP calls to communicate with a remote transaction program.

The following application programs make this possible:

1.  An I/O PCB-enabled remote host transaction program.

2.  The `PGA_TCP_IMSC` mapping table that has been populated, using the pg4tcpmap tool, with the `SIDE PROFILE` name as well as the TCP/IP hostname, port number and other IMS Connect parameters.

3.  A Transaction Interface Package (TIP). A TIP is a PL/SQL package that handles communication between the client and the gateway and performs datatype conversions between COBOL and PL/SQL.

4.  PGAU generates the TIP specification for you. In the shipped samples, the PGAU-generated package is called `pgtflip.pkb`. This generated TIP includes at least three function calls that map to the remote transaction program:

    - `pgtflip_init` initializes the conversation with the remote transaction program

    - `pgtflip_main` exchanges application data with the remote transaction program

    - `pgtflip_term` terminates the conversation with the remote transaction program

    Refer to [Tip Internals](tip-internals-oracle-database-gateway-appc.md) for more information about TIPs, if you are writing your own TIP or debugging.

5.  A client application that calls the TIP.

    The client application calls the three TIP functions with input and output arguments. In the example, the client application passes an input and the remote transaction and the remote transaction sends back the flipped input as an output.

Table 7-1 demonstrates the logic flow between the PL/SQL driver, the TIP, and the gateway using the example IMS Connect-IMS transaction.

Table 7-1 Logic Flow of IMS Connect-IMS Example

| Client Application | Oracle TIP                                               | Procedures Established Between the Gateway and the Remote Transaction (mainframe IMS)                                                                                                                                                                             |
|:-------------------|:---------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Calls `tip_init`   | Calls `PGAINIT`                                          | Gateway issues TCP/IP socket and connect to initiate the conversation with IMS Connect.                                                                                                                                                                           |
| Calls `tip_main`   | Calls `PGAXFER` to send the input and receive the output | Gateway issues TCP/IP `send()` to IMS Connect. IMS Connect, through OTMA and XCF, talks to the IMS instance. IMS `RECEIVE` completes. IMS performs application logic and issues `SEND` back to gateway. The gateway issues TCP/IP` receive()`; receive completes. |
| Calls `tip_term`   | Calls `PGATERM`                                          | Gateway issues TCP/IP `close()`.                                                                                                                                                                                                                                  |

A client application which utilizes the gateway to exchange data with a remote host transaction performs some tasks for itself and instructs the TIP to perform other tasks on its behalf. The client application designer must consequently know the behavior of the remote transaction and how the TIP facilitates the exchange.

The following sections provide an overview of remote host transaction behavior, how this behavior is controlled by the client application and how TIP function calls and data declarations support the client application to control the remote host transaction. These sections also provide background information about what the TIP does for the client application and how the TIP calls exchange data with the remote host transaction.

### Preparing the Client Application

To prepare the client application for execution you must understand the remote host transaction requirements and then perform these steps:

1.  Make sure that the pg4tcpmap tool has been used to map the `SIDEPROFILE` name, defined in the `.ctl` file for the PGAU utility, to TCP/IP and IMS Connect attributes.
    Refer to [PG4TCPMAP Commands (TCP/IP Only)](pg4tcpmap-commands-tcpip.md) in this guide for detailed information about mapping parameters.
2.  Make certain that you have identified the remote host transaction program facilities to be called.
3.  Move relevant COBOL records layout (copybooks) to the gateway system for input to PGAU.
4.  Describe the remote host transaction data and calls to the PG Data Dictionary (PG DD) with `DEFINE DATA`, `DEFINE CALL`, and `DEFINE TRANSACTION` statements.
5.  Generate the TIP in the Oracle database, using `GENERATE`.
6.  Create the client application that calls the TIP public functions.
7.  Grant privileges on the newly created package.

#### TIP Content and Purpose

The content of a PGAU-generated TIP reflects the calls available to the remote host transaction and the data that has been exchanged. Understanding this content helps when designing and debugging client applications that call the TIP.

A TIP is a PL/SQL package, and accordingly has two sections:

- A Package Specification containing:

  - Public function prototypes and parameters

- A Package Body containing:

  - Private functions and internal control variables

  - Public functions

  - Package initialization following the last public function

The purpose of the TIP is to provide a PL/SQL callable public function for every allowed remote transaction program interaction. A remote transaction program interaction is a logically related group of data exchanges through one or more `PGAXFER` RPC calls. This is conceptually similar to a screen or menu interaction in which several fields are filled in, the enter key is pressed, and several fields are returned to the user. Carrying the analogy further:

- the user might be likened to the TIP or client application

- fields to be filled in are `IN` parameters on the TIP function call

- fields returned are `OUT` parameters on the TIP function call

- screen or menu is the group of `IN` and `OUT` parameters combined

- a pressed enter key is likened to the `PGAXFER` remote procedural call (RPC)

The actual grouping of parameters that constitute a transaction call is defined by the user. The gateway places no restrictions on how a remote transaction program might correspond to a collection of TIP function calls, each call having many `IN` and `OUT` parameters.

PGA users typically have one TIP per remote transaction program. How the TIP function calls are grouped and what data parameters are exchanged on each call depends on the size, complexity and behavior of the remote transaction program.

Refer to Oracle's [Oracle Database PL/SQL Language Reference](../lnpls/index.md) for a discussion of how PL/SQL packages work. The following discussion covers the logic that must be performed within a TIP. Refer to the sample TIP and driver supplied in the `%ORACLE_HOME%\dg4appc\demo\IMS` directory on Microsoft Windows and in `$ORACLE_HOME/dg4appc/demo/IMS` directory on UNIX based systems, in files `pgtflip.pkh`, `pgtflip.pkb`, and `pgtflipd.sql`.

#### Remote Host Transaction Types

From a database gateway application perspective, there are three main types of remote host transactions:

- transaction socket

- persistent socket

- non-persistent socket

You should be familiar with the remote host transaction types. Refer to the IBM IMS Connect Guide and Reference for a full description of these transaction types.

### Ensuring TIP and Remote Transaction Program Correspondence

A remote host transaction program and its related TIP with client application must correspond on two key requirements:

- Parameter datatype conversion, which results from the way in which transaction DATA is defined. Refer to [Datatype Conversions](data-type-conversion-oracle-database-gateway-appc.md) for a discussion of how PGAU-generated TIPs convert data based on the data definitions.

- TCP/IP send/receive synchronization, which results from the way in which transaction `CALL`s are defined.

These `DATA` and `CALL` definitions are then included by reference in a `TRANSACTION` definition.

Make certain that the `SIDEPROFILE` name has been mapped to TCP/IP and IMS Connect attributes, using the `pg4tcpmap` tool.

#### DATA Correspondence

Using data definitions programmed in the language of the remote host transaction, the PGAU `DEFINE DATA` command stores in the PG DD the information needed for PGAU `GENERATE` to create the TIP function logic to perform:

- all data conversion from PL/SQL `IN` parameters supplied by the receiving remote host transaction

- all buffering into the format expected by the receiving remote host transaction

- all data unbuffering from the format supplied by the sending remote host transaction

- all data conversion to PL/SQL `OUT` parameters supplied by the sending remote host transaction

PGAU determines the information needed to generate the conversion and buffering logic from the data definitions included in the remote host transaction program. PGAU `DEFINE DATA` reads this information from files, such as COBOL copy books, or in-stream from scripts and saves it in the PG DD for repeated use. The Gateway Administrator needs to transfer these definition files from the remote host to the Oracle host where PGAU runs.

From the data definitions stored in the PG DD, PGAU `GENERATE` determines the remote host datatype and matches it to an appropriate PL/SQL datatype. It also determines data lengths and offsets within records and buffers and generates the needed PL/SQL logic into the TIP. Refer to the PGAU "[DEFINE DATA](pga-utility-oracle-database-gateway-appc.md)" statement in [Procedural Gateway Administration Utility](pga-utility-oracle-database-gateway-appc.md) and "[Sample PGAU DEFINE DATA Statements](admin-utility-samples-oracle-database-gateway-appc.md)" in [Administration Utility Samples](admin-utility-samples-oracle-database-gateway-appc.md) for more information.

All data that are referenced as parameters by subsequent calls must first be defined using PGAU `DEFINE DATA`. Simple data items, such as single numbers or character strings, and complex multi-field data aggregates, such as records or structures, can be defined. PGAU automatically generates equivalent PL/SQL variables and records of fields or tables for the client application to reference in its calls to the generated TIP.

As discussed, a parameter might be a simple data item, such as an employee number, or a complex item, such as an employee record. PGAU `DEFINE DATA` automatically extracts the datatype information it needs from the input program data definition files.

In this example, `FLIPIN` and `FLIPOUT` are the arguments to be exchanged.

    PGTFLIP_MAIN(trannum,FLIPIN,FLIPOUT)

A PGAU `DEFINE DATA` statement must therefore be issued for each of these parameters:

    DEFINE DATA FLIPIN
           PLSDNAME (FLIPIN)
           USAGE (PASS)
           LANGUAGE (IBMVSCOBOLII)
           (
           01 MSGIN PIC X(20).
           );

    DEFINE DATA FLIPOUT
           PLSDNAME (flipout)
           USAGE (PASS)
           LANGUAGE (IBMVSCOBOLII)
           (
           01 MSGOUT PIC X(20).
           );

Note that a definition is not required for the `trannum` argument. This is the APPC conversation identifier and does not require a definition in PGAU.

#### CALL Correspondence

The requirement to synchronize TCP/IP send() and receive() means that when the remote transaction program expects data parameters to be input, it issues TCP/IP receive() to read the data parameters. Accordingly, the TIP must cause the gateway to issue TCP/IP send() to write the data parameters to the remote transaction program. The TIP must also cause the gateway to issue TCP/IP receive() when the remote transaction program issues TCP/IP send().

The PGAU `DEFINE CALL` statement specifies how the generated TIP is to be called by the client application and which data parameters are to be exchanged with the remote host transaction for that call. Each PGAU `DEFINE CALL` statement might specify the name of the TIP function, one or more data parameters, and the `IN/OUT` mode of each data parameter. Data parameters must have been previously defined with PGAU `DEFINE DATA` statements. Refer to "[DEFINE CALL](pga-utility-oracle-database-gateway-appc.md)" in [Procedural Gateway Administration Utility](pga-utility-oracle-database-gateway-appc.md) and "[Sample PGAU DEFINE CALL Statements](admin-utility-samples-oracle-database-gateway-appc.md)" in [Administration Utility Samples](admin-utility-samples-oracle-database-gateway-appc.md) for more information.

PGAU `DEFINE CALL` processing stores the specified information in the PG DD for later use by PGAU `GENERATE`. PGAU `GENERATE` then creates the following in the TIP package specification:

- declarations of public PL/SQL functions for each `CALL` defined with PL/SQL parameters for each `DATA` definition specified on the `CALL`

- declarations of the public PL/SQL data parameters

The client application calls the TIP public function as a PL/SQL function call, using the function name and parameter list specified in the PGAU `DEFINE CALL` statement. The client application might also declare, by reference, private variables of the same datatype as the TIP public data parameters to facilitate data passing and handling within the client application, thus sharing the declarations created by PGAU `GENERATE`.

In this example, the following PGAU `DEFINE CALL` statement must be issued to define the TIP public function:

    DEFINE CALL FLIPMAIN
           PKGCALL (pgtflip_main)
           PARMS ((FLIPIN IN),(FLIPOUT OUT));

##### Flexible Call Sequence

The number of data parameters exchanged between the TIP and the gateway on each call can vary at the user's discretion, as long as the remote transaction program's `SEND/RECEIVE` requests are satisfied. For example, the remote transaction program data exchange sequence might be:

    TCP/IP SEND      5 fields (field1-field5)
    TCP/IP RECEIVE   1 fields (field6)
    TCP/IP SEND      1 field (field7)
    TCP/IP RECEIVE   3 fields (field8 - field10)

The resulting TIP/application call sequence could be:

    tip_call1(parm1 OUT, <-- TCP/IP SEND field1 from remote TP
              parm2 OUT, <-- TCP/IP SEND field2 from remote TP
              parm3 OUT); <-- TCP/IP SEND field3 from remote TP

    tip_call2(parm4 OUT, <-- TCP/IP SEND field4 from remote TP
              parm5 OUT); <-- TCP/IP SEND field5 from remote TP
    tip_call3(parm6 IN OUT); --> TCP/IP RECEIVE field6 in remote TP
                            <-- TCP/IP SEND field7 from remote TP

    tip_call4(parm8 IN, --> TCP/IP RECEIVE field8 into remote TP
              parm9 IN, --> TCP/IP RECEIVE field9 into remote TP
              parm10 IN); --> TCP/IP RECEIVE field10 into remote TP

To define these four public functions to the TIP, four PGAU `DEFINE CALL` statements must be issued, each specifying its unique public function name (`tip_callx`) and the data parameter list to be exchanged. Once a data item is defined using `DEFINE DATA`, it can be referenced in multiple calls in any mode (`IN`, `OUT`, or `IN OUT`). For example, `parm5` could be used a second time in place of `parm6` This implies the same data is being exchanged in both instances, received into the TIP and application on `tip_call2` and returned, possibly updated, to the remote host in `tip_call4`.

Notice also that the remote transaction program's first five written fields are read by two separate TIP function calls, `tip_call1` and `tip_call2`. This could also have been equivalently accomplished with five TIP function calls of one `OUT` parameter each or a single TIP function call with five `OUT` parameters. Then the remote transaction program's first read field (`field6`) and subsequent written field (`field7`) correspond to a single TIP function call (`tip_call3`) with a single `IN OUT` parameter (`parm6`).

This use of a single` IN OUT` parameter implies that the remote transaction program's datatype for `field6` and `field7` are both the same and correspond to the conversion performed for the datatype of `parm6`. If `field6` and `field7` were of different datatypes, then they have to correspond to different PL/SQL parameters (for example, `parm6 IN` and `parm7 OUT`). They could still be exchanged as two parameters on a single TIP call or one parameter each on two TIP calls, however.

Lastly, the remote transaction program's remaining three `RECEIVE` fields are supplied by `tip_call4` parameters 8-10. They also could have been done with three TIP calls passing one parameter each or two TIP calls passing one parameter on one call and two parameters on the other, in either order. This flexibility permits the user to define the correspondence between the remote transaction program's operation and the TIP function calls in whatever manner best suits the user.

##### Call Correspondence Order Restrictions

Each TIP public function first sends all `IN` parameters, before it receives any `OUT` parameters. Thus, a remote transaction program expecting to send one field and then receive one field must correspond to separate TIP calls.

For example:

    tip_callO( parmO OUT); <-- TCP/IP SEND outfield from remote TP

`PGAXFER` RPC checks first for parameters to send, but finds none and proceeds to receive parameters:

    tip_callI( parmI IN); --> TCP/IP RECEIVE infield to remote TP

`PGAXFER` RPC processes parameters to send and then checks for parameters to receive, but finds none and completes; therefore, a single TIP public function with an `OUT` parameter followed by an `IN` parameter does not work, because the `IN` parameter is processed first--regardless of its position in the parameter list.

#### TRANSACTION Correspondence

The remote host transaction is defined with the PGAU `DEFINE TRANSACTION` statement with additional references to prior definitions of `CALL`s that the transaction supports.

You specify the remote host transaction attributes, such as:

- transaction ID or name

- network address or location

- system type (such as IBM370)

- Oracle National Language of the remote host

  **Note:**

  The PL/SQL package name is specified when the transaction is defined; this is the name by which the TIP is referenced and which the public function calls to be included within the TIP. Each public function must have been previously defined with a PGAU `DEFINE CALL` statement, which has been stored in the PG DD. If you do not specify a package name (TIP name) in the `GENERATE` statement, the transaction name you specified will become the package name by default. In that case, the transaction name (`tname) `must be unique and must be in valid PL/SQL syntax within the database containing the PL/SQL packages.

  For more information, refer to "[DEFINE TRANSACTION](pga-utility-oracle-database-gateway-appc.md)" in [Procedural Gateway Administration Utility](pga-utility-oracle-database-gateway-appc.md) and "[Sample PGAU DEFINE TRANSACTION Statement](admin-utility-samples-oracle-database-gateway-appc.md)" in [Administration Utility Samples](admin-utility-samples-oracle-database-gateway-appc.md).

In this example, the following `DEFINE TRANSACTION `statement is used to match this information with the inserted row in the `PGA_TCP_IMSC` table.

    DEFINE TRANSACTION IMSFLIP
       CALL (FLIPMAIN)
       SIDEPROFILE(PGATCP)
       TPNAME(FLIP)
       NLS_LANGUAGE("american_america.us7ascii");

### Calling the TIP from the Client Application

Once a TIP is created, a client application must be written to interface with the TIP. A client application that calls the TIP functions must include five logical sections:

- declaring TIP variables

- initializing the conversation

- exchanging data

- terminating the conversation

- error handling

#### Declaring TIP Variables

The user declarations section of the `tipname`.`doc` file documents the required declarations.

When passing PL/SQL parameters on calls to TIP functions, the client application must use the exact same PL/SQL data types for TIP function arguments as are defined by the TIP in its specification section. Assume, for example, the following is in the TIP specification, or `tipname``.doc`:

    FUNCTION tip_call1    tranuse,   IN      BINARY_INTEGER,
                          tip_var1   io_mode pls_type1,
                          tip_record io_mode tran_rectype)
    RETURN INTEGER;

    TYPE  tran_rectype is RECORD
          (rec_field1 pls_type1,
          ...
          rec_fieldN pls_typeN);

Where Table 7-2 provides a description of each of the parameters:

Table 7-2 Function Declarations

| Parameter      | Description                                                                                                                                            |
|:---------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------|
| `tip_call1`    | The TIP function name as defined in the package specification.                                                                                         |
| `tranuse`      | The remote transaction instance parameter returned from the TIP init function identifying the conversation on which this TIP call is to exchange data. |
| `tran_rectype` | The PL/SQL record data type declared in the `tipname`TIP specification. This is the same value as in the `TYPE``tran_rectype`` is RECORD` statement.   |
| `pls_typeN`    | Is a PL/SQL atomic data type.                                                                                                                          |
| `rec_fieldN`   | Is a PL/SQL record field corresponding to a remote transaction program record field.                                                                   |

In the client application PL/SQL atomic data types should be defined as the exact same data type of their corresponding arguments in the TIP function definition. The following should be coded in the client application before the `BEGIN` command:

    appl_var  pls_type1;    /* declare appl variable for ....  */

You do not need to redefine TIP data types. They must be declared locally within the client application, appearing in the client application before the `BEGIN`:

    appl_record tipname.tran_rectype;  /* declare appl record */

Table 7-3 describes the meaning of each procedure declaration:

Table 7-3 Procedure Declarations

| Item           | Description                                                                                                                                                                 |
|:---------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `appl_record`  | Is a PL/SQL record exchanged with the TIP and used within the client application.                                                                                           |
| `tipname`      | Is the PL/SQL package (TIP) name as stored in Oracle database. This is the same value as in the statement `CREATE` or `REPLACE PACKAGE` `tipname` in the TIP specification. |
| `tran_rectype` | Is the PL/SQL record data type declared in the `tipname` TIP specification. This is the same value as in the `TYPE` `tran_rectype` is `RECORD` statement.                   |

Refer to the `tipname``.doc` content file for a complete description of the user declarations you can reference.

The client application calls the TIP public function as if it were any local PL/SQL function:

    rc = tip_call1( tranuse,
                    appl_var,
                    appl_record);

In the TCP/IP IMS Connect example, the PL/SQL driver `pgtflipd.sql`, which islocated in `%ORACLE_HOME%\dg4appc\demo\IMS` directory on Microsoft Windows and in `$ORACLE_HOME/dg4appc/demo/IMS` directory on UNIX based systems, is the client application and includes the following declaration:

    ...
    ...
    CREATE or REPLACE PROCEDURE pgtflipd(mesgin IN CHAR) IS
    trannum INTEGER :=0               /* transaction usage number     */
    mesgout VARCHAR2(254);            /* the output parameter       */
    rc INTEGER :=0                    /* PGA RPC return codes         */
    term INTEGER :=0;                 /* 1 if pgtflip_term called     */
    ...
    ...

#### Initializing the Conversation

The call to initialize the conversation serves several purposes:

- To cause the PL/SQL package, the TIP, to be loaded and to perform the initialization logic programmed in the TIP initialization section.

- To cause the TIP init function to call the `PGAINIT` remote procedural call (RPC), which in turn establishes communication with the remote transaction program (RTP), and returns a transaction instance number to the application.

Optionally, calls to initialize the conversation can be used to:

- Override default RHT/OLTP identification, network address attributes, and conversation security user ID and password.

- Specify what diagnostic traces the TIP is to produce. Refer to [Troubleshooting](troubleshooting-oracle-database-gateway-appc.md) for more information about diagnostic traces.

PGAU-generated TIPs provide four different initialization functions that client applications can call. These are overloaded functions which all have the same name, but vary in the types of parameters passed.

Three initialization parameters are passed:

- The transaction instance number for RHT socket file descriptor. The `tranuse` parameter is required on all TIP initializations.

- TIP diagnostic flags for TIP runtime diagnostic controls. The `tipdiag` parameter is optional. Refer to [Troubleshooting](troubleshooting-oracle-database-gateway-appc.md) for a discussion of TIP diagnostics.

- TIP default overrides for overriding OLTP and network attributes. The `override` parameter is optional.

The following four functions are shown as they might appear in the TIP Content documentation file. Examples of client application use are provided later.

    TYPE override_Typ IS RECORD (
            tranname  VARCHAR2(2000),  /* Transaction Program     */
            transync  BINARY_INTEGER, /* RESERVED                */
            trannls   VARCHAR2(50),   /* RESERVED                */
            oltpname  VARCHAR2(2000),  /* Logical Unit            */
            oltpmode  VARCHAR2(2000),  /* LOG Mode Entry          */
            netaddr   VARCHAR2(2000),  /* Side Profile            */
            tracetag  VARCHAR2(2000),    /* gateway trace idtag  */

    FUNCTION pgtflip_init(                /* init standard */
               tranuse IN OUT BINARY_INTEGER)
               RETURN INTEGER;

    FUNCTION pgtflip_init(                /* init override */
               tranuse IN OUT BINARY_INTEGER,
               override IN override_Typ)
               RETURN INTEGER;

    FUNCTION pgtflip_init(               /* init diagnostic */
               tranuse IN OUT BNARY_INTEGER,
               tipdiag IN CHAR)
               RETURN INTEGER;

    FUNCTION pgtflip_init(                /* init over-diag */
               tranuse IN OUT BINARY_INTEGER,
               override IN override_Typ,
               tipdiag IN CHAR)
               RETURN INTEGER;

##### Transaction Instance Parameter

This transaction instance number (shown in examples as `tranuse`) must be passed to subsequent TIP exchange and terminate functions. It identifies to the gateway on which TCP/IP conversation--and therefore which iteration of a remote transaction program--the data is to be transmitted or communication terminated.

A single client application might control multiple instances of the same remote transaction program or multiple different remote transaction programs, all concurrently. The transaction instance number is the TIP‘s mechanism for routing the client application call through the gateway to the intended remote transaction program.

It is the responsibility of the client application to save the transaction instance number of each active transaction and pass the correct one to each TIP function called for that transaction.

The client application calls the TIP initialization function as if it were any local PL/SQL function. For example:

    ...
    ...
    trannum INTEGER := 0;/* transaction usage number*/
    ...
    ...
    BEGIN
     rc := pgtflip.pgtflip_init(trannum);
    ...
    ...

##### Overriding TIP Initializations

Note that in the preceding example the client application did not specify any remote transaction program name, network connection, or security information. The TIP has such information internally coded as defaults and the client application simply calls the appropriate TIP for the chosen remote transaction program. The client application can, however, optionally override some TIP defaults and supply security information.

You do not need to change any client applications that do not require overrides.

When the remote host transaction was defined in the PG DD, the `DEFINE TRANSACTION` statement specified certain default OLTP and network identification attributes which can be overridden:

- TPname

- Side Profile

Refer to "[DEFINE TRANSACTION](pga-utility-oracle-database-gateway-appc.md)" in [Procedural Gateway Administration Utility](pga-utility-oracle-database-gateway-appc.md) for more information about the `DEFINE TRANSACTION` statement.

These PG DD-defined transaction attributes are generated into TIPs as defaults and can be overridden at TIP initialization time. This facilitates the use of one TIP, which can be used with a test transaction or system, and can later be used with a production transaction or system, without having to regenerate the TIP.

The `override_Typ` record datatype describes the various transaction attributes that can be overridden by the client application. The following overrides are currently supported:

- `tranname` can be set to override the value that was specified by the `TPNAME` parameter of the `DEFINE TRANSACTION` statement

- `netaddr` can be set to override the value that was specified by the `SIDEPROFILE` parameter of the `DEFINE TRANSACTION` statement

In addition to the transaction attributes defined in the PG DD, there are two security-related parameters, conversation security user ID and conversation security password, that can be overridden at TIP initialization time. The values for these parameters normally come from either the database link used to access the gateway or the Oracle database session. There are cases when the Oracle database user ID is not sufficient for accessing the OLTP system. The user ID and password overrides provide a way to specify those parameters to the OLTP system.

The following overrides are currently supported:

- `oltpuser` can be set to override the user ID used to initialize the conversation with the OLTP

- `oltppass` can be set to override the password used to initialize the conversation with the OLTP

The security overrides have an effect only if `PGA_SECURITY_TYPE=PROGRAM` is specified in the gateway initialization file, and the OLTP system is configured to accept a user ID and password on incoming conversation requests.

The `transync` (IMS Connect `SYNCLEVEL`) and `trannls` (Globalization Support character set) are defined in the override record datatype, but are reserved for future use. The RHT `SYNCLEVEL` and Globalization Support name cannot be overridden.

The client application might override the default attributes at TIP initialization for the following reasons:

- to start a different version of the RHT (such as production instead of test)

- to change the location of the OLTP containing the RHT (if the OLTP was moved due to migration or a switch to backup configuration)

Client applications requiring overrides can use any combination of override and initialization parameters and might alter the combination at any time without regenerating the TIP or affecting applications that do not override parameters.

To override the TIP defaults, an additional client application record variable must be declared as `override_Typ` datatype, values must be assigned to the override subfields, and the override record variable must be passed on the TIP initialization call from the client application. For example:

       ...
       ...
       my_overrides pgtflip.override_Typ;   -- declaration
       ...
       ...
       my_overrides.oltpname := 'IVTNO'; -- swap to production IMS
       my_overrides.tranname := 'IVTNV';     -- new transaction name

    BEGIN
       rc := pgtflip.pgtflip_init(trannum,my_overrides); -- init
       ...
       ...

Within the TIP, override attributes are checked for syntax problems and passed to the gateway server.

##### Security Considerations

The security requirements of the default and overridden OLTPs must be the same because the same gateway server is used in either conversation, as dictated by the database link names in the PGA RPC calls. The gateway server startup security mode is set at gateway server initialization time and passed unchanged to the OLTP at TIP or conversation initialization time.

### Exchanging Data

The client application should pass the transaction instance number, returned from a previous `tip_init` call, to identify which remote transaction program is affected and to identify any client application data parameters to be exchanged with the remote transaction program.

In this IMS Connect inquiry example, we pass an employee number and receive an employee record back:

    rc = pgtflip.pgtflip_main(trannum, /* transfer data         */
                               mesgin,   /* input parameter       */
                               mesgout); /* output parameter*/

#### Terminating the Conversation

The client application calls the TIP termination function as if it were any local PL/SQL function. For example:

    ...
    ...
    term := 1;    /* indicate term called */
     rc := pgtflip.pgtflip_term(trannum,0); /* terminate normally  */
    ...
    ...

After a transaction instance number has been passed on a TIP terminate call to terminate the transaction, or after the remote transaction program has abended, that particular transaction instance number might be forgotten.

#### Error Handling

The client application should include an exception handler that can clean up any active TCP/IP conversations before the client application terminates. The sample client application provided in `pgtflipd.sql` contains an example of exception handling.

Gateway exceptions are reported in the range `PGA-20900` to `PGA-20999` and `PGA-22000` to `PGA 22099`. When an exception occurs, the TIP termination function should be called for any active conversations that have been started by prior calls to the TIP initialization function.

For example:

    EXCEPTION
     WHEN OTHERS THEN
      IF term = 0 THEN         /* terminate function not called yet */
       rc := pgtflip.pgtflip_term(trannum,1); /*terminate abnormally*/
      END IF;
     RAISE;

The remote transaction should also include provisions for error handling and debugging, such as writing debugging information to the IMS temporary storage queue area. Refer to the [Oracle Database PL/SQL Language Reference](../lnpls/overview-exception-handling.md) for a discussion of how to intercept and handle Oracle exceptions.

#### Granting Execute Authority

The TIP is a standard PL/SQL package and execute authority must be granted to users who call the TIP from their client application. In this example, we grant execute on the `pgtflip` package to user `SCOTT`:

    GRANT EXECUTE ON PGTFLIP TO SCOTT

Refer to the [Oracle Database Administrator's Guide](../admin/getting-started-with-database-administration.md) for further information.

### Calling PG4TCPMAP

PGAU need not be modified in order to have a conversation on a gateway using TCP/IP. You use the APPC format of PGAU, but you will map parameters to TCP/IP using the `pg4tcpmap` tool.

To map the `DEFINE TRANSACTION` parameters using TCP/IP, you must have a valid input within the `PGA_TCP_IMSC` table before executing the application. Refer to [PG4TCPMAP Commands (TCP/IP Only)](pg4tcpmap-commands-tcpip.md) for information about setting up and using the mapping tool.

### Executing the Application

Before executing the client application, ensure that a connection to the host is established and that the receiving partner is available. In this example we use PL/SQL driver `PGTFLIPD` to execute the IMS/IMS Connect inquiry. To execute this client application, enter from SQL\*Plus:

    set serveroutput on
    execute pgtflipd('hello');

### Application Development with Multi-Byte Character Set Support

COBOL presently only supports double byte character sets (DBCS) for PIC G datatypes.

PGAU processes IBM VS COBOLII` PIC G` datatypes as PL/SQL `VARCHAR2` variables and generates TIPs which automatically convert the data according to the Oracle `NLS_LANGUAGE`s specified for the remote host data and the local Oracle data.

These Oracle `NLS_LANGUAGE`s can be specified as defaults for all `PIC G` data exchanged by the TIP with the remote transaction (see `DEFINE TRANSACTION ... REMOTE_MBCS` or `LOCAL_MBCS`). The Oracle `NLS_LANGUAGE`s for any individual `PIC G` data item can be further overridden (see `REDEFINE DATA ... REMOTE` or `LOCAL_LANGUAGE`).

DBCS data can be encoded in any combination of supported DBCS character sets. For example, a remote host application which allows different codepages for each field of data in a record is supported by the Oracle Database Gateway MBCS support.

Use of `REDEFINE DATA ... REMOTE_LANGUAGE` or `LOCAL_LANGUAGE` on `PIC X` items is also supported. Thus a TIP can perform DBCS or MBCS conversions for specified `PIC X` data fields, in addition to SBCS conversions by default for the remaining `PIC X` data fields. Default SBCS conversion is according to the `DEFINE TRANSACTION... NLS_LANGUAGE` and local Oracle default `LANGUAGE` environment values.

When PGAU is generating a TIP, the `PIC G` datatypes are converted to PL/SQL `VARCHAR2` datatypes. After conversion by the TIP, received `'PIC G' VARCHAR2s` can have a length less then the maximum due to deletion of shift-out and shift-in meta characters, and sent `'PIC G' `RAW datatypes will have the shift-out and shift-in characters inserted as required by the remote host character set specified.

This is different from the conversions performed for `PIC X` data which is always a known fixed-length and hence `CHAR` datatypes are used in TIPs for `PIC X` data fields. However, even when the `PIC X` field contains DBCS or MBCS data, a `CHAR` variable is still used and padded with blanks if needed.

Some remote host applications bracket a `PIC G` field with` PIC X` bytes used for shift-out, shift-in meta-character insertion. Such a COBOL definition might look like:

    01 MY_RECORD.
       05 SO PIC X.
       05 MY_MBCS_DATA PIC G(50).
       05 SI PIC X.

This is not processed correctly by PGAU, because all three fields are defined, and consequently treated, as separate data items when conversion is performed.

To be properly processed, the definition input to PGAU should be:

    01 MY_RECORD.
       05 MY_MBCS_DATA PIC G(51).

The PGAU `REDEFINE DATA` statement can redefine the 3-field definition to the 1-field definition by specifying `USAGE(SKIP)` on fields `SO` and `SI`, and `'05 MY_MBCS_DATA PIC G(51).'` to redefine `MY_MBCS_DATA`. The three `REDEFINE` statements can be placed in the PGAU input control file, and thus the remote host definition need not be altered.

### Privileges Needed to Use TIPs

Execute privileges must be explicitly granted to callers of TIPs or procedures. This privilege cannot be granted through a role.

Any TIP user wanting to trace a TIP must be granted execute privileges on the rtrace and ptrace procedures. Refer to the "Configuring PGAU" section appropriate for your communications protocol in the installation guides and the [Oracle Database Development Guide](../adfns/security.md) for more information.

For example:

On Microsoft Windows:

    C:\> sqlplus pgaadmin\pw@database_specification_string
    SQL> grant execute on pgaadmin.purge_trace to tip_user_userid;
    SQL> grant execute on pgaadmin.read_trace to tip_user_userid;

On UNIX based systems:

    $ sqlplus pgaadmin/pw@database_specification_string
    SQL> grant execute on pgaadmin.purge_trace to tip_user_userid;
    SQL> grant execute on pgaadmin.read_trace to tip_user_userid;

After a TIP has been developed, the TIP user must be granted execute privileges on the TIP by the TIP owner. The TIP owner is usually `PGAADMIN`, but can be another user who has been granted either the `PGDDDEF` or `PGDDGEN` roles. For example:

For Microsoft Windows:

    C:\> sqlplus tip_owner\pw@database_specification_string
    SQL> grant execute on tipname to tip_user_userid;

For UNIX based systems:

    $ sqlplus tip_owner/pw@database_specification_string
    SQL> grant execute on tipname to tip_user_userid;

where` ``database_specification_string` is the Oracle Net identifier for the Oracle database where the gateway `UTL_RAW` and `UTL_PG` components were installed. This is the same Oracle database where the TIPs are executed and where grants on the TIPs are performed from the TIP owner user ID.

A SQL script for performing these grants is provided in the `%ORACLE_HOME%\dg4appc\admin` directory for Microsoft Windows and `$ORACLE_HOME/dg4appc/admin` in the directory for UNIX based systems. The `pgddausr.sql` script performs the grants for private access to the packages by a single TIP user. If private grants are to be used, the `pgddausr.sql` script must be run once for each TIP user's user ID.

To run these scripts, use SQL\*Plus to connect to the Oracle database as user `PGAADMIN`. From SQL\*Plus, run the `pgddausr.sql` script from the `%ORACLE_HOME%\dg4appc\admin` directory on Microsoft Windows or `$ORACLE_HOME/dg4appc/admin` directory on UNIX based systems. The script performs the necessary grants as previously described. You are prompted for the required user IDs, passwords, and database specification strings. If you are using private grants, repeat this step for each user ID requiring access to the packages.

No script has been provided to perform public grants. To do this, issue the following commands:

For Microsoft Windows:

    C:\> sqlplus tip_owner\pw@database_specification_string
    SQL> grant execute on tipname to PUBLIC;

For UNIX based systems:

    $ sqlplus tip_owner/pw@database_specification_string
    SQL> grant execute on tipname to PUBLIC;
