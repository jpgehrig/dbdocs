This following sections show in detail how you can define, generate and compile a Transaction Interface Package (TIP). It assumes that a remote host transaction program (RTP) already exists. This transaction program has operational characteristics that dictate how the TIP is defined and how the TIP is used by the client application.

- Granting Privileges for TIP Creators

- Evaluating the RHT

- Defining and Generating the TIP

- Compiling the TIP

- TIP Content Documentation (tipname.doc)

The following steps create a TIP for use with a remote host transaction (RHT):

- evaluating the RHT

- preparing the PGAU statements

- defining and generating the TIP

- compiling the TIP

### Granting Privileges for TIP Creators

Every TIP developer requires access to the following PL/SQL packages, which are shipped with the Oracle database:

For Microsoft Windows:

- `DBMS_PIPE` in `%ORACLE_HOME%\rdbms\admin`

- `UTL_RAW` in `%ORACLE_HOME%\rdbms\admin`

- `UTL_PG` in `%ORACLE_HOME%\rdbms\admin`

For UNIX based systems:

- `DBMS_PIPE` in `$ORACLE_HOME/rdbms/admin`

- `UTL_RAW` in `$ORACLE_HOME/rdbms/admin`

- `UTL_PG` in `$ORACLE_HOME/rdbms/admin`

If anyone other than user `PGAADMIN` will be developing TIPs, they will need explicit grants to perform these operations. Refer to the "Optional Configuration Steps" section in the configuration section appropriate to your communication protocol in the installation guides for more information about private and public grants.

### Evaluating the RHT

Follow the steps below to identify and become familiar with your remote host transaction data exchanges.

1.  Identify the Remote Host Transaction
2.  PGAU DEFINE CALL Command
3.  PGAU DEFINE DATA Command
4.  PGAU DEFINE TRANSACTION Command on a Gateway Using SNA
5.  PGAU DEFINE TRANSACTION Command on a Gateway Using TCP/IP
6.  Writing the PGAU Statements
7.  Writing a PGAU Script File

#### Identify the Remote Host Transaction

You must first identify the RHT data exchange steps. These are the send and receive calls embedded within the RHT program.

##### If your gateway is using the SNA communication protocol:

The RHT data exchange steps are identified under the following languages:

- You may use COBOL for:

  - CICS

  - IMS

- You may use IBM 370 Assembler for:

  - CICS

  - IMS

- You may use IBM REXX for:

  - CICS

  - IMS

  - z/OS

##### If your gateway is using the TCP/IP communication protocol:

IMS is the only OLTP that is supported when the gateway is using TCP/IP support for IMS Connect. The RHT programs must use embedded I/O PCB function calls. The function is identified only under the COBOL and Assembler languages.

#### PGAU DEFINE CALL Command

Make a call list of every data exchange. This list dictates a series of PGAU `DEFINE CALL` statements. Refer to "[DEFINE CALL](pga-utility-oracle-database-gateway-appc.md)" in [Procedural Gateway Administration Utility](pga-utility-oracle-database-gateway-appc.md) for more information about this PGAU command.

The three important parameters that you will use for each call are:

- `cname`: the name of the call definition to be created;

- `dname`: the name of the data structure to be exchanged; and

- whether it is send (`OUT`) or receive (`IN`)

RHT send corresponds to a TIP `OUT` and RHT receive corresponds to a TIP `IN`.

If your communication protocol is SNA: Refer to [Flexible Call Sequence](developing-appc-client-app-sna-only.md) for more information about PGAU `DEFINE CALL` commands.

If your communication protocol is TCP/IP: Refer to [Flexible Call Sequence](developing-appc-client-app-tcpip-only.md) for more information about PGAU `DEFINE CALL` commands.

PGAU call entries are only defined once, so eliminate any duplicates.

This call list defines the TIP function calls, not the order in which they are used. Note that the order in which each call is made is a behavior of the transaction and dictates the order of calls made by the high-level application to the TIP, which then calls the RHT through the Database Gateway server. While this calling sequence is critical to maintaining the synchronization between the application and the RHT, the TIP is only an access method for the application and has no knowledge of higher level sequencing of calls.

#### PGAU DEFINE DATA Command

For each call in the RHT call list, identify the RHT data structures being sent or received in the call buffers.

Make a data list of every such structure. This list dictates a series of PGAU `DEFINE DATA` statements.

The two important parameters that you will use for `DEFINE DATA` are:

- `dname:` the name of the data definition to be created; and

- `dname.ext:` the file in which the data definition is stored.

PGAU data entries are only defined once, so eliminate any duplicates.

**Note:**

Move COBOL record layouts (copybooks) to the gateway system.

PGAU can use copybooks as input when defining the data items. Once you have identified the data items to be exchanged, use a file transfer program to download the copybooks to the gateway system. The copybooks are later used to define the data items. The sample copybook used in the example is documented in [Administration Utility Samples](admin-utility-samples-oracle-database-gateway-appc.md).

#### PGAU DEFINE TRANSACTION Command on a Gateway Using SNA

