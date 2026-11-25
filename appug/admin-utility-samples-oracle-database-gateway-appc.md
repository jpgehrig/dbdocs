Use the following sample input statements and report output for the Procedural Gateway Administration Utility to guide you in designing your own PGAU statements.

Sample PGAU statements:

- Sample PGAU DEFINE DATA Statements

- Sample PGAU DEFINE CALL Statements

- Sample PGAU DEFINE TRANSACTION Statement

- Sample PGAU GENERATE Statement

- Sample Implicit Versioning Definitions

- Sample PGAU REDEFINE DATA Statements

- Sample PGAU UNDEFINE Statements

### Sample PGAU DEFINE DATA Statements

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

where the file `emp.cob` contains the following:

    01 DCLEMP.
       10 EMPNO              PIC X(6).
       10 FIRSTNME.
         49 FIRSTNME-LEN     PIC S9(4) USAGE COMP.
         49 FIRSTNME-TEXT    PIC X(12).
       10 MIDINIT            PIC X(1).
       10 LASTNAME.
         49 LASTNAME-LEN     PIC S9(4) USAGE COMP.
         49 LASTNAME-TEXT    PIC X(15).
       10 WORKDEPT           PIC X(3).
       10 PHONENO            PIC X(4).
       10 HIREDATE           PIC X(10).
       10 JOB                PIC X(8).
       10 EDLEVEL            PIC S9(4) USAGE COMP.
       10 SEX                PIC X(1)
       10 BIRTHDATE          PIC X(10).
       10 SALARY             PIC S9999999V99 USAGE COMP-3.
       10 BONUS              PIC S9999999V99 USAGE COMP-3.
       10 COMM               PIC S9999999V99 USAGE COMP-3.

    DEFINE DATA DB2INFO
           PLSDNAME (DB2)
           USAGE (PASS)
           LANGUAGE (IBMVSCOBOLII)
           INFILE("db2.cob");

where the file `db2.cob` contains the following:

    01  DB2.
        05 SQLCODE          PIC S9(9) COMP-4.
        05 SQLERRM.
          49 SQLERRML       PIC S9(4) COMP-4.
          49 SQLERRT        PIC X(70).
        05 DSNERRM.
          49 DSNERRML       PIC S9(4) COMP-4.
          49 DSNERRMT       PIC X(240) OCCURS 8 TIMES
                                           INDEXED BY ERROR-INDEX

### Sample PGAU DEFINE CALL Statements

    DEFINE CALL DB2IMAIN
           PKGCALL (PGADB2I_MAIN)
           PARMS ( (EMPNO      IN ),
                   (EMPREC     OUT)  );
    DEFINE CALL DB2IDIAG
           PKGCALL (PGADB2I_DIAG)
           PARMS ( (DB2INFO    OUT)  );

### Sample PGAU DEFINE TRANSACTION Statement

    DEFINE TRANSACTION DB2I
       CALL (   DB2IMAIN,
                DB2IDIAG   )
       SIDEPROFILE(CICSPROD)
       TPNAME(DB2I)
       LOGMODE(ORAPLU62)
       SYNCLEVEL(0)
       NLS_LANGUAGE("AMERICAN_AMERICA.WE8EBCDIC37C");

### Sample PGAU GENERATE Statement

    GENERATE DB2I
       PKGNAME(PGADB2I)
       OUTFILE("pgadb2i");

A user's high-level application now uses this TIP by referencing these PL/SQL datatypes passed and returned.

Table F-1 provides a description of the TIP user transaction datatypes in package name `PGADB2I`:

Table F-1 TIP User Transaction Datatypes Used in Package Name PGADB2I

| Datatype         | Description                                                  |
|:-----------------|:-------------------------------------------------------------|
| `PGADB2I.EMPNO`  | is a PL/SQL variable corresponding to COBOL `EMPNO`.         |
| `PGADB2I.DCLEMP` | Which is a PL/SQL `RECORD` corresponding to COBOL `DCLEMP`.  |
| `PGADB2I.DB2`    | Which is a PL/SQL `RECORD` corresponding to COBOL `DB2INFO`. |

and the application calls:

    PGADB2I.PGADB2I_INIT(trannum);
    PGADB2I.PGADB2I_MAIN( trannum, empno, emprec );
    PGADB2I.PGADB2I_DIAG( trannum, db2 );
    PGADB2I.PGADB2I_TERM(trannum, termtype);

### Sample Implicit Versioning Definitions

The examples are sample definitions of `DATA`, `CALL`, and `TRANSACTION` entries with implicit versioning.

