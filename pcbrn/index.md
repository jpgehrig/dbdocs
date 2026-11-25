## About these Release Notes

This document contains important information about Pro\*COBOL release 19c.

It contains the following topics:

- Documentation Accessibility

- New Features in Pro\*COBOL Release 19c

- New Features in Previous Releases

- Bugs Fixed

- Support

## Documentation Accessibility

For information about Oracle's commitment to accessibility, visit the Oracle Accessibility Program website at [`http://www.oracle.com/pls/topic/lookup?ctx=acc&id=docacc`](http://www.oracle.com/pls/topic/lookup?ctx=acc&id=docacc).

### Access to Oracle Support

Oracle customers have access to electronic support through My Oracle Support. For information, visit [`http://www.oracle.com/pls/topic/lookup?ctx=acc&id=info`](http://www.oracle.com/pls/topic/lookup?ctx=acc&id=info) or visit [`http://www.oracle.com/pls/topic/lookup?ctx=acc&id=trs`](http://www.oracle.com/pls/topic/lookup?ctx=acc&id=trs) if you are hearing impaired.

## New Features in Pro\*COBOL Release 19c

Micro Focus Visual COBOL v6.0 compiler supports the following platforms:

- Linux x86 (32-bit and 64-bit) on OL8 & SLES15
- Windows x86 (32-bit and 64-bit)
- HPUX on Itanium (32-bit and 64-bit)
- Solaris SPARC (32-bit and 64-bit)
- IBM AIX (32-bit and 64-bit)
- Linux for IBM System z (31-bit and 64-bit)

## New Features in Previous Releases

This section lists new features introduced to Pro\*COBOL in previous releases.

### Features in Pro\*COBOL Release 18c, Version 18.1

The following feature is new in this release:

- Support for Oracle Connection Manager in Traffic Director Mode

  Oracle Connection Manager in Traffic Director Mode is a proxy that is placed between supported database clients and database instances for improved high availability, connection multiplexing, and load balancing.

### Features in Pro\*COBOL 12.2 Production

- Support for long identifiers (object lengths of 128 bytes). In previous releases, the object length limit was 30 bytes.

- Support for Oracle Instant Client - Basic Light version.

- New command line option, `trim_password`, to prevent authentication issues caused by password strings that contain trailing blank space.

- Support for Micro Focus Visual COBOL 2.2 Update 2 compiler for the following platforms:

  - Linux x64

  - Windows 64-bit and 32-bit

  - Solaris x86 (32-bit and 64-bit)

  - Solaris SPARC (32-bit and 64-bit)

### Features in Pro\*COBOL 12.1 Production

- Support for Auto Increment Columns

- Support for 32k Columns

- Support for Prefetch By Memory

- Support for SQL Plan Management (SPM)

## Bugs Fixed

The following section lists bugs fixed in Pro\*COBOL. Numbers in parentheses following the description refer to bug numbers in the Oracle Bug Database.

### Bugs Fixed in Pro\*COBOL Release 12.2 Production

- Pro\*COBOL no longer throws CSF-S-00000 error when common_parser=yes in the timezone.pc file (9531787)

- Pro\*COBOL no longer throws ORA-01008 error when binds are used in the Select list while common_parser=yes (14127422)

- Pro\*COBOL no longer throws ORA-932 error when precompiling with option USERID and common_parser=yes for an INSERT statement which has CASE clause and TIMESTAMP function (14335958, 19473788)

- Pro\*COBOL no longer throws PCB-S-00576, PLS-103 error while precompiling with embedded PL/SQL using the select /\*+ index hint \*/ statement (953338)

- Pro\*COBOL no longer fails to set SQLSTATE during rollback, with MODE=ANSI and without declaring SQLCODE (5891984)

- Pro\*COBOL no longer fails to generate a proper log file (17280039)

- Pro\*COBOL no longer throws PCB-S-00400 error while precompiling a program with a Level 88 initialised variable (20194289)

- Pro\*COBOL no longer gets SIGSEGV for duplicate host variables when precompiling with common_parser=yes (19473788)

- Pro\*COBOL no longer throws PCB-S-00576 error while precompiling a program with common_parser=yes (18800170)

- Pro\*COBOL now checks for a fatal error during precompilation before deleting log and sql files (17871321)

- Pro\*COBOL no longer throws ORA-538976288 error when using a "SELECT INTO" statement for PIC N variable (17189633)

- Pro\*COBOL no longer creates a .sql file containing "plan_run=yes" when precompilation fails (16240153)

- Pro\*COBOL no longer creates over 72 columns when a variable is modified by varying with comp5=yes (14708769)

- SQLGLS calls in Pro\*COBOL now work as expected (14640230)

- Pro\*COBOL no longer returns PCB-S-00400 error during precompilation when a variable identifier follows a COPY statement (14113014)

- Pro\*COBOL no longer returns PCB-S-00400 error when a COPY modifier is used (13478294)

- Pro\*COBOL no longer generates a UNIX Return Code of 0 when precompilation fails (10083052)

- Pro\*COBOL no longer generates .cob files after errors are encountered (9303962)

### Bugs Fixed in Pro\*COBOL Release 12.1

- Pro\*COBOL no longer crashes while parsing long token/ SQL statement (13006848)

- Pro\*COBOL no longer returns PCB-S-400 when precompiling SQL that includes an inline view written as embedded SQL (EXEC SQL), in-spite of using common_parser=yes (12641413)

- Pro\*COBOL no longer throws PCB-0400 error when using numeric as first character of a group element (10265545)

- Pro\*COBOL on Windows no longer crashes when option comp1=integer is set (10040552)

- Pro\*COBOL no longer returns ORA-6502 with PL/SQL bind (9905110)

- Pro\*COBOL no longer crashes when a large source file contains a large number of host variables (9689604)

- Pro\*COBOL now parses statements with a double dot after a COBOL COPY clause after installing patch 9218271 (9470397)

- Pro\*COBOL no longer generates illegal values when a statement is declared at a remote DB and then prepared by passing a string instead of bind-var) (9402996)

- Pro\*COBOL non longer fails with ORA-12899 when max_rows_insert is set (9381997)

- Pro\*COBOL non longer returns PCB-S-00214 when JUSTFIED clause is used with host variables (9266470)

- Pro\*COBOL no longer returns PCB-S-400 error if SCREEN SECTION is used (9151190)

- Pro\*COBOL no longer returns PCB-W-233 when host variable was used for AT clause (9147830)

- Pro\*COBOL no longer returns PCB-S-400 when COPY is used in OCCURS clause of an array declaration (9128157)

- Pro\*COBOL no longer returns PCB-S-400 when a COPY statement ends with double dots (9055457)

- Pro\*COBOL now correctly translates SQL statements which contain a list of lists (8932394)

- Pro\*COBOL no longer returns ORA-933 when cursors are declared with outline enabled (8770900)

- Pro\*COBOL no longer returns PCB-S-00400 when an EXE SQL INCLUDE statement is used without an ending period in DATA SECTION (8713408)

## Support

For Pro\*COBOL support, contact your local Oracle Support Services Center.

------------------------------------------------------------------------

Title and Copyright Information

Pro\*COBOL Release Notes, 19c

E96464-02

June 2021

[Copyright © ](./sp_common/en/cpyr.md)1996, 2021, Oracle and/or its affiliates.
