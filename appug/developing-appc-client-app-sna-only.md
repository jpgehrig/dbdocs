The following sections discuss how you will call a TIP and control a remote host transaction. It also provides you with the steps for preparing and executing a gateway transaction. The following assumptions are made:

- a remote host transaction (RHT) has already been written

- a TIP corresponding to the RHT has already been defined using the steps described in [Creating a TIP](creating-tip-oracle-database-gateway-appc.md)

  **Note:**

  If your gateway uses the TCP/IP support for IMS Connect, refer to [Client Application Development (TCP/IP Only)](developing-appc-client-app-tcpip-only.md) for information about calling a TIP and controlling a remote host transaction.

Topics:

- Overview of Client Application

- Preparing the Client Application

- Understanding the Remote Host Transaction Requirements

- Customized TIPs for Each Remote Host Transaction

- Client Application Requirements

- Ensuring TIP and Remote Transaction Program Correspondence

- Calling the TIP from the Client Application

- Exchanging Data

- Executing the Application

- APPC Conversation Sharing

- Application Development with Multi-Byte Character Set Support

- Modifying a Terminal-Oriented Transaction to Use APPC

- Privileges Needed to Use TIPs

### Overview of Client Application

The Procedural Gateway Administration Utility (PGAU) generates a complete TIP using definitions you provide. The client application can then call the TIP to access the remote host transaction. [Procedural Gateway Administration Utility](pga-utility-oracle-database-gateway-appc.md) , discusses the use of PGAU in detail.

This overview explains what you must do in order to call a TIP and control a remote host transaction.

The gateway receives PL/SQL calls from the Oracle database and issues APPC calls to communicate with a remote transaction program. The following three application programs make this possible:

- an APPC-enabled remote host transaction program

- a Transaction Interface Package, or TIP. A TIP is a PL/SQL package that handles communication between the client and the gateway and performs datatype conversions between COBOL and PL/SQL.

  PGAU generates the TIP specification for you. In the shipped samples, the PGAU-generated package is called `pgadb2i.pkb`. This generated TIP includes at least three function calls that map to the remote transaction program:

  - `pgadb2i_init` initializes the conversation with the remote transaction program

  - `pgadb2i_main` exchanges application data with the remote transaction program

  - `pgadb2i_term` terminates the conversation with the remote transaction program

  Refer to [Tip Internals](tip-internals-oracle-database-gateway-appc.md) for more information about TIPs, if you are writing your own TIP or debugging.

- a client application that calls the TIP.

  The client application calls the three TIP functions with input and output arguments. In the example, the client application passes `empno`, an employee number to the remote transaction and the remote transaction sends back `emprec` an employee record.

Table 4-1 demonstrates the logic flow between the PL/SQL driver, the TIP, and the gateway using the example CICS-DB2 transaction.

Table 4-1 Logic Flow of CICS-DB2 Example

| Client Application | Oracle TIP                                           | Procedures Established Between the Gateway and the Remote Transaction (mainframe)                                                                                                                                                             |
|:-------------------|:-----------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `calls tip_init`   | Calls `PGAINIT`                                      | Gateway sets up control blocks and issues APPC `ALLOCATE`. Mainframe program initiates.                                                                                                                                                       |
| `calls tip_main`   | Calls `PGAXFER` to send `empno` and receive `emprec` | Gateway issues APPC `SEND` to the mainframe. Mainframe `RECEIVE` completes. Mainframe performs application logic and issues APPC `SEND` back to gateway. The gateway- issues APPC `RECEIVE`; receive completes. Mainframe issues APPC `TERM`. |
| `calls tip_term`   | Call `PGATERM`                                       | Gateway cleans up control blocks.                                                                                                                                                                                                             |

A client application which utilizes the gateway to exchange data with a remote host transaction performs some tasks for itself and instructs the TIP to perform other tasks on its behalf. The client application designer must consequently know the behavior of the remote transaction and how the TIP facilitates the exchange.

The following sections provide an overview of remote host transaction behavior, how this behavior is controlled by the client application and how TIP function calls and data declarations support the client application to control the remote host transaction. These sections also provide background information about what the TIP does for the client application and how the TIP calls exchange data with the remote host transaction.

### Preparing the Client Application

To prepare the client application for execution you must understand the remote host transaction requirements and then perform these steps:

1.  Move relevant COBOL records layout (copybooks) to the gateway system for input to PGAU.
2.  Describe the remote host transaction data and calls to the PG Data Dictionary (PG DD) with `DEFINE DATA`, `DEFINE CALL`, and `DEFINE TRANSACTION` statements.
3.  Generate the TIP in the Oracle database, using `GENERATE`.
4.  Create the client application that calls the TIP public functions.
5.  Grant privileges on the newly created package.

### Understanding the Remote Host Transaction Requirements

Browse through the remote host transaction program (RTP) to determine:

- the PL/SQL parameters required on the various client application to TIP calls

- the order in which the calls are made

Identify the remote host transaction program (RTP) facilities to be called and the data to be exchanged on each call. You will then define the following, and store them in the PG DD:

- `DEFINE DATA`

- `DEFINE CALL`

- `DEFINE TRANSACTION`

Refer to [Creating a TIP](creating-tip-oracle-database-gateway-appc.md) for specific definition steps and for the actual creation and generation of a TIP.

#### TIP Content and Purpose

The content of a PGAU-generated TIP reflects the calls available to the remote host transaction and the data that has been exchanged. Understanding this content helps when designing and debugging client applications that call the TIP.

A TIP is a PL/SQL package, and accordingly has two sections:

- A Package Specification containing:

  - Public function prototypes and parameters, and

- A Package Body containing:

  - Private functions and internal control variables

  - Public functions

  - Package initialization following the last public function.

The purpose of the TIP is to provide a PL/SQL callable public function for every allowed remote transaction program interaction. A remote transaction program interaction is a logically related group of data exchanges through one or more `PGAXFER` RPC calls. This is conceptually similar to a screen or menu interaction in which several fields are filled in, the enter key is pressed, and several fields are returned to the user. Carrying the analogy further:

- the user might be likened to the TIP or client application

- fields to be filled in are `IN` parameters on the TIP function call

- fields returned are `OUT` parameters on the TIP function call

- screen or menu is the group of `IN` and `OUT` parameters combined

- a pressed enter key is likened to the `PGAXFER` remote procedural call (RPC)

The actual grouping of parameters that constitute a transaction call is defined by the user. The gateway places no restrictions on how a remote transaction program might correspond to a collection of TIP function calls, each call having many `IN` and `OUT` parameters.

PGA users typically have one TIP per remote transaction program. How the TIP function calls are grouped and what data parameters are exchanged on each call depends on the size, complexity and behavior of the remote transaction program.

Refer to Oracle's [Oracle Database PL/SQL Language Reference](../lnpls/index.md) for a discussion of how PL/SQL packages work. The following discussion covers the logic that must be performed within a TIP. Refer to the sample TIP and driver supplied in the `%ORACLE_HOME%\dg4appc\demo\CICS `directory for Microsoft Windows or `$ORACLE_HOME/dg4appc/demo/CICS` directory for UNIX based systems, in files `pgadb2i.pkh`, `pgadb2i.pkb`, and `pgadb2id.sql`.

#### Remote Host Transaction Types

From a database gateway application perspective, there are three main types of remote host transactions:

- one-shot

- persistent

- multi-conversational

##### One-Shot Transactions

A simple remote transaction program which receives one employee number and returns the employee record could have a TIP which provides one call, passing the employee number as an `IN` parameter and returning the employee record as an `OUT` parameter. An additional two function calls must be provided by this and every TIP:

- a remote transaction program init function call

- a remote transaction program terminate function call

The most simple TIP has three public functions, such as `tip_init`, `tip_main`, and `tip_term`.