This example creates a new `DATA` version of '`EMPREC`' because '`EMPREC`' `DATA` was defined previously:

    DEFINE DATA EMPREC
           PLSDNAME (NEWEMP)
           USAGE (PASS)
           LANGUAGE (IBMVSCOBOLII)
           INFILE("emp2.cob");

where the file `emp2.cob` contains the following:

    01 NEWEMP.
        10 EMPNO                   PIC X(6).
        10 FIRSTNME.
          49 FIRSTNME-LEN          PIC S9(4) USAGE COMP.
          49 FIRSTNME-TEXT         PIC X(12).
        10 MIDINIT                 PIC X(1).
        10 LASTNAME.
          49 LASTNAME-LEN          PIC S9(4) USAGE COMP.
          49 LASTNAME-TEXT         PIC X(15).
        10 WORKDEPT                PIC X(3).
        10 PHONENO                 PIC X(3).
        10 HIREDATE                PIC X(10).
        10 JOB                     PIC X(8).
        10 EDLEVEL                 PIC S9(4) USAGE COMP.
        10 SEX                     PIC X(1).
        10 BIRTHDATE               PIC X(10).
        10 SALARY                  PIC S9999999V99 USAGE COMP-3.
        10 BONUS                   PIC S9999999V99 USAGE COMP-3.
        10 COMM                    PIC S9999999V99 USAGE COMP-3.
        10 YTD.
          15 SAL                   PIC S9(9)V99 USAGE COMP-3.
          15 BON                   PIC S9(9)V99 USAGE COMP-3.
          15 COM                   PIC S9(9)V99 USAGE COMP-3.

To determine which `DATA` version number was assigned, this SQL query can be issued:

    SELECT MAX(pd.version)
           FROM pga_data pd
           WHERE pd.dname = 'EMPREC';

To determine additional information related to the updated version of '`EMPREC`' this query can be used:

    SELECT *
           FROM pga_data pd
           WHERE pd.dname = 'EMPREC';

This example creates a new `CALL` version of '`DB2IMAIN`' because the '`DB2IMAIN`' `CALL` was defined previously:

    DEFINE CALL DB2IMAIN
           PKGCALL (PGADB2I_MAIN)
           PARMS ( (EMPNO      IN                   ),
                   (EMPREC     OUT   VERSION(ddddd) )  );

where `ddddd` is the version number of the `EMPREC DATA` definition queried after the previous `DEFINE DATA` updated `EMPREC`.

To determine which call version number was assigned, this SQL query can be issued:

    SELECT MAX(pc.version)
           FROM pga_call pc
           WHERE pc.cname = 'DB2IMAIN';

To determine additional information related to the updated version of '`DB2IMAIN`' this query can be used:

     SELECT *
            FROM pga_call pc
            WHERE pc.cname = 'DB2IMAIN';

The `DEFINE TRANSACTION` example creates a new `TRANSACTION` version of '`DB2I`' because the `'DB2I' TRANSACTION` was defined previously. The essential difference of the new version of the DB2I transaction is that the first call uses a new PL/SQL record format "`NEWEMP`" (which corresponds to the COBOL `NEWEMP` format) to query the employee data.

**Note:**

Record format changes like that discussed above must be synchronized with the requirements of the remote transaction program. Changes to the PGA TIP alone result in errors. A new remote transaction program with the corequisite changes could be running on a separate CICS system and started through the change from "`CICSPROD`" to "`CICSTEST`" in the `SIDEPROFILE` parameter below.

    DEFINE TRANSACTION DB2I
           CALL (  DB2IMAIN   VERSION (ccccc),
                   DB2IDIAG )
           SIDEPROFILE(CICSTEST)
           TPNAME(DB2I)
           LOGMODE(ORAPLU62)
           SYNCLEVEL(0)
           NLS_LANGUAGE("AMERICAN_AMERICA.WE8EBCDIC37C");

where `ccccc` is the version number of the `DB2IMAIN` `CALL` definition queried after the previous `DEFINE CALL` updated `DB2IMAIN`.

There are two versions of the DB2I transaction definition in the PGA DD. The original uses the old "`DCLEMP`" record format and starts transaction "`DB2I`" on the production CICS system. The latest uses the "`NEWEMP`" record format and starts transaction "`DB2I`" on the test CICS system.

To determine which transaction version number was assigned, this SQL query can be issued:

    SELECT MAX(pt.version)
      FROM pga_trans pt
      WHERE pt.tname = 'DB2I';

To determine additional information related to the updated version of '`DB2I`' this query can be used:

    SELECT *
      FROM pga_trans pt
      WHERE pt.tname = 'DB2I';

This example generates a new package using the previously defined new versions of the `TRANSACTION`, `CALL`, and `DATA` definitions:

    GENERATE DB2I
    VERSION(ttttt)
    PKGNAME(NEWDB2I)
    OUTFILE("pgadb2i");

