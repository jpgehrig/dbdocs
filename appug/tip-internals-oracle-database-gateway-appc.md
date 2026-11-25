PGAU generates complete and operational TIPs for most circumstances. TIP internals information is provided to assist you in diagnosing problems with PGAU-generated TIPs, and in writing custom TIPs, if you choose to do so.

- If your gateway is using the SNA communication protocol:

  This appendix refers to a sample called `pgadb2i`. The source for this TIP is in file `pgadb2i.sql` in the `%ORACLE_HOME%\dg4appc\demo\CICS` directory for Microsoft Windows and `$ORACLE_HOME/dg4appc/demo/CICS` directory for UNIX based systems.

- If your gateway is using the TCP/IP communication protocol:

  This appendix refers to a sample called `pgaims`. The source for this TIP is in file `pgtflipd.sql` in the `%ORACLE_HOME%\dg4appc\demo\IMS` directory for Microsoft Windows and `$ORACLE_HOME/dg4appc/demo/IMS` directory on UNIX based systems.

Toipics:

- Background Reading

- PL/SQL Package and TIP File Separation

### Background Reading

Several topics are important to understanding TIP operation and development; following is a list of concepts that are key to TIP operation and suggested sources to which you can refer for more information.

- For information about PL/SQL Packages, refer to the [Oracle Database PL/SQL Packages and Types Reference](../arpls/index.md).

- For information about PGA Application Concepts, refer to the following chapters in this guide:

- If your communication protocol is SNA: refer to [Client Application Development (SNA Only)](developing-appc-client-app-sna-only.md);

- If your communication protocol is TCP/IP: refer to [Client Application Development (TCP/IP Only)](developing-appc-client-app-tcpip-only.md).

- For information about PGA RPC Interface, refer to [Gateway RPC Interface](oracle-database-gateway-appc-rpc-interface.md).

- For information about PGA `UTL_PG` Interface, refer to [The UTL_PG Interface](oracle-database-gateway-appc-utl_pg-interface.md).

### PL/SQL Package and TIP File Separation

PGAU `GENERATE` writes each output TIP into a standard PL/SQL package specification file and body file. This separation is beneficial and important. Refer to the [Oracle Database Development Guide ](../adfns/index.md)and the [Oracle Database PL/SQL Language Reference](../lnpls/index.md) for more information. Also refer to "[GENERATE](pga-utility-oracle-database-gateway-appc.md)" in [Procedural Gateway Administration Utility](pga-utility-oracle-database-gateway-appc.md) for more information about building the PL/SQL package.

TIPs are PL/SQL packages. Any time a package specification is recompiled, all objects which depend on that package are invalidated and implicitly recompiled as they are referenced, even if the specification did not change.

Objects which depend on a TIP specification include client applications that call the TIP to interact with remote host transactions.

It might be important to change the TIP body for the following reasons:

- Oracle ships maintenance which affects the TIP body.

- Oracle ships maintenance for the `UTL_RAW` or `UTL_PG` conversion functions upon which the TIP body relies.

  Refer to [The UTL_PG Interface](oracle-database-gateway-appc-utl_pg-interface.md) for more detailed information about these functions.

- If the remote host network or program location parameters have changed. Refer to "[DEFINE TRANSACTION](pga-utility-oracle-database-gateway-appc.md)" in [Procedural Gateway Administration Utility](pga-utility-oracle-database-gateway-appc.md) for more information

Provided that the TIP specification does not need to change or be recompiled, the TIP body can be regenerated and recompiled to pick up changes without causing invalidation and implicit recompilation of client applications that call the TIP.

It is for this reason that PGAU now separates output TIPs into specification and body files. Refer to "[GENERATE](pga-utility-oracle-database-gateway-appc.md)" in [Procedural Gateway Administration Utility](pga-utility-oracle-database-gateway-appc.md) for a discussion of file identification.

#### Independent TIP Body Changes

Independent TIP body changes are internal and require no change to the TIP specification. Examples of such changes include: a change in `UTL_RAW` or `UTL_PG` conversions, inclusion of diagnostics, or a change to network transaction parameters.

In these cases, when PGAU is used to regenerate the TIP, the new TIP specification file can be saved or discarded, but should not be recompiled. The new TIP body should be recompiled under SQL\*Plus. Provided that the TIP body change is independent, the new body compilation completes without errors and the former TIP specification remains valid.

##### Determine if a Specification Has Remained Valid

To determine if a specification has remained valid, issue the following statements from SQL\*Plus, depending upon your communication protocol:

- If your gateway is using the SNA communication protocol, issue the following:

      SQL>  column ddl_date format A22 heading 'LAST_DDL'
      SQL> select object_name,
        2   object_type,
        3   to_char(last_ddl_time,'MON-DD-YY HH:MM:SS') ddl_date,
        4   status
        5   from all_objects where owner = 'PGAADMIN'
        6   order by object_type, object_name;

      OBJECT_NAME  OBJECT_TYPE   LAST_DDL                 STATUS
      -----------  -----------   --------------------     ---------
      PGADB2I      PACKAGE       NOV-24-1999 09:09:13     VALID
      PGADB2I      PACKAGE BODY  NOV-24-1999 09:11:44     VALID
      DB2IDRIV     PROCEDURE     DEC-30-1999 12:12:14     VALID
      DB2IDRVM     PROCEDURE     DEC-30-1999 12:12:53     VALID
      DB2IFORM     PROCEDURE     DEC-14-1999 11:12:24     VALID

  The `LAST_DDL` column is the date and time at which the last DDL change against the object was done. It shows that the order of compilation was:

      PGADB2I PACKAGE (the specification)
      DB2IDRVM PROCEDURE (1st client application depending on PGADB2I)
      DB2IFORM PROCEDURE (2nd client application depending on PGADB2I)
      DB2IDRIV PROCEDURE (3rd client application depending on PGADB2I)
      PGADB2I PACKAGE BODY (a recompilation of the body)

  Note that the recompilation of the body does not invalidate its dependent object, the specification, or the client application indirectly.

- If your gateway is using the TCP/IP communication protocol, issue the following fro SQL\*Plus:

      SQL>  column ddl_date format A22 heading 'LAST_DDL'
      SQL> select object_name,
        2   object_type,
        3   to_char(last_ddl_time,'MON-DD-YY HH:MM:SS') ddl_date,
        4   status
        5   from all_objects where owner = 'PGAADMIN'
        6   order by object_type, object_name;

      OBJECT_NAME  OBJECT_TYPE   LAST_DDL                 STATUS
      -----------  -----------   --------------------     ---------
      PGTFLIP      PACKAGE       APR-24-03 03:04:58       VALID
      PGTFLIP      PACKAGE BODY  APR-24-03 03:04:02       VALID
      PGTFLIPD     PROCEDURE     APR-24-03 03:04:09       VALID

  The `LAST_DDL` column is the date and time at which the last DDL change against the object was done. It shows that the order of compilation was:

      PGTFLIP PACKAGE (the specification)
      PGTFLIPD PROCEDURE (client application depending on PGADB2I)
      PGTFLIP PACKAGE BODY (a recompilation of the body)

Note that the recompilation of the body does not invalidate its dependent object, the specification, or the client application indirectly.

#### Dependent TIP Body or Specification Changes

You can also change the data structures or call exchange sequences of the remote host transaction. However, this kind of change is exposed to dependent client applications because the public datatypes or functions in the TIP specification will also change and necessitate recompilation, which in turn causes the Oracle database to recompile such dependent client applications.

- If your gateway is using the SNA communication protocol, issue the following:

      SQL> column ddl_date format A22 heading 'LAST_DDL'
      SQL> select object_name,
        2   object_type,
        3   to_char(LAST_DDL_TIME,'MON-DD-YY HH:MM:SS') ddl_date,
        4   status
        5   from all_objects where owner = 'PGAADMIN'
        6   order by object_type, object_name;

      OBJECT_NAME    OBJECT_TYPE      LAST_DDL                 STATUS
      ----------     -----------      ---------------------    ---------
      PGADB2I        PACKAGE          NOV-24-1999 09:09:13     VALID
      PGADB2I        PACKAGE BODY     NOV-24-1999 09:11:44     INVALID
      DB2IDRIV       PROCEDURE        DEC-30-1999 12:12:14     INVALID
      DB2IDRVM       PROCEDURE        DEC-30-1999 12:12:53     INVALID
      DB2IFORM       PROCEDURE        DEC-14-1999 11:12:24     INVALID

- If your gateway is using the TCP/IP communication protocol, issue the following:

      SQL> column ddl_date format A22 heading 'LAST_DDL'
      SQL> select object_name,
        2   object_type,
        3   to_char(LAST_DDL_TIME,'MON-DD-YY HH:MM:SS') ddl_date,
        4   status
        5   from all_objects where owner = 'PGAADMIN'
        6   order by object_type, object_name;

      OBJECT_NAME    OBJECT_TYPE      LAST_DDL                 STATUS
      ----------     -----------      ---------------------    ---------
      PGTFLIP        PACKAGE          APR-24-03 03:04:58       VALID
      PGTFLIP        PACKAGE BODY     APR-24-03 05:03:52       INVALID
      PGTFLIP        PROCEDURE        APR-24-03 05:04:29       INVALID


##### Recompile the TIP Body

Note that the recompilation of the specification has invalidated its dependent objects, the three client applications in addition to the package body. To complete these changes, the body must be recompiled to bring it into compliance with the specification and then the three client applications could be compiled manually, or the Oracle database compiles them automatically as they are referenced.

If the client applications are recompiled by the Oracle database as they are referenced, there is a one-time delay during recompilation.

Recompilation errors in the client application, if any, are due to:

- customer changes in the client application source

- an altered PG DD definition for the TIP if the TIP has been regenerated

- the wrong version being generated from multiple transaction entry versions saved in the PG DD if the TIP has been regenerated

#### Inadvertent Alteration of TIP Specification

If you make a mistake when you generate a tip (for example, if you alter a PG DD transaction definition, or if you have inadvertently specified the wrong version during regeneration), then the recompiled body will not match the stored specification; as a result, the Oracle database would invalidate the specification and any dependent client applications.

You may have to regenerate and recompile the TIP and its dependent client applications to restore correct operation.