The client application calls `tip_init`, `tip_main`, and `tip_term` in succession. The corresponding activity at the remote site is remote transaction program start, data exchange, and remote transaction program end.

The remote transaction program might even terminate itself before receiving a terminate signal from the gateway. This sequence is usual and is handled normally by gateway logic. This kind of remote transaction program is termed one-shot.

##### Persistent Transactions

A more complex remote transaction program has two modes of behavior: an `INQUIRY` or reporting mode, and an `UPDATE` mode. These modes can have two TIP data transfer function calls: one for `INQUIRY` and one for `UPDATE`. Such a TIP might have five public functions. For example:

- `tip_init`

  This initializes communications with the remote transaction program.

- `tip_mode`

  This accepts a mode selection parameter and puts the transaction program into either inquiry or update mode.

- `tip_inqr`

  This returns an employee record for a given employee number.

- t`ip_updt`

  This accepts an employee record for a given employee number.

- `tip_term`

  This terminates communications with the remote transaction program.

The client application calls `tip_init` and then `tip_mode` to place the remote transaction program in inquiry mode which then scans employee records, searching for some combination of attributes (known to the client application and end-user). Some parameter on an inquiry call is then set to signal a change to update mode and the client application calls `tip_updt` to update some record. The client application finally calls `tip_term` to terminate the remote transaction program.

The corresponding activity at the remote site is:

- remote transaction program start

- mode selection exchange

- loop reading records

- switch to update mode

- update one record

- remote transaction program end

Such a remote transaction program is called persistent because it interacts until it is signalled to terminate.

The remote transaction program can be written to permit a return to inquiry mode and repeat the entire process indefinitely.

##### Multi-Conversational Transactions

A client application might need to get information from one transaction, `tran_A`, and subsequently write or lookup information from another, `tran_B`. This is possible with a properly written client application and TIPs for `tran_A` and `tran_B`. In fact, any number of transactions might be concurrently controlled by a single client application. All transactions could be read-only, with the client application retrieving data from each and consolidating it into a local Oracle database or displaying it in an Oracle Form.

Alternatively, a transaction could be capable of operating in different modes or performing different services depending on what input selections were supplied by the client application. For example, one instance of `tran_C` can perform one service while a second instance of `tran_C` performs a second service. Each instance of `tran_C` would have its own unique conversation with the client application and each instance could have its own behavior (one-shot or persistent) depending on the nature of the service being performed.

### Customized TIPs for Each Remote Host Transaction

Each remote host system might have hundreds of remote transaction programs (RTPs) which a user might want to call. Each remote transaction program is different, passes different data, and performs different functions. The interface between the user and each remote transaction program must consequently be specialized and customized to the user's requirements for each remote transaction program. The Transaction Interface Package provides this customized interface.

#### Example

Assume that the remote site has a transaction program which manages employee information in an employee database or other file system. The remote transaction program's name, in the remote host, is `EMPT` for Employee Tracking. `EMPT` provides both inquiry and update facilities, and different Oracle users are required to access and use these `EMPT` facilities.

Some users might be restricted to inquiry-only use of `EMPT`, while others might have update requirements. In support of the Oracle users' client applications, at least three possible TIPs could exist:

1.  `EMP_MGMT` to provide access to all facilities of the `EMPT` remote transaction program.

2.  `EMP_UPDT` to access only the update functions of the `EMPT` remote transaction program.

3.  `EMP_INQR` to access only the lookup functions of the `EMPT` remote transaction program.

End-user access to these TIPs is controlled by Oracle privileges. Additional security might be imposed on the end-user by the remote host.

Each TIP also has encoded within it the name of the remote transaction program (`EMPT`) and network information sufficient to establish an APPC conversation with `EMPT`.

### Client Application Requirements

Using the TIP, the client application must correspond with and control the remote host transaction. This involves:

- client application initialization

- user input and output

- remote host transaction initialization using the TIP initialization functions (with and without overrides)

- remote host transaction control and data exchange using the TIP user functions

- remote host transaction termination using the TIP termination function

  The preceding three steps vary, based on the requirements of the remote host transaction.

- exception handling

- client application termination

#### One-shot remote host transaction client applications must:

- Declare RHT/TIP datatypes to be exchanged. All client applications must declare variables to be exchanged with the RHTs using TIPs. PL/SQL datatypes for such variables have already been defined in the TIP corresponding to each RHT and the client application need only reference the TIP datatype in its declaration. Refer also to "Declaring TIP Variables" for more information. Also refer to the TIP content documentation file for the specific TIP/RHT for more information about the exact usage of these variables.

- Initialize the RHT using the TIP initialization function. The TIP directs the gateway server to initialize a conversation with the desired RHT, specifying either default RHT identifying parameters (supplied when the RHT was defined in the PG DD and encoded within the TIP when it was generated) or override RHT identifying parameters supplied by the user or client application when the TIP initialization function is called. Refer to "Initializing the Conversation" and "Overriding TIP Initializations" for more details.