where `ttttt` is the version number of the `DB2I TRANSACTION` definition queried after the previous` DEFINE TRANSACTION` updated `DB2I`.

Note that the previous PL/SQL package files `pgadb2i.pkh` and `pgadb2i.pkb` are overwritten. To keep the new package separate, change the output file specification. For example:

    GENERATE DB2I
    VERSION(ttttt)
    PKGNAME(NEWDB2I)
    OUTFILE("newdb2i");

A user's high-level application now uses this TIP by referencing the PL/SQL datatypes passed and returned.

Table F-2 provides a description of the TIP user transaction datatypes in package name `NEWDB2I`:

Table F-2 TIP User Transaction Datatypes for Package Name NEWDB2I

| Datatype         | Description                                           |
|:-----------------|:------------------------------------------------------|
| `NEWDB2I.EMPNO`  | Is a PL/SQL variable corresponding to COBOL `EMPNO`.  |
| `NEWDB2I.NEWEMP` | Is a PL/SQL `RECORD` corresponding to COBOL `NEWEMP`. |
| `NEWDB2I.DB2`    | Is a PL/SQL `RECORD` corresponding to COBOL `DB2`.    |

and the application calls:

    NEWDB2I.PGADB2I_INIT(trannum);
    NEWDB2I.PGADB2I_MAIN( trannum, empno, newemp );
    NEWDB2I.PGADB2I_DIAG( trannum, db2 );
    NEWDB2I.PGADB2I_TERM(trannum, termtype);

### Sample PGAU REDEFINE DATA Statements

Single-field redefinition in which `EDLEVEL USAGE` becomes `COMP-3`:

    REDEFINE DATA EMPREC
             PLSDNAME(DCLEMP)
             LANGUAGE(IBMVSCOBOLII)
             FIELD(EDLEVEL)
             PLSFNAME(PLSRECTYPE)
           (
           10 EDLEVEL  PIC S9(4) USAGE IS COMP-3.
           );

By default, this redefines the latest version of `EMPREC` which implicitly affects the latest call and transaction definitions which refer to it.

Sample multi-field redefinition in which the employee's first and last name fields are expanded and the employee's middle initial is removed.

    REDEFINE DATA EMPREC
             VERSION(1)
             PLSDNAME(DCLEMP)
             LANGUAGE(IBMVSCOBOLII)
             INFILE("emp1.cob");

where the file `emp1.cob` contains the following:

    01 DCLEMP.
      10 EMPNO                     PIC X(6).
      10 FIRSTNME.
           49 FIRSTNME-LEN         PIC S9(4) USAGE COMP.
           49 FIRSTNME-TEXT        PIC X(15).
      10 LASTNAME.
           49 LASTNAME-LEN         PIC S9(4) USAGE COMP.
           49 LASTNAME-TEXT        PIC X(20).
      10 WORKDEPT                  PIC X(3).
      10 PHONENO                   PIC X(4).
      10 HIREDATE                  PIC X(10).
      10 JOB                       PIC X(8).
      10 EDLEVEL                   PIC S9(4) USAGE COMP.
      10 SEX                       PIC X(1).
      10 BIRTHDATE                 PIC X(10).
      10 SALARY                    PIC S9999999V99 USAGE COMP-3.
      10 BONUS                     PIC S9999999V99 USAGE COMP-3.
      10 COMM                      PIC S9999999V99 USAGE COMP-3.


The assumption is that version 1 of the data definition for '`EMPREC`' is to be redefined. This causes a redefinition of the first '`EMPREC`' sample data definition without changing the version number. Thus, existing call and transaction definitions which referenced version 1 of '`EMPREC`' automatically reflect the changed '`EMPREC`'. This change becomes effective when a TIP is next generated for a transaction that references the call which referenced version 1 of '`EMPREC`'.

This implicitly affects both versions of the transaction because both refer to `EMPREC` in the second call to update the employee data.

### Sample PGAU UNDEFINE Statements

This sample illustrates the deletion of a specific version of a definition which has multiple versions, followed by deletion of all versions of a specific named definition.

    UNDEFINE DATA EMPREC VERSION (ddddd);
    UNDEFINE DATA EMPREC VERSION (ALL);
    UNDEFINE CALL DB2IMAIN VERSION (ccccc);
    UNDEFINE CALL DB2IMAIN VERS (all);
    UNDEFINE TRANSACTION DB2I vers (ttttt);
    UNDEFINE TRANSACTION DB2I vers (all);

Note that the previous `UNDEFINE` statements leave the `DATA` definition for `EMPNO` and the `CALL` definition for `DB2IDIAG` in the PGA DD.