Determine the network address information for the RHT program. Your network or OLTP system programmer can provide you with this information.

The five important parameters that you will use for PGAU `DEFINE TRANSACTION` are:

- `Side Profile name`

- `TP name`

- `LU name`

- `LOGMODE`

- `SYNCLEVEL`

You must also identify the Globalization Support character set (`charset`) for the language in which the OLTP expects the data.

At this point, if your gateway is using SNA, then proceed to Writing the PGAU Statements.

#### PGAU DEFINE TRANSACTION Command on a Gateway Using TCP/IP

Before you use this command, you will need to know the IMS Connect hostname (or TCP/IP address), port number and the other IMS Connect parameters that are defined as columns within the `PGA_TCP_IMSC` table. Refer to [PG4TCPMAP Commands (TCP/IP Only)](pg4tcpmap-commands-tcpip.md) for complete information about preparation for mapping parameters to TCP/IP using the `pg4tcpmap` tool.

When you run the `pg4tcpmap` tool you need to specify a unique name (Side Profile Name). That name must be the same name that you are using here to create your TIP.

If you are converting your gateway from the SNA to a TCP/IP communications protocol to invoke IMS transactions, then you need to regenerate the TIPs.

Refer to [Procedural Gateway Administration Utility](pga-utility-oracle-database-gateway-appc.md) for details.

#### Writing the PGAU Statements

After evaluating the RHT, define the TIP to PGAU for placement in the PG DD.

1.  Write a `DEFINE DATA` statement for each entry in your data list. If, for example, your RHT had three different data structures, your data definitions might be:

        DEFINE DATA dname1 LANGUAGE(IBMVSCOBOLII) INFILE(dnamel.ext);
        DEFINE DATA dname2 LANGUAGE(IBMVSCOBOLII) INFILE(dname2.ext);
        DEFINE DATA dname3 LANGUAGE(IBMVSCOBOLII) INFILE(dname3.ext);

    Then you must copy or transfer the source file containing these data definitions to the directory where PGAU can read them as input.

2.  Write a `DEFINE CALL` statement for each entry in your call list. If, for example, your RHT had a receive send receive send sequence, your call definitions would be:

        DEFINE CALL cname1 PARMS((dnamel IN));
        DEFINE CALL cname2 PARMS((dname2 OUT));
        DEFINE CALL cname3 PARMS((dname3 IN));
        DEFINE CALL cname4 PARMS((dname2 OUT));

    **Note:**

    Optionally, you can rewrite your call definitions to consolidate the data transmission into fewer exchanges, as long as you do not alter the data transmission sequence. For example:

    `DEFINE CALL cname1 PARMS((dname1 IN),`

    ` (dname2 OUT));`

    `DEFINE CALL cname3 PARMS((dname3 IN),`

    ` (dname2 OUT));`

    This reduces the calls between the application and the TIP from four calls to two calls passing an `IN` and `OUT` parameter on each call. Because TIPs always process `IN` parameters before `OUT` parameters, the data transmission sequence is unchanged. However, this consolidation is not always possible.

    If your communication protocol is SNA: Refer to [Flexible Call Sequence](developing-appc-client-app-sna-only.md) for more information about PGAU `DEFINE CALL` commands.

    If your communication protocol is TCP/IP: Refer to [Flexible Call Sequence](developing-appc-client-app-tcpip-only.md) for more information about PGAU `DEFINE CALL` commands.

3.  Write a `DEFINE TRANSACTION `statement that contains every call, specifying the network address and Globalization Support information:

        DEFINE TRANSACTION tname CALLS(cname1
                                       cname2, ....
                                       cnameN)
                           ENVIRONMENT(IBM370)
                           SIDEPROF(profname) |
                             TPNAME(tpid) LUNAME(luname) LOGMODE(mode)
                           SYNCLEVEL(n)
                           NLS_LANGUAGE(charset);

4.  You can add a `GENERATE` statement to create the TIP specification:

        GENERATE tname

    **Note:**

    You can also add a `REPORT` statement to list the PG DD entries for `tname`:

    `REPORT TRANSACTION tname with CALLS with DATA;`

    Also annotate the script with Comments:

    `REM this is a Comment`

#### Writing a PGAU Script File

The previous section describes the steps you need to follow in order to execute PGAU statements via your PGAU command line processor. As a time saving measure, you can choose to write all of the statements (`DEFINE DATA`, `DEFINE CALL` and `DEFINE TRANSACTION`) into a single PGAU script file named `tname.ctl`, in the following order:

1.  define data

2.  define call

3.  define transaction

4.  generate

    **Note:**

    Because you will probably run this script more than once, you should include `UNDEFINE` statements first to remove any previous entries in the PG DD.