- Exchange data with the RHT using the TIP user function (one call). As previously discussed, a one-shot remote host transaction only accommodates a single data exchange and upon completion of that exchange, the RHT terminates on its own. The client application consequently needs only to execute a single call to the user-defined TIP function to cause the data exchange.

  Refer to the TIP content documentation file in `%ORACLE_HOME%\dg4appc\demo\CICS\` on Microsoft Windows or `$ORACLE_HOME/dg4appc/demo/CICS/` on UNIX based systems, for the specific TIP/RHT for the exact syntax of this call.

  The client application should initialize values into `IN` or `IN OUT` parameter values before calling the TIP function call. These are the same variables that were declared above, when you declared the RHT/TIP datatypes to be exchanged.

  All TIP function calls return a `0` return code value and all returned user gateway data values are exchanged in the function parameters. Any exception conditions are raised as required and can be intercepted in an exception handler.

  Upon return from the TIP function call, the client application can analyze and operate on the `IN OUT` or `OUT` parameter values. These are the same variables that were declared above, when you declared the RHT/TIP datatypes to be exchanged.

  Refer to [Datatype Conversions](data-type-conversion-oracle-database-gateway-appc.md) for details about how TIPs convert the various types and formats of remote host data.

- Terminate the RHT using the TIP termination function. Regardless of the type of RHT being accessed, the TIP terminate function should be called to clean up and terminate the conversation with the RHT. Conversations with one-shot RHTs can be terminated from the gateway server before the RHT terminates. The TIP must perform its cleanup as well. Cleanup is only performed at the termination request of the client application.

  The client application can request a normal or an aborted termination.

  Refer to "Terminating the Conversation" for more information.

#### Persistent remote host transaction client applications must:

- Declare RHT/TIP datatypes to be exchanged. All client applications must declare variables to be exchanged with the RHTs using TIPs. PL/SQL datatypes for such variables have already been defined in the TIP corresponding to each RHT; the client application need only reference the TIP datatype in its declaration. Refer to "Declaring TIP Variables" for more information. Refer also to the TIP content documentation file for the specific TIP/RHT for more information about the exact usage of these variables.

- Initialize the RHT using the TIP initialization function. The TIP directs the gateway server to initialize a conversation with the desired RHT, specifying either default RHT identifying parameters (supplied when the RHT was defined in the PG DD and encoded within the TIP when it was generated) or override RHT identifying parameters supplied by the user or client application when the TIP initialization function is called. Refer to "Initializing the Conversation" and "Overriding TIP Initializations" for more details.

- Repetitively exchange data with RHT using the TIP user function(s). Remote host transactions that provide or require ongoing or repetitive control sequences should be controlled by the client application in the same manner that the RHT would be operated by an interactive user or other control program. The intercession of the TIP and gateway server does not alter the RHT behavior; instead, it extends control of that behavior to the client application using the various function calls defined in the TIP.

  A persistent RHT can be controlled with one or more TIP function calls. The RHT might be designed, for example, to loop and return output for every input until the conversation is explicitly terminated. Or it could have been designed to accept as input a count or list of operations to perform and return the results in multiple exchanges for which the TIP function has only `OUT` parameters.

  A persistent RHT can also be interactive, each output being specified by a previous input selection and ending only when the conversation has been explicitly terminated by the client application.

  The TIP function calls available to the client applications and their specific syntax is documented in the TIP Content documentation file for the specific TIP/RHT.

  The manner in which the RHT interprets the TIP `IN` parameters and returns TIP `OUT` parameters must be determined from the RHT or explained by the RHT programmer. The TIP provides the function calls and the exchanged parameter datatypes to facilitate the client application's control of the RHT and imposes no limitations or preconditions on the sequence of operations the RHT is directed to perform. The TIP provides the client application with the calls and data parameters the RHT was defined to accept in the PG DD.

- Terminate the RHT using the TIP termination function. Regardless of the type of RHT being accessed, the TIP terminate function should be called to clean up and terminate the conversation with the RHT. Conversations with persistent RHTs can be terminated from the gateway server before the RHT terminates, or the RHT might have already terminated. The TIP must perform its cleanup as well and this cleanup is only performed at the termination request of the client application.

  The client application can request a normal or an aborted termination.

  Refer to "Terminating the Conversation" for more information.

#### Multi-conversational remote host transaction client applications must:

- Declare RHT/TIP datatypes to be exchanged. All client applications must declare variables to be exchanged with the RHTs using TIPs. PL/SQL datatypes for such variables have already been defined in the TIP corresponding to each RHT, and the client application need only reference the TIP datatype in its declaration. Refer to "Declaring TIP Variables" for more information. Also refer to the TIP content documentation file for the specific TIP/RHT for more information about the exact usage of these variables.

- Initialize each RHT involved, using the TIP initializing function. A specific customized TIP exists for each RHT as defined in the PG DD. Client applications that control multiple RHTs are multi-conversational and must start each RHT and its associated conversation. This is done by calling each TIP initialization function as before; but multiple TIPs are initialized.

  If a single RHT is designed to perform multiple services for one or more callers and if the client application is designed to use this RHT, the TIP corresponding to that RHT can be initialized multiple times by the client application.

  The client application subsequently distinguishes from active RHTs under its control using:

  - TIP schema `tipname.callname` when multiple TIP/RHTs are being controlled. By encoding the same TIP schema name on TIP user calls, the client application specifies to which RHT the call is being made.

  - `tranuse` `IN OUT` parameter value when multiple instances of the same TIP/RHT are being controlled. This is the value returned on the TIP initialization function call and subsequently passed as an `IN` parameter on the user-defined TIP function calls. The returned `tranuse` value corresponds to that conversation connected to a given instance of an RHT. By supplying the same `tranuse` value on TIP user calls, the client application specifies to which RHT instance the given RHT call is being made.

  Client application logic must keep track of which RHTs have been started and which TIPs and `tranuse` values correspond to started RHTs.

- Exchange data with each RHT, using the TIP user function(s), either once or repetitively if the RHT is one-shot or persistent. Client application logic must sequence the RHTs though their allowed steps in accordance with proper RHT operation, as does a user operating the RHTs interactively.

  Client application logic must also perform any cross-RHT result analysis or data transfer that might be required. All TIPs execute in isolation from each other.

  Output from one RHT intended as input to another RHT must be received in the client application as an `IN` or `IN OUT` parameter from the first RHT and sent as an `IN` or `IN OUT` parameter from the client application to the second RHT. All TIP-to-RHT function calls must be performed by the client application and data parameters exchanged must have been declared as variables by the client application. The TIPs provide both the required datatype definitions and the RHT function calls for the client application.

  Refer to the TIP content documentation file for each specific TIP/RHT for the exact syntax of the TIP function calls and definitions of the parameter datatypes exchanged.

- Terminate each initialized RHT, using the TIP termination function. To terminate an RHT, its corresponding TIP termination function must be called to terminate the RHT and its conversation and to initiate TIP cleanup. The RHT to be terminated is specified by its TIP schema name (the same schema as for its data exchange function calls) and the `tranuse` value when multiple instances of the same RHT are being terminated.

  RHTs and their corresponding TIPs can be terminated in any sequence desired by the client application and do not have to be terminated in the same order in which they are initialized.

  **Note:**

  The specific syntax of the various TIP data exchange variables function calls is the same as was previously defined in the PG DD for the particular RHT and can be researched by examining the TIP content documentation file (`tipname.doc`) or the TIP specification file produced when the TIP was generated. If a TIP has not yet been generated for the RHT being accessed, refer to [Creating a TIP](creating-tip-oracle-database-gateway-appc.md), and "DATA Correspondence", "CALL Correspondence", and "TRANSACTION Correspondence" for more information. It is preferable to define and generate the TIP first, however, so that the client application reference documentation is available to you when needed.

### Ensuring TIP and Remote Transaction Program Correspondence

A remote host transaction program and its related TIP with client application must correspond on two key requirements:

- Parameter datatype conversion, which results from the way in which transaction `DATA` is defined. Refer to [Datatype Conversions](data-type-conversion-oracle-database-gateway-appc.md) for a discussion of how PGAU-generated TIPs convert data based on the data definitions.

- APPC send/receive synchronization, which results from the way in which transaction `CALL`s are defined

These `DATA` and `CALL` definitions are then included by reference in a `TRANSACTION` definition.

#### DATA Correspondence

Using data definitions programmed in the language of the remote host transaction, the PGAU `DEFINE DATA` command stores in the PG DD the information needed for PGAU `GENERATE` to create the TIP function logic to perform:

- all data conversion from PL/SQL `IN` parameters supplied by the receiving remote host transaction

- all buffering into the format expected by the receiving remote host transaction

- all data unbuffering from the format supplied by the sending remote host transaction

- all data conversion to PL/SQL `OUT` parameters supplied by the sending remote host transaction

PGAU determines the information needed to generate the conversion and buffering logic from the data definitions included in the remote host transaction program. PGAU `DEFINE DATA` reads this information from files, such as COBOL copy books, or in-stream from scripts and saves it in the PG DD for repeated use. The gateway Administrator needs to transfer these definition files from the remote host to the Oracle host where PGAU runs.

From the data definitions stored in the PG DD, PGAU `GENERATE` determines the remote host datatype and matches it to an appropriate PL/SQL datatype. It also determines data lengths and offsets within records and buffers and generates the needed PL/SQL logic into the TIP. Refer to the PGAU "[DEFINE DATA](pga-utility-oracle-database-gateway-appc.md)" statement in [Procedural Gateway Administration Utility](pga-utility-oracle-database-gateway-appc.md) and "[Sample PGAU DEFINE DATA Statements](admin-utility-samples-oracle-database-gateway-appc.md)" in [Administration Utility Samples](admin-utility-samples-oracle-database-gateway-appc.md) for more information.

All data that are referenced as parameters by subsequent calls must first be defined using PGAU `DEFINE DATA`. Simple data items, such as single numbers or character strings, and complex multi-field data aggregates, such as records or structures, can be defined. PGAU automatically generates equivalent PL/SQL variables and records of fields or tables for the client application to reference in its calls to the generated TIP.

As discussed, a parameter might be a simple data item, such as an employee number, or a complex item, such as an employee record. PGAU `DEFINE DATA` automatically extracts the datatype information it needs from the input program data definition files.

In this example, `empno` and `emprec` are the arguments to be exchanged.

    pgadb2i_main(trannum,empno,emprec)

A PGAU `DEFINE DATA` statement must therefore be issued for each of these parameters:

    DEFINE DATA EMPNO
           PLSDNAME (EMPNO)
           USAGE (PASS)
           LANGUAGE (IBMVSCOBOLII)
           (
           01 EMP-NO PIC X(6).
           );

    DEFINE DATA EMPREC
           PLSDNAME (DCLEMP)
           USAGE (PASS)
           LANGUAGE (IBMVSCOBOLII)
           INFILE("emp.cob");

Note that a definition is not required for the `trannum` argument. This is the APPC conversation identifier and does not require a definition in PGAU.

#### CALL Correspondence

The requirement to synchronize APPC `SEND`s and `RECEIVE`s means that when the remote transaction program expects data parameters to be input, it issues APPC `RECEIVE`s to read the data parameters. Accordingly, the TIP must cause the gateway to issue APPC `SEND`s to write the data parameters to the remote transaction program. The TIP must also cause the gateway to issue APPC `RECEIVE`s when the remote transaction program issues APPC `SEND`s.

The PGAU `DEFINE CALL` statement specifies how the generated TIP is to be called by the client application and which data parameters are to be exchanged with the remote host transaction for that call. Each PGAU `DEFINE CALL` statement might specify the name of the TIP function, one or more data parameters, and the `IN/OUT` mode of each data parameter. Data parameters must have been previously defined with PGAU `DEFINE DATA` statements. Refer to "[DEFINE CALL](pga-utility-oracle-database-gateway-appc.md)" in [Procedural Gateway Administration Utility](pga-utility-oracle-database-gateway-appc.md) and "[Sample PGAU DEFINE CALL Statements](admin-utility-samples-oracle-database-gateway-appc.md)" in [Administration Utility Samples](admin-utility-samples-oracle-database-gateway-appc.md) for more information.

PGAU `DEFINE CALL` processing stores the specified information in the PG DD for later use by PGAU `GENERATE`. PGAU `GENERATE` then creates the following in the TIP package specification:

- declarations of public PL/SQL functions for each `CALL` defined with PL/SQL parameters for each `DATA` definition specified on the `CALL`

- declarations of the public PL/SQL data parameters

The client application calls the TIP public function as a PL/SQL function call, using the function name and parameter list specified in the PGAU `DEFINE CALL` statement. The client application might also declare, by reference, private variables of the same datatype as the TIP public data parameters to facilitate data passing and handling within the client application, thus sharing the declarations created by PGAU `GENERATE`.

In this example, the following PGAU `DEFINE CALL` statement must be issued to define the TIP public function:

    DEFINE CALL DB2IMAIN
           PKGCALL (pgadb2i_main)
           PARMS ((empno IN),(emprec OUT));

##### Flexible Call Sequence

The number of data parameters exchanged between the TIP and the gateway on each call can vary at the user's discretion, as long as the remote transaction program's `SEND/RECEIVE` requests are satisfied. For example, the remote transaction program data exchange sequence might be:

    APPC SEND    5 fields  (field1-field5)
    APPC RECEIVE 1 fields  (field6)
    APPC SEND    1 field   (field7)
    APPC RECEIVE 3 fields  (field8 - field10)

The resulting TIP/application call sequence could be:

    tip_call1(parm1 OUT,  <-- APPC SEND field1 from remote TP
             parm2 OUT,  <-- APPC SEND field2 from remote TP
             parm3 OUT); <-- APPC SEND field3 from remote TP

    tip_call2(parm4 OUT,  <-- APPC SEND field4 from remote TP
             parm5 OUT); <-- APPC SEND field5 from remote TP
    tip_call3(parm6 IN OUT); --> APPC RECEIVE field6 in remote TP
                             <-- APPC SEND field7 from remote TP

    tip_call4(parm8 IN,   --> APPC RECEIVE field8 into remote TP
              parm9 IN,   --> APPC RECEIVE field9 into remote TP
              parm10 IN); --> APPC RECEIVE field10 into remote TP

To define these four public functions to the TIP, four PGAU `DEFINE CALL` statements must be issued, each specifying its unique public function name (`tip_callx`) and the data parameter list to be exchanged. Once a data item is defined using `DEFINE DATA`, it can be referenced in multiple calls in any mode (`IN`, `OUT`, or` IN OUT`). For example, `parm5` could be used a second time in place of `parm6`. This implies the same data is being exchanged in both instances, received into the TIP and application on ` tip_call2` and returned, possibly updated, to the remote host in `tip_call4`.

Notice also that the remote transaction program's first five written fields are read by two separate TIP function calls, `tip_call1` and `tip_call2`. This could also have been equivalently accomplished with five TIP function calls of one `OUT` parameter each or a single TIP function call with five `OUT` parameters. Then the remote transaction program's first read field (`field6`) and subsequent written field (`field7`) correspond to a single TIP function call (`tip_call3`) with a single `IN OUT `parameter (`parm6`).

This use of a single `IN OUT` parameter implies that the remote transaction program's datatype for `field6` and `field7` are both the same and correspond to the conversion performed for the datatype of `parm6`. If `field6` and `field7` were of different datatypes, then they have to correspond to different PL/SQL parameters (for example, `parm6` `IN` and `parm7` `OUT`). They could still be exchanged as two parameters on a single TIP call or one parameter each on two TIP calls, however.

Lastly, the remote transaction program's remaining three `RECEIVE` fields are supplied by `tip_call4` parameters 8-10. They also could have been done with three TIP calls passing one parameter each or two TIP calls passing one parameter on one call and two parameters on the other, in either order. This flexibility permits the user to define the correspondence between the remote transaction program's operation and the TIP function calls in whatever manner best suits the user.

##### Call Correspondence Order Restrictions

Each TIP public function first sends all `IN` parameters, before it receives any `OUT` parameters. Thus, a remote transaction program expecting to send one field and then receive one field must correspond to separate TIP calls.

For example:

    tip_callO( parmO OUT); <-- APPC SEND outfield from remote TP

`PGAXFER` RPC checks first for parameters to send, but finds none and proceeds to receive parameters:

    tip_callI( parmI IN);  --> APPC RECEIVE infield to remote TP

`PGAXFER` RPC processes parameters to send and then checks for parameters to receive, but finds none and completes; therefore, a single TIP public function with an `OUT` parameter followed by an `IN` parameter does not work, because the `IN` parameter is processed first--regardless of its position in the parameter list.

#### TRANSACTION Correspondence

The remote host transaction is defined with the PGAU` DEFINE TRANSACTION` statement with additional references to prior definitions of `CALL`s that the transaction supports.

You specify the remote host transaction attributes, such as:

- transaction ID or name

- network address or location

- system type (such as IBM370)

- Oracle National Language of the remote host

  **Note:**

  The PL/SQL package name is specified when the transaction is defined; this is the name by which the TIP is referenced and which the public function calls to be included within the TIP. Each public function must have been previously defined with a PGAU `DEFINE CALL` statement, which has been stored in the PG DD. If you do not specify a package name (TIP name) in the `GENERATE` statement, the transaction name you specified will become the package name by default. In that case, the transaction name (`tname) `must be unique and must be in valid PL/SQL syntax within the database containing the PL/SQL packages.

  For more information, refer to "[DEFINE TRANSACTION](pga-utility-oracle-database-gateway-appc.md)" in [Procedural Gateway Administration Utility](pga-utility-oracle-database-gateway-appc.md) and "[Sample PGAU DEFINE TRANSACTION Statement](admin-utility-samples-oracle-database-gateway-appc.md)" in [Administration Utility Samples](admin-utility-samples-oracle-database-gateway-appc.md).

In this example, the following `DEFINE TRANSACTION` statements are used to define a remote CICS transaction called `DB2I`:

    DEFINE TRANSACTION DB2I
       CALL (   DB2IMAIN,
                DB2IDIAG   )
       SIDEPROFILE(CICSPROD)
       TPNAME(DB2I)
       LOGMODE(ORAPLU62)
       SYNCLEVEL(0)
       NLS_LANGUAGE("AMERICAN_AMERICA.WE8EBCDIC37C");

### Calling the TIP from the Client Application

Once a TIP is created, a client application must be written to interface with the TIP. A client application that calls the TIP functions must include five logical sections:

- declaring TIP variables

- initializing the conversation

- exchanging data

- terminating the conversation

- error handling

#### Declaring TIP Variables

The user declarations section of the `tipname.doc` file documents the required declarations.

When passing PL/SQL parameters on calls to TIP functions, the client application must use the exact same PL/SQL datatypes for TIP function arguments as are defined by the TIP in its specification section. Assume, for example, the following is in the TIP specification, or `tipname.doc:`

    FUNCTION tip_call1    tranuse,   IN      BINARY_INTEGER,
                          tip_var1   io_mode pls_type1,
                          tip_record io_mode tran_rectype)
    RETURN INTEGER;

    TYPE  tran_rectype is RECORD
          (rec_field1 pls_type1,
          ...
          rec_fieldN pls_typeN);

Table 4-2 provides a description of the function declarations:

Table 4-2 Function Declarations

| Item           | Description                                                                                                                                            |
|:---------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------|
| `tip_call1`    | The TIP function name as defined in the package specification.                                                                                         |
| `tranuse`      | The remote transaction instance parameter returned from the TIP init function identifying the conversation on which this TIP call is to exchange data. |
| `tran_rectype` | The PL/SQL record datatype declared in the `tipname`TIP specification. This is the same value as in the TYPE`tran_rectype`` is RECORD` statement.      |
| `pls_typeN`    | Is a PL/SQL atomic datatype.                                                                                                                           |
| `rec_fieldN`   | Is a PL/SQL record field corresponding to a remote transaction program record field.                                                                   |

In the client application PL/SQL atomic datatypes should be defined as the exact same datatype of their corresponding arguments in the TIP function definition. The following should be coded in the client application before the `BEGIN` command:

    appl_var  pls_type1;    /* declare appl variable for ....  */

TIP datatypes need not be redefined. They must be declared `locally` within the client application, appearing in the client application before the `BEGIN`:

    appl_record tipname.tran_rectype;  /* declare appl record */

Table 4-3 describes the command line arguments:

Table 4-3 Command Line Arguments

| Item           | Description                                                                                                                                            |
|:---------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------|
| `tip_call1`    | The TIP function name as defined in the package specification.                                                                                         |
| `tranuse`      | The remote transaction instance parameter returned from the TIP init function identifying the conversation on which this TIP call is to exchange data. |
| `tran_rectype` | The PL/SQL record datatype declared in the `tipname`TIP specification. This is the same value as in the `TYPE``tran_rectype`` is RECORD` statement.    |

Refer to the `tipname``.doc` content file for a complete description of the user declarations you can reference.

The client application calls the TIP public function as if it were any local PL/SQL function:

    rc = tip_call1( tranuse,
                    appl_var,
                    appl_record);

In the CICS-DB2 inquiry example, the PL/SQL driver `pgadb2id.sql`, which islocated in `%ORACLE_HOME%\dg4appc\demo\CICS` directory for Microsoft Windows and `$ORACLE_HOME/dg4appc/demo/CICS` directory for UNIX based systems, is the client application and includes the following declaration:

    ...
    ...
    CREATE or REPLACE PROCEDURE db2idriv(empno IN CHAR) IS
    tranuse INTEGER :=0               /* transaction usage number     */
    DCLEMP PGADB2I.DCLEMP_typ;        /* DB2 EMP row definition       */
    DB2 PGADB2I.DB2_typ;              /* DB2 diagnostic information   */
    rc INTEGER :=0                    /* PGA RPC return codes         */
    line VARCHAR2(132);               /* work buffer for output       */
    term INTEGER :=0;                 /* 1 if pgadb2i_term called     */
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

- The transaction instance number for RHT conversation identification. The `tranuse` parameter is required on all TIP initializations.

- TIP diagnostic flags for TIP runtime diagnostic controls. The `tipdiag` parameter is optional. Refer to [Troubleshooting](troubleshooting-oracle-database-gateway-appc.md) for a discussion of TIP diagnostics.

- TIP default overrides for overriding OLTP and network attributes. The `override` parameter is optional.

The following four functions are shown as they might appear in the TIP Content documentation file. Examples of client application use are provided later.

    TYPE override_Typ IS RECORD (
            tranname  VARCHAR2(255),  /* Transaction Program     */
            transync  BINARY_INTEGER, /* RESERVED                */
            trannls   VARCHAR2(50),   /* RESERVED                */
            oltpname  VARCHAR2(255),  /* Logical Unit            */
            oltpmode  VARCHAR2(255),  /* LOG Mode Entry          */
            netaddr   VARCHAR2(255),  /* Side Profile            */
            oltpuser  VARCHAR2(8),    /* userid for OLTP access  */
            oltppass  VARCHAR2(8));   /* password for OLTP access*/

    FUNCTION pgadb2i_init(                /* init standard */
               tranuse IN OUT BINARY_INTEGER)
               RETURN INTEGER;

    FUNCTION pgadb2i_init(                /* init override */
               tranuse IN OUT BINARY_INTEGER,
               override IN override_Typ)
               RETURN INTEGER;

    FUNCTION pgadb2i_init(               /* init diagnostic */
               tranuse IN OUT BNARY_INTEGER,
               tipdiag IN CHAR)
               RETURN INTEGER;

    FUNCTION pgadb2i_init(                /* init over-diag */
               tranuse IN OUT BINARY_INTEGER,
               override IN override_Typ,
               tipdiag IN CHAR)
               RETURN INTEGER;

##### Transaction Instance Parameter

This transaction instance number (shown in examples as `tranuse`) must be passed to subsequent TIP exchange and terminate functions. It identifies to the gateway on which APPC conversation--and therefore which iteration of a remote transaction program--the data is to be transmitted or communication terminated.

A single client application might control multiple instances of the same remote transaction program or multiple different remote transaction programs, all concurrently. The transaction instance number is the TIP‘s mechanism for routing the client application call through the gateway to the intended remote transaction program.

It is the responsibility of the client application to save the transaction instance number of each active transaction and pass the correct one to each TIP function called for that transaction.

The client application calls the TIP initialization function as if it were any local PL/SQL function. For example:

    ...
    ...
    tranuse INTEGER := 0;/* transaction usage number*/
    ...
    ...
    BEGIN
     rc := pgadb2i.pgadb2i_init(tranuse);
    ...
    ...

##### Overriding TIP Initializations

Note that in the preceding example the client application did not specify any remote transaction program name, network connection, or security information. The TIP has such information internally coded as defaults and the client application simply calls the appropriate TIP for the chosen remote transaction program. The client application can, however, optionally override some TIP defaults and supply security information.

You do not need to change any client applications that do not require overrides.

When the remote host transaction was defined in the PG DD, the `DEFINE TRANSACTION` statement specified certain default OLTP and network identification attributes which can be overridden:

- `TPname`

- `LUname`

- `LOGMODE`

- `Side Profile`

Refer to "[DEFINE TRANSACTION](pga-utility-oracle-database-gateway-appc.md)" in [Procedural Gateway Administration Utility](pga-utility-oracle-database-gateway-appc.md) for more information about the `DEFINE TRANSACTION `statement.

These PG DD-defined transaction attributes are generated into TIPs as defaults and can be overridden at TIP initialization time. This facilitates the use of one TIP, which can be used with a test transaction or system, and can later be used with a production transaction or system, without having to regenerate the TIP.

The `override_Typ` record datatype describes the various transaction attributes that can be overridden by the client application. The following overrides are currently supported:

- `tranname` can be set to override the value that was specified by the `TPNAME` parameter of the `DEFINE TRANSACTION `statement

- `oltpname` can be set to override the value that was specified by the `LUNAME` parameter of the `DEFINE TRANSACTION` statement

- `oltpmode` can be set to override the value that was specified by the `LOGMODE` parameter of the `DEFINE TRANSACTION` statement

- `netaddr` can be set to override the value that was specified by the `SIDEPROFILE` parameter of the `DEFINE TRANSACTION` statement

In addition to the transaction attributes defined in the PG DD, there are two security-related parameters, conversation security user ID and conversation security password, that can be overridden at TIP initialization time. The values for these parameters normally come from either the database link used to access the gateway or the Oracle database session. There are cases when the Oracle database user ID is not sufficient for accessing the OLTP system. The user ID and password overrides provide a way to specify those parameters to the OLTP system.

The following overrides are currently supported:

- `oltpuser` can be set to override the user ID used to initialize the conversation with the OLTP

- `oltppass` can be set to override the password used to initialize the conversation with the OLTP

The security overrides have an effect only if `PGA_SECURITY_TYPE=PROGRAM` is specified in the gateway initialization file, and the OLTP system is configured to accept a user ID and password on incoming conversation requests.

The `transync` (APPC `SYNCLEVEL`) and `trannls` (Globalization Support character set) are defined in the override record datatype, but are reserved for future use. The RHT `SYNCLEVEL` and Globalization Support name cannot be overridden.

The client application might override the default attributes at TIP initialization for the following reasons:

- to start a different version of the RHT (such as production instead of test)

- to change the location of the OLTP containing the RHT (if the OLTP was moved due to migration or a switch to backup configuration)

Client applications requiring overrides can use any combination of override and initialization parameters and might alter the combination at any time without regenerating the TIP or affecting applications that do not override parameters.

To override the TIP defaults, an additional client application record variable must be declared as `override_Typ` datatype, values must be assigned to the override subfields, and the override record variable must be passed on the TIP initialization call from the client application.

For example:

       ...
       ...
       my_overrides pgadb2i.override_Typ;   -- declaration
       ...
       ...
       my_overrides.oltpname := 'CICSPROD'; -- swap to production CICS
       my_overrides.tranname := 'TNEW';     -- new transaction name

    BEGIN
       rc := pgadb2i.pgadb2i_init(tranuse,my_overrides); -- init
       ...
       ...

Within the TIP, override attributes are checked for syntax problems and passed to the gateway server.

##### Security Considerations

The security requirements of the default and overridden OLTPs must be the same because the same gateway server is used in either conversation, as dictated by the database link names in the PGA RPC calls. The gateway server startup security mode is set at gateway server initialization time and passed unchanged to the OLTP at TIP or conversation initialization time.

### Exchanging Data

The client application should pass the transaction instance number, returned from a previous `tip_init` call, to identify which remote transaction program is affected and to identify any client application data parameters to be exchanged with the remote transaction program.

In this CICS-DB2 inquiry example, we pass an employee number and receive an employee record back:

    rc = pgadb2i.pgadb2i_main(tranuse, /* transfer data         */
                               empno,   /* employee number       */
                               DCLEMP); /* return employee record*/

#### Terminating the Conversation

The client application calls the TIP termination function as if it were any local PL/SQL function. For example:

    ...
    ...
    term := 1;    /* indicate term called* */
     rc := pgadb2i.pgadb2i_term(tranuse,0); /* terminate normally  */
    ...
    ...

After a transaction instance number has been passed on a TIP terminate call to terminate the transaction, or after the remote transaction program has abended, that particular transaction instance number may be forgotten.

#### Error Handling

The client application should include an exception handler that can clean up any active APPC conversations before the client application terminates. The sample client application provided in `pgadb2id.sql` contains an example of exception handling.

Gateway exceptions are reported in the range PGA-20900 to PGA-20999. When an exception occurs, the TIP termination function should be called for any active conversations that have been started by prior calls to the TIP initialization function.

For example:

    EXCEPTION
     WHEN OTHERS THEN
      IF term = 0 THEN         /* terminate function not called yet */
       rc := pgadb2i.pgadb2i_term(tranuse,1); /*terminate abnormally*/
      END IF;
     RAISE;
    ...
    ...

The remote transaction should also include provisions for error handling and debugging, such as writing debugging information to the CICS temporary storage queue area. Refer to the [Oracle Database PL/SQL Language Reference](../lnpls/overview-exception-handling.md) for a discussion of how to intercept and handle Oracle exceptions.

#### Granting Execute Authority

The TIP is a standard PL/SQL package and execute authority must be granted to users who call the TIP from their client application. In this example, we grant execute on the `PGADB2I` package to user `SCOTT`:

    GRANT EXECUTE ON PGADB2I TO SCOTT

Refer to the [Oracle Database Administrator's Guide](../admin/getting-started-with-database-administration.md) for further information.

### Executing the Application

Before executing the client application, ensure that a connection to the host is established and that the receiving partner is available. In this example we use PL/SQL driver `DB2IDRIV` to execute the CICS-DB2 inquiry. To execute this client application, enter from SQL\*Plus:

    set serveroutput on
    execute DB2IDRIV('nnnnnn');

### APPC Conversation Sharing

Multiple TIPs can share the same APPC conversation with one or more Remote Host Transactions (RHTs) which are also sharing that same conversation. Two benefits derive from this feature:

- Existing RHTs which rely upon passing control of a conversation are supported by Oracle Database Gateway for APPC.

- TIPs otherwise too large for PL/SQL compilation can be separated into multiple smaller TIPs, each with fewer user-defined functions, providing the client application with the same set of function calls and data definitions without any change to the RHT.

#### APPC Conversation Sharing Concepts

Mainframe OLTPs, such as IMS, allow transactions to share a single APPC conversation by passing it when the transaction calls another transaction. RHTs are defined to PGAU as single transactions with calls, inputs and outputs for which PGAU generates a single TIP with initialization, transfer and termination functions corresponding to that specific RHT.

Logic generated into every TIP allows that TIP either:

- to initiate a new conversation when its init function is called, or

- to transfer data on an existing conversation when its user-defined functions are called, or

- to terminate an existing conversation when its "term" function is called.

An APPC conversation is treated as a resource shared and managed by multiple TIPs. There is no requirement for any TIP to be the sole user of an APPC conversation.

Any TIP generated at 3.4.0 or later can perform any of the following combinations of service:

- initiate

- initiate and transfer

- initiate, transfer, and terminate (standard operation)

- transfer

- transfer and terminate

- terminate

- initiate and terminate (assumes other TIPs perform transfer)

A single APPC conversation can be shared in the following ways:

- from one TIP to multiple RHTs

- from multiple TIPs to one RHT

- from multiple TIPs to multiple RHTs

Without APPC conversation sharing, a single TIP must be defined which contains all functions and data for all RHTs which a client application might need to call. Creating TIPs with a superset of RHTs often causes such TIPs to be too large for PL/SQL to compile.

Conversely, with APPC conversation sharing, each RHT (or even each RHT data exchange for those RHTs which perform multiple, different data exchange operations) can be defined in a single TIP which is smaller and less likely to exceed PL/SQL compilation limits.

#### APPC Conversation Sharing Usage

APPC conversation sharing is automatically available in every TIP generated at 3.4.0 or later. No TIPs generated before 3.4.0 can participate in APPC conversation sharing. TIPs generated before 3.4.0 must be regenerated using PGAU 3.4.0. or later to participate in APPC conversation sharing. PGAU is upward compatible and regeneration should be transparent, provided only the regenerated TIP body (`tipname``.pkb`) is recompiled. If the TIP specification is also recompiled, the client application needs recompilation as well. Refer to [Tip Internals](tip-internals-oracle-database-gateway-appc.md) for more detailed information.

Definition and generation of TIPs is accomplished as previously discussed in Chapters 1, 2, and 3. No additional options or parameters need be specified.

Run-time use of APPC conversation sharing is under the control of the client application. It is accomplished simply by calling the init function of one of the TIPs that share a conversation and passing the `tranuse` value returned to the other TIP functions as each is called in its desired order. Any TIP init function can be used, provided that all TIPs were defined with the same `DEFINE TRANSACTION TPNAME` or `SIDEPROFILE` value. The `TPNAME` or `SIDEPROFILE` value specifies which RHT to initialize.

When the init function of an APPC conversation sharing-capable TIP is called to initialize a conversation, the `tranuse` value returned indicates conversation sharing is enabled. By passing that same `tranuse` value when calling functions in other TIPs, those other TIPs perform their transfers on the same conversation already initialized, provided that all TIPs involved were generated at Version 3.4.0 or later.

#### APPC Conversation Sharing TIP Compatibility

TIPs generated at 3.4.0 or later of the database gateway use and expect different values for `tranuse` than do pre-3.4.0 TIPs. If a pre-3.4.0 TIP is used to initialize a conversation and its `tranuse` value is passed to a 3.4.0 or later generated TIP, the following exception is raised:

    ORA-20704 PGA_TIP: tranuse value cannot be shared

Pre-3.4.0 generated TIPs do not detect the different `tranuse` value for shared conversations, however, and this can result in unpredictable errors.

**Note:**

All TIPs called in a shared conversation must have been generated at 3.4.0 or later.

No TIPs generated before 3.4.0 can participate in APPC conversation sharing.

The `tranuse` values are incompatible between pre-3.4.0 and 3.4.0 or later releases. This should not pose a problem for you for the following reason: before 3.4.0, all RHT functions defined in a TIP had to be called through that TIPs functions, and the init function of that same TIP had to be called first to initialize the conversation. The `tranuse` value was only valid for the TIP which initialized it. Thus, unless you make programming changes, it is not possible for an existing application to accidentally mix `tranuse` values.

Pre-3.4.0 TIPs and client applications can continue to be used without change and old client applications can call new 3.4.0 or later TIPs without change. This is made possible when an old TIP body is regenerated and compiled; the TIP now becomes capable of APPC conversation sharing, even though the old client application has not changed.

None of the functions of a pre-3.4.0 TIP can share an APPC conversation. However, once a TIP is regenerated at 3.4.0 or later, any of its functions can share APPC conversations.

#### APPC Conversation Sharing for TIPs That Are Too Large

You can use conversation sharing to circumvent a TIP that is too large to compile. This is identified by '`PLS-00123 - package too large to compile`', or some other problem symptom such as PL/SQL compilation hanging. In this case you must choose which function calls to remove from the former TIP and define into new TIPs.

Specifically, you must decide which PGAU` DEFINE CALL` statements and their related `DEFINE DATA` statements should be moved from the old PGAU control file (`.ctl`) into one or more new PGAU control files. In addition, you must decide which PGAU `DEFINE TRANSACTION` statements should be included in each new PGAU control file defining each new TIP.

You must consider several PGAU statements; refer to Table 4-4 for a list of the PGAU statements and their descriptions:

Table 4-4 PGAU Statements

| Statement                       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|:--------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `DEFINE DATA` statements        | Must be unique. They can be shared by all affected PGAU control files, provided they are defined to the Procedural Gateway Data Dictionary (PG DD) before being referenced by `DEFINE CALL` statements. No changes are needed to these statements.                                                                                                                                                                                                |
| `DEFINE CALL` statements        | Must be unique. They need only be referenced by the new `DEFINE TRANSACTION` statement of the TIP in which they are included, provided they are defined to the PG DD before being referenced by a `DEFINE TRANSACTION` statement. The `DEFINE CALL` statements can optionally be moved to the new PGAU control file of the TIP in which they are included.                                                                                        |
| `DEFINE TRANSACTION` statements | Specified for each new TIP desired and will reference those call definitions moved from the former large TIP to the new small TIPs. No transaction attributes will change. This allows any new TIP to perform the same initialization or termination with the same RHT as the former large TIP. The old `DEFINE TRANSACTION` statement (of the former large TIP) should now exclude any call definitions which are being moved to new small TIPs. |

#### APPC Conversation Sharing Example

Assume the existence of RHTs `A`, `B` and `C`, and that RHT `A` performs a menu selection and calls RHT `B` for a query function or RHT `C` for an update followed by a select function.

You could define the following `DATA` and `CALL`s:

- `DEFINE DATA` `choice ...`

- `DEFINE DATA` `input ...`

- `DEFINE DATA` `answer ...`

- `DEFINE DATA` `record ... `

- `DEFINE CALL menu_A callname(pick) parms(choice in);`

- `DEFINE CALL query_B callname(query) parms((input in), (answer out));`

- `DEFINE CALL update_C callname(update) parms(record in);`

- `DEFINE CALL select_C callname(select) parms(record out);`

The following example TIPs could be defined:

##### Example 1

This example does not use APPC conversation sharing, but is a valid TIP definition created before release 3.4.0, combining the functions of RHTs `A`, `B` and `C`.

    DEFINE TRANSACTION rhtABC calls(menu_A,
                                    query_B,
                                    update_C,
                                    select_C)
                              tpname(RHTA);

This TIP includes all data definitions and calls, and might be too large to compile. This TIP does not use APPC conversation sharing as there is only the one TIP, `rhtABC`. The RHTs do, however, perform their normal sharing of the conversation at the remote host. If the TIP was small enough to compile, the client application calls TIP functions as follows:

    rc := rhtABC.rhtABC_init(tranuse);
    rc := rhtABC.pick(tranuse, choice);
    rc := rhtABC.query(tranuse, input, answer);
    rc := rhtABC.update(tranuse, record);
    rc := rhtABC.select(tranuse, record);
    rc := rhtABC.rhtABC_term(tranuse);

##### Example 2

This example demonstrates defining a set of TIPs with APPC conversation sharing, separating the functions of RHTs `A`, `B` and `C` into three TIPs:

    DEFINE TRANSACTION rhtA calls(menu_A)   tpname(RHTA);
    DEFINE TRANSACTION rhtB calls(query_B)  tpname(RHTA);
    DEFINE TRANSACTION rhtC calls(update_C,
                                  select_C) tpname(RHTA);

Each TIP includes only the call and data it requires, and each TIP automatically performs APPC conversation sharing. The client application calls these functions as follows:

    rc := rhtA.rhtA_init(tranuse);
    rc := rhtA.pick(tranuse, choice);
    rc := rhtB.query(tranuse, input, answer);
    rc := rhtC.update(tranuse, record);
    rc := rhtC.select(tranuse, record);
    rc := rhtB.rhtB_term(tranuse);

The only client application difference between the two examples is in the schema qualifier on each of the TIP calls. This is because the function being called is in a different TIP which has a different package name in the database.

Only new `DEFINE TRANSACTION` statements were needed to make use of APPC conversation sharing. The `CALL` and `DATA` definitions were used as-is. This means the old TIP `rhtABC` is still defined as it was and might still be too large to compile.

##### Example 3

If you performed Sample 2 but you still believe that the TIP may be too large to compile, try this:

    DEFINE TRANSACTION rhtABC calls(menu_A)   tpname(RHTA);
    DEFINE TRANSACTION rhtB   calls(query_B)  tpname(RHTA);
    DEFINE TRANSACTION rhtCU  calls(update_C) tpname(RHTA);
    DEFINE TRANSACTION rhtCS  calls(select_C) tpname(RHTA);

TIP `rhtABC` has had three functions removed so it is now smaller and more likely to compile. TIP `rhtB` has one function and TIP `rhtC` has been separated into two TIPs even though the corresponding host functions remain in a single RHT.

The client application calls these functions as follows:

    rc := rhtB.rhtB_init(tranuse);
    rc := rhtABC.pick(tranuse, choice);
    rc := rhtB.query(tranuse, input);
    rc := rhtCU.update(tranuse, record);
    rc := rhtCS.select(tranuse, record);
    rc := rhtABC.rhtABC_term(tranuse);

A different TIP is used for initialization, illustrating that all TIPs contain the init and term functions, and because the `DEFINE TRANSACTION `statements all specified the same `tpname(RHTA)`, the same remote host transaction is always called for initialization.

#### APPC Conversation Sharing Overrides and Diagnostics

TIP default override parameters are processed in the TIP init function which was called to perform initialization. Once the APPC conversation is established, no further sharing of overriding parameters is necessary. You need do nothing more than pass the overrides to the TIP init function.

TIP diagnostic parameters are shared among all TIPs sharing a given conversation. In effect, requesting diagnostics of the TIP performing initialization causes the same diagnostics to be requested of all TIPs sharing the conversation. Requesting diagnostics from only one TIP of several sharing a conversation is not possible. The application designer or user need only pass the TIP runtime trace controls to the TIP init function.

### Application Development with Multi-Byte Character Set Support

COBOL presently only supports double byte character sets (DBCS) for `PIC G` datatypes.

PGAU processes COBOLII `PIC G` datatypes as PL/SQL `VARCHAR2` variables and generates TIPs which automatically convert the data according to the Oracle `NLS_LANGUAGE`s specified for the remote host data and the local Oracle data.

These Oracle `NLS_LANGUAGE`s can be specified as defaults for all `PIC G `data exchanged by the TIP with the remote transaction (see `DEFINE TRANSACTION` `... ``REMOTE_MBCS` or `LOCAL_MBCS`). The Oracle `NLS_LANGUAGE`s for any individual `PIC G` data item can be further overridden (see `REDEFINE DATA` `... ``REMOTE` or `LOCAL_LANGUAGE`).

DBCS data can be encoded in any combination of supported DBCS character sets. For example, a remote host application which allows different codepages for each field of data in a record is supported by the Oracle Database Gateway MBCS support.

Use of `REDEFINE DATA ... REMOTE_LANGUAGE` or `LOCAL_LANGUAGE` on `PIC X` items is also supported. Thus a TIP can perform DBCS or MBCS conversions for specified `PIC X` data fields, in addition to SBCS conversions by default for the remaining `PIC X` data fields. Default SBCS conversion is according to the `DEFINE TRANSACTION... NLS_LANGUAGE` and local Oracle default `LANGUAGE` environment values.

When PGAU is generating a TIP, the `PIC G` datatypes are converted to PL/SQL `VARCHAR2` datatypes. After conversion by the TIP, received `'PIC G' VARCHAR2` datatypes can have a length less then the maximum due to deletion of shift-out and shift-in meta characters, and sent `'PIC G' `RAWs will have the shift-out and shift-in characters inserted as required by the remote host character set specified.

This is different from the conversions performed for `PIC X` data which is always a known fixed-length and hence `CHAR` datatypes are used in TIPs for `PIC X` data fields. However, even when the `PIC X` field contains DBCS or MBCS data, a `CHAR` variable is still used and padded with blanks if needed.

Some remote host applications bracket a` PIC G` field with `PIC X` bytes used for shift-out, shift-in meta-character insertion. Such a COBOL definition might look like:

    01 MY_RECORD.
       05 SO PIC X.
       05 MY_SBCS_DATA PIC G(52).
       05 SI PIC X.

This is not processed correctly by PGAU, because all three fields are defined, and consequently treated, as separate data items when conversion is performed.

To be properly processed, the definition input to PGAU should be:

    01 MY_RECORD.
       05 MY_MBCS_DATA PIC G(51).

The PGAU `REDEFINE DATA` statement can redefine the 3-field definition to the 1-field definition by specifying `USAGE(SKIP)` on fields `SO` and `SI`, and `'05 MY_MBCS_DATA PIC G(51).'` to redefine `MY_MBCS_DATA`. The three `REDEFINE` statements can be placed in the PGAU input control file, and thus the remote host definition need not be altered.

### Modifying a Terminal-Oriented Transaction to Use APPC

The remote transaction program must include mapped APPC verbs to initiate, communicate, and terminate the APPC conversation. However, when the remote transaction program is terminal-oriented, the following options are available:

- You can separate the terminal logic from the application and I/O logic. Once this separation is achieved, a small front end remote transaction program can be written to interface between the gateway calls and the transaction application logic. For example, in CICS the CICS `LINK` is used to implement this technique.

- You can modify your existing program so that APPC calls are embedded. In the example, `PGADB2I`, we use CICS and its associated mapped APPC verbs as follows:

  - EXEC CICS `ASSIGN` accepts the conversation initiated by the gateway.

  - EXEC CICS `RECEIVE` receives the arguments.

  - EXEC CICS `SEND` ends the results.

  - EXEC CICS `RETURN` terminates the conversation.

- If you do not want to modify your terminal-oriented transaction, you can insert an APPC-capable interface, such as IBM Corporation's FEPI for CICS Transaction Server for z/OS, between the terminal-oriented program and the gateway.

- With IMS/TM, existing unmodified IMS transactions can be accessed with the gateway using the implicit APPC facility. With implicit APPC, the standard DLI GU, GN, and ISRT calls using the I/O PCB are automatically converted to appropriate APPC send or receive calls when the IMS transaction is invoked through APPC.

### Privileges Needed to Use TIPs

Execute privileges must be explicitly granted to callers of TIPs or procedures. This privilege cannot be granted through a role.

Any TIP user wanting to trace a TIP must be granted execute privileges on the rtrace and ptrace procedures. Refer to the "Configuring PGAU" section in the chapter appropriate for your communications protocol in the installation guides for more information.

For example, on Microsoft Windows:

    C:\> sqlplus pgaadmin\pw@database_specification_string
    SQL> grant execute on pgaadmin.purge_trace to tip_user_userid;
    SQL> grant execute on pgaadmin.read_trace to tip_user_userid;

On UNIX based systems:

    $ sqlplus pgaadmin/pw@database_specification_string
    SQL> grant execute on pgaadmin.purge_trace to tip_user_userid;
    SQL> grant execute on pgaadmin.read_trace to tip_user_userid;

After a TIP has been developed, the TIP user must be granted execute privileges on the TIP by the TIP owner. The TIP owner is usually `PGAADMIN`, but can be another user who has been granted either the `PGDDDEF` or `PGDDGEN` roles.

For example, on Microsoft Windows:

    C:\> sqlplus tip_owner\pw@database_specification_string
    SQL> grant execute on tipname to tip_user_userid;

On UNIX based systems:

    $ sqlplus tip_owner/pw@database_specification_string
    SQL> grant execute on tipname to tip_user_userid;

where` database_specification_string` is the Oracle Net identifier for the Oracle database where the gateway `UTL_RAW` and `UTL_PG` components were installed. This is the same Oracle database where the TIPs are executed and where grants on the TIPs are performed from the TIP owner user ID.

A SQL script for performing these grants is provided in the `%ORACLE_HOME%\dg4appc\admin` directory on Microsoft Windows and in the `$ORACLE_HOME/dg4appc/admin` directory on UNIX based system. The `pgddausr.sql` script performs the grants for private access to the packages by a single TIP user. If private grants are to be used, the `pgddausr.sql` script must be run once for each TIP user's user ID.

To run these scripts, use SQL\*Plus to connect to the Oracle database as user `PGAADMIN`. From SQL\*Plus, run the `pgddausr.sql` script from the `%ORACLE_HOME%\dg4appc\admin` directory on Microsoft Windows or `$ORACLE_HOME/dg4appc/admin` directory on UNIX based system. The script performs the necessary grants as previously described. You are prompted for the required user IDs, passwords, and database specification strings. If you are using private grants, repeat this step for each user ID requiring access to the packages.

No script has been provided to perform public grants. To do this, issue the following commands:

For Microsoft Windows:

    C:\> sqlplus tip_owner\pw@database_specification_string
    SQL> grant execute on tipname to PUBLIC;

For UNIX based systems:

    $ sqlplus tip_owner/pw@database_specification_string
    SQL> grant execute on tipname to PUBLIC;