This is an example of a `tname.ctl `PGAU script file:

    UNDEFINE TRANSACTION tname Version(all);
    UNDEFINE CALL cname1 Version(all);
    UNDEFINE CALL cname2 Version(all);
    UNDEFINE DATA dname1 Version(all);
    UNDEFINE DATA dname2 Version(all);
    UNDEFINE DATA dname3 Version(all);
    DEFINE DATA dname1 LANGUAGE(IBMVSCOBOLII) INFILE(dnamel.ext);
    DEFINE DATA dname2 LANGUAGE(IBMVSCOBOLII) INFILE(dname2.ext);
    DEFINE DATA dname3 LANGUAGE(IBMVSCOBOLII) INFILE(dname3.ext);
    DEFINE CALL cname1 PARMS(dname1 IN),
                              (dname2 OUT));
    DEFINE CALL cname2 PARMS(dname3 IN),
                             (dname2 OUT));
    DEFINE TRANSACTION tname CALLS(cname1,
                                  cname2, ....
                                  cnameN)
                       ENVIRONMENT(IBM370)
                       SIDEPROF(profname) |
                         TPNAME(tpid) LUNAME(luname) LOGMODE(mode)
                       SYNCLEVEL(n)
                       NLS_LANGUAGE(charset);
    Generate tname

### Defining and Generating the TIP

After you have created your control file, use PGAU to create the PG DD entries and the TIP specification files.

**Note:**

The user ID under which you run PGAU must have:

- write access to output the specification files (`pgau.pkh, pgau.pkb`, and `pgau.doc`), where `pgau` is the default name; and

- read access to the data definition source files (`dname.ext`), where `dname.ext` will be specified in PGAU `DEFINE DATA` statement(s).

Invoke PGAU against your PG DD stored in the Oracle Database Gateway for APPC Administrator's user ID:

For Microsoft Windows:

    C:\> pgau
    PGAU> connect pgaadmin\pw@database_specification_string

For UNIX based systems:

    $ pgau
    PGAU> connect pgaadmin/pw@database_specification_string

Issue the following commands:

    PGAU> set echo on
    PGAU> spool tname.def
    PGAU> @tname.ctl
    PGAU> spool off

The TIP is now ready to be compiled. By default, the `GENERATE` statement writes your TIP specifications to the following output files in your current directory:

    pgau.pkh (TIP Header)
    pgau.pkb (TIP Body)
    pgau.doc (TIP content documentation)

**Note:**

You can optionally add spool and echo to your script (`tname.ctl`) or make other enhancements, such as using PG DD roles and the PGAU `GROUP` statement for shared PG DDs.

- If your gateway is using SNA: Refer to [Client Application Development (SNA Only)](developing-appc-client-app-sna-only.md) for more information.

- If your gateway is using TCP/IP support for IMS Connect: Refer to [Client Application Development (TCP/IP Only)](developing-appc-client-app-tcpip-only.md) for more information.

### Compiling the TIP

Exit PGAU. Remain in your current directory and invoke SQL\*Plus.

For Microsoft Windows:

    C:\> sqlplus userid/pw@database_specification_string
    SQL> set echo on
    SQL> @pgau.pkh
    SQL> @pgau.pkb

For UNIX based systems:

    $ sqlplus userid/pw@database_specification_string
    SQL> set echo on
    SQL> @pgau.pkh
    SQL> @pgau.pkb

The last two commands compile the TIP specification and body, respectively.

You have now compiled a TIP which can be called by your client application. If your client application is already written you can begin testing.

For more information about designing your client application and compiling a TIP, refer to [Introduction to Oracle Database Gateway for APPC](oracle-database-gateway-appc-introduction.md) and [Tip Internals](tip-internals-oracle-database-gateway-appc.md).

If your gateway is using SNA: Refer to [Client Application Development (SNA Only)](developing-appc-client-app-sna-only.md) for information about PGAU statement syntax and usage.

If your gateway is using TCP/IP support for IMS Connect: Refer to [Client Application Development (TCP/IP Only)](developing-appc-client-app-tcpip-only.md) for information about PGAU statement syntax and usage.

### TIP Content Documentation (tipname.doc)

This section discusses the TIP documentation file that is produced when the user issues a PGAU `GENERATE` command. This TIP content file describes the function calls and PL/`SQL` variables and datatypes available in the TIP.

PGAU `GENERATE` always produces a TIP content file named `tipname``.doc`. The filename is the name of the transaction that was specified in the PGAU `GENERATE` command, and the filetype is always `.doc`. This TIP content file contains the following sections:

- `GENERATION` Status

  This section contains the status under which the TIP is generated.

- TIP Transaction

  This section identifies the defined transaction attributes. These result from the `PGAU DEFINE TRANSACTION` definition.

- TIP Default Calls

  This section identifies the syntax of the calls made by the user's application to initialize and terminate the transaction. PGAU generates these calls into every TIP regardless of how the TIP or transaction is defined.

- TIP User Calls

  This section identifies the syntax of the calls which the user defines for the application to interact with the transaction.

- TIP User Declarations

  This section identifies the TIP package public datatype declarations, implied by the user's data definition specified in each call parameter.

- TIP User Variables

  This section contains TIP variables that can be referred to by applications or referenced by applications.
